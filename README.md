# domain_scraper

Scrapes domains from one input URL or from a file list of domains for broken links,
valid emails and valid social media links.

## Usage

* Check URL's from text file to scrape for emails and social media links. This also
  checks common paths found from the input domain such as contact and team pages to add
  to the queue to new URL's to scrape for emails and social media links. This
  does not store broken links, but does output them to STDOUT during runtime. This
  does save to a file all valid & unique emails addresses and social media links
  during runtime so data is stored in the event of an error.

```
$ ./scrape_new_links_emails_and_social_media.py [FILE_WITH_URLS]
```

* Same as above, but do not check for new links to add to the queue

```
$ ./scrape_emails_and_social_media_no_new_links.py [FILE_WITH_URLS]
```

* extract name associations from email list

```
$ ./extract_name_from_email.py [FILE_WITH_EMAILS]
```

* To check all URLS from the same domain based off of one main input URL

```
$ ./scrape_url_and_check_broken_links.py [URL_TO_CHECK]
```

* Check URL's for broken links from text file

```
$ ./check_file_for_broken_links.py [FILE_WITH_URLS]
```

## Data storage

Data is written to a file during runtime of the email and social media scraper.  Data is only
written to files at program completion for the broken link checkers.

TODO: The broken link checkers should output results to a file during runtime and not wait until
the end of the program

## Example file & file cleanup

```
$ cat example_file_bad_format.txt
https://google.com/^Mhttps://cecinestpasun.site/^Mhttps://google.com/^Mhttp://www.davidjohncoleman.com/wp-content/uploads/2017/06/headshot-retro.png

# replace ^M character after copying from .csv file
$ tr '\r' '\n' < example_file_bad_format.txt > example_file.txt

# remove repeat links
$ awk '!seen[$0]++' example_file.txt > example_file_no_repeats.txt

$ cat example_file.txt
https://google.com/
https://cecinestpasun.site/
http://www.davidjohncoleman.com/wp-content/uploads/2017/06/headshot-retro.png
```

## Author

* David John Coleman II, [davidjohncoleman.com](http://www.davidjohncoleman.com/)
| [@djohncoleman](https://twitter.com/djohncoleman)

## License

MIT License
