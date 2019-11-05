# vagrant-automation-demo

This demo uses `vagrant` to run `ansible` which creates an `nginx` reverse proxy, that forwards traffic to the `python` web/app server, with a `postgres` backend.

If everything goes to plan you should see the app on `http://localhost:8090/` in your browser after you `vagrant up`.