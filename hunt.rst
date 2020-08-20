.. _hunt:

Hunt
====

:ref:`soc` gives you access to our new Hunt interface. This interface allows you to hunt through all of the data in Elasticsearch and is highly tuned for stacking, pivoting, data expansion, and data reduction.

The first two elements shown are the query bar and time picker. Once you perform a query, Hunt will display the number of events found in the upper right and then render three main sections of output.

.. image:: https://user-images.githubusercontent.com/1659467/90804454-3eac7100-e2e8-11ea-9cd3-d0f5cc5640fe.png
  :target: https://user-images.githubusercontent.com/1659467/90804454-3eac7100-e2e8-11ea-9cd3-d0f5cc5640fe.png

Query Bar
---------
The easiest way to get started is to click the query drop down box and select one of the pre-defined queries. These pre-defined queries cover most of the major data types that you would expect to see in a Security Onion deployment: NIDS alerts from Suricata, HIDS alerts from Wazuh, protocol metadata logs from Zeek or Suricata, endpoint logs, and firewall logs. Each of the entries in the drop down list will show the actual query followed by a description of what that query does.

.. image:: https://user-images.githubusercontent.com/1659467/87226434-b1c5dd80-c361-11ea-8259-843aa2b8b64b.png
  :target: https://user-images.githubusercontent.com/1659467/87226434-b1c5dd80-c361-11ea-8259-843aa2b8b64b.png

Time Picker
-----------

By default, Hunt searches the last 24 hours. If you want to search a different time frame, you can change it in the upper right corner of the screen. You can use the default relative time or click the clock icon to change to absolute time.

.. image:: https://user-images.githubusercontent.com/1659467/87226453-cbffbb80-c361-11ea-82e3-8b1809171c8a.png
  :target: https://user-images.githubusercontent.com/1659467/87226453-cbffbb80-c361-11ea-82e3-8b1809171c8a.png

Visualization
-------------

The first section of output contains a Most Occurences visualization, a timeline visualization, and a Fewest Occurences visualization. Aggregation defaults to 10 values, so Most Occurences is the Top 10 and Fewest Occurences is the Bottom 10 (long tail). The number of aggregation values is controlled by the Fetch Limit setting in the Group Metrics section.

.. image:: https://user-images.githubusercontent.com/1659467/87226466-e2a61280-c361-11ea-8767-77e3b3ed13fd.png
  :target: https://user-images.githubusercontent.com/1659467/87226466-e2a61280-c361-11ea-8767-77e3b3ed13fd.png

Group Metrics
-------------

The middle section of output is the Group Metrics section and it's a data table that allows you to stack (aggregate) arbitrary fields. The Group Metrics are controlled by the ``groupby`` parameter in the search bar. Clicking the table headers allows you to sort ascending or descending. Values in the Group Metrics table have plus and minus magnifying glass icons to the left which allow you to include or exclude (respectively) those values in your query. The default Fetch Limit is ``10`` so if you need to see more than the top 10, you can increase the Fetch Limit and then page through the output using the left and right arrow icons or increase the ``Rows per page`` setting.

.. image:: https://user-images.githubusercontent.com/1659467/87226473-f6ea0f80-c361-11ea-941d-4b82b7795cd7.png
  :target: https://user-images.githubusercontent.com/1659467/87226473-f6ea0f80-c361-11ea-941d-4b82b7795cd7.png

Events
------

The third and final section of output is a data table that contains all search results and allows you to drill into individual search results as necessary. Clicking the table headers allows you to sort ascending or descending. Starting from the left side of each row, there is an arrow which will expand the result to show all of its fields. Next to that arrow is two pcap links that allow you to pivot to the :ref:`PCAP` web interface to access your full packet capture. Click the first pcap link to use the current window or use the second pcap link to open pcap in a new window. To the right of the pcap links is the ``Timestamp`` field. Next, a few standard fields are shown: ``source.ip``, ``source.port``, ``destination.ip``, ``destination.port``, ``log.id.uid`` (Zeek unique identifier), ``network.community_id`` (Community ID), and ``event.dataset``. Values in these fields have plus and minus magnifying glass icons to the left which allow you to include or exclude (respectively) those values in your query. The default Fetch Limit for the Events table is ``100`` so if you need to see more than 100 events, you can increase the Fetch Limit and then page through the output using the left and right arrow icons or increase the ``Rows per page`` setting.

.. image:: https://user-images.githubusercontent.com/1659467/87226485-09fcdf80-c362-11ea-8f8d-e28cd112047f.png
  :target: https://user-images.githubusercontent.com/1659467/87226485-09fcdf80-c362-11ea-8f8d-e28cd112047f.png

When you click the down arrow to expand a row in the Events table, it will show all of the individual fields from that event. Field names are shown on the left and field values on the right. When looking at the field names, there is an icon to the left that will add that field to the ``groupby`` section of your query. The field values on the right have plus and minus magnifying glass icons which allow you to include or exclude (respectively) those values in your query.

.. image:: https://user-images.githubusercontent.com/1659467/87226504-2436bd80-c362-11ea-8aab-1543739e9eb8.png
  :target: https://user-images.githubusercontent.com/1659467/87226504-2436bd80-c362-11ea-8aab-1543739e9eb8.png

Statistics
----------

The bottom left corner of the page shows statistics about the current query including the speed of the backend data fetch and the total round trip time.

.. image:: https://user-images.githubusercontent.com/1659467/87226518-37498d80-c362-11ea-9414-e18df4cddd43.png
  :target: https://user-images.githubusercontent.com/1659467/87226518-37498d80-c362-11ea-9414-e18df4cddd43.png

Auto Hunt
---------

The bottom right corner of the page has a toggle for Auto Hunt. When enabled, Hunt will automatically submit your query any time you change filters, groupings, or date ranges.

.. image:: https://user-images.githubusercontent.com/1659467/87226525-46c8d680-c362-11ea-978d-c0e6f0c6b608.png
  :target: https://user-images.githubusercontent.com/1659467/87226525-46c8d680-c362-11ea-978d-c0e6f0c6b608.png

OQL
---

Onion Query Language (OQL) starts with standard `Lucene query syntax <https://lucene.apache.org/core/2_9_4/queryparsersyntax.html>`_ and then allows you to add optional segments that control what Hunt does with the results from the query. The ``groupby`` segment tells Hunt to group by (aggregate) a particular field. So, for example, if you want to group by destination IP address, you can add ``| groupby destination.ip`` to your search (assuming it didn't already have a groupby statement). The ``groupby`` segment supports multiple aggregations so you can add more fields that you want to group by, separating those fields with spaces. For example, to group by destination IP address and then destination port, you could use ``| groupby destination.ip destination.port``.

Videos
------

.. seealso::

  To see Hunt in action, check out these Youtube videos:

  https://www.youtube.com/watch?v=Y-nZInToH8s

  https://www.youtube.com/watch?v=Is2shLAOyJs
