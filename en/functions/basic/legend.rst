.. _legend:

Legend
******

The legend object shows a legend of the layers that are displayed in the map. Every single layer is listed which includes point, line and/or polygon objects.

.. image:: ../../../figures/legend.png
     :scale: 80

Configuration
=============

.. image:: ../../../figures/legend_configuration.png
     :scale: 80


* **Auto-open:** If activated, the legend opens when the application is started. Default is active.
* **Title:** Title of the element. The title will be listed in "Layouts". Is also shown next to the button, if "Show layer title" is activated.
* **Tooltip:** Text that will be indicated if the mouse hovers over the legend for a longer time.
* **Elementtype:** Sets output as a dialog or blockelement, default is dialog.
* **Display type:** Accordion-like display or list. Default is list.
* **Target:** ID of Map element to query.

* **Show source title:** shows WMS/source title, default is true.
* **Show layer title:** shows layer title, default is true.
* **Show grouped layer title:** shows group title for grouped layers, default is true.

The Legend element is integrated via a button or in the sidepane. If you look for configurational details for the button, head over to this page: `Button <../misc/button.html>`_.


Configuration Examples:
========================

Legend in the Sidepane:
-----------------------
If yout want to integrate a legend in the sidepane, click the ``+`` -button in the "Layouts"-tab (section "Sidepane").

.. image:: ../../../figures/de/add_sidepane.png
     :scale: 80

Then, choose the element "Legend" in the appearing window. The configurational dialog "Add element – Legend" will open.

.. image:: ../../../figures/legend_example_sidepane_dialog.png
     :scale: 80

Our configured element has the title "Legend". It is defined as *Elementtype* "blockelement", because it is integrated into the sidepane. *Display type* is set to "list" and *target* is set to "Main Map". The legends opens automatically (set checkbox *Auto-open*). Moreover, the layer title and the title of all grouped layers appears (set checkboxes *Show layer title* and *Show grouped layer title*).

Given this configuration, the result looks like this:

.. image:: ../../../figures/legend_example_sidepane.png
     :scale: 80

It is recommended that a legend element is always set as "blockelement" if integrated into the sidepane. If it is set as *Element type* "dialog", a pop up window opens and the legend will not be shown in the sidepane. If configured wrong, you can only see the heading ("Legend") in the sidepane. If the dialog is closed, it is impossible to bring it back via the frontend surface. If the legend should be integrated in the toolbar, the best way is to configure it with a "Button" element.

Legend in the toolbar:
----------------------
The legend element can be integrated with a button in the toolbar. First step: Integrate the legend element. Open the application backend and add the element into the content section of the Layout-tab.

.. image:: ../../../figures/de/add_content.png
     :scale: 80

In this example, the following settings are chosen:

.. image:: ../../../figures/legend_example_toolbar_dialog.png
     :scale: 80

As always, it is important to set the *Element type* to the appropriate setting - in this case, "dialog". In our example, the checkbox *Auto-open* is dismissed. Therefore, the legend opens only with a click on the button.
This button has to be implemented into the toolbar section. For detailed instructions on buttons, see the Mapbender-Documentation page `Button <../misc/button.html>`_.

The configuration of a button can look like this:

.. image:: ../../../figures/legend_example_button.png
     :scale: 80

Following the above instructions, the result in the application looks like this:

.. image:: ../../../figures/legend_example_toolbar.png
     :scale: 80

The toolbar shows the button for the legend element. If the button is clicked, the dialog with the generated legend opens.

The activation and deactivation of checkboxes in the configurational settings leads to:

.. image:: ../../../figures/legend_example_toolbar_checkboxes.png
     :scale: 80