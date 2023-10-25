# gcloud-issue-test-1
Testing an issue with app engine static files not being found. The purpose is 
either to solve the issue, or to prove it is a bug (and file a bug report).
- https://cloud.google.com/appengine/docs/standard/go/building-app#local-machine
- https://cloud.google.com/appengine/docs/standard/serving-static-files?tab=go#serving_from_your_application

Remarks while trying to exactly follow the procedure about building an app:
- Install the bundled Python version to be sure to have the correct version.
- Using the [project selector](https://console.cloud.google.com/projectselector2/home/dashboard) 
  I created a new project with for both it's name and id: `gcloud-issue-test-1`.
- During `gcloud init` I selected this project named `gcloud-issue-test-1` .
- During `gcloud app create` I selected location `europe-west3`.
- After `gcloud app deploy` using `gcloud app browse` showed the output of this app.

Note that this app is reachable with, but also without the region in the URL:
- https://gcloud-issue-test-1.ey.r.appspot.com/
- https://gcloud-issue-test-1.appspot.com/

So far so good, now let's add a first static file:
- Add the following section in `app.yaml`:
  ```
  handlers:
    - url: /favicon\.ico
      static_files: favicon.ico
      upload: favicon\.ico
  ```
- Add `favicon.ico` in the `go-app` directory.
- Use `gcloud app deploy` to deploy the updated version.
- Use `gcloud app browse` and check if the new icon shows up.

I needed a `shift-F5` for the icon to show up. Now let's add an html file:
- To be continued ...








