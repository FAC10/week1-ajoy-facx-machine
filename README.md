# FACX Machine's Nice Site

After cloning the repo run `npm install` to install the development dependencies (currently only Browser-sync).

To work on the site run `npm start` and your browser should open `index.html`.

Browser-sync will watch any `.html`, `.css` and `.js` files and automatically refresh the browser for you when you save.

To add a warning instruction when pushing to master run the command `cp pre-push .git/hooks/ && chmod +x .git/hooks/pre-push`
