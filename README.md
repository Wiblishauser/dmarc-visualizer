# dmarc-visualizer

Analyse and visualize DMARC results using open-source tools.

* [parsedmarc](https://github.com/domainaware/parsedmarc) for parsing DMARC reports,
* [Elasticsearch](https://www.elastic.co/) to store aggregated data.
* [Grafana](https://grafana.com/) to visualize the aggregated reports.

See the full blog post with instructions at https://debricked.com/blog/2020/05/14/analyse-and-visualize-dmarc-results-using-open-source-tools/.

## Note
This was tested with:
- parsedmarc 8.16.1
- Elasticsearch 8.10.2
- Grafan 11.4.0

All data is stored in volumes and if not imported via imap the data has to be manually copied afterwards.
Run the following commands:
```bash
docker volume ls # find the fullname for the volume ending in 'parsedmarc_input'. In my case 'dmarc-visualizer_parsedmarc_input'.
docker volume inspect dmarc-visualizer_parsedmarc_input
# In the output you will find the 'Mountpoint' where the data has to becopied. Restart the stack or just parsedmarc should be enough.
```
There is also an added healthcheck and some other settings for Elasticsearch which should smooth over the starting process of the stack. If you see a bunch of error messages just give it time.
## Screenshot

![Screenshot of Grafana dashboard](/big_screenshot.png?raw=true)
