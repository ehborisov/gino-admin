Changelog
=========
Version 0.1.0 (current master) Updates
------------------------------------------
1. Added REST endpoint to upload data from CSV file to DB.
2. Cleaned up styles in UI.


Version 0.0.12 Updates
----------------------

1. Now menu in top menu are  hidden if you are not authorized

2. Added History logging for actions in Admin panel (edit, delete, add, init_db, load presets and etc) and History page for displaying.

3. Drop DB renamed in Init DB, that better describe feature

4. Fixed deepcopy for models with Integer IDs + other minor issues

5. In UI added normal Display for Bool properties - with check boxes

6. Added Calendar (date & time) pickers in UI for Datetime fields.

Version 0.0.11:
---------------
1. Added possibility to define custom route to Gino Admin Panel. With 'route=' config setting
By default, used '/admin' route

2. Added Demo Panel  `Gino-Admin demo`_ - you can log in and play with it. Login & pass - admin / 1234
If you don't see any data in UI maybe somebody before you cleaned it - go to Presets and load one of the data presets.

3. Fixed minors issues: 1)floats now displayed with fixed number of symbols. Parameter can be changed with config param `round_number=`.
2) now file upload fill not raise error if no file was chosen

4. Deepcopy now ask id - you can use auto-generated or define own id to 'deepcopy object'


Version 0.0.10 Updates:
-----------------------
1. GinoAdmin Config moved to Pydantic.
Added possible to send any properties to config with config dict.

2. Added Config param 'name' - this is a name, that will be showed in header near menu.
By Default it is display "Sanic-Gino Admin Panel", now you can change it to your header.

3. UI updates: Gino Admin Panel version now showed in UI footer, Login page now more presentable,
changed index page of Admin Panel, now it presented main feature.

4. Initialised first project's docs

5. Edit/Delete now take object's unique key as argument and stop fall if in key was '/' symbol

6. Added param 'csv_update_existed' in Config. By default 'csv_update_existed = True'. This mean if you upload CSV with rows with unique keys, that already exist in DB - it will update all fields with values from CSV.
You can turn off it with set 'csv_update_existed = False'.


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