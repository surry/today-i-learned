# RPM Changelog Date Format
rpmbuild will complain if the date for a `%changelog` entry is not in the right
format. Here's one way to get a date in the correct format for a changelog on Linux:

`date "+%a %b %d %Y"`

https://fedoraproject.org/wiki/Packaging:Guidelines?rd=Packaging/Guidelines#Changelogs
