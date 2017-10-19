# Dashboard

### Register

Please register to PDFsquid if you do not have an account already.

`https://dashboard.pdfsquid.com`

After verifying your email address you get access to dashboard. We will create a default project for you - starting with name `Demo project ...`. You can change it in Menu->Project settings.

## Navigation

Switch between projects with drop down selector on toolbar. Left menu navigation works in context with current selected project. Your account settings actions are hooked with the round button in top right window corner.

## Projects

Projects are isolated sets of all features - API accesses, cloud storage slots, user accesses. It also have separate billing information and invoices (on paid plans). You are administrator of at least one project which means you have full access to all features and you can eg. add new users to your project - see User management section. By default you can have two projects with administrator rights and unlimited projects as with different role - when somebody will invite you to his project. If you need more project with administrator rights please contact us with description of your needs.

## User management

As project administrator you can add new users to your project. On the user management view click `Add new` then fill in user email and desired permission role. You can select between:
Developer - user will have access to Overview, API accesses, Cloud storage, Live debug
Accountant - user will have access to Overview, Invoices, Reports
You can update user role later or delete user access.

## API accesses

In this view you can create, update and remove API access. In the simplest scenario you can just click `Add new` and click `Create`. Save generated credentials and your ready to convert documents.
However if you decide to convert documents asynchronously you might want to fill `Callback ping URL` to receive information after conversion. Check `Ping notifications` section for details. You can also set up `Storage slot`. Take a note these two features work in asynchronous mode only.
Api access works only in specified zone.

## Cloud storage

In this view you can create, update and remove cloud storage slots. We support Amazon S3 and Google GCS now.
These slots will be available in API access options. While setting up new slot we perform test upload to specified bucket to test access. Then we store credentials in encrypted storage.

## Invoices

List of available invoices. If project is on free plan we do not issue invoice.

## Reports

Aggregated statistics about API access usage - conversions count and data transfer in specified time period.

## Project settings

In this view you can set up project name, select plan for project and add business entity information for invoicing.

## Live debug

This function works like real time API monitor. It reports all actions that have place in all APIs in current project. Useful for debug purposes especially with asynchronous conversions.

## Account settings

You can find this view in user menu in top right window corner. There you can set up your personal settings.
