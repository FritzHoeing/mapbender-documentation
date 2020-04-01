.. _helpsites_en:

How to create custom Help Sites?
################################

Adding new Help Sites
********************

The customisation of the existing help sites is possible. It is important however, changes reference back to the version control. With every edit the Web-directory should be refreshed and the cache cleared, because they save the sites.

.. code-block:: php

    #installing Assets for the Web-directory
    app/console assets:install web --symlink --relative

    #empty Cache (prod and dev directory)
    rm -rf app/cache/*

The following syntax shows the help sites:

.. code-block:: php

    [Mapbender-URL] + /help/
    z.B. https://my-mapbender.com/mapbender/help/

New help sites can be implemented with HelpController.php. For this implementation of a new site at the right place the indent has to mirror the structure below. New help sites additionally have to be created in the view-directory and saved as [filename].html.twig.

.. code-block:: php

    cd /application/src/Mapbender/HelpBundle/Controller/HelpController.php

    #Example of the syntax implementing a site for the linklist in the footer (file HelpController)

            'user interface' => array(
                [...]
                'footer' => array(
                    'coordinate display'        => array(),
                    'coordiante system choice'  => array(),
                    'linklist'                 => array(),
                    'benchmark choice'           => array(),

    # create new site
    cd application/src/Mapbender/HelpBundle/Resources/views/Pages/
    touch linkliste.html.twig

    # Above the title we find the site in the overview:

    {% set title = "linklist" %}

    #installing assets for the Web directory
    app/console assets:install web --symlink --relative

    #clearing cache (prod and dev directory)
    rm -rf app/cache/*


Editing existing Help Sites
**************************
To edit existing help sites the respective file in the view directorycan be changed

.. code-block:: php


    cd application/src/Mapbender/HelpBundle/Resources/views/Pages
    #editing exist5ing data z.B. userinterface.html.twig

    #installing assets for the Web directory
    app/console assets:install web --symlink --relative

    #clearing cache (prod and dev directory)
    rm -rf app/cache/*


Changing the design of the Help Sites
*************************************
The design templates can be changed according to ones wishes. These can be stated for the help sites via css-files.

.. code-block:: php

    cd application/src/Mapbender/HelpBundle/Resources/public
    # most important parameters are in help.css

    #installing assets for the Web directory
    app/console assets:install web --symlink --relative

    #clearing cache (prod and dev directory)
    rm -rf app/cache/*


Referecing a picture of the Help Sites
*************************************
Esitsing images are stored in the images-directory and are referenced in the files. To exchange existing pictures or implement new ones you can edit here:

.. code-block:: php

    cd application/src/Mapbender/HelpBundle/Resources/public/images

    #Reference in the help sites, e.g. via the footer
        <img src="{{ asset('bundles/mapbenderhelp/images/fussleiste.png') }}" alt="footer" title="footer"/>
