# csanewsc_mtc

## assets



name                  | column_type | ext_info       | ref                          | default | comment
--------------------- | ----------- | -------------- | ---------------------------- | ------- | -------
id                    | int         | [pk, not null] |                              |         |        
category_id           | int         | [null]         | [categories.id](#categories) |         |        
is_published          | tinyint     | [not null]     |                              |         |        
date_added            | datetime    | [null]         |                              |         |        
created_by            | int         | [null]         |                              |         |        
created_by_user       | varchar     | [null]         |                              |         |        
date_modified         | datetime    | [null]         |                              |         |        
modified_by           | int         | [null]         |                              |         |        
modified_by_user      | varchar     | [null]         |                              |         |        
checked_out           | datetime    | [null]         |                              |         |        
checked_out_by        | int         | [null]         |                              |         |        
checked_out_by_user   | varchar     | [null]         |                              |         |        
title                 | varchar     | [not null]     |                              |         |        
description           | longtext    | [null]         |                              |         |        
alias                 | varchar     | [not null]     |                              |         |        
storage_location      | varchar     | [null]         |                              |         |        
path                  | varchar     | [null]         |                              |         |        
remote_path           | longtext    | [null]         |                              |         |        
original_file_name    | longtext    | [null]         |                              |         |        
lang                  | varchar     | [not null]     |                              |         |        
publish_up            | datetime    | [null]         |                              |         |        
publish_down          | datetime    | [null]         |                              |         |        
download_count        | int         | [not null]     |                              |         |        
unique_download_count | int         | [not null]     |                              |         |        
revision              | int         | [not null]     |                              |         |        
extension             | varchar     | [null]         |                              |         |        
mime                  | varchar     | [null]         |                              |         |        
size                  | int         | [null]         |                              |         |        
disallow              | tinyint     | [null]         |                              |         |        

## asset_downloads



name          | column_type | ext_info       | ref                              | default | comment
------------- | ----------- | -------------- | -------------------------------- | ------- | -------
id            | bigint      | [pk, not null] |                                  |         |        
asset_id      | int         | [null]         | [assets.id](#assets)             |         |        
ip_id         | int         | [not null]     | [ip_addresses.id](#ip_addresses) |         |        
lead_id       | bigint      | [null]         | [leads.id](#leads)               |         |        
email_id      | int         | [null]         | [emails.id](#emails)             |         |        
date_download | datetime    | [not null]     |                                  |         |        
code          | int         | [not null]     |                                  |         |        
referer       | longtext    | [null]         |                                  |         |        
tracking_id   | varchar     | [not null]     |                                  |         |        
source        | varchar     | [null]         |                                  |         |        
source_id     | int         | [null]         |                                  |         |        

## audit_log



name       | column_type | ext_info       | ref | default | comment        
---------- | ----------- | -------------- | --- | ------- | ---------------
id         | bigint      | [pk, not null] |     |         |                
user_id    | int         | [not null]     |     |         |                
user_name  | varchar     | [not null]     |     |         |                
bundle     | varchar     | [not null]     |     |         |                
object     | varchar     | [not null]     |     |         |                
object_id  | bigint      | [not null]     |     |         |                
action     | varchar     | [not null]     |     |         |                
details    | longtext    | [null]         |     |         | (DC2Type:array)
date_added | datetime    | [not null]     |     |         |                
ip_address | varchar     | [not null]     |     |         |                

## cache_items



name          | column_type | ext_info       | ref | default | comment
------------- | ----------- | -------------- | --- | ------- | -------
item_id       | varbinary   | [pk, not null] |     |         |        
item_data     | longblob    | [not null]     |     |         |        
item_lifetime | int         | [null]         |     |         |        
item_time     | int         | [not null]     |     |         |        

## campaigns



name                | column_type | ext_info       | ref                          | default | comment        
------------------- | ----------- | -------------- | ---------------------------- | ------- | ---------------
id                  | int         | [pk, not null] |                              |         |                
category_id         | int         | [null]         | [categories.id](#categories) |         |                
is_published        | tinyint     | [not null]     |                              |         |                
date_added          | datetime    | [null]         |                              |         |                
created_by          | int         | [null]         |                              |         |                
created_by_user     | varchar     | [null]         |                              |         |                
date_modified       | datetime    | [null]         |                              |         |                
modified_by         | int         | [null]         |                              |         |                
modified_by_user    | varchar     | [null]         |                              |         |                
checked_out         | datetime    | [null]         |                              |         |                
checked_out_by      | int         | [null]         |                              |         |                
checked_out_by_user | varchar     | [null]         |                              |         |                
name                | varchar     | [not null]     |                              |         |                
description         | longtext    | [null]         |                              |         |                
publish_up          | datetime    | [null]         |                              |         |                
publish_down        | datetime    | [null]         |                              |         |                
canvas_settings     | longtext    | [null]         |                              |         | (DC2Type:array)
allow_restart       | int         | [not null]     |                              |         |                

## campaign_events



name                          | column_type | ext_info       | ref                                    | default | comment        
----------------------------- | ----------- | -------------- | -------------------------------------- | ------- | ---------------
id                            | int         | [pk, not null] |                                        |         |                
campaign_id                   | int         | [not null]     | [campaigns.id](#campaigns)             |         |                
parent_id                     | int         | [null]         | [campaign_events.id](#campaign_events) |         |                
name                          | varchar     | [not null]     |                                        |         |                
description                   | longtext    | [null]         |                                        |         |                
type                          | varchar     | [not null]     |                                        |         |                
event_type                    | varchar     | [not null]     |                                        |         |                
event_order                   | int         | [not null]     |                                        |         |                
properties                    | longtext    | [not null]     |                                        |         | (DC2Type:array)
trigger_date                  | datetime    | [null]         |                                        |         |                
trigger_interval              | int         | [null]         |                                        |         |                
trigger_interval_unit         | varchar     | [null]         |                                        |         |                
trigger_hour                  | time        | [null]         |                                        |         |                
trigger_restricted_start_hour | time        | [null]         |                                        |         |                
trigger_restricted_stop_hour  | time        | [null]         |                                        |         |                
trigger_restricted_dow        | longtext    | [null]         |                                        |         | (DC2Type:array)
trigger_mode                  | varchar     | [null]         |                                        |         |                
decision_path                 | varchar     | [null]         |                                        |         |                
temp_id                       | varchar     | [null]         |                                        |         |                
channel                       | varchar     | [null]         |                                        |         |                
channel_id                    | int         | [null]         |                                        |         |                

## campaign_form_xref



name        | column_type | ext_info       | ref                        | default | comment
----------- | ----------- | -------------- | -------------------------- | ------- | -------
campaign_id | int         | [pk, not null] | [campaigns.id](#campaigns) |         |        
form_id     | int         | [pk, not null] | [forms.id](#forms)         |         |        

## campaign_leadlist_xref



name        | column_type | ext_info       | ref                          | default | comment
----------- | ----------- | -------------- | ---------------------------- | ------- | -------
campaign_id | int         | [pk, not null] | [campaigns.id](#campaigns)   |         |        
leadlist_id | int         | [pk, not null] | [lead_lists.id](#lead_lists) |         |        

## campaign_leads



name             | column_type | ext_info       | ref                        | default | comment
---------------- | ----------- | -------------- | -------------------------- | ------- | -------
campaign_id      | int         | [pk, not null] | [campaigns.id](#campaigns) |         |        
lead_id          | bigint      | [pk, not null] | [leads.id](#leads)         |         |        
date_added       | datetime    | [not null]     |                            |         |        
manually_removed | tinyint     | [not null]     |                            |         |        
manually_added   | tinyint     | [not null]     |                            |         |        
date_last_exited | datetime    | [null]         |                            |         |        
rotation         | int         | [not null]     |                            |         |        

## campaign_lead_event_failed_log



name       | column_type | ext_info       | ref                                                    | default | comment
---------- | ----------- | -------------- | ------------------------------------------------------ | ------- | -------
log_id     | bigint      | [pk, not null] | [campaign_lead_event_log.id](#campaign_lead_event_log) |         |        
date_added | datetime    | [not null]     |                                                        |         |        
reason     | longtext    | [null]         |                                                        |         |        

## campaign_lead_event_log



name                  | column_type | ext_info       | ref                                    | default | comment        
--------------------- | ----------- | -------------- | -------------------------------------- | ------- | ---------------
id                    | bigint      | [pk, not null] |                                        |         |                
event_id              | int         | [not null]     | [campaign_events.id](#campaign_events) |         |                
lead_id               | bigint      | [not null]     | [leads.id](#leads)                     |         |                
campaign_id           | int         | [null]         | [campaigns.id](#campaigns)             |         |                
ip_id                 | int         | [null]         | [ip_addresses.id](#ip_addresses)       |         |                
rotation              | int         | [not null]     |                                        |         |                
date_triggered        | datetime    | [null]         |                                        |         |                
is_scheduled          | tinyint     | [not null]     |                                        |         |                
trigger_date          | datetime    | [null]         |                                        |         |                
system_triggered      | tinyint     | [not null]     |                                        |         |                
metadata              | longtext    | [null]         |                                        |         | (DC2Type:array)
channel               | varchar     | [null]         |                                        |         |                
channel_id            | int         | [null]         |                                        |         |                
non_action_path_taken | tinyint     | [null]         |                                        |         |                

## categories



name                | column_type | ext_info       | ref | default | comment
------------------- | ----------- | -------------- | --- | ------- | -------
id                  | int         | [pk, not null] |     |         |        
is_published        | tinyint     | [not null]     |     |         |        
date_added          | datetime    | [null]         |     |         |        
created_by          | int         | [null]         |     |         |        
created_by_user     | varchar     | [null]         |     |         |        
date_modified       | datetime    | [null]         |     |         |        
modified_by         | int         | [null]         |     |         |        
modified_by_user    | varchar     | [null]         |     |         |        
checked_out         | datetime    | [null]         |     |         |        
checked_out_by      | int         | [null]         |     |         |        
checked_out_by_user | varchar     | [null]         |     |         |        
title               | varchar     | [not null]     |     |         |        
description         | longtext    | [null]         |     |         |        
alias               | varchar     | [not null]     |     |         |        
color               | varchar     | [null]         |     |         |        
bundle              | varchar     | [not null]     |     |         |        

## channel_url_trackables



name        | column_type | ext_info       | ref                                  | default | comment
----------- | ----------- | -------------- | ------------------------------------ | ------- | -------
channel_id  | int         | [pk, not null] |                                      |         |        
redirect_id | bigint      | [pk, not null] | [page_redirects.id](#page_redirects) |         |        
channel     | varchar     | [not null]     |                                      |         |        
hits        | int         | [not null]     |                                      |         |        
unique_hits | int         | [not null]     |                                      |         |        

## companies



name                       | column_type | ext_info       | ref                | default | comment        
-------------------------- | ----------- | -------------- | ------------------ | ------- | ---------------
id                         | int         | [pk, not null] |                    |         |                
owner_id                   | int         | [null]         | [users.id](#users) |         |                
is_published               | tinyint     | [not null]     |                    |         |                
date_added                 | datetime    | [null]         |                    |         |                
created_by                 | int         | [null]         |                    |         |                
created_by_user            | varchar     | [null]         |                    |         |                
date_modified              | datetime    | [null]         |                    |         |                
modified_by                | int         | [null]         |                    |         |                
modified_by_user           | varchar     | [null]         |                    |         |                
checked_out                | datetime    | [null]         |                    |         |                
checked_out_by             | int         | [null]         |                    |         |                
checked_out_by_user        | varchar     | [null]         |                    |         |                
social_cache               | longtext    | [null]         |                    |         | (DC2Type:array)
score                      | int         | [null]         |                    |         |                
companyemail               | varchar     | [null]         |                    |         |                
companyaddress1            | varchar     | [null]         |                    |         |                
companyaddress2            | varchar     | [null]         |                    |         |                
companyphone               | varchar     | [null]         |                    |         |                
companycity                | varchar     | [null]         |                    |         |                
companystate               | varchar     | [null]         |                    |         |                
companyzipcode             | varchar     | [null]         |                    |         |                
companycountry             | varchar     | [null]         |                    |         |                
companyname                | varchar     | [null]         |                    |         |                
companywebsite             | longtext    | [null]         |                    |         |                
companyindustry            | varchar     | [null]         |                    |         |                
companydescription         | longtext    | [null]         |                    |         |                
companynumber_of_employees | double      | [null]         |                    |         |                
companyfax                 | varchar     | [null]         |                    |         |                
companyannual_revenue      | double      | [null]         |                    |         |                

## companies_leads



name       | column_type | ext_info       | ref                        | default | comment
---------- | ----------- | -------------- | -------------------------- | ------- | -------
company_id | int         | [pk, not null] | [companies.id](#companies) |         |        
lead_id    | bigint      | [pk, not null] | [leads.id](#leads)         |         |        
date_added | datetime    | [not null]     |                            |         |        
is_primary | tinyint     | [null]         |                            |         |        

## contact_merge_records



name       | column_type | ext_info       | ref                | default | comment
---------- | ----------- | -------------- | ------------------ | ------- | -------
id         | int         | [pk, not null] |                    |         |        
contact_id | bigint      | [not null]     | [leads.id](#leads) |         |        
date_added | datetime    | [not null]     |                    |         |        
merged_id  | int         | [not null]     |                    |         |        
name       | varchar     | [not null]     |                    |         |        

## dynamic_content



name                  | column_type | ext_info       | ref                                    | default | comment             
--------------------- | ----------- | -------------- | -------------------------------------- | ------- | --------------------
id                    | int         | [pk, not null] |                                        |         |                     
category_id           | int         | [null]         | [categories.id](#categories)           |         |                     
translation_parent_id | int         | [null]         | [dynamic_content.id](#dynamic_content) |         |                     
variant_parent_id     | int         | [null]         | [dynamic_content.id](#dynamic_content) |         |                     
is_published          | tinyint     | [not null]     |                                        |         |                     
date_added            | datetime    | [null]         |                                        |         |                     
created_by            | int         | [null]         |                                        |         |                     
created_by_user       | varchar     | [null]         |                                        |         |                     
date_modified         | datetime    | [null]         |                                        |         |                     
modified_by           | int         | [null]         |                                        |         |                     
modified_by_user      | varchar     | [null]         |                                        |         |                     
checked_out           | datetime    | [null]         |                                        |         |                     
checked_out_by        | int         | [null]         |                                        |         |                     
checked_out_by_user   | varchar     | [null]         |                                        |         |                     
name                  | varchar     | [not null]     |                                        |         |                     
description           | longtext    | [null]         |                                        |         |                     
publish_up            | datetime    | [null]         |                                        |         |                     
publish_down          | datetime    | [null]         |                                        |         |                     
sent_count            | int         | [not null]     |                                        |         |                     
content               | longtext    | [null]         |                                        |         |                     
utm_tags              | longtext    | [null]         |                                        |         | (DC2Type:json_array)
lang                  | varchar     | [not null]     |                                        |         |                     
variant_settings      | longtext    | [null]         |                                        |         | (DC2Type:array)     
variant_start_date    | datetime    | [null]         |                                        |         |                     
filters               | longtext    | [null]         |                                        |         | (DC2Type:array)     
is_campaign_based     | tinyint     | [not null]     |                                        |         |                     
slot_name             | varchar     | [null]         |                                        |         |                     

## dynamic_content_lead_data



name               | column_type | ext_info       | ref                                    | default | comment
------------------ | ----------- | -------------- | -------------------------------------- | ------- | -------
id                 | int         | [pk, not null] |                                        |         |        
lead_id            | bigint      | [not null]     | [leads.id](#leads)                     |         |        
dynamic_content_id | int         | [null]         | [dynamic_content.id](#dynamic_content) |         |        
date_added         | datetime    | [null]         |                                        |         |        
slot               | longtext    | [not null]     |                                        |         |        

## dynamic_content_stats



name               | column_type | ext_info       | ref                                    | default | comment        
------------------ | ----------- | -------------- | -------------------------------------- | ------- | ---------------
id                 | bigint      | [pk, not null] |                                        |         |                
dynamic_content_id | int         | [null]         | [dynamic_content.id](#dynamic_content) |         |                
lead_id            | bigint      | [null]         | [leads.id](#leads)                     |         |                
date_sent          | datetime    | [not null]     |                                        |         |                
source             | varchar     | [null]         |                                        |         |                
source_id          | int         | [null]         |                                        |         |                
tokens             | longtext    | [null]         |                                        |         | (DC2Type:array)
sent_count         | int         | [null]         |                                        |         |                
last_sent          | datetime    | [null]         |                                        |         |                
sent_details       | longtext    | [null]         |                                        |         | (DC2Type:array)

## emails



name                  | column_type | ext_info       | ref                          | default | comment             
--------------------- | ----------- | -------------- | ---------------------------- | ------- | --------------------
id                    | int         | [pk, not null] |                              |         |                     
category_id           | int         | [null]         | [categories.id](#categories) |         |                     
translation_parent_id | int         | [null]         | [emails.id](#emails)         |         |                     
variant_parent_id     | int         | [null]         | [emails.id](#emails)         |         |                     
unsubscribeform_id    | int         | [null]         | [forms.id](#forms)           |         |                     
preference_center_id  | int         | [null]         | [pages.id](#pages)           |         |                     
is_published          | tinyint     | [not null]     |                              |         |                     
date_added            | datetime    | [null]         |                              |         |                     
created_by            | int         | [null]         |                              |         |                     
created_by_user       | varchar     | [null]         |                              |         |                     
date_modified         | datetime    | [null]         |                              |         |                     
modified_by           | int         | [null]         |                              |         |                     
modified_by_user      | varchar     | [null]         |                              |         |                     
checked_out           | datetime    | [null]         |                              |         |                     
checked_out_by        | int         | [null]         |                              |         |                     
checked_out_by_user   | varchar     | [null]         |                              |         |                     
name                  | varchar     | [not null]     |                              |         |                     
description           | longtext    | [null]         |                              |         |                     
subject               | longtext    | [null]         |                              |         |                     
from_address          | varchar     | [null]         |                              |         |                     
from_name             | varchar     | [null]         |                              |         |                     
reply_to_address      | varchar     | [null]         |                              |         |                     
bcc_address           | varchar     | [null]         |                              |         |                     
template              | varchar     | [null]         |                              |         |                     
content               | longtext    | [null]         |                              |         | (DC2Type:array)     
utm_tags              | longtext    | [null]         |                              |         | (DC2Type:array)     
plain_text            | longtext    | [null]         |                              |         |                     
custom_html           | longtext    | [null]         |                              |         |                     
email_type            | longtext    | [null]         |                              |         |                     
use_owner_as_mailer   | tinyint     | [null]         |                              |         |                     
publish_up            | datetime    | [null]         |                              |         |                     
publish_down          | datetime    | [null]         |                              |         |                     
read_count            | int         | [not null]     |                              |         |                     
sent_count            | int         | [not null]     |                              |         |                     
variant_sent_count    | int         | [not null]     |                              |         |                     
variant_read_count    | int         | [not null]     |                              |         |                     
revision              | int         | [not null]     |                              |         |                     
lang                  | varchar     | [not null]     |                              |         |                     
variant_settings      | longtext    | [null]         |                              |         | (DC2Type:array)     
variant_start_date    | datetime    | [null]         |                              |         |                     
dynamic_content       | longtext    | [null]         |                              |         | (DC2Type:array)     
headers               | longtext    | [not null]     |                              |         | (DC2Type:json_array)
public_preview        | tinyint     | [null]         |                              |         |                     

## email_assets_xref



name     | column_type | ext_info       | ref                  | default | comment
-------- | ----------- | -------------- | -------------------- | ------- | -------
email_id | int         | [pk, not null] | [emails.id](#emails) |         |        
asset_id | int         | [pk, not null] | [assets.id](#assets) |         |        

## email_copies



name         | column_type | ext_info       | ref | default | comment
------------ | ----------- | -------------- | --- | ------- | -------
id           | varchar     | [pk, not null] |     |         |        
date_created | datetime    | [not null]     |     |         |        
body         | longtext    | [null]         |     |         |        
subject      | longtext    | [null]         |     |         |        

## email_list_xref



name        | column_type | ext_info       | ref                          | default | comment
----------- | ----------- | -------------- | ---------------------------- | ------- | -------
email_id    | int         | [pk, not null] | [emails.id](#emails)         |         |        
leadlist_id | int         | [pk, not null] | [lead_lists.id](#lead_lists) |         |        

## email_stats



name                | column_type | ext_info       | ref                              | default | comment            
------------------- | ----------- | -------------- | -------------------------------- | ------- | -------------------
id                  | bigint      | [pk, not null] |                                  |         |                    
email_id            | int         | [null]         | [emails.id](#emails)             |         |                    
lead_id             | bigint      | [null]         | [leads.id](#leads)               |         |                    
list_id             | int         | [null]         | [lead_lists.id](#lead_lists)     |         |                    
ip_id               | int         | [null]         | [ip_addresses.id](#ip_addresses) |         |                    
copy_id             | varchar     | [null]         | [email_copies.id](#email_copies) |         |                    
email_address       | varchar     | [not null]     |                                  |         |                    
date_sent           | datetime    | [not null]     |                                  |         |                    
is_read             | tinyint     | [not null]     |                                  |         |                    
is_failed           | tinyint     | [not null]     |                                  |         |                    
viewed_in_browser   | tinyint     | [not null]     |                                  |         |                    
date_read           | datetime    | [null]         |                                  |         |                    
tracking_hash       | varchar     | [null]         |                                  |         |                    
retry_count         | int         | [null]         |                                  |         |                    
source              | varchar     | [null]         |                                  |         |                    
source_id           | int         | [null]         |                                  |         |                    
tokens              | longtext    | [null]         |                                  |         | (DC2Type:array)    
open_count          | int         | [null]         |                                  |         |                    
last_opened         | datetime    | [null]         |                                  |         |                    
open_details        | longtext    | [null]         |                                  |         | (DC2Type:array)    
generated_sent_date | date        | [null]         |                                  |         | (DC2Type:generated)

## email_stats_devices



name        | column_type | ext_info       | ref                              | default | comment
----------- | ----------- | -------------- | -------------------------------- | ------- | -------
id          | bigint      | [pk, not null] |                                  |         |        
device_id   | bigint      | [null]         | [lead_devices.id](#lead_devices) |         |        
stat_id     | bigint      | [null]         | [email_stats.id](#email_stats)   |         |        
ip_id       | int         | [null]         | [ip_addresses.id](#ip_addresses) |         |        
date_opened | datetime    | [not null]     |                                  |         |        

## email_stat_replies



name         | column_type | ext_info       | ref                            | default | comment       
------------ | ----------- | -------------- | ------------------------------ | ------- | --------------
id           | char        | [pk, not null] |                                |         | (DC2Type:guid)
stat_id      | bigint      | [not null]     | [email_stats.id](#email_stats) |         |               
date_replied | datetime    | [not null]     |                                |         |               
message_id   | varchar     | [not null]     |                                |         |               

## focus



name                | column_type | ext_info       | ref                          | default | comment        
------------------- | ----------- | -------------- | ---------------------------- | ------- | ---------------
id                  | int         | [pk, not null] |                              |         |                
category_id         | int         | [null]         | [categories.id](#categories) |         |                
is_published        | tinyint     | [not null]     |                              |         |                
date_added          | datetime    | [null]         |                              |         |                
created_by          | int         | [null]         |                              |         |                
created_by_user     | varchar     | [null]         |                              |         |                
date_modified       | datetime    | [null]         |                              |         |                
modified_by         | int         | [null]         |                              |         |                
modified_by_user    | varchar     | [null]         |                              |         |                
checked_out         | datetime    | [null]         |                              |         |                
checked_out_by      | int         | [null]         |                              |         |                
checked_out_by_user | varchar     | [null]         |                              |         |                
name                | varchar     | [not null]     |                              |         |                
description         | longtext    | [null]         |                              |         |                
focus_type          | varchar     | [not null]     |                              |         |                
style               | varchar     | [not null]     |                              |         |                
website             | varchar     | [null]         |                              |         |                
publish_up          | datetime    | [null]         |                              |         |                
publish_down        | datetime    | [null]         |                              |         |                
properties          | longtext    | [null]         |                              |         | (DC2Type:array)
utm_tags            | longtext    | [null]         |                              |         | (DC2Type:array)
form_id             | int         | [null]         |                              |         |                
cache               | longtext    | [null]         |                              |         |                
html_mode           | varchar     | [null]         |                              |         |                
editor              | longtext    | [null]         |                              |         |                
html                | longtext    | [null]         |                              |         |                

## focus_stats



name       | column_type | ext_info       | ref                | default | comment
---------- | ----------- | -------------- | ------------------ | ------- | -------
id         | int         | [pk, not null] |                    |         |        
focus_id   | int         | [not null]     | [focus.id](#focus) |         |        
lead_id    | bigint      | [null]         | [leads.id](#leads) |         |        
type       | varchar     | [not null]     |                    |         |        
type_id    | int         | [null]         |                    |         |        
date_added | datetime    | [not null]     |                    |         |        

## forms



name                        | column_type | ext_info       | ref                          | default | comment
--------------------------- | ----------- | -------------- | ---------------------------- | ------- | -------
id                          | int         | [pk, not null] |                              |         |        
category_id                 | int         | [null]         | [categories.id](#categories) |         |        
is_published                | tinyint     | [not null]     |                              |         |        
date_added                  | datetime    | [null]         |                              |         |        
created_by                  | int         | [null]         |                              |         |        
created_by_user             | varchar     | [null]         |                              |         |        
date_modified               | datetime    | [null]         |                              |         |        
modified_by                 | int         | [null]         |                              |         |        
modified_by_user            | varchar     | [null]         |                              |         |        
checked_out                 | datetime    | [null]         |                              |         |        
checked_out_by              | int         | [null]         |                              |         |        
checked_out_by_user         | varchar     | [null]         |                              |         |        
name                        | varchar     | [not null]     |                              |         |        
description                 | longtext    | [null]         |                              |         |        
alias                       | varchar     | [not null]     |                              |         |        
form_attr                   | varchar     | [null]         |                              |         |        
cached_html                 | longtext    | [null]         |                              |         |        
post_action                 | varchar     | [not null]     |                              |         |        
post_action_property        | varchar     | [null]         |                              |         |        
publish_up                  | datetime    | [null]         |                              |         |        
publish_down                | datetime    | [null]         |                              |         |        
template                    | varchar     | [null]         |                              |         |        
in_kiosk_mode               | tinyint     | [null]         |                              |         |        
render_style                | tinyint     | [null]         |                              |         |        
form_type                   | varchar     | [null]         |                              |         |        
no_index                    | tinyint     | [null]         |                              |         |        
progressive_profiling_limit | int         | [null]         |                              |         |        

## form_actions



name         | column_type | ext_info       | ref                | default | comment        
------------ | ----------- | -------------- | ------------------ | ------- | ---------------
id           | int         | [pk, not null] |                    |         |                
form_id      | int         | [not null]     | [forms.id](#forms) |         |                
name         | varchar     | [not null]     |                    |         |                
description  | longtext    | [null]         |                    |         |                
type         | varchar     | [not null]     |                    |         |                
action_order | int         | [not null]     |                    |         |                
properties   | longtext    | [not null]     |                    |         | (DC2Type:array)

## form_fields



name                     | column_type | ext_info       | ref                | default | comment             
------------------------ | ----------- | -------------- | ------------------ | ------- | --------------------
id                       | int         | [pk, not null] |                    |         |                     
form_id                  | int         | [not null]     | [forms.id](#forms) |         |                     
label                    | longtext    | [not null]     |                    |         |                     
show_label               | tinyint     | [null]         |                    |         |                     
alias                    | varchar     | [not null]     |                    |         |                     
type                     | varchar     | [not null]     |                    |         |                     
is_custom                | tinyint     | [not null]     |                    |         |                     
custom_parameters        | longtext    | [null]         |                    |         | (DC2Type:array)     
default_value            | longtext    | [null]         |                    |         |                     
is_required              | tinyint     | [not null]     |                    |         |                     
validation_message       | longtext    | [null]         |                    |         |                     
help_message             | longtext    | [null]         |                    |         |                     
field_order              | int         | [null]         |                    |         |                     
properties               | longtext    | [null]         |                    |         | (DC2Type:array)     
validation               | longtext    | [null]         |                    |         | (DC2Type:json_array)
label_attr               | varchar     | [null]         |                    |         |                     
input_attr               | varchar     | [null]         |                    |         |                     
container_attr           | varchar     | [null]         |                    |         |                     
lead_field               | varchar     | [null]         |                    |         |                     
save_result              | tinyint     | [null]         |                    |         |                     
is_auto_fill             | tinyint     | [null]         |                    |         |                     
show_when_value_exists   | tinyint     | [null]         |                    |         |                     
show_after_x_submissions | int         | [null]         |                    |         |                     
always_display           | tinyint     | [null]         |                    |         |                     

## form_results_1_sa_cricket



name               | column_type | ext_info       | ref | default | comment
------------------ | ----------- | -------------- | --- | ------- | -------
submission_id      | int         | [pk, not null] |     |         |        
form_id            | int         | [not null]     |     |         |        
first_name         | longtext    | [null]         |     |         |        
last_name          | longtext    | [null]         |     |         |        
email_address      | longtext    | [null]         |     |         |        
phone_number       | longtext    | [null]         |     |         |        
your_home_province | longtext    | [null]         |     |         |        

## form_results_2_extraearly



name                      | column_type | ext_info       | ref | default | comment
------------------------- | ----------- | -------------- | --- | ------- | -------
submission_id             | int         | [pk, not null] |     |         |        
form_id                   | int         | [not null]     |     |         |        
first_name                | longtext    | [null]         |     |         |        
last_name                 | longtext    | [null]         |     |         |        
email_address             | longtext    | [null]         |     |         |        
phone_number              | longtext    | [null]         |     |         |        
your_home_province        | longtext    | [null]         |     |         |        
i_acknowledge_that_as_par | longtext    | [null]         |     |         |        
i_agree_to_the_terms__con | longtext    | [null]         |     |         |        
your_home_province1       | longtext    | [null]         |     |         |        

## form_results_3_sa_cricket



name                      | column_type | ext_info       | ref | default | comment
------------------------- | ----------- | -------------- | --- | ------- | -------
submission_id             | int         | [pk, not null] |     |         |        
form_id                   | int         | [not null]     |     |         |        
email_address             | longtext    | [null]         |     |         |        
your_home_province1       | longtext    | [null]         |     |         |        
i_acknowledge_that_as_par | longtext    | [null]         |     |         |        
i_agree_to_the_terms__con | longtext    | [null]         |     |         |        
first_name                | longtext    | [null]         |     |         |        
last_name                 | longtext    | [null]         |     |         |        
phone_number              | longtext    | [null]         |     |         |        

## form_results_4_sa_cricket



name                      | column_type | ext_info       | ref | default | comment
------------------------- | ----------- | -------------- | --- | ------- | -------
submission_id             | int         | [pk, not null] |     |         |        
form_id                   | int         | [not null]     |     |         |        
first_name                | longtext    | [null]         |     |         |        
last_name                 | longtext    | [null]         |     |         |        
email_address             | longtext    | [null]         |     |         |        
phone_number              | longtext    | [null]         |     |         |        
your_home_province1       | longtext    | [null]         |     |         |        
i_acknowledge_that_as_par | longtext    | [null]         |     |         |        
i_agree_to_the_terms__con | longtext    | [null]         |     |         |        

## form_results_5_sa_cricket



name                      | column_type | ext_info       | ref | default | comment
------------------------- | ----------- | -------------- | --- | ------- | -------
submission_id             | int         | [pk, not null] |     |         |        
form_id                   | int         | [not null]     |     |         |        
first_name                | longtext    | [null]         |     |         |        
last_name                 | longtext    | [null]         |     |         |        
email_address             | longtext    | [null]         |     |         |        
phone_number              | longtext    | [null]         |     |         |        
your_home_province1       | longtext    | [null]         |     |         |        
i_acknowledge_that_as_par | longtext    | [null]         |     |         |        
i_agree_to_the_terms__con | longtext    | [null]         |     |         |        

## form_submissions



name           | column_type | ext_info       | ref                              | default | comment
-------------- | ----------- | -------------- | -------------------------------- | ------- | -------
id             | bigint      | [pk, not null] |                                  |         |        
form_id        | int         | [not null]     | [forms.id](#forms)               |         |        
ip_id          | int         | [not null]     | [ip_addresses.id](#ip_addresses) |         |        
lead_id        | bigint      | [null]         | [leads.id](#leads)               |         |        
page_id        | int         | [null]         | [pages.id](#pages)               |         |        
tracking_id    | varchar     | [null]         |                                  |         |        
date_submitted | datetime    | [not null]     |                                  |         |        
referer        | longtext    | [not null]     |                                  |         |        

## imports



name                | column_type | ext_info       | ref | default | comment             
------------------- | ----------- | -------------- | --- | ------- | --------------------
id                  | int         | [pk, not null] |     |         |                     
is_published        | tinyint     | [not null]     |     |         |                     
date_added          | datetime    | [null]         |     |         |                     
created_by          | int         | [null]         |     |         |                     
created_by_user     | varchar     | [null]         |     |         |                     
date_modified       | datetime    | [null]         |     |         |                     
modified_by         | int         | [null]         |     |         |                     
modified_by_user    | varchar     | [null]         |     |         |                     
checked_out         | datetime    | [null]         |     |         |                     
checked_out_by      | int         | [null]         |     |         |                     
checked_out_by_user | varchar     | [null]         |     |         |                     
dir                 | varchar     | [not null]     |     |         |                     
file                | varchar     | [not null]     |     |         |                     
original_file       | varchar     | [null]         |     |         |                     
line_count          | int         | [not null]     |     |         |                     
inserted_count      | int         | [not null]     |     |         |                     
updated_count       | int         | [not null]     |     |         |                     
ignored_count       | int         | [not null]     |     |         |                     
priority            | int         | [not null]     |     |         |                     
status              | int         | [not null]     |     |         |                     
date_started        | datetime    | [null]         |     |         |                     
date_ended          | datetime    | [null]         |     |         |                     
object              | varchar     | [not null]     |     |         |                     
properties          | longtext    | [null]         |     |         | (DC2Type:json_array)

## integration_entity



name                  | column_type | ext_info       | ref | default | comment        
--------------------- | ----------- | -------------- | --- | ------- | ---------------
id                    | int         | [pk, not null] |     |         |                
date_added            | datetime    | [not null]     |     |         |                
integration           | varchar     | [null]         |     |         |                
integration_entity    | varchar     | [null]         |     |         |                
integration_entity_id | varchar     | [null]         |     |         |                
internal_entity       | varchar     | [null]         |     |         |                
internal_entity_id    | int         | [null]         |     |         |                
last_sync_date        | datetime    | [null]         |     |         |                
internal              | longtext    | [null]         |     |         | (DC2Type:array)

## ip_addresses



name       | column_type | ext_info       | ref | default | comment        
---------- | ----------- | -------------- | --- | ------- | ---------------
id         | int         | [pk, not null] |     |         |                
ip_address | varchar     | [not null]     |     |         |                
ip_details | longtext    | [null]         |     |         | (DC2Type:array)

## leads



name                     | column_type | ext_info       | ref                  | default | comment        
------------------------ | ----------- | -------------- | -------------------- | ------- | ---------------
id                       | bigint      | [pk, not null] |                      |         |                
owner_id                 | int         | [null]         | [users.id](#users)   |         |                
stage_id                 | int         | [null]         | [stages.id](#stages) |         |                
is_published             | tinyint     | [not null]     |                      |         |                
date_added               | datetime    | [null]         |                      |         |                
created_by               | int         | [null]         |                      |         |                
created_by_user          | varchar     | [null]         |                      |         |                
date_modified            | datetime    | [null]         |                      |         |                
modified_by              | int         | [null]         |                      |         |                
modified_by_user         | varchar     | [null]         |                      |         |                
checked_out              | datetime    | [null]         |                      |         |                
checked_out_by           | int         | [null]         |                      |         |                
checked_out_by_user      | varchar     | [null]         |                      |         |                
points                   | int         | [not null]     |                      |         |                
last_active              | datetime    | [null]         |                      |         |                
internal                 | longtext    | [null]         |                      |         | (DC2Type:array)
social_cache             | longtext    | [null]         |                      |         | (DC2Type:array)
date_identified          | datetime    | [null]         |                      |         |                
preferred_profile_image  | varchar     | [null]         |                      |         |                
title                    | varchar     | [null]         |                      |         |                
firstname                | varchar     | [null]         |                      |         |                
lastname                 | varchar     | [null]         |                      |         |                
company                  | varchar     | [null]         |                      |         |                
position                 | varchar     | [null]         |                      |         |                
email                    | varchar     | [null]         |                      |         |                
phone                    | varchar     | [null]         |                      |         |                
mobile                   | varchar     | [null]         |                      |         |                
address1                 | varchar     | [null]         |                      |         |                
address2                 | varchar     | [null]         |                      |         |                
city                     | varchar     | [null]         |                      |         |                
state                    | varchar     | [null]         |                      |         |                
zipcode                  | varchar     | [null]         |                      |         |                
timezone                 | varchar     | [null]         |                      |         |                
country                  | varchar     | [null]         |                      |         |                
fax                      | varchar     | [null]         |                      |         |                
preferred_locale         | varchar     | [null]         |                      |         |                
attribution_date         | datetime    | [null]         |                      |         |                
attribution              | double      | [null]         |                      |         |                
website                  | longtext    | [null]         |                      |         |                
facebook                 | varchar     | [null]         |                      |         |                
foursquare               | varchar     | [null]         |                      |         |                
instagram                | varchar     | [null]         |                      |         |                
linkedin                 | varchar     | [null]         |                      |         |                
skype                    | varchar     | [null]         |                      |         |                
twitter                  | varchar     | [null]         |                      |         |                
dob                      | date        | [null]         |                      |         |                
opscmember               | tinyint     | [null]         |                      |         |                
ticketmember             | tinyint     | [null]         |                      |         |                
appmember                | tinyint     | [null]         |                      |         |                
contactid_centraldbs     | double      | [null]         |                      |         |                
source                   | varchar     | [null]         |                      |         |                
tcchecktickets           | tinyint     | [null]         |                      |         |                
sentemailcheckfortickets | tinyint     | [null]         |                      |         |                
homeprovince             | varchar     | [null]         |                      |         |                
created_date             | datetime    | [null]         |                      |         |                

## lead_categories



name             | column_type | ext_info       | ref                          | default | comment
---------------- | ----------- | -------------- | ---------------------------- | ------- | -------
id               | int         | [pk, not null] |                              |         |        
category_id      | int         | [not null]     | [categories.id](#categories) |         |        
lead_id          | bigint      | [not null]     | [leads.id](#leads)           |         |        
date_added       | datetime    | [not null]     |                              |         |        
manually_removed | tinyint     | [not null]     |                              |         |        
manually_added   | tinyint     | [not null]     |                              |         |        

## lead_companies_change_log



name        | column_type | ext_info       | ref                | default | comment
----------- | ----------- | -------------- | ------------------ | ------- | -------
id          | int         | [pk, not null] |                    |         |        
lead_id     | bigint      | [not null]     | [leads.id](#leads) |         |        
type        | tinytext    | [not null]     |                    |         |        
event_name  | varchar     | [not null]     |                    |         |        
action_name | varchar     | [not null]     |                    |         |        
company_id  | int         | [not null]     |                    |         |        
date_added  | datetime    | [not null]     |                    |         |        

## lead_devices



name                | column_type | ext_info       | ref                | default | comment        
------------------- | ----------- | -------------- | ------------------ | ------- | ---------------
id                  | bigint      | [pk, not null] |                    |         |                
lead_id             | bigint      | [not null]     | [leads.id](#leads) |         |                
date_added          | datetime    | [not null]     |                    |         |                
client_info         | longtext    | [null]         |                    |         | (DC2Type:array)
device              | varchar     | [null]         |                    |         |                
device_os_name      | varchar     | [null]         |                    |         |                
device_os_shortname | varchar     | [null]         |                    |         |                
device_os_version   | varchar     | [null]         |                    |         |                
device_os_platform  | varchar     | [null]         |                    |         |                
device_brand        | varchar     | [null]         |                    |         |                
device_model        | varchar     | [null]         |                    |         |                
tracking_id         | varchar     | [null]         |                    |         |                

## lead_donotcontact



name       | column_type | ext_info       | ref                | default | comment
---------- | ----------- | -------------- | ------------------ | ------- | -------
id         | int         | [pk, not null] |                    |         |        
lead_id    | bigint      | [null]         | [leads.id](#leads) |         |        
date_added | datetime    | [not null]     |                    |         |        
reason     | smallint    | [not null]     |                    |         |        
channel    | varchar     | [not null]     |                    |         |        
channel_id | int         | [null]         |                    |         |        
comments   | longtext    | [null]         |                    |         |        

## lead_event_log



name       | column_type | ext_info       | ref                | default | comment             
---------- | ----------- | -------------- | ------------------ | ------- | --------------------
id         | bigint      | [pk, not null] |                    |         |                     
lead_id    | bigint      | [null]         | [leads.id](#leads) |         |                     
user_id    | int         | [null]         |                    |         |                     
user_name  | varchar     | [null]         |                    |         |                     
bundle     | varchar     | [null]         |                    |         |                     
object     | varchar     | [null]         |                    |         |                     
action     | varchar     | [null]         |                    |         |                     
object_id  | int         | [null]         |                    |         |                     
date_added | datetime    | [not null]     |                    |         |                     
properties | longtext    | [null]         |                    |         | (DC2Type:json_array)

## lead_fields



name                        | column_type | ext_info       | ref | default | comment        
--------------------------- | ----------- | -------------- | --- | ------- | ---------------
id                          | int         | [pk, not null] |     |         |                
is_published                | tinyint     | [not null]     |     |         |                
date_added                  | datetime    | [null]         |     |         |                
created_by                  | int         | [null]         |     |         |                
created_by_user             | varchar     | [null]         |     |         |                
date_modified               | datetime    | [null]         |     |         |                
modified_by                 | int         | [null]         |     |         |                
modified_by_user            | varchar     | [null]         |     |         |                
checked_out                 | datetime    | [null]         |     |         |                
checked_out_by              | int         | [null]         |     |         |                
checked_out_by_user         | varchar     | [null]         |     |         |                
label                       | varchar     | [not null]     |     |         |                
alias                       | varchar     | [not null]     |     |         |                
type                        | varchar     | [not null]     |     |         |                
field_group                 | varchar     | [null]         |     |         |                
default_value               | varchar     | [null]         |     |         |                
is_required                 | tinyint     | [not null]     |     |         |                
is_fixed                    | tinyint     | [not null]     |     |         |                
is_visible                  | tinyint     | [not null]     |     |         |                
is_short_visible            | tinyint     | [not null]     |     |         |                
is_listable                 | tinyint     | [not null]     |     |         |                
is_publicly_updatable       | tinyint     | [not null]     |     |         |                
is_unique_identifer         | tinyint     | [null]         |     |         |                
field_order                 | int         | [null]         |     |         |                
object                      | varchar     | [null]         |     |         |                
properties                  | longtext    | [null]         |     |         | (DC2Type:array)
column_is_not_created       | tinyint     | [not null]     |     |         |                
original_is_published_value | tinyint     | [not null]     |     |         |                

## lead_frequencyrules



name              | column_type | ext_info       | ref                | default | comment
----------------- | ----------- | -------------- | ------------------ | ------- | -------
id                | int         | [pk, not null] |                    |         |        
lead_id           | bigint      | [not null]     | [leads.id](#leads) |         |        
date_added        | datetime    | [not null]     |                    |         |        
frequency_number  | smallint    | [null]         |                    |         |        
frequency_time    | varchar     | [null]         |                    |         |        
channel           | varchar     | [not null]     |                    |         |        
preferred_channel | tinyint     | [not null]     |                    |         |        
pause_from_date   | datetime    | [null]         |                    |         |        
pause_to_date     | datetime    | [null]         |                    |         |        

## lead_ips_xref



name    | column_type | ext_info       | ref                              | default | comment
------- | ----------- | -------------- | -------------------------------- | ------- | -------
lead_id | bigint      | [pk, not null] | [leads.id](#leads)               |         |        
ip_id   | int         | [pk, not null] | [ip_addresses.id](#ip_addresses) |         |        

## lead_lists



name                 | column_type | ext_info       | ref                          | default | comment        
-------------------- | ----------- | -------------- | ---------------------------- | ------- | ---------------
id                   | int         | [pk, not null] |                              |         |                
is_published         | tinyint     | [not null]     |                              |         |                
date_added           | datetime    | [null]         |                              |         |                
created_by           | int         | [null]         |                              |         |                
created_by_user      | varchar     | [null]         |                              |         |                
date_modified        | datetime    | [null]         |                              |         |                
modified_by          | int         | [null]         |                              |         |                
modified_by_user     | varchar     | [null]         |                              |         |                
checked_out          | datetime    | [null]         |                              |         |                
checked_out_by       | int         | [null]         |                              |         |                
checked_out_by_user  | varchar     | [null]         |                              |         |                
name                 | varchar     | [not null]     |                              |         |                
description          | longtext    | [null]         |                              |         |                
alias                | varchar     | [not null]     |                              |         |                
filters              | longtext    | [not null]     |                              |         | (DC2Type:array)
is_global            | tinyint     | [not null]     |                              |         |                
is_preference_center | tinyint     | [not null]     |                              |         |                
public_name          | varchar     | [not null]     |                              |         |                
category_id          | int         | [null]         | [categories.id](#categories) |         |                

## lead_lists_leads



name             | column_type | ext_info       | ref                          | default | comment
---------------- | ----------- | -------------- | ---------------------------- | ------- | -------
leadlist_id      | int         | [pk, not null] | [lead_lists.id](#lead_lists) |         |        
lead_id          | bigint      | [pk, not null] | [leads.id](#leads)           |         |        
date_added       | datetime    | [not null]     |                              |         |        
manually_removed | tinyint     | [not null]     |                              |         |        
manually_added   | tinyint     | [not null]     |                              |         |        

## lead_notes



name                | column_type | ext_info       | ref                | default | comment
------------------- | ----------- | -------------- | ------------------ | ------- | -------
id                  | int         | [pk, not null] |                    |         |        
lead_id             | bigint      | [not null]     | [leads.id](#leads) |         |        
is_published        | tinyint     | [not null]     |                    |         |        
date_added          | datetime    | [null]         |                    |         |        
created_by          | int         | [null]         |                    |         |        
created_by_user     | varchar     | [null]         |                    |         |        
date_modified       | datetime    | [null]         |                    |         |        
modified_by         | int         | [null]         |                    |         |        
modified_by_user    | varchar     | [null]         |                    |         |        
checked_out         | datetime    | [null]         |                    |         |        
checked_out_by      | int         | [null]         |                    |         |        
checked_out_by_user | varchar     | [null]         |                    |         |        
text                | longtext    | [not null]     |                    |         |        
type                | varchar     | [null]         |                    |         |        
date_time           | datetime    | [null]         |                    |         |        

## lead_points_change_log



name        | column_type | ext_info       | ref                              | default | comment
----------- | ----------- | -------------- | -------------------------------- | ------- | -------
id          | bigint      | [pk, not null] |                                  |         |        
lead_id     | bigint      | [not null]     | [leads.id](#leads)               |         |        
ip_id       | int         | [not null]     | [ip_addresses.id](#ip_addresses) |         |        
type        | tinytext    | [not null]     |                                  |         |        
event_name  | varchar     | [not null]     |                                  |         |        
action_name | varchar     | [not null]     |                                  |         |        
delta       | int         | [not null]     |                                  |         |        
date_added  | datetime    | [not null]     |                                  |         |        

## lead_stages_change_log



name        | column_type | ext_info       | ref                  | default | comment
----------- | ----------- | -------------- | -------------------- | ------- | -------
id          | int         | [pk, not null] |                      |         |        
lead_id     | bigint      | [not null]     | [leads.id](#leads)   |         |        
stage_id    | int         | [null]         | [stages.id](#stages) |         |        
event_name  | varchar     | [not null]     |                      |         |        
action_name | varchar     | [not null]     |                      |         |        
date_added  | datetime    | [not null]     |                      |         |        

## lead_tags



name | column_type | ext_info       | ref | default | comment
---- | ----------- | -------------- | --- | ------- | -------
id   | int         | [pk, not null] |     |         |        
tag  | varchar     | [not null]     |     |         |        

## lead_tags_xref



name    | column_type | ext_info       | ref                        | default | comment
------- | ----------- | -------------- | -------------------------- | ------- | -------
lead_id | bigint      | [pk, not null] | [leads.id](#leads)         |         |        
tag_id  | int         | [pk, not null] | [lead_tags.id](#lead_tags) |         |        

## lead_utmtags



name         | column_type | ext_info       | ref                | default | comment        
------------ | ----------- | -------------- | ------------------ | ------- | ---------------
id           | int         | [pk, not null] |                    |         |                
lead_id      | bigint      | [not null]     | [leads.id](#leads) |         |                
date_added   | datetime    | [not null]     |                    |         |                
query        | longtext    | [null]         |                    |         | (DC2Type:array)
referer      | longtext    | [null]         |                    |         |                
remote_host  | varchar     | [null]         |                    |         |                
url          | longtext    | [null]         |                    |         |                
user_agent   | longtext    | [null]         |                    |         |                
utm_campaign | varchar     | [null]         |                    |         |                
utm_content  | varchar     | [null]         |                    |         |                
utm_medium   | varchar     | [null]         |                    |         |                
utm_source   | varchar     | [null]         |                    |         |                
utm_term     | varchar     | [null]         |                    |         |                

## messages



name                | column_type | ext_info       | ref                          | default | comment
------------------- | ----------- | -------------- | ---------------------------- | ------- | -------
id                  | int         | [pk, not null] |                              |         |        
category_id         | int         | [null]         | [categories.id](#categories) |         |        
is_published        | tinyint     | [not null]     |                              |         |        
date_added          | datetime    | [null]         |                              |         |        
created_by          | int         | [null]         |                              |         |        
created_by_user     | varchar     | [null]         |                              |         |        
date_modified       | datetime    | [null]         |                              |         |        
modified_by         | int         | [null]         |                              |         |        
modified_by_user    | varchar     | [null]         |                              |         |        
checked_out         | datetime    | [null]         |                              |         |        
checked_out_by      | int         | [null]         |                              |         |        
checked_out_by_user | varchar     | [null]         |                              |         |        
name                | varchar     | [not null]     |                              |         |        
description         | longtext    | [null]         |                              |         |        
publish_up          | datetime    | [null]         |                              |         |        
publish_down        | datetime    | [null]         |                              |         |        

## message_channels



name       | column_type | ext_info       | ref                      | default | comment             
---------- | ----------- | -------------- | ------------------------ | ------- | --------------------
id         | int         | [pk, not null] |                          |         |                     
message_id | int         | [not null]     | [messages.id](#messages) |         |                     
channel    | varchar     | [not null]     |                          |         |                     
channel_id | int         | [null]         |                          |         |                     
properties | longtext    | [not null]     |                          |         | (DC2Type:json_array)
is_enabled | tinyint     | [not null]     |                          |         |                     

## message_queue



name           | column_type | ext_info       | ref                                    | default | comment        
-------------- | ----------- | -------------- | -------------------------------------- | ------- | ---------------
id             | bigint      | [pk, not null] |                                        |         |                
event_id       | int         | [null]         | [campaign_events.id](#campaign_events) |         |                
lead_id        | bigint      | [not null]     | [leads.id](#leads)                     |         |                
channel        | varchar     | [not null]     |                                        |         |                
channel_id     | int         | [not null]     |                                        |         |                
priority       | smallint    | [not null]     |                                        |         |                
max_attempts   | smallint    | [not null]     |                                        |         |                
attempts       | smallint    | [not null]     |                                        |         |                
success        | tinyint     | [not null]     |                                        |         |                
status         | varchar     | [not null]     |                                        |         |                
date_published | datetime    | [null]         |                                        |         |                
scheduled_date | datetime    | [null]         |                                        |         |                
last_attempt   | datetime    | [null]         |                                        |         |                
date_sent      | datetime    | [null]         |                                        |         |                
options        | longtext    | [null]         |                                        |         | (DC2Type:array)

## migrations



name        | column_type | ext_info       | ref | default | comment                     
----------- | ----------- | -------------- | --- | ------- | ----------------------------
version     | varchar     | [pk, not null] |     |         |                             
executed_at | datetime    | [not null]     |     |         | (DC2Type:datetime_immutable)

## monitoring



name                | column_type | ext_info       | ref                          | default | comment        
------------------- | ----------- | -------------- | ---------------------------- | ------- | ---------------
id                  | int         | [pk, not null] |                              |         |                
category_id         | int         | [null]         | [categories.id](#categories) |         |                
is_published        | tinyint     | [not null]     |                              |         |                
date_added          | datetime    | [null]         |                              |         |                
created_by          | int         | [null]         |                              |         |                
created_by_user     | varchar     | [null]         |                              |         |                
date_modified       | datetime    | [null]         |                              |         |                
modified_by         | int         | [null]         |                              |         |                
modified_by_user    | varchar     | [null]         |                              |         |                
checked_out         | datetime    | [null]         |                              |         |                
checked_out_by      | int         | [null]         |                              |         |                
checked_out_by_user | varchar     | [null]         |                              |         |                
title               | varchar     | [not null]     |                              |         |                
description         | longtext    | [null]         |                              |         |                
lists               | longtext    | [null]         |                              |         | (DC2Type:array)
network_type        | varchar     | [null]         |                              |         |                
revision            | int         | [not null]     |                              |         |                
stats               | longtext    | [null]         |                              |         | (DC2Type:array)
properties          | longtext    | [null]         |                              |         | (DC2Type:array)
publish_up          | datetime    | [null]         |                              |         |                
publish_down        | datetime    | [null]         |                              |         |                

## monitoring_leads



name       | column_type | ext_info       | ref                          | default | comment
---------- | ----------- | -------------- | ---------------------------- | ------- | -------
monitor_id | int         | [pk, not null] | [monitoring.id](#monitoring) |         |        
lead_id    | bigint      | [pk, not null] | [leads.id](#leads)           |         |        
date_added | datetime    | [not null]     |                              |         |        

## monitor_post_count



name       | column_type | ext_info       | ref                          | default | comment
---------- | ----------- | -------------- | ---------------------------- | ------- | -------
id         | int         | [pk, not null] |                              |         |        
monitor_id | int         | [null]         | [monitoring.id](#monitoring) |         |        
post_date  | date        | [not null]     |                              |         |        
post_count | int         | [not null]     |                              |         |        

## notifications



name       | column_type | ext_info       | ref                | default | comment
---------- | ----------- | -------------- | ------------------ | ------- | -------
id         | int         | [pk, not null] |                    |         |        
user_id    | int         | [not null]     | [users.id](#users) |         |        
type       | varchar     | [null]         |                    |         |        
header     | varchar     | [null]         |                    |         |        
message    | longtext    | [not null]     |                    |         |        
date_added | datetime    | [not null]     |                    |         |        
icon_class | varchar     | [null]         |                    |         |        
is_read    | tinyint     | [not null]     |                    |         |        

## oauth2_accesstokens



name       | column_type | ext_info       | ref                                  | default | comment
---------- | ----------- | -------------- | ------------------------------------ | ------- | -------
id         | int         | [pk, not null] |                                      |         |        
client_id  | int         | [not null]     | [oauth2_clients.id](#oauth2_clients) |         |        
user_id    | int         | [null]         | [users.id](#users)                   |         |        
token      | varchar     | [not null]     |                                      |         |        
expires_at | bigint      | [null]         |                                      |         |        
scope      | varchar     | [null]         |                                      |         |        

## oauth2_authcodes



name         | column_type | ext_info       | ref                                  | default | comment
------------ | ----------- | -------------- | ------------------------------------ | ------- | -------
id           | int         | [pk, not null] |                                      |         |        
client_id    | int         | [not null]     | [oauth2_clients.id](#oauth2_clients) |         |        
user_id      | int         | [not null]     | [users.id](#users)                   |         |        
token        | varchar     | [not null]     |                                      |         |        
expires_at   | bigint      | [null]         |                                      |         |        
scope        | varchar     | [null]         |                                      |         |        
redirect_uri | longtext    | [not null]     |                                      |         |        

## oauth2_clients



name                | column_type | ext_info       | ref                | default | comment        
------------------- | ----------- | -------------- | ------------------ | ------- | ---------------
id                  | int         | [pk, not null] |                    |         |                
name                | varchar     | [not null]     |                    |         |                
random_id           | varchar     | [not null]     |                    |         |                
secret              | varchar     | [not null]     |                    |         |                
redirect_uris       | longtext    | [not null]     |                    |         | (DC2Type:array)
allowed_grant_types | longtext    | [not null]     |                    |         | (DC2Type:array)
role_id             | int         | [null]         | [roles.id](#roles) |         |                

## oauth2_refreshtokens



name       | column_type | ext_info       | ref                                  | default | comment
---------- | ----------- | -------------- | ------------------------------------ | ------- | -------
id         | int         | [pk, not null] |                                      |         |        
client_id  | int         | [not null]     | [oauth2_clients.id](#oauth2_clients) |         |        
user_id    | int         | [not null]     | [users.id](#users)                   |         |        
token      | varchar     | [not null]     |                                      |         |        
expires_at | bigint      | [null]         |                                      |         |        
scope      | varchar     | [null]         |                                      |         |        

## oauth2_user_client_xref



name      | column_type | ext_info       | ref                                  | default | comment
--------- | ----------- | -------------- | ------------------------------------ | ------- | -------
client_id | int         | [pk, not null] | [oauth2_clients.id](#oauth2_clients) |         |        
user_id   | int         | [pk, not null] | [users.id](#users)                   |         |        

## pages



name                  | column_type | ext_info       | ref                          | default | comment        
--------------------- | ----------- | -------------- | ---------------------------- | ------- | ---------------
id                    | int         | [pk, not null] |                              |         |                
category_id           | int         | [null]         | [categories.id](#categories) |         |                
translation_parent_id | int         | [null]         | [pages.id](#pages)           |         |                
variant_parent_id     | int         | [null]         | [pages.id](#pages)           |         |                
is_published          | tinyint     | [not null]     |                              |         |                
date_added            | datetime    | [null]         |                              |         |                
created_by            | int         | [null]         |                              |         |                
created_by_user       | varchar     | [null]         |                              |         |                
date_modified         | datetime    | [null]         |                              |         |                
modified_by           | int         | [null]         |                              |         |                
modified_by_user      | varchar     | [null]         |                              |         |                
checked_out           | datetime    | [null]         |                              |         |                
checked_out_by        | int         | [null]         |                              |         |                
checked_out_by_user   | varchar     | [null]         |                              |         |                
title                 | varchar     | [not null]     |                              |         |                
alias                 | varchar     | [not null]     |                              |         |                
template              | varchar     | [null]         |                              |         |                
custom_html           | longtext    | [null]         |                              |         |                
content               | longtext    | [null]         |                              |         | (DC2Type:array)
publish_up            | datetime    | [null]         |                              |         |                
publish_down          | datetime    | [null]         |                              |         |                
hits                  | int         | [not null]     |                              |         |                
unique_hits           | int         | [not null]     |                              |         |                
variant_hits          | int         | [not null]     |                              |         |                
revision              | int         | [not null]     |                              |         |                
meta_description      | varchar     | [null]         |                              |         |                
redirect_type         | varchar     | [null]         |                              |         |                
redirect_url          | varchar     | [null]         |                              |         |                
is_preference_center  | tinyint     | [null]         |                              |         |                
no_index              | tinyint     | [null]         |                              |         |                
lang                  | varchar     | [not null]     |                              |         |                
variant_settings      | longtext    | [null]         |                              |         | (DC2Type:array)
variant_start_date    | datetime    | [null]         |                              |         |                

## page_hits



name              | column_type | ext_info       | ref                                  | default | comment        
----------------- | ----------- | -------------- | ------------------------------------ | ------- | ---------------
id                | bigint      | [pk, not null] |                                      |         |                
page_id           | int         | [null]         | [pages.id](#pages)                   |         |                
redirect_id       | bigint      | [null]         | [page_redirects.id](#page_redirects) |         |                
email_id          | int         | [null]         | [emails.id](#emails)                 |         |                
lead_id           | bigint      | [null]         | [leads.id](#leads)                   |         |                
ip_id             | int         | [not null]     | [ip_addresses.id](#ip_addresses)     |         |                
device_id         | bigint      | [null]         | [lead_devices.id](#lead_devices)     |         |                
date_hit          | datetime    | [not null]     |                                      |         |                
date_left         | datetime    | [null]         |                                      |         |                
country           | varchar     | [null]         |                                      |         |                
region            | varchar     | [null]         |                                      |         |                
city              | varchar     | [null]         |                                      |         |                
isp               | varchar     | [null]         |                                      |         |                
organization      | varchar     | [null]         |                                      |         |                
code              | int         | [not null]     |                                      |         |                
referer           | longtext    | [null]         |                                      |         |                
url               | longtext    | [null]         |                                      |         |                
url_title         | varchar     | [null]         |                                      |         |                
user_agent        | longtext    | [null]         |                                      |         |                
remote_host       | varchar     | [null]         |                                      |         |                
page_language     | varchar     | [null]         |                                      |         |                
browser_languages | longtext    | [null]         |                                      |         | (DC2Type:array)
tracking_id       | varchar     | [not null]     |                                      |         |                
source            | varchar     | [null]         |                                      |         |                
source_id         | int         | [null]         |                                      |         |                
query             | longtext    | [null]         |                                      |         | (DC2Type:array)

## page_redirects



name                | column_type | ext_info       | ref | default | comment
------------------- | ----------- | -------------- | --- | ------- | -------
id                  | bigint      | [pk, not null] |     |         |        
is_published        | tinyint     | [not null]     |     |         |        
date_added          | datetime    | [null]         |     |         |        
created_by          | int         | [null]         |     |         |        
created_by_user     | varchar     | [null]         |     |         |        
date_modified       | datetime    | [null]         |     |         |        
modified_by         | int         | [null]         |     |         |        
modified_by_user    | varchar     | [null]         |     |         |        
checked_out         | datetime    | [null]         |     |         |        
checked_out_by      | int         | [null]         |     |         |        
checked_out_by_user | varchar     | [null]         |     |         |        
redirect_id         | varchar     | [not null]     |     |         |        
url                 | longtext    | [not null]     |     |         |        
hits                | int         | [not null]     |     |         |        
unique_hits         | int         | [not null]     |     |         |        

## permissions



name    | column_type | ext_info       | ref                | default | comment
------- | ----------- | -------------- | ------------------ | ------- | -------
id      | int         | [pk, not null] |                    |         |        
role_id | int         | [not null]     | [roles.id](#roles) |         |        
bundle  | varchar     | [not null]     |                    |         |        
name    | varchar     | [not null]     |                    |         |        
bitwise | int         | [not null]     |                    |         |        

## plugins



name        | column_type | ext_info       | ref | default | comment
----------- | ----------- | -------------- | --- | ------- | -------
id          | int         | [pk, not null] |     |         |        
name        | varchar     | [not null]     |     |         |        
description | longtext    | [null]         |     |         |        
is_missing  | tinyint     | [not null]     |     |         |        
bundle      | varchar     | [not null]     |     |         |        
version     | varchar     | [null]         |     |         |        
author      | varchar     | [null]         |     |         |        

## plugin_citrix_events



name       | column_type | ext_info       | ref                | default | comment
---------- | ----------- | -------------- | ------------------ | ------- | -------
id         | int         | [pk, not null] |                    |         |        
lead_id    | bigint      | [not null]     | [leads.id](#leads) |         |        
product    | varchar     | [not null]     |                    |         |        
email      | varchar     | [not null]     |                    |         |        
event_name | varchar     | [not null]     |                    |         |        
event_desc | varchar     | [null]         |                    |         |        
event_type | varchar     | [not null]     |                    |         |        
event_date | datetime    | [not null]     |                    |         |        

## plugin_crm_pipedrive_owners



name     | column_type | ext_info       | ref | default | comment
-------- | ----------- | -------------- | --- | ------- | -------
id       | int         | [pk, not null] |     |         |        
email    | varchar     | [not null]     |     |         |        
owner_id | int         | [null]         |     |         |        

## plugin_integration_settings



name               | column_type | ext_info       | ref                    | default | comment        
------------------ | ----------- | -------------- | ---------------------- | ------- | ---------------
id                 | int         | [pk, not null] |                        |         |                
plugin_id          | int         | [null]         | [plugins.id](#plugins) |         |                
name               | varchar     | [not null]     |                        |         |                
is_published       | tinyint     | [not null]     |                        |         |                
supported_features | longtext    | [null]         |                        |         | (DC2Type:array)
api_keys           | longtext    | [not null]     |                        |         | (DC2Type:array)
feature_settings   | longtext    | [null]         |                        |         | (DC2Type:array)

## points



name                | column_type | ext_info       | ref                          | default | comment        
------------------- | ----------- | -------------- | ---------------------------- | ------- | ---------------
id                  | int         | [pk, not null] |                              |         |                
category_id         | int         | [null]         | [categories.id](#categories) |         |                
is_published        | tinyint     | [not null]     |                              |         |                
date_added          | datetime    | [null]         |                              |         |                
created_by          | int         | [null]         |                              |         |                
created_by_user     | varchar     | [null]         |                              |         |                
date_modified       | datetime    | [null]         |                              |         |                
modified_by         | int         | [null]         |                              |         |                
modified_by_user    | varchar     | [null]         |                              |         |                
checked_out         | datetime    | [null]         |                              |         |                
checked_out_by      | int         | [null]         |                              |         |                
checked_out_by_user | varchar     | [null]         |                              |         |                
name                | varchar     | [not null]     |                              |         |                
description         | longtext    | [null]         |                              |         |                
type                | varchar     | [not null]     |                              |         |                
publish_up          | datetime    | [null]         |                              |         |                
publish_down        | datetime    | [null]         |                              |         |                
repeatable          | tinyint     | [not null]     |                              |         |                
delta               | int         | [not null]     |                              |         |                
properties          | longtext    | [not null]     |                              |         | (DC2Type:array)

## point_lead_action_log



name       | column_type | ext_info       | ref                              | default | comment
---------- | ----------- | -------------- | -------------------------------- | ------- | -------
point_id   | int         | [pk, not null] | [points.id](#points)             |         |        
lead_id    | bigint      | [pk, not null] | [leads.id](#leads)               |         |        
ip_id      | int         | [null]         | [ip_addresses.id](#ip_addresses) |         |        
date_fired | datetime    | [not null]     |                                  |         |        

## point_lead_event_log



name       | column_type | ext_info       | ref                                              | default | comment
---------- | ----------- | -------------- | ------------------------------------------------ | ------- | -------
event_id   | int         | [pk, not null] | [point_trigger_events.id](#point_trigger_events) |         |        
lead_id    | bigint      | [pk, not null] | [leads.id](#leads)                               |         |        
ip_id      | int         | [null]         | [ip_addresses.id](#ip_addresses)                 |         |        
date_fired | datetime    | [not null]     |                                                  |         |        

## point_triggers



name                   | column_type | ext_info       | ref                          | default | comment
---------------------- | ----------- | -------------- | ---------------------------- | ------- | -------
id                     | int         | [pk, not null] |                              |         |        
category_id            | int         | [null]         | [categories.id](#categories) |         |        
is_published           | tinyint     | [not null]     |                              |         |        
date_added             | datetime    | [null]         |                              |         |        
created_by             | int         | [null]         |                              |         |        
created_by_user        | varchar     | [null]         |                              |         |        
date_modified          | datetime    | [null]         |                              |         |        
modified_by            | int         | [null]         |                              |         |        
modified_by_user       | varchar     | [null]         |                              |         |        
checked_out            | datetime    | [null]         |                              |         |        
checked_out_by         | int         | [null]         |                              |         |        
checked_out_by_user    | varchar     | [null]         |                              |         |        
name                   | varchar     | [not null]     |                              |         |        
description            | longtext    | [null]         |                              |         |        
publish_up             | datetime    | [null]         |                              |         |        
publish_down           | datetime    | [null]         |                              |         |        
points                 | int         | [not null]     |                              |         |        
color                  | varchar     | [not null]     |                              |         |        
trigger_existing_leads | tinyint     | [not null]     |                              |         |        

## point_trigger_events



name         | column_type | ext_info       | ref                                  | default | comment        
------------ | ----------- | -------------- | ------------------------------------ | ------- | ---------------
id           | int         | [pk, not null] |                                      |         |                
trigger_id   | int         | [not null]     | [point_triggers.id](#point_triggers) |         |                
name         | varchar     | [not null]     |                                      |         |                
description  | longtext    | [null]         |                                      |         |                
type         | varchar     | [not null]     |                                      |         |                
action_order | int         | [not null]     |                                      |         |                
properties   | longtext    | [not null]     |                                      |         | (DC2Type:array)

## push_ids



name    | column_type | ext_info       | ref                | default | comment
------- | ----------- | -------------- | ------------------ | ------- | -------
id      | int         | [pk, not null] |                    |         |        
lead_id | bigint      | [null]         | [leads.id](#leads) |         |        
push_id | varchar     | [not null]     |                    |         |        
enabled | tinyint     | [not null]     |                    |         |        
mobile  | tinyint     | [not null]     |                    |         |        

## push_notifications



name                | column_type | ext_info       | ref                          | default | comment        
------------------- | ----------- | -------------- | ---------------------------- | ------- | ---------------
id                  | int         | [pk, not null] |                              |         |                
category_id         | int         | [null]         | [categories.id](#categories) |         |                
is_published        | tinyint     | [not null]     |                              |         |                
date_added          | datetime    | [null]         |                              |         |                
created_by          | int         | [null]         |                              |         |                
created_by_user     | varchar     | [null]         |                              |         |                
date_modified       | datetime    | [null]         |                              |         |                
modified_by         | int         | [null]         |                              |         |                
modified_by_user    | varchar     | [null]         |                              |         |                
checked_out         | datetime    | [null]         |                              |         |                
checked_out_by      | int         | [null]         |                              |         |                
checked_out_by_user | varchar     | [null]         |                              |         |                
name                | varchar     | [not null]     |                              |         |                
description         | longtext    | [null]         |                              |         |                
lang                | varchar     | [not null]     |                              |         |                
url                 | longtext    | [null]         |                              |         |                
heading             | longtext    | [not null]     |                              |         |                
message             | longtext    | [not null]     |                              |         |                
button              | longtext    | [null]         |                              |         |                
utm_tags            | longtext    | [null]         |                              |         | (DC2Type:array)
notification_type   | longtext    | [null]         |                              |         |                
publish_up          | datetime    | [null]         |                              |         |                
publish_down        | datetime    | [null]         |                              |         |                
read_count          | int         | [not null]     |                              |         |                
sent_count          | int         | [not null]     |                              |         |                
mobile              | tinyint     | [not null]     |                              |         |                
mobileSettings      | longtext    | [not null]     |                              |         | (DC2Type:array)

## push_notification_list_xref



name            | column_type | ext_info       | ref                                          | default | comment
--------------- | ----------- | -------------- | -------------------------------------------- | ------- | -------
notification_id | int         | [pk, not null] | [push_notifications.id](#push_notifications) |         |        
leadlist_id     | int         | [pk, not null] | [lead_lists.id](#lead_lists)                 |         |        

## push_notification_stats



name            | column_type | ext_info       | ref                                          | default | comment        
--------------- | ----------- | -------------- | -------------------------------------------- | ------- | ---------------
id              | bigint      | [pk, not null] |                                              |         |                
notification_id | int         | [null]         | [push_notifications.id](#push_notifications) |         |                
lead_id         | bigint      | [null]         | [leads.id](#leads)                           |         |                
list_id         | int         | [null]         | [lead_lists.id](#lead_lists)                 |         |                
ip_id           | int         | [null]         | [ip_addresses.id](#ip_addresses)             |         |                
date_sent       | datetime    | [not null]     |                                              |         |                
date_read       | datetime    | [null]         |                                              |         |                
is_clicked      | tinyint     | [not null]     |                                              |         |                
date_clicked    | datetime    | [null]         |                                              |         |                
tracking_hash   | varchar     | [null]         |                                              |         |                
retry_count     | int         | [null]         |                                              |         |                
source          | varchar     | [null]         |                                              |         |                
source_id       | int         | [null]         |                                              |         |                
tokens          | longtext    | [null]         |                                              |         | (DC2Type:array)
click_count     | int         | [null]         |                                              |         |                
last_clicked    | datetime    | [null]         |                                              |         |                
click_details   | longtext    | [null]         |                                              |         | (DC2Type:array)

## reports



name                     | column_type | ext_info       | ref | default | comment             
------------------------ | ----------- | -------------- | --- | ------- | --------------------
id                       | int         | [pk, not null] |     |         |                     
is_published             | tinyint     | [not null]     |     |         |                     
date_added               | datetime    | [null]         |     |         |                     
created_by               | int         | [null]         |     |         |                     
created_by_user          | varchar     | [null]         |     |         |                     
date_modified            | datetime    | [null]         |     |         |                     
modified_by              | int         | [null]         |     |         |                     
modified_by_user         | varchar     | [null]         |     |         |                     
checked_out              | datetime    | [null]         |     |         |                     
checked_out_by           | int         | [null]         |     |         |                     
checked_out_by_user      | varchar     | [null]         |     |         |                     
name                     | varchar     | [not null]     |     |         |                     
description              | longtext    | [null]         |     |         |                     
system                   | tinyint     | [not null]     |     |         |                     
source                   | varchar     | [not null]     |     |         |                     
columns                  | longtext    | [null]         |     |         | (DC2Type:array)     
filters                  | longtext    | [null]         |     |         | (DC2Type:array)     
table_order              | longtext    | [null]         |     |         | (DC2Type:array)     
graphs                   | longtext    | [null]         |     |         | (DC2Type:array)     
group_by                 | longtext    | [null]         |     |         | (DC2Type:array)     
aggregators              | longtext    | [null]         |     |         | (DC2Type:array)     
settings                 | longtext    | [null]         |     |         | (DC2Type:json_array)
is_scheduled             | tinyint     | [not null]     |     |         |                     
schedule_unit            | varchar     | [null]         |     |         |                     
to_address               | varchar     | [null]         |     |         |                     
schedule_day             | varchar     | [null]         |     |         |                     
schedule_month_frequency | varchar     | [null]         |     |         |                     

## reports_schedulers



name          | column_type | ext_info       | ref                    | default | comment
------------- | ----------- | -------------- | ---------------------- | ------- | -------
id            | int         | [pk, not null] |                        |         |        
report_id     | int         | [not null]     | [reports.id](#reports) |         |        
schedule_date | datetime    | [not null]     |                        |         |        

## roles



name                 | column_type | ext_info       | ref | default | comment        
-------------------- | ----------- | -------------- | --- | ------- | ---------------
id                   | int         | [pk, not null] |     |         |                
is_published         | tinyint     | [not null]     |     |         |                
date_added           | datetime    | [null]         |     |         |                
created_by           | int         | [null]         |     |         |                
created_by_user      | varchar     | [null]         |     |         |                
date_modified        | datetime    | [null]         |     |         |                
modified_by          | int         | [null]         |     |         |                
modified_by_user     | varchar     | [null]         |     |         |                
checked_out          | datetime    | [null]         |     |         |                
checked_out_by       | int         | [null]         |     |         |                
checked_out_by_user  | varchar     | [null]         |     |         |                
name                 | varchar     | [not null]     |     |         |                
description          | longtext    | [null]         |     |         |                
is_admin             | tinyint     | [not null]     |     |         |                
readable_permissions | longtext    | [not null]     |     |         | (DC2Type:array)

## saml_id_entry



name            | column_type | ext_info       | ref | default | comment
--------------- | ----------- | -------------- | --- | ------- | -------
id              | varchar     | [pk, not null] |     |         |        
entity_id       | varchar     | [pk, not null] |     |         |        
expiryTimestamp | int         | [not null]     |     |         |        

## sms_messages



name                | column_type | ext_info       | ref                          | default | comment
------------------- | ----------- | -------------- | ---------------------------- | ------- | -------
id                  | int         | [pk, not null] |                              |         |        
category_id         | int         | [null]         | [categories.id](#categories) |         |        
is_published        | tinyint     | [not null]     |                              |         |        
date_added          | datetime    | [null]         |                              |         |        
created_by          | int         | [null]         |                              |         |        
created_by_user     | varchar     | [null]         |                              |         |        
date_modified       | datetime    | [null]         |                              |         |        
modified_by         | int         | [null]         |                              |         |        
modified_by_user    | varchar     | [null]         |                              |         |        
checked_out         | datetime    | [null]         |                              |         |        
checked_out_by      | int         | [null]         |                              |         |        
checked_out_by_user | varchar     | [null]         |                              |         |        
name                | varchar     | [not null]     |                              |         |        
description         | longtext    | [null]         |                              |         |        
lang                | varchar     | [not null]     |                              |         |        
message             | longtext    | [not null]     |                              |         |        
sms_type            | longtext    | [null]         |                              |         |        
publish_up          | datetime    | [null]         |                              |         |        
publish_down        | datetime    | [null]         |                              |         |        
sent_count          | int         | [not null]     |                              |         |        

## sms_message_list_xref



name        | column_type | ext_info       | ref                              | default | comment
----------- | ----------- | -------------- | -------------------------------- | ------- | -------
sms_id      | int         | [pk, not null] | [sms_messages.id](#sms_messages) |         |        
leadlist_id | int         | [pk, not null] | [lead_lists.id](#lead_lists)     |         |        

## sms_message_stats



name          | column_type | ext_info       | ref                              | default | comment             
------------- | ----------- | -------------- | -------------------------------- | ------- | --------------------
id            | bigint      | [pk, not null] |                                  |         |                     
sms_id        | int         | [null]         | [sms_messages.id](#sms_messages) |         |                     
lead_id       | bigint      | [null]         | [leads.id](#leads)               |         |                     
list_id       | int         | [null]         | [lead_lists.id](#lead_lists)     |         |                     
ip_id         | int         | [null]         | [ip_addresses.id](#ip_addresses) |         |                     
date_sent     | datetime    | [not null]     |                                  |         |                     
tracking_hash | varchar     | [null]         |                                  |         |                     
source        | varchar     | [null]         |                                  |         |                     
source_id     | int         | [null]         |                                  |         |                     
tokens        | longtext    | [null]         |                                  |         | (DC2Type:array)     
is_failed     | tinyint     | [null]         |                                  |         |                     
details       | longtext    | [not null]     |                                  |         | (DC2Type:json_array)

## stages



name                | column_type | ext_info       | ref                          | default | comment
------------------- | ----------- | -------------- | ---------------------------- | ------- | -------
id                  | int         | [pk, not null] |                              |         |        
category_id         | int         | [null]         | [categories.id](#categories) |         |        
is_published        | tinyint     | [not null]     |                              |         |        
date_added          | datetime    | [null]         |                              |         |        
created_by          | int         | [null]         |                              |         |        
created_by_user     | varchar     | [null]         |                              |         |        
date_modified       | datetime    | [null]         |                              |         |        
modified_by         | int         | [null]         |                              |         |        
modified_by_user    | varchar     | [null]         |                              |         |        
checked_out         | datetime    | [null]         |                              |         |        
checked_out_by      | int         | [null]         |                              |         |        
checked_out_by_user | varchar     | [null]         |                              |         |        
name                | varchar     | [not null]     |                              |         |        
description         | longtext    | [null]         |                              |         |        
weight              | int         | [not null]     |                              |         |        
publish_up          | datetime    | [null]         |                              |         |        
publish_down        | datetime    | [null]         |                              |         |        

## stage_lead_action_log



name       | column_type | ext_info       | ref                              | default | comment
---------- | ----------- | -------------- | -------------------------------- | ------- | -------
stage_id   | int         | [pk, not null] | [stages.id](#stages)             |         |        
lead_id    | bigint      | [pk, not null] | [leads.id](#leads)               |         |        
ip_id      | int         | [null]         | [ip_addresses.id](#ip_addresses) |         |        
date_fired | datetime    | [not null]     |                                  |         |        

## sync_object_field_change_report



name         | column_type | ext_info       | ref | default | comment
------------ | ----------- | -------------- | --- | ------- | -------
id           | int         | [pk, not null] |     |         |        
integration  | varchar     | [not null]     |     |         |        
object_id    | bigint      | [not null]     |     |         |        
object_type  | varchar     | [not null]     |     |         |        
modified_at  | datetime    | [not null]     |     |         |        
column_name  | varchar     | [not null]     |     |         |        
column_type  | varchar     | [not null]     |     |         |        
column_value | varchar     | [not null]     |     |         |        

## sync_object_mapping



name                     | column_type | ext_info       | ref | default | comment             
------------------------ | ----------- | -------------- | --- | ------- | --------------------
id                       | int         | [pk, not null] |     |         |                     
date_created             | datetime    | [not null]     |     |         |                     
integration              | varchar     | [not null]     |     |         |                     
internal_object_name     | varchar     | [not null]     |     |         |                     
internal_object_id       | bigint      | [not null]     |     |         |                     
integration_object_name  | varchar     | [not null]     |     |         |                     
integration_object_id    | varchar     | [not null]     |     |         |                     
last_sync_date           | datetime    | [not null]     |     |         |                     
internal_storage         | longtext    | [not null]     |     |         | (DC2Type:json_array)
is_deleted               | tinyint     | [not null]     |     |         |                     
integration_reference_id | varchar     | [null]         |     |         |                     

## tweets



name                | column_type | ext_info       | ref                          | default | comment
------------------- | ----------- | -------------- | ---------------------------- | ------- | -------
id                  | int         | [pk, not null] |                              |         |        
category_id         | int         | [null]         | [categories.id](#categories) |         |        
page_id             | int         | [null]         | [pages.id](#pages)           |         |        
asset_id            | int         | [null]         | [assets.id](#assets)         |         |        
is_published        | tinyint     | [not null]     |                              |         |        
date_added          | datetime    | [null]         |                              |         |        
created_by          | int         | [null]         |                              |         |        
created_by_user     | varchar     | [null]         |                              |         |        
date_modified       | datetime    | [null]         |                              |         |        
modified_by         | int         | [null]         |                              |         |        
modified_by_user    | varchar     | [null]         |                              |         |        
checked_out         | datetime    | [null]         |                              |         |        
checked_out_by      | int         | [null]         |                              |         |        
checked_out_by_user | varchar     | [null]         |                              |         |        
name                | varchar     | [not null]     |                              |         |        
description         | longtext    | [null]         |                              |         |        
media_id            | varchar     | [null]         |                              |         |        
media_path          | varchar     | [null]         |                              |         |        
text                | varchar     | [not null]     |                              |         |        
sent_count          | int         | [null]         |                              |         |        
favorite_count      | int         | [null]         |                              |         |        
retweet_count       | int         | [null]         |                              |         |        
lang                | varchar     | [null]         |                              |         |        

## tweet_stats



name             | column_type | ext_info       | ref                  | default | comment             
---------------- | ----------- | -------------- | -------------------- | ------- | --------------------
id               | int         | [pk, not null] |                      |         |                     
tweet_id         | int         | [null]         | [tweets.id](#tweets) |         |                     
lead_id          | bigint      | [null]         | [leads.id](#leads)   |         |                     
twitter_tweet_id | varchar     | [null]         |                      |         |                     
handle           | varchar     | [not null]     |                      |         |                     
date_sent        | datetime    | [null]         |                      |         |                     
is_failed        | tinyint     | [null]         |                      |         |                     
retry_count      | int         | [null]         |                      |         |                     
source           | varchar     | [null]         |                      |         |                     
source_id        | int         | [null]         |                      |         |                     
favorite_count   | int         | [null]         |                      |         |                     
retweet_count    | int         | [null]         |                      |         |                     
response_details | longtext    | [null]         |                      |         | (DC2Type:json_array)

## users



name                | column_type | ext_info       | ref                | default | comment        
------------------- | ----------- | -------------- | ------------------ | ------- | ---------------
id                  | int         | [pk, not null] |                    |         |                
role_id             | int         | [not null]     | [roles.id](#roles) |         |                
is_published        | tinyint     | [not null]     |                    |         |                
date_added          | datetime    | [null]         |                    |         |                
created_by          | int         | [null]         |                    |         |                
created_by_user     | varchar     | [null]         |                    |         |                
date_modified       | datetime    | [null]         |                    |         |                
modified_by         | int         | [null]         |                    |         |                
modified_by_user    | varchar     | [null]         |                    |         |                
checked_out         | datetime    | [null]         |                    |         |                
checked_out_by      | int         | [null]         |                    |         |                
checked_out_by_user | varchar     | [null]         |                    |         |                
username            | varchar     | [not null]     |                    |         |                
password            | varchar     | [not null]     |                    |         |                
first_name          | varchar     | [not null]     |                    |         |                
last_name           | varchar     | [not null]     |                    |         |                
email               | varchar     | [not null]     |                    |         |                
position            | varchar     | [null]         |                    |         |                
timezone            | varchar     | [null]         |                    |         |                
locale              | varchar     | [null]         |                    |         |                
last_login          | datetime    | [null]         |                    |         |                
last_active         | datetime    | [null]         |                    |         |                
preferences         | longtext    | [null]         |                    |         | (DC2Type:array)
signature           | longtext    | [null]         |                    |         |                

## user_tokens



name          | column_type | ext_info       | ref                | default | comment
------------- | ----------- | -------------- | ------------------ | ------- | -------
id            | int         | [pk, not null] |                    |         |        
user_id       | int         | [not null]     | [users.id](#users) |         |        
authorizator  | varchar     | [not null]     |                    |         |        
secret        | varchar     | [not null]     |                    |         |        
expiration    | datetime    | [null]         |                    |         |        
one_time_only | tinyint     | [not null]     |                    |         |        

## video_hits



name              | column_type | ext_info       | ref                              | default | comment        
----------------- | ----------- | -------------- | -------------------------------- | ------- | ---------------
id                | int         | [pk, not null] |                                  |         |                
lead_id           | bigint      | [null]         | [leads.id](#leads)               |         |                
ip_id             | int         | [not null]     | [ip_addresses.id](#ip_addresses) |         |                
date_hit          | datetime    | [not null]     |                                  |         |                
date_left         | datetime    | [null]         |                                  |         |                
country           | varchar     | [null]         |                                  |         |                
region            | varchar     | [null]         |                                  |         |                
city              | varchar     | [null]         |                                  |         |                
isp               | varchar     | [null]         |                                  |         |                
organization      | varchar     | [null]         |                                  |         |                
code              | int         | [not null]     |                                  |         |                
referer           | longtext    | [null]         |                                  |         |                
url               | longtext    | [null]         |                                  |         |                
user_agent        | longtext    | [null]         |                                  |         |                
remote_host       | varchar     | [null]         |                                  |         |                
guid              | varchar     | [not null]     |                                  |         |                
page_language     | varchar     | [null]         |                                  |         |                
browser_languages | longtext    | [null]         |                                  |         | (DC2Type:array)
channel           | varchar     | [null]         |                                  |         |                
channel_id        | int         | [null]         |                                  |         |                
time_watched      | int         | [null]         |                                  |         |                
duration          | int         | [null]         |                                  |         |                
query             | longtext    | [null]         |                                  |         | (DC2Type:array)

## webhooks



name                | column_type | ext_info       | ref                          | default | comment
------------------- | ----------- | -------------- | ---------------------------- | ------- | -------
id                  | int         | [pk, not null] |                              |         |        
category_id         | int         | [null]         | [categories.id](#categories) |         |        
is_published        | tinyint     | [not null]     |                              |         |        
date_added          | datetime    | [null]         |                              |         |        
created_by          | int         | [null]         |                              |         |        
created_by_user     | varchar     | [null]         |                              |         |        
date_modified       | datetime    | [null]         |                              |         |        
modified_by         | int         | [null]         |                              |         |        
modified_by_user    | varchar     | [null]         |                              |         |        
checked_out         | datetime    | [null]         |                              |         |        
checked_out_by      | int         | [null]         |                              |         |        
checked_out_by_user | varchar     | [null]         |                              |         |        
name                | varchar     | [not null]     |                              |         |        
description         | longtext    | [null]         |                              |         |        
webhook_url         | longtext    | [not null]     |                              |         |        
secret              | varchar     | [not null]     |                              |         |        
events_orderby_dir  | varchar     | [null]         |                              |         |        

## webhook_events



name       | column_type | ext_info       | ref                      | default | comment
---------- | ----------- | -------------- | ------------------------ | ------- | -------
id         | int         | [pk, not null] |                          |         |        
webhook_id | int         | [not null]     | [webhooks.id](#webhooks) |         |        
event_type | varchar     | [not null]     |                          |         |        

## webhook_logs



name        | column_type | ext_info       | ref                      | default | comment
----------- | ----------- | -------------- | ------------------------ | ------- | -------
id          | int         | [pk, not null] |                          |         |        
webhook_id  | int         | [not null]     | [webhooks.id](#webhooks) |         |        
status_code | varchar     | [not null]     |                          |         |        
date_added  | datetime    | [null]         |                          |         |        
note        | varchar     | [null]         |                          |         |        
runtime     | double      | [null]         |                          |         |        

## webhook_queue



name       | column_type | ext_info       | ref                                  | default | comment
---------- | ----------- | -------------- | ------------------------------------ | ------- | -------
id         | int         | [pk, not null] |                                      |         |        
webhook_id | int         | [not null]     | [webhooks.id](#webhooks)             |         |        
event_id   | int         | [not null]     | [webhook_events.id](#webhook_events) |         |        
date_added | datetime    | [null]         |                                      |         |        
payload    | longtext    | [not null]     |                                      |         |        

## widgets



name                | column_type | ext_info       | ref | default | comment        
------------------- | ----------- | -------------- | --- | ------- | ---------------
id                  | int         | [pk, not null] |     |         |                
is_published        | tinyint     | [not null]     |     |         |                
date_added          | datetime    | [null]         |     |         |                
created_by          | int         | [null]         |     |         |                
created_by_user     | varchar     | [null]         |     |         |                
date_modified       | datetime    | [null]         |     |         |                
modified_by         | int         | [null]         |     |         |                
modified_by_user    | varchar     | [null]         |     |         |                
checked_out         | datetime    | [null]         |     |         |                
checked_out_by      | int         | [null]         |     |         |                
checked_out_by_user | varchar     | [null]         |     |         |                
name                | varchar     | [not null]     |     |         |                
type                | varchar     | [not null]     |     |         |                
width               | int         | [not null]     |     |         |                
height              | int         | [not null]     |     |         |                
cache_timeout       | int         | [null]         |     |         |                
ordering            | int         | [null]         |     |         |                
params              | longtext    | [null]         |     |         | (DC2Type:array)

