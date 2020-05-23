Changelog
=========

Version 0.0.9 Updates:
----------------------
1. Added New feature: REST API to load DB Presets with token auth. Routes: admin/api/auth, admin/api/presets, admin/api/drop_db

2. New feature: Base Cli interface. Was added command `gino_admin run`

Version 0.0.8 Updates:
----------------------
1. Added more possibilities to use Gino Admin with applications in different frameworks (Fast API, or aiohttp, or any others)

1.1 Added example how to Gino Admin if main application developed with different Framework (Fast API or smth else). Example in **examples/use_with_any_framework_in_main_app**
1.2 added **create_admin_app** method to full init admin app as separate server
1.3 Old example moved to **base_example/** folder
1.4 in method 'init_admin_app' argument 'gino_models' was renamed to 'db_models'

2. Added support for Unique columns that used in models to identify data row.
Previous, your model must have 'id' column for correct work copy/edit/delete methods, but now required ANY unique column in table

Admin Panel checks 'unique' flag in the column. And first unique column will be used to define that row to delete/edit/or copy

If model does not have 'unique' column - it will not showed in admin panel and you will see error message about it in logs as warning.

3. Added display max len of fields in 'Add & Edit' forms

4. New feature "Composite CSV upload"
4.1 Added **Feature "Composite CSV data upload"** - possibility to define one CSV files, that contains several relative tables.
Used special to prepare dataset for demo purposes or tests. When it more effective and fast to define
relative data in one file.
4.2 Added new config param **composite_csv_settings** that allow to describe some patterns how must be parsed Composite CSV files.
Check more information in example and doc's section **Config**
4.3 Example with CSVs samples added to
5. Fixed issue with Logout.
6. Added page 'Settings' to check that Settings are used in admin panel. Display now composite_csv param & presets folder.
7. Added New Feature "Deepcopy" - recursive copy object and all objects, that depend on it.


Version 0.0.7 Updates:
----------------------
1. Fixes: datetime issue in 'Copy' action, delete all modal
2. New feature "Presets" (define multiple CSV files with data - upload all with one click).
3. New feature "Drop DB" (full clean up & recreate tables).

New features can be find under menu with 'Cogs' near 'SQL-Runner' button.



Version 0.0.6 Updates:
----------------------
1. Clean up template, hide row controls under menu.
2. Added 'Copy' option to DB row.
3. Now errors showed correct in table view pages in process of Delete, Copy, CSV Upload
4. Added possible to work without auth (for Debug purposes). Set env variable 'ADMIN_AUTH_DISABLE=True'
5. Template updated
6. Added export Table's Data to CSV
7. First version of SQL-query execution (run any query and get answer from PostgreSQL)
8. Fixed error display on csv upload


Version 0.0.5 Updates
----------------------

1. Upload from CSV: fixed upload from _hash fields - now in step of upload called hash function (same as in edit, or add per item)
2. Fixed errors relative to datetime fields edit, added datetime_str_formats field to Config object, that allows to add custom datetime str formats. They used in step of convert str from DB to datetime object.
3. Now '_hash' fields values in table showed as '***********'
4. Fixed errors relative to int id's. Now they works correct in edit and delete.
5. Update Menu template. Now if there is more when 4 models - they will be available under Dropdown menu.


Version 0.0.4 Updates:
----------------------

1. Upload from CSV - works, added example to `examples/` files. You can upload data from '.csv' tables.
2. Edit per row - now exist button 'edit'.
3. Fixed delete for ALL rows of the model
4. Fixed delete per element.
5. Now works full 'CRUD'.
6. Fixed auth, now it sets 'cookie' and compare user-agent (for multiple users per login)