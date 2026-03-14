# Week 5 AWS S3 + CloudFront Static Site

This repository is the plain HTML/CSS/JavaScript deployment for the Week 5 AWS assignment.

The project is intended to be uploaded to an S3 bucket and served publicly through a CloudFront distribution while keeping the S3 bucket private.

## Live Deployment

- CloudFront URL: `ADD_YOUR_CLOUDFRONT_URL_HERE`

## Related React Deployment

- React repo: `https://github.com/jessecube1234-beep/level-4-week-2-assignment`
- React CloudFront URL: `ADD_YOUR_REACT_CLOUDFRONT_URL_HERE`

## Project Files

- `index.html` - main static page
- `styles.css` - page styles
- `app.js` - small client-side interaction
- `not_found.html` - fallback static error page
- `gh-actions-s3-cloudfront-vite-deploy.md` - CI/CD reference for later automation

## How To Run Locally

Because this is a plain static site, there is no build step.

Open `index.html` in a browser, or serve the folder with any static server.

## Deployment Summary

1. Create an S3 bucket with Block Public Access enabled.
2. Upload `index.html`, `styles.css`, `app.js`, and any other static assets.
3. Create a CloudFront distribution using the S3 bucket as the origin.
4. Allow private S3 bucket access through CloudFront.
5. Set the default root object to `index.html`.
6. Wait for the distribution to finish deploying and test the CloudFront domain.
