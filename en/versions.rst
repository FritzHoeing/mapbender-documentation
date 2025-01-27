.. _versions:

Version history
===============

`German Version of this document. <../de/versions.html>`_

You find the milestones at: https://github.com/mapbender/mapbender/milestones


Version 3.2.4
-------------

Release date: 04.03.2021

**Improvements and bugfixes:**

* https://github.com/mapbender/mapbender-starter/blob/master/CHANGELOG.md#v324


Version 3.2.3
-------------

Release date: 21.12.2020

**Improvements and bugfixes:**

* https://github.com/mapbender/mapbender-starter/blob/master/CHANGELOG.md#v323


Version 3.2.2
-------------

Release date: 02.11.2020

**Improvements and bugfixes:**

* https://github.com/mapbender/mapbender-starter/blob/master/CHANGELOG.md#v322


Version 3.2.1
-------------

Release date: 06.08.2020

**Improvements and bugfixes:**

* https://github.com/mapbender/mapbender-starter/blob/master/CHANGELOG.md#v321


Version 3.2.0
-------------

Release date: 29.07.2020

**Improvements and bugfixes:**

* https://github.com/mapbender/mapbender-starter/blob/master/CHANGELOG.md#v320


Version 3.0.8.6
---------------

Release date: 15.09.2020

**Improvements and bugfixes:**

* https://github.com/mapbender/mapbender-starter/blob/master/CHANGELOG.md#v3086 


Version 3.0.8.5
---------------

Release date: 05.02.2020

**Improvements and bugfixes:**

* https://github.com/mapbender/mapbender-starter/blob/master/CHANGELOG.md#v3085


Version 3.0.8.4
---------------

Release date: 04.09.2019

**Improvements and bugfixes:**

* https://github.com/mapbender/mapbender-starter/blob/master/CHANGELOG.md#v3084


Version 3.0.8.3
---------------

Release date: 05.07.2019

**Improvements and bugfixes:**

* https://github.com/mapbender/mapbender-starter/blob/master/CHANGELOG.md#v3083


Version 3.0.8.2.1
-----------------

Release date: 05.07.2019

**Improvements and bugfixes:**

* https://github.com/mapbender/mapbender-starter/blob/master/CHANGELOG.md#v30821


Version 3.0.8.2
---------------

Release date: 03.07.2019

**Improvements and bugfixes:**

* https://github.com/mapbender/mapbender-starter/blob/master/CHANGELOG.md#v3082


Version 3.0.8.1
---------------

Release date: 14.05.2019

**Improvements and bugfixes:**

* https://github.com/mapbender/mapbender-starter/blob/master/CHANGELOG.md#v3081


Version 3.0.8
-------------

Release date: 12.04.2019

**Improvements and bugfixes:**

* https://github.com/mapbender/mapbender-starter/blob/master/CHANGELOG.md#v308

**Upgrading**

https://github.com/mapbender/mapbender/blob/master/UPGRADING.md#308


Version 3.0.7.7
---------------

Release date: 07.11.2018


**Improvements and bugfixes:**

* https://github.com/mapbender/mapbender-starter/blob/master/CHANGELOG.md#v3077


Version 3.0.7.6
---------------

Release date: 18.10.2018


**Improvements and bugfixes:**

* https://github.com/mapbender/mapbender-starter/blob/master/CHANGELOG.md#v3076


Version 3.0.7.5
---------------

Release date: 26.09.2018


**Improvements and bugfixes:**

* Find the description of the fixes in the repository links
* Update Mapbender-Starter `v3.0.7.5 <https://github.com/mapbender/mapbender-starter/releases/tag/v3.0.7.5>`_
* Update Mapbender to `v3.0.7.5 <https://github.com/mapbender/mapbender/releases/tag/v3.0.7.5>`_
* Update Owsproxy to `v3.0.6.4 <https://github.com/mapbender/owsproxy3/releases/tag/v3.0.6.4>`_, includes Owsproxy dependencies
* Update mapbender/vis-ui.js to `0.0.72 <https://github.com/mapbender/vis-ui.js/releases/tag/0.0.72>`_
* Update mapbender/data-source to `0.1.8 <https://github.com/mapbender/data-source/releases/tag/0.1.8>`_
* Update mapbender/digitizer to `1.1.66 <https://github.com/mapbender/mapbender-digitizer/releases/tag/1.1.66>`_
* Update bundled Composer to `1.6.5 <https://github.com/composer/composer/releases/tag/1.6.5>`_ 
* Misc ComposerBootstrap cleanups


Version 3.0.7.4
---------------

Release date: 29.08.2018


**Improvements and bugfixes:**

* [Security] In some development environment a XSS error can occur with the assets. This error was only observed on some environments with specific debug PHP settings (error_reporting z.B. E_ALL). 
* Revert the column type of the keyword-column to "varchar" to avoid incompatibilities with Oracle. Very long keywords are truncated back to 255 characters (#1000).
* Some JavaScript fixes that leads to problems with defunct Internet Explorer 11 (#990).
* Empty layer-names are not requested again in FeatureInfo (PR #1010).
* Doctrine optimizations to store layer-order settings in PostgreSQL.
* Reqgression fix in WMSLoader and image format / info format settings.
* Fix on Delete Cascade SQL statements with PostgreSQL, when deleting a WMS source.
* Fix in translations when only a placeholder was set. These fall back now to the fallback translation (per default: english).
* Update OSGeo Logo (PR #861)


**Notes for the update:**

Please call again the **app/console doctrine:schema:update** command to set back the keyword-table and column to varchar.

.. code-block:: bash

                $ app/console doctrine:schema:update

If this statement fails, for example with the PostgreSQL error ``SQLSTATE[22001]: String data, right truncated:`` and ``7 ERROR:  Value too long for type character varying(255)``, you probably have a keyword-entry in the table ``mb_core_keyword``, that exceeds the length of 255 characters. You can find out this entry with the following SQL-statement:

.. code-block:: postgres

                SELECT x, id, length(x) FROM (
                  select value, id from  mb_core_keyword
                ) AS t(x) order by length desc;



Version 3.0.7.3
---------------

Release date: 13.07.2018

**General:**

* Change of the Mapbender logo and the name: Mapbender3 is due to simplicity reasons renamed into Mapbender and we have change all texts in this documentation and the logos. Our URL were changed to http://mapbender.org some time ago.
* Mapbender requires at least PHP > 5.6 for running. We recommend PHP 7.

**New functions:**

* QGIS Server layer ordering, documented at :ref:`layerset`
* New element: :ref:`coordinate_utility`
* Mouse-Over in SearchRouter
* GPS Button in POI
* Dynamic Loading of legend-images in the legend-element (PR #605, PR #606)
* Display of a cookie banner in applications. See :ref:`cookieconsent`.


**Changes:**

* Die default applications are moved to the directory `(application)/app/config/applications`, each in its own file. This includes

  * the Mapbender Demo Map application
  * the Mapbender Demo Map basic application
  * the Mapbender mobile application

Additional YAML-applications can be placed there.


**Improvements:**

WMS Loader and WMS Services:

* Improvements in WMS Loader service compatibility, which logic now matches the backend
* Fix in the GetLegendGraphic request for a secured service via the tunnel
* Fixes and improvements for the URL-signing (#590)
* Many improvements in the WMS Backend
* Fix in instance-tunnel while requesting secured services
* Fix on accessing WMS services with undefined contact information.
* Various fixes to displaying and handling min / max scale definition from sublayers vs root layers
* Fix saving layer order on PostgreSQL
* Services loaded with WMS Loader and their metadata display. We cannot read the properties, but we don't throw an error anymore.



Design and CSS:
  
* Changed Opacity for zoombar and toolbar to get a unique button color
* Fix for creating an application and adding the screenshot


Print:

* Fix printing PNG8 maps if the image format was specified as "image/png; mode=8bit".
* Fix printing special font-sizes (especially at Windows with PHP 7.1)
* Fix in printing if PHP notices were switched on in php.ini and the yStartPosition was missing (#555)


FOM:

* Improvements in FOM: Wrong Type Definition in ACL Provider Constructor #641
* Improvements in FOM at SSPI


Translations:

* Improvements in the translations. Thanks to the Code-Sprint of the FOSS4G!
* Changes in translations from XLIF to YAML in the modules FOM and OWSProxy


Miscellaneous:

* Per default the maximum feature count for GetFeatureInfo is now 1000.
* Fix in the scale-selector, which did not want to refresh itself
* Fix in the call of Mapbender with the POI parameter (#642)
* Fix in the legend-element for oversized legend-images (#640)
* Fix on adding new elements in the backend
* Fix foreign key violation error in PostgreSQL when deleting data source (PR#840).
* Add cookieconsent code for Mapbender
* Change default prefix for printouts to mapbender


**Code-Improvements:**

* Update to Symfony 2.8 (please see the PHP requirements)
* Introduction of the Doctrine Migrations framework
* Fix possible URL signing spoof with input URLs missing query parameters.
* Doctrine Param Coverter definitions (PR #645)
* WMSLayerSource: getAuthority (PR #542)
* DimensionsHandler (#610). This will be published in the forthcoming versions
* Adding elements in backend can fail with "Warning: usort(): Array was modified ..." (#586)
* Element Template and AdminType Fixes (#743)
* Serialization of MetadataURL (#747)
* UnitTest and Pre-Conditions (#760)
* USort und array_multisort with a PHP-bug (#586)
* Fix strict SCSS warnings when compiling with ruby-sass
* Fix unbounded growth in "authority" on repeated export / reimport / cloning of applications
* Bypass (potentially very long) WmsLoader DTD / XSD validation of GetCapabilities document
* PHP 5.6 compatibility with Migrations


**Documentation:**

* New design of the documentation. We have changed the theme to the Sphinx RTD theme. The documentation is now easily readable on mobile devices. You can also print out specific pages.

* Restructuring of the documentation. The specific :ref:`functions` are sectioned into:
  
  * :ref:`basic`
  * :ref:`search`
  * :ref:`export`
  * :ref:`editing`
  * :ref:`wmc`
  * :ref:`backend`
  * :ref:`fom`
  * :ref:`misc`

* Improved documentation for the elements:
  
  * :ref:`basesourceswitcher`
  * :ref:`button`
  * :ref:`coordinates_display`
  * :ref:`html`
  * :ref:`legend`
  * :ref:`map`
  * :ref:`overview`
  * :ref:`search_router`
  * :ref:`srs_selector`
  * :ref:`zoom_bar`

* Improvements for the :ref:`printclient` and the new dynamic features on print-templates.

* Included the MS4W package for installation under :ref:`installation_windows`. Please take a look. And thank Jeff McKenna.


**Notes for the update:**

Please call the command **app/console doctrine:schema:update** for the Update to this version. The QGIS layer ordering needs a change in the Mapbender database. Also the 255 characters for WMS services require a change of the database.

.. code-block:: bash

                $ app/console doctrine:schema:update


Version 3.0.7.2, 3.0.7.1 und 3.0.7.0
------------------------------------

Due to tagging-errors of the code in Github these versions were never officially released. It's not a good idea to re-tag the code, so we continued with Version 3.0.7.3.


  

Version 3.0.6.3
---------------

Release date: 27.07.2017

**Bugfixes:**

* Regression: Fixed coordinate order at requests to a WMS 1.3.0. Coordinate reference systems with reversed axis-orientation are supported by map, print and export. (#529)
* Regression: Fixed ScaleHint for WMS services. Some WMS services that defined a Scale in their Capabilities couldn't be put into an application. (#584)



Version 3.0.6.2
---------------

Release date: 20.07.2017

**Bugfixes:**

* Search Router: Error with OpenLayers fixed (#543)
* Search Router: Auto Close after Click in mobile application (#548)
* Coordinate order (axis order) on requests to WMS 1.3.0 fixed (#529)
* Print: Rendering of points and labels on high-resolution Print (#573, #574, #492)
* Saving of WMC in WMC editor dialog (#577)
* ScaleHint for sub-layers of 1:1 fixed (#565)
* Widen the Title-Columns on Layerset-Instances (#559)
* Command to update the image-path in existing map-elements (#530)
* Translation of Print-button in FeatureInfo dialog (#552)
* Change of default-value of "immediate" in measure-tools (#538)
* SRS: Update of definitions (#550, #562) and update of YAML standard applications (#561)
* Update documentation for handling of translations.

**Additional update steps:**

**(1) Update of EPSG-Codes**

Execute again the command ``app/console doctrine:fixtures:load --fixtures=mapbender/src/Mapbender/CoreBundle/DataFixtures/ORM/Epsg/ --append``. Two new coordinate-systems are added to the Mapbender database-table ``mb_core_srs``: EPSG:4839|ETRS89 / LCC Germany (N-E) and EPSG:5243|ETRS89 / LCC Germany (E-N)).

**(2) Update of parameters im Map-Control**

Execute the command ``app/console mapbender:upgrade:database``, to update the OL-imagePath Parameter from ``bundles/mapbendercore/mapquery/lib/openlayers/img`` to ``components/mapquery/lib/openlayers/img``. This is necessary if you use the POI-Elements or call Mapbender with the poi-parameter and see no bubble-icon for the poi. Example: https://demo.mapbender.org/application/mapbender_user?poi[point]=366164%2C5623183&poi[scale]=25000&poi[label]=Please+take+a+look+at+this+POI%3A



Version 3.0.6.1
---------------

Release date: 24.05.2017

**Bugfixes:**

- Print map showed wrong scale in map-display.
- Specific WMS could not be printed due to HTTP response image/png; charset-iso....
- Backend: FOM dialogues with many entries made checkboxes unusable.
- config.php back in mapbender-starter.
- Update bin/composer build command for building Mapbender.
- Style-Fix for administrations-dialog of Basesource-switcher.
- Add WmcEditor Default Parameters for width and height.
- Update landing-page of this documentation.
- Some minor styling changes in backend.
- Some cleanup.



Version 3.0.6.0
---------------

Release date: 05.05.2017

**Architecture:**

- System Requirement PHP: 5.5.4 or higher.
- Support of PHP 7.
- Mapbender, FOM and OWSProxy excluded into Modules. They are now bind in composer.json
- Documentation is part of the composer.
- Adjustments of the ElementGenerator
- Determining of user-roles
- Composer entries with https
- Adjustments of Controllers and Bundles.
- Doctrine generate commands are marked deprecated
- Doctrine assets:dump command is marked deprecated
- Update of the JOII library
- Introduction of symblinks to the different binaries in the bin directory of mapbender-starter
- Composer shipped in application/bin directory
- Check in the Composer-installation, if the SASS Compiler Binaries are executable. If not, they are set executable.
- New Composer commands for documentation: Generate API documentation only: bin/composer gen-api-docs
- New Composer commands for documentation: Generate User-documentation only: bin/composer gen-user-docs
- Use of own forks of open-sans, joii, compass-mixins and codemirror libraries.


**Bugfixes und Features:**

- Measuring shows the coordinates directly, by moving the mouse the calculated lengths of the segment are displayed live.
- New measuring results are shown on Top. The current result is visible at first place and you don't need to scroll.
- The login-dialog (registration, forgotten password) is optimized for mobile devices to achieve a better workflow to secured mobile applications.
- New added layerset instances are now per default not marked as base-source.

- The `Copyright element popup <functions/misc/copyright.html>`_ can be defined with a height and a width.

- Deleting a layerset led in some cases to a corrupt map element and a wrong layertree.

- Adjustments and Simplification of the general style of the FullScreenTemplate
- Introduction of the check of the CSS statements in a application

- Fix in the delay when switching layers.
- Fix in GetMap request if the layer order was changed manually in the TOC.
- Fix for WMS support 1.3.0
- Fix for secured WMS services on GetMap, GetFeatureInfo, Print, Export and Legend.
- Fix for secured WMS services where the username or password included a hash-character.
- Fixes for the WMS parameter Exception Format for the GetMap and GetFeatureInfo Request (Github-Issue 400)
- Fixes of Layer-Styles for GetMap und GetFeatureInfo request
- Default Tile Size for the Map set to 512 (was 256)
- WMS Keyword limit (was: 255 characters) is changed. The column-type is now "text". The command app/console doctrine:schema:update is necessary to update the Mapbender database of a previous version.
- Fix when importing YAML based applications and creating duplicate WMS data-sources.
- Fix on minimal and maximal scale hint on WMS services.

- Print: Color can be set for variable texts.
- Print: Printout of the legend, if the service is built in with the proxy.
- Print: Services registered with PNG8 could not be printed or exported in some cases. The types image/png8 and image/png mode=24bit is not supported.
- Print: In some cases, the legend wasn't printed if OWSProxy was activated

- BaseSourceSwitcher: Duplicate request on WMS which was not visible and where the BaseSourceSwitcher was used as a menu.
- Unneccessary requests on specifc WMS configurations with scale.

- Saving of YML applications in application/app/config/applications: mapbender_mobile.yml, mapbender_user_basic.yml, mapbender_user.yml and adjustments in their referenced WMS Version
- Fixes in administration interface of the YAML editing after saving (Github-Issue 350)

- Fixes in POI-Coordinate: Transformation and SRS and the trailing digits after the comma.
- Fix of a XSS error in POI dialog
- Fix in POI dialog, if useMailto is set to false

- GPS: Error messages if no GPS signal and the dependency to Chrome-browser and https.
- GPS: Pan the map only on first position.

- User-Interface: Scrolling of a drop-down list in backend, for example the icons for the buttons, did also scroll the background.

- "Only valid" Checkbox on `loading a  WMS <functions/backend/source.html>`_ is now per default not activated anymore.

 - Reformatted messages if the schemes of a WMS are not accessible when adding a WMS.

- The `SearchRouter <functions/search/search_router.html>`_ shows, if placed in the sidebar, the Search and Reset buttons.

- Internet Explorer Compatibility: Adjustments in the `Zoombar <functions/basic/zoom_bar.html>`_..
- Internet Explorer Compatibility: Adjustments in the `OverviewMap <functions/basic/overview.html>`_.
- MS Egde Compatibility: Trying to fix the Import Dialog (https://connect.microsoft.com/IE/feedback/details/1574105/microsoft-edge-file-upload-bug-build-10240-rtm)

- Improvement of the performance on *some* Windows installations through  WinCachePHP and PHP Opcache (for details see `Installation under Windows <installation/installation_windows.html>`_)

- Change in System-Requirement for Windows: For PHP, the "Non-Thread-Safe" version is needed!

- Copying of applications through users who are not root (ACL Application: owner, Users: owner, ACLs: owner, Element: owner, Groups: owner, Service Source: owner, specific applications: owner)


**FOM and Security:**

- `Show the users  <functions/backend/FOM/users.html>`_ who have a access on an element in an application.
- Rework of the Secure Elements dialog.
- User with the role View for services are allowed to view the Metadata and to load the services into an application.


**miscellaneous**

- Design and presentation of the FeatureInfo dialog if shown as Accordion. Also if shown as "not from source".
- Drag of Popups in an application.
- WMC Editor: Adjustments in size. XSS fix.
- Fix of translations

- YAML based applications can adjust the sidebar: align (left/right), closed (true/false), width (px/em/%)

- Backend: Target field: Empty option of a Drop-Down field.
- Adjustments of WMS Scale, ScaleHint and Min/Max values when a Layerset-Instance is opened.
- Display of WMS Title in the metadata of the TOC, when the WMS was updated.
- Display of the application logo in the Configuration.
- Display Issues of Simple Search and Search Router.

- Fixes for error messages on a wrong configured Layerset-Instance.

- Print: Introduction of setasign/pdf instead of toooni/fpdf
- Print: Fix of error messages on a missing print-template
- Measuring of lines and polygons in  WGS84 (EPSG:4326)

- Adjustments of display of the element ACL

- WMS Update: remove user/password from web-browser autocomplete
- Display of number of digits in coordinates-display.

- Adjustments and extending EPSG import
- fix default visibility for a layer and the scale
- remove of DataSource Monitor icon (comes in version "next")
- Administration: Movement on the tabs with the tab-key
- Improvement of the display of the configuration interface
- Display of Source-ID in applications

- Improvements of Caching Mechanisms
- Improvements of Export and Copy mechanism.
- Improvements for the creation of new elements.

- Remove the provide ext-ldap statement in Composer. The components are released from the core. We will build in the LDAP module in version 3.0.7.

- Restructuring of DataManager and DataSource since `version 1.0.2 of data-manager <https://github.com/mapbender/data-manager/releases/tag/1.0.2>`_.


**Mobile template**

- General improvements of the mobile template.
- Fix handle mobile template button click if target isn't defined
- Set mobile icon label font weight to normal
- Fix and improve mobile template button handling
- Fix register mobile application event handler "on moveend"


**Digitizer**

- Update `Digitizer <functions/editing/digitizer.html>`_ to version 1.1.
- Printing of Multipolygons.
- Objects don't appear in the printout if they are not displayed in the Digitizer.
- MinScale restriction added
- Objects with a line-width of 0 are now not shown anymore in the printout.
- Adjustments of the Close Button: "allowCancelButton" and "allowDeleteByCancelNewGeometry".


**Form Generator:**

- Adjustments: Add HTMLElement handling  of service and DataStore configuration.


**Dokumentation**

- Introduction of the `FAQ <faq.html>`_.
- Introduction of Contributing Guide for `Mapbender-Starter <https://github.com/mapbender/mapbender-starter/blob/release/3.0.6/CONTRIBUTING.md>`_ and `OWSProxy <https://github.com/mapbender/owsproxy3/blob/release/3.0.6/CONTRIBUTING.md>`_. Mapbender itself and FOM will follow. This is the main documentation for developers and contributors of Mapbender.
- The developer documentation will be maintained there and be transferred step-by-step from this user-documentation. So in the future this documentation here will be more for users and the developers have their documentation directly in the source code of the different modules.
- Better `Layertree <functions/basic/layertree.html>`_ documentation


**config.yml Anpassungen**

DBAL-Parameter:

- default_connection: If more database entries are defined, this parameter
- persistent: Persistent connections to the database for performance reasons (Oracle)

.. code-block:: yaml

   doctrine:
     dbal:
       default_connection: default
         connections:
           default:
             ...
             persistent: true


**mapbender-starter/application/app/config/applications/**

Directory where YAML-based application definition are stored. As an example the well-known applications Mapbender-User, Mapbeder-User-Basic and Mapbender-Mobile are placed here.


**app/console doctrine:schema:update**

.. code-block:: bash

                $ app/console doctrine:schema:update --dump-sql
                ALTER TABLE mb_core_keyword ALTER value TYPE TEXT;
                ALTER TABLE mb_core_keyword ALTER value DROP DEFAULT;



Version 3.0.5.3
-----------------

Release date: 04.02.2016


**Bugfixes:**

Notable Modifications:

- Performance: The CSS, JavaScript and Translation files are now held in the Symfony Cache for the `production mode <installation/configuration.html#production-and-development-environment-and-caching-app-php-and-app-dev-php>`_. This can lead to better performance on slower machines. These cache is not used by the `development-mode <installation/configuration.html#production-and-development-environment-and-caching-app-php-and-app-dev-php>`_.
- The package `eslider/sassc-binaries <https://github.com/eSlider/sassc-binaries>`_ offers now a sassc Compiler for 32-bit Linux systems. This led to a wrong display on 32-bit Linux-Systems (http://lists.osgeo.org/pipermail/mapbender_users/2015-December/004768.html)
- Redlining: The contents of the Redlining element is visible and Redlining can now be used as a Dialog or an Element in the Sidepane. See also the `documentation of the Redlining Element <functions/editing/redlining.html>`_. The scroll bar for the Geometry-Types in the configuration dialog is now displayed correctly.

Users and security:

- Users can be switched active or inactive by an Administrator, who has at least the ACL-user-right "operator". This can be used for users, who have self-registered but not yet activated their account. See the `documentation of user-management <functions/backend/FOM/users.html>`_ for details.
- The text, translations and styles for the Self-Register process and the Password Reset are improved. Also the `Documentation <functions/backend/FOM/users.html>`_ is adjusted.

Print and export image:

- The `Print module <functions/export/printclient.html>`_ can now also be used in the Sidepane.
- Print legend: The size of the legend in the print-out was scaled down to improve the quality.
- Print-templates: The default print-templates have changed. The padding of the dynamic texts to their border and their justification were improved.
- Print: The Print configuration messed up mandatory (required: true) and optional fields (required: false), if they were used in combination. Optional fields were partly shown as mandatory (Github #380).
- In some cases Mapbender printed the legend of all WMS-layers, even if the layer was not set active (seen in Mapbender_Users WMS).
- Export Image: Transparency of tiled and non-tiled services is supported in Export Image.

Copy and import:

- Copying an application under SQLite and MySQL: There was en error that applications could not be copied if the database was SQLite or MySQL.
- Errors at the import of application as JSON on MySQL (elements lose their target) was fixed.

Individual Elements:

- **WMC** and thematic layertree: If a WMC is loaded and Keep Sources is set to "no", the thematic layers are now also removed from the layertree.
- **WMS-URL parameter** and legend: If a service was loaded with the wms_url parameter, the complete legend was shown. This behaviour is fixed.

  - *Note:* WMS services exists, which define a legend in the root-layer element. According to the WMS-specification, this legend will be inherited by sub-layers who itself haven't defined a legend (for example if they only contain the annotations). The effect is similar in MB3 but the cause is different, so that in these cases a change in the WMS capabilities is needed (define a static legend image for these layers).

- **Thematic Layer**: Fix in switching layers on and off which are in their own Layerset but not displayed as a thematic layer.
- **Coordinate display**: The coordinate-element display doesn't show "null" as prefix or separator anymore, although the field was defined as empty. The element has get a fixed with so that the layout in the footer region is more sable. The value can be changed (see the chapter `CSS-customizing of the element <functions/basic/coordinates_display.html>`_).
- **SearchRouter**: The content of the result uses the whole space of the dialog and fits itself to changes of the size. In the sidebar the whole height is used. The search router can be configured `with a width and a height <functions/search/search_router.html>`_.
- **ScaleSelector**: The width of the element can be `customized with a CSS-Statement <functions/basic/scale_selector.html>`_ and is no more set to 155 pixel.
- If all layer in a **layerset-instance** are set to visible=off they were not visible in the layertree and the legend. This is fixed.
- Improvements in the styling of the **POI dialog** if "usemailto" is set to false.
- **Layertree**: Titles are now shown per default with a length of 40. The default value has been changed. You can set the `parameter Titlemaxlength in the configuration dialog <functions/basic/layertree.html>`_.
- **GPS**: Improvements in the GPS handling.

General changes:

- Changing the Base Data, the Layout, the Layerset, the CSS and the Security of an application does not change the tab anymore and doesn't jump back to the base data tab.
- General improvements of the `Digitizer Code <https://github.com/mapbender/mapbender-digitizer>`_ version 1.0. Version 1.1 is compatible with Mapbender 3.0.5.3.
- Github files: Small clean up actions in the Github repository to improve the automatic build-processes.
- Transparency of services: Services with a transparency refreshed with a poor effect, caused by the "transitionEffect" in OpenLayers. The effect was removed.
- Group filter: The security configuration dialog got improvements at the selection of Groups, if the Groups had the same name but a different suffix.
- TileSize Parameter in the map configuration was not set in some cases.
- Display of symbols in Internet Explorer 11 and MS Edge 25 (also an error in MS Edge 20).
- mapbender.yml: At the initial import of the mapbender.yml the values of GetFeatureInfo are now set to text/html. The mapbender.yml can now customized with Redlining.


**Change of the Mapbender domains:**

- We have switched the URL www.mapbender.org to the Mapbender3 page. In future, the Mapbender3 page is also available via www.mapbender.org and www.mapbender3.org. Mapbender2 is now available at www.mapbender2.org

  - http://www.mapbender.org: Mapbender3,
  - http://www.mapbender3.org: Mapbender3,
  - http://www.mapbender2.org: Mapbender2.

**Known Issues:**

- The Sketch Tool doesn't work correctly and will be built into the `Redlining Tool <functions/editing/redlining.html>`_.
- Share map doesn't work for Facebook, Twitter und Google+.



Version 3.0.5.2
-----------------

Release Datum: 27.10.2015

**Bugfixes:**

- Copy applications: User-Rights and groups are copied. The user who copied the application becomes owner of the copied application.
- FOM: Changes in behaviour of wrong logins and user locking. It is only shown that the login failed, independent if the user exists or not.
- Fixed error message when creating a user with a too short password.
- Print: Fix of replace pattern.
- Print: Fix if a wrong configured WMS has special characters (%26) in the legend URL.
- Image export in Firefox.
- WMC Loader: Loading WMC and Behaviour of BaseSources.
- BaseSourceSwitcher: Tiles of a not visible service are not pre-fetched.
- BaseSourceSwitcher: If a group is defined, only one theme is switched on.
- SearchRouter: Fix of quotes for table-names.
- Copy applications: Fix of the search in the copied application.
- Simple Search: Catch the return key.
- FeatureInfo: Add WMS functionality and WMS Loader.
- Icon Polygon is visible in the toolbar of applications.
- Icons, which are not based on FontAwesome also work in the mobile application.
- Administration of the map element: The view of the configuration dialog in the backend starts on top.
- Administration data source: No form data auto-complete from the browser for username and password.
- Mobile application: Design in Firefox for Android.
- Update 3.0.4.x: FeatureInfo autoopen=true is kept.
- Doku: FOM `UserBundle translation <functions/backend/FOM/index.html>`_ and `additional information for failed user logins <functions/backend/FOM/users.html>`_.
- Doku: URL parameter scale in `map element <functions/basic/map.html>`_.
- Doku: `WMC Loader <functions/wmc/wmc_loader.html>`_ and KeepSources.

**Changes in config.yml:**

* The following changes are optional parameters for the behaviour of the login (see also `the chapter in the FOM bundle for details <functions/backend/FOM/users.html>`_):

    .. code-block:: yaml

                    fom_user:

                      # Allow to create user log table on the fly if the table doesn't exits.
                      # Default: true
                      auto_create_log_table: true

                      # Time between to check login tries
                      login_check_log_time: "-5 minutes"

                      # Login attemps before delay starts
                      login_attempts_before_delay: 3

                      # Login delay after all attemps are failed
                      login_delay_after_fail: 2 # Seconds


Version 3.0.5.1
-----------------

Release Datum: 26.08.2015

**New functions**: in the `Map element <functions/basic/map.html>`_ and in the `Print client <functions/export/printclient.html>`_:

* Map: OpenLayers TileSize: You can set the tile-size for the map. Default: 256x256.
* Map: Delay before Tiles: For WMS-T, for example with temporal parameters (in future)
* Print: Show coordinates in PDF print
* Print: get print scale depending on map-scale
* Print: print legend_default_behaviour
* Print: add print templates with the + symbol
* Print: user-defined logo and text


**Bugfixes:**

- Layertree: loading symbol and exclamation mark symbol.
- Layertree: zoom Symbol not for layers without a BBOX information
- WMS Reload: FeatureInfo
- WMS Reload: some WMS couldn't be reloaded.
- Export/Import of application and miscellaneous bugfixes
- WMC-Editor and WMC-Load fixes.
- WMC from a Mapbender 3.0.4.1 application
- Tile buffer and BBOX buffer fixes
- FeatureInfo: Fixes in design and when shown as an Accordion Panel
- FeatureInfo: Print
- Wrong Jquery-UI link in layerset instance
- Save Layerset and Save Layout leaves you on the page
- Classic Template: SCSS corrections
- Mobile Template: Bootstrap message hides close button
- Mobile Template: close SearchRouter window
- Mobile Template: Mozilla Firefox Fixes on layout
- Backend: Layerset Filter and +-Buttons doesn't hide everything anymore
- composer.json upgrade version of Digitizer to 1.0.*
- Documentation of the JS-UI Generator (Form-Generator): https://github.com/eSlider/vis-ui.js
- Restructured `Installations-Dokumentation <installation.html>`_ and some changes (php-pear, assets-Verzeichnis, init:acl, openssl).
- Better documentation of the `Mapbender3 Templates <customization/templates.html>`_
- Better documentation of the `Quickstart <quickstart.html>`_

**Known Issues:**

- After copying an application from Mapbender 3.0.4.x you have to set the layerset in the map/overview element. Please save the map and overview element beforehand.
- Regional Template removed


Version 3.0.5.0
-----------------

Release Date: 01.07.2015

For details have a look at:  https://github.com/mapbender/mapbender-starter/blob/develop/CHANGELOG.md

* **WMS reload:** WMS sources can now be reloaded if the structure has changed.

* **Digitizer:** The digitizer allows the editing of geometries and their attributes. Right now it needs access to the database where the editable tables are. The definition of the digitizer is done in YAML syntax. To provide an usable interface for the attributes, you can declare the form in your configuration file. The form supports different input fields (textboxes, checkboxes, date-pickers, and so on..), validation, tabs and it uses Bootstrap.

* **Print with legend:** The print element supports the print-out of the legend on a seperate page. This can be set with a checkbox.

* **Configurable layertree:** The layertree supports the usage of more than one layerset. You have to adjust the map element to define which layersets should be shown and the layertree element itself. The usage is documented `on the Layertree page <functions/basic/layertree.html>`_.

* **Improved FeatureInfo dialog:** You can set a) the width and height of the FeatureInfo dialog, b) if the dialog should show the original format of the WMS and c) if it should only open if a valid entry is found (otherwise a messagebox is displayed). See the documentation of the `FeatureInfo Dialog <functions/basic/feature_info.html>`_.

* **Mobile template:** A new modern mobile template is provided.

* **SASS Compiler:** Architectual changes are made at the SASS compiler which leads to a more performant interface.

* **Vendor Specific Parameters:** A WMS layer instance supports the definition of Vendor Specific Parameters that are added to the WMS request. You can define hard coded values or the user or group information of the logged-in user. See the documentation of `Vendor Specific Parameters <quickstart.html#configure-your-wms>`_ for details.

* **Expanded functionality of HTML elements with a form-builder:** This approach is used in the Digitizer to provide the forms for attribute editing.

* **New button colletion:** The new buttons are based on a new font, the old buttons are available under the "FontAwesome" name.

* **Starting mapbender with URL parameters:** Mapbender3 can be started with URL parameters. See the documentation of `URL parameters <functions/basic/map.html#controlling-by-url>`_.

* New translations for Portuguese and Russian.

* Symfony updated to 2.3.30.


**Changes in config.yml:**

* Changes in a dbal connection:

  * **logging: false**: This options sets, that *all* SQL statements are not logged. Further information can be found here: http://www.loremipsum.at/blog/doctrine-2-sql-profiler-in-debugleiste/

  * **profiling: false**: This option handles the profiling of SQL statements. This option can be switched off in production environments.

  If possible the options should be set this way, so that they are only active in debug mode:

  .. code-block:: yaml

                  logging:               "%kernel.debug%"
                  profiling:             "%kernel.debug%"


**Known Issues**

* After copying an application from Mapbender 3.0.4.x you have to set the layerset in the map/overview element.


Version 3.0.4.1
-----------------

Release Datum: 23-01-2015

For details have a look at:  https://github.com/mapbender/mapbender-starter/blob/develop/CHANGELOG.md

* option 'removelayer' added into layertree menu
* parameter 'layerRemove' removed from layertree configuration
* container accordion structure changed
* import / export from applications added (without acls)
* display layer metadata
* Frontend: Sidepane Accordeon Legend is displayed without horizontal Scrollbar
* Backend: WMS Instanz configuration - contextmenu for layers shows wrong ID (only instance ID)
* Frontend: Legend - displays WMS Information although the checkbox Show
* Frontend: Layertree - contextmenu zoomlayer does not use the layer extent
* Backend: Add Source with user/password - informations is added to field originUrl not to fields user and password
* app/console mapbender:generate:element fixed errors
* bug visiblelayers fixed
* WMS with authentication saves in table mb_wms_wmssource username and password
* no metadata for applications coming from mapbender.yml definition (no entry in context menu)
* copy an application via button on application fixed
* print template resize northarrow, overview added
* improved screenshot for application handling
* https://github.com/mapbender/mapbender/milestones/3.0.4.1


Version 3.0.4.0
---------------

release date: 12-09-2014

For details have a look at https://github.com/mapbender/mapbender-starter/blob/develop/CHANGELOG.md

* Switched to MIT license
* Symfony Update 2.3 LTS
* OpenLayers 2.13 with additional patches
* Switch Services (BaseSourceSwitcher) with menu
* added generic HTML element
* added custom CSS editor for applications
* added accordion container for SidePane
* added screenshot management to application editing
* import/export of applications/sources
* spanish translation


Version 3.0.3
---------------

release date: 17-03-2014

For details have a look at: https://github.com/mapbender/mapbender/issues?milestone=8

* Enhancements for Search-Router für SQL-Suchen (Selectboxes, Distinct)
* WMC Editor and Loader
* WMSLoader Enhancement add WMS via link
* i18n - Internationalisation (english / german)
* Sketch to draw temporary objects
* POI - Meetingpoint
* Imageexport to generate png or jpg
* Change WMS Collection via button (BaselayerSwitcher)
* Print with overview
* Sidepane with different elements (chnage via button)
* Layertree context menue to change opacity and to zoom to layer
* Open application with parameters (f.e. position)
* ACL for elements
* Added function for validate WMS GetCapabilities documents


Version 3.0.2
---------------

release date: 27-11-2013

For details have a look at https://github.com/mapbender/mapbender/issues?milestone=6

* SearchRouter
* WMC Editor and Loader
* WMSLoader enhancement to load a WMS from a link


Version 3.0.1
---------------

release date: 06-09-2013

For details have a look at https://github.com/mapbender/mapbender/issues?milestone=5

* Kopieren einer Anwendung mit Diensten
* Popup - draggable
* PrintClient Erweiterung Druck EPSG 4326, neue Drucklayouts, Druck A4-A0
* Catch login failures to avoid  brute force login attempts
* Bug fixes


Version 3.0.0.2
-----------------

Bugfix-Release Date: 19-07-2013

For details have a look at: https://github.com/mapbender/mapbender/issues?milestone=4



Version 3.0.0.1
-----------------

Bugfix-Release Date: 07-06-2013

For details have a look at: https://github.com/mapbender/mapbender/issues?milestone=3



Version 3.0.0.0
-----------------

release date: 29-05-2013

For details have a look at https://github.com/mapbender/mapbender/issues?milestone=1

* Administration Backend for Service, Application, User/Group and security administration
* Backend-/Frontend Design
* Security
* User/Group Administration
* WMS Administration
* Map
* Layertree
* Legend
* Overview Map
* Navigation Toolbar (Zoombar)
* Feature Info
* Coordinates Display
* Copyright
* Line/Area Ruler
* Scale Selector
* ScaleBar
* Spatial Reference System Selector
* GPS-Position
* Print
* Add WMS to application
* Documentation at http://doc.mapbender.org
