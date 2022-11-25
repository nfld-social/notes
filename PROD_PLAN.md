# Proper Production Instance Plan

We have a 'test' instance running at the moment, defined at a high level as such:

- DigitalOcean VPS:
  - Specs:
    - RAM: 2 GB Memory
    - Storage 25 GB Disk
    - Data Center: TOR1
    - Image: Ubuntu 22.10 x64
  - Non-docker services:
    - nginx - web server, proxies connections to the web backend, serves static files
    - acme.sh - renews the ssl cert for nfld.social every 60 days
  - Docker services:
    - postgresql / postgres:14
    - redis / redis:7
    - redis-volatile / redis:7
    - website / tootsuite/mastodon:v4.0.2 (bundle exec rails s -p 3000)
    - streaming / tootsuite/mastodon:v4.0.2 (node ./streaming)
    - sidekiq / tootsuite/mastodon:v4.0.2 (bundle exec sidekiq)

## Next Steps

- Make a note within this document of current issues with the test instance
- Figure out a ballpark cost per month
- Get an instance banner / icon created
- Figure out a plan of where this instance is going to be posted elsewhere

