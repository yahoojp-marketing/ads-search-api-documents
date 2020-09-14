# AuditLog of Search Ads
1. [AuditLog field](#anchor1)
2. [Active entity name](#anchor2)
3. [Active event type](#anchor3)
4. [Entity output item](#anchor4)
5. [Column](#anchor5)

## Item
AuditLog item of Search Ad are as follows. *Data as of August 28, 2020.

#### 1. AuditLog field
<a id="anchor1"></a>

|Item (English)|
|---|
|Date|
|User|
|Source Type|
|Account Name|
|Account ID|
|Campaign Name|
|Campaign ID|
|Ad Group Name|
|Ad Group ID|
|Ad Name|
|Ad ID|
|Ad Type|
|Keyword|
|Keyword ID|
|Data Assignment List ID|
|Page Feed ID|
|Ad Display Option ID|
|Auto Bidding ID|
|Target List Name|
|Target List ID|
|Page Feed Target ID|
|Conversion Tracker ID|
|Negative Keywords List ID|
|Label ID|
|Label Name|
|Entity Type|
|Event Type|
|Item|
|Before|
|After|

#### 2. Active entity name
<a id="anchor2"></a>

|Entity type|Item (English)|
|---|---|
|CAMPAIGN|Campaigns|
|NEGATIVE_CAMPAIGN_CRITERION|Negative Keywords (Campaign)|
|CAMPAIGN_CRITERION|Campaign Targeting|
|AD_GROUP|Ad Groups|
|AD_GROUP_BID_MULTIPLIER|Ad Groups|
|BIDDABLE_AD_GROUP_CRITERION|Keywords|
|NEGATIVE_AD_GROUP_CRITERION|Negative Keywords (Ad Group)|
|AD|Ads|
|FEED|Feed|
|FEED_ITEM|Ad Display Option|
|SS_IO|Account|
|SS_CONVERSION|Conversion Analytics|
|CAMPAIGN_FEED|Ad Display Option|
|AD_GROUP_FEED|Ad Display Option|

#### 3. Active event type
<table id= 'anchor3'>
<tr>
 <th>Entity Type</th>
 <th>Item (English)</th>
</tr>

<tr><td rowspan='4'>CAMPAIGN</td><td>Change Campaign Settings</td></tr>
<tr><td>Change Display Settings</td></tr>
<tr><td>Add</td></tr>
<tr><td>Delete</td></tr>
<tr><td rowspan='3'>CAMPAIGN_CRITERION</td><td>Add</td></tr>
<tr><td>Change Bid Adjustment</td></tr>
<tr><td>Delete</td></tr>
<tr><td rowspan='2'>NEGATIVE_CAMPAIGN_CRITERION</td><td>Add</td></tr>
<tr><td>Delete</td></tr>
<tr><td rowspan='5'>AD_GROUP</td><td>Change Ad Group Settings</td></tr>
<tr><td>Change Display Settings</td></tr>
<tr><td>Set Ad Group Bid</td></tr>
<tr><td>Add</td></tr>
<tr><td>Delete</td></tr>
<tr><td rowspan='3'>AD_GROUP_BID_MULTIPLIER</td><td>Add</td></tr>
<tr><td>Change Ad Group Settings</td></tr>
<tr><td>Delete</td></tr>
<tr><td rowspan='6'>BIDDABLE_AD_GROUP_CRITERION</td><td>Change Keyword Settings</td></tr>
<tr><tdEditorial Review</td></tr>
<tr><td>Change Display Settings</td></tr>
<tr><td>Set Keyword Bid</td></tr>
<tr><td>Add</td></tr>
<tr><td>Delete</td></tr>
<tr><td rowspan='2'>NEGATIVE_AD_GROUP_CRITERION</td><td>Add</td></tr>
<tr><td>Delete</td></tr>
<tr><td rowspan='5'>AD</td><td>Add</td></tr>
<tr><td>Change Ad Settings</td></tr>
<tr><td>Delete Ad</td></tr>
<tr><td>Review Ad</td></tr>
<tr><td>Change Display Settings</td></tr>

</table>

#### 4. Entity output item
<table id="anchor4">
<tr>
 <th>Entity Type</th>
 <th>Item (English)</th>
</tr>
 
<tr><td rowspan='35'>CAMPAIGN</td><td>Campaign Name</td></tr>
<tr><td>Display Settings</td></tr>
<tr><td>Start Date</td></tr>
<tr><td>End Date</td></tr>
<tr><td>Ad Rotation</td></tr>
<tr><td>Campaign Daily Budget</td></tr>
<tr><td>Display Method</td></tr>
<tr><td>Bidding</td></tr>
<tr><td>Bid Limit</td></tr>
<tr><td>Advanced Location Options</td></tr>
<tr><td>Advanced Location Options Excluded</td></tr>
<tr><td>Platform bid multiplier</td></tr>
<tr><td>Auto Bidding setting</td></tr>
<tr><td>Campaign Type</td></tr>
<tr><td>OS</td></tr>
<tr><td>App ID/Package name</td></tr>
<tr><td>Tracking URL</td></tr>
<tr><td>Custom Parameters Key 1</td></tr>
<tr><td>Custom Parameters Key 2</td></tr>
<tr><td>Custom Parameters Key 3</td></tr>
<tr><td>Custom Parameters Value 1</td></tr>
<tr><td>Custom Parameters Value 2</td></tr>
<tr><td>Custom Parameters Value 3</td></tr>
<tr><td>Page Feed ID</td></tr>
<tr><td>Target Users</td></tr>
<tr><td>Enhanced CPC</td></tr>
<tr><td>Target ROAS</td></tr>
<tr><td>Bid Limit (Target ROAS)</td></tr>
<tr><td>Lower Bid Limit (Target ROAS)</td></tr>
<tr><td>Bid Limit (Maximize Clicks)</td></tr>
<tr><td>Target Daily Budget</td></tr>
<tr><td>Target CPA</td></tr>
<tr><td>Bid Limit (Target CPA)</td></tr>
<tr><td>Lower Bid Limit (Target CPA)</td></tr>
<tr><td>How specified</td></tr>
<tr><td rowspan='3'>CAMPAIGN_TARGET</td><td>Day of Week / Hours</td></tr>
<tr><td>Geographic Location</td></tr>
<tr><td>Ad Distribution</td></tr>
<tr><td rowspan='4'>CAMPAIGN_CRITERION</td><td>Geographic Location</td></tr>
<tr><td>Day of Week / Hours</td></tr>
<tr><td>Devices</td></tr>
<tr><td>Ad Distribution</td></tr>
<tr><td rowspan='2'>NEGATIVE_CAMPAIGN_CRITERION</td><td>Negative Keywords</td></tr>
<tr><td>Match Type</td></tr>
<tr><td rowspan='14'>AD_GROUP</td><td>Ad Group Name</td></tr>
<tr><td>Display Settings</td></tr>
<tr><td>Ad Group Bid</td></tr>
<tr><td>Auto Bidding setting</td></tr>
<tr><td>Auto Bidding Type</td></tr>
<tr><td>Target Users</td></tr>
<tr><td>Tracking URL</td></tr>
<tr><td>Custom Parameters Key 1</td></tr>
<tr><td>Custom Parameters Key 2</td></tr>
<tr><td>Custom Parameters Key 3</td></tr>
<tr><td>Custom Parameters Value 1</td></tr>
<tr><td>Custom Parameters Value 2</td></tr>
<tr><td>Custom Parameters Value 3</td></tr>
<tr><td>Ad Rotation</td></tr>
<tr><td rowspan='1'>AD_GROUP_BID_MULTIPLIER</td><td>Bid multiplier</td></tr>
<tr><td rowspan='19'>BIDDABLE_AD_GROUP_CRITERION</td><td>Keyword</td></tr>
<tr><td>Match Type</td></tr>
<tr><td>Display Settings</td></tr>
<tr><td>Custom URL</td></tr>
<tr><td>Editorial Status</td></tr>
<tr><td>Bid</td></tr>
<tr><td>REVIEW_COMP_DATE</td></tr>
<tr><td>Auto Bidding setting</td></tr>
<tr><td>Auto Bidding Type</td></tr>
<tr><td>Landing Page URL</td></tr>
<tr><td>Smartphone Landing Page URL</td></tr>
<tr><td>Tracking URL</td></tr>
<tr><td>Custom Parameters Key 1</td></tr>
<tr><td>Custom Parameters Key 2</td></tr>
<tr><td>Custom Parameters Key 3</td></tr>
<tr><td>Custom Parameters Value 1</td></tr>
<tr><td>Custom Parameters Value 2</td></tr>
<tr><td>Custom Parameters Value 3</td></tr>
<tr><td>Brand term User Status</td></tr>
<tr><td rowspan='2'>NEGATIVE_AD_GROUP_CRITERION</td><td>Negative Keywords</td></tr>
<tr><td>Match Type</td></tr>
<tr><td rowspan='20'>AD</td><td>Ad Name</td></tr>
<tr><td>Ad Type</td></tr>
<tr><td>Focus Device</td></tr>
<tr><td>Display Settings</td></tr>
<tr><td>Title</td></tr>
<tr><td>Title2</td></tr>
<tr><td>Description1</td></tr>
<tr><td>Description2</td></tr>
<tr><td>Destination URL</td></tr>
<tr><td>Display URL</td></tr>
<tr><td>Directory1</td></tr>
<tr><td>Directory2</td></tr>
<tr><td>OS</td></tr>
<tr><td>App ID/Package name</td></tr>
<tr><td>Editorial Status</td></tr>
<tr><td>Landing Page URL</td></tr>
<tr><td>Smartphone Landing Page URL</td></tr>
<tr><td>Tracking URL</td></tr>
<tr><td>REVIEW_COMP_DATE</td></tr>
<tr><td>Brand term User Status</td></tr>
<tr><td rowspan='22'>FEED</td><td>Feed ID</td></tr>
<tr><td>Feed Name</td></tr>
<tr><td>Attribute1</td></tr>
<tr><td>Attribute2</td></tr>
<tr><td>Attribute3</td></tr>
<tr><td>Attribute4</td></tr>
<tr><td>Attribute5</td></tr>
<tr><td>Attribute6</td></tr>
<tr><td>Attribute7</td></tr>
<tr><td>Attribute8</td></tr>
<tr><td>Attribute9</td></tr>
<tr><td>Attribute10</td></tr>
<tr><td>Attribute11</td></tr>
<tr><td>Attribute12</td></tr>
<tr><td>Attribute13</td></tr>
<tr><td>Attribute14</td></tr>
<tr><td>Attribute15</td></tr>
<tr><td>Attribute16</td></tr>
<tr><td>Attribute17</td></tr>
<tr><td>Attribute18</td></tr>
<tr><td>Attribute19</td></tr>
<tr><td>Attribute20</td></tr>
<tr><td rowspan='53'>FEED_ITEM</td><td>Geographic Location</td></tr>
<tr><td>Editorial Status</td></tr>
<tr><td>REVIEW_COMP_DATE</td></tr>
<tr><td>Ad Display Option Id</td></tr>
<tr><td>Campaign ID</td></tr>
<tr><td>Ad Group ID</td></tr>
<tr><td>Keyword</td></tr>
<tr><td>Match Type</td></tr>
<tr><td>Link Text</td></tr>
<tr><td>Link Url</td></tr>
<tr><td>QuickLink Description 1</td></tr>
<tr><td>QuickLink Description 2</td></tr>
<tr><td>Phone Number</td></tr>
<tr><td>Link Text(Image)</td></tr>
<tr><td>Link Url(Image)</td></tr>
<tr><td>Media Id</td></tr>
<tr><td>Callout Text</td></tr>
<tr><td>STRUCTURED_SNIPPET_HEADER</td></tr>
<tr><td>STRUCTURED_SNIPPET_VALUES</td></tr>
<tr><td>Focus Device</td></tr>
<tr><td>Start Date</td></tr>
<tr><td>End Date</td></tr>
<tr><td>Day of Week / Hours</td></tr>
<tr><td>Landing Page URL</td></tr>
<tr><td>Smartphone Landing Page URL</td></tr>
<tr><td>Tracking URL</td></tr>
<tr><tdCustom Parameters Key 1</td></tr>
<tr><td>Custom Parameters Key 2</td></tr>
<tr><td>Custom Parameters Key 3</td></tr>
<tr><td>Custom Parameters Value 1</td></tr>
<tr><td>Custom Parameters Value 2</td></tr>
<tr><td>Custom Parameters Value 3</td></tr>
<tr><td>Data Auto Insertion List 1</td></tr>
<tr><td>Data Auto Insertion List 2</td></tr>
<tr><td>Data Auto Insertion List 3</td></tr>
<tr><td>Data Auto Insertion List 4</td></tr>
<tr><td>Data Auto Insertion List 5</td></tr>
<tr><td>Data Auto Insertion List 6</td></tr>
<tr><td>Data Auto Insertion List 7</td></tr>
<tr><td>Data Auto Insertion List 8</td></tr>
<tr><td>Data Auto Insertion List 9</td></tr>
<tr><td>Data Auto Insertion List 10</td></tr>
<tr><td>Data Auto Insertion List 11</td></tr>
<tr><td>Data Auto Insertion List 12</td></tr>
<tr><td>Data Auto Insertion List 13</td></tr>
<tr><td>Data Auto Insertion List 14</td></tr>
<tr><td>Data Auto Insertion List 15</td></tr>
<tr><td>Data Auto Insertion List 16</td></tr>
<tr><td>Data Auto Insertion List 17</td></tr>
<tr><td>Data Auto Insertion List 18</td></tr>
<tr><td>Data Auto Insertion List 19</td></tr>
<tr><td>Data Auto Insertion List 20</td></tr>
<tr><td>Brand term User Status</td></tr>
<tr><td rowspan='18'>SS_IO</td><td>Account Name</td></tr>
<tr><td>Account Budget</td></tr>
<tr><td>Primary Business Contact (Name)</td></tr>
<tr><td>Agency Location</td></tr>
<tr><td>Advertiser Location</td></tr>
<tr><td>Start Date</td></tr>
<tr><td>End Date</td></tr>
<tr><td>Contact Name (Advertiser)</td></tr>
<tr><td>Automatic Charge Amount</td></tr>
<tr><td>Automatic Charge</td></tr>
<tr><td>Automatic Charge Credit Card Holder (Yahoo! JAPAN Business ID)</td></tr>
<tr><td>Promotion No</td></tr>
<tr><td>Display Settings</td></tr>
<tr><td>Display Settings (Internal)</td></tr>
<tr><td>Primary Business Contact (Yahoo! JAPAN Business ID)</td></tr>
<tr><td>Fund Allocatio</td></tr>
<tr><td>Tracking URL</td></tr>
<tr><td>Auto-tagging</td></tr>
<tr><td rowspan='13'>SS_CONVERSION</td><td>Conversion Name</td></tr>
<tr><td>Conversion Type</td></tr>
<tr><td>Conversion Tracking Purpose</td></tr>
<tr><td>Status</td></tr>
<tr><td>Counting Type</td></tr>
<tr><td>for Auto Bidding</td></tr>
<tr><td>Counting Period</td></tr>
<tr><td>Value per Conversion</td></tr>
<tr><td>OS</td></tr>
<tr><td>Action you''d like to track</td></tr>
<tr><td>Package Name</td></tr>
<tr><td>Post back URL</td></tr>
<tr><td>Cross device conversion setting</td></tr>
<tr><td rowspan='2'>CAMPAIGN_FEED</td><td>Relation to Campaign</td></tr>
<tr><td>Device</td></tr>
<tr><td rowspan='2'>AD_GROUP_FEED</td><td>Relation to Ad Group</td></tr>
<tr><td>Device</td></tr>

</table>

#### 5.Column
<table id="anchor5">
<tr>
 <th>Item (English)</th>
 <th>Value</th>
</tr>

<tr><td rowspan='6'>Ad Rotation</td><td>Optimize (display higher quality ads)</td></tr>
<tr><td>Rotate Evenly for 90 Days (display ads evenly for 90 days)</td></tr>
<tr><td>Always Rotate Evenly (rotate ads evenly without optimization)</td></tr>
<tr><td>Optimize (display higher conversion rate ads)</td></tr>
<tr><td>Optimize</td></tr>
<tr><td>Rotate Evenly</td></tr>
<tr><td rowspan='6'>Ad Type</td><td>Text Ad(15-33)</td></tr>
<tr><td>Text Ad(15-19-19)</td></tr>
<tr><td>Short Ad(12-12)</td></tr>
<tr><td>App Ad(12-17-17)</td></tr>
<tr><td>Text Ad(15-15-40)</td></tr>
<tr><td>Dynamic Ads for Search</td></tr>
<tr><td rowspan='5'>Editorial Status</td><td>Approved</td></tr>
<tr><td>Editorial Pending</td></tr>
<tr><td>Editorial Declined</td></tr>
<tr><td>Editorial Removed</td></tr>
<tr><td>Change Requested</td></tr>
<tr><td rowspan='7'>Auto Bidding Type</td><td>Auto Bid</td></tr>
<tr><td>Individual CPC</td></tr>
<tr><td>Target position in search results</td></tr>
<tr><td>Target ROAS</td></tr>
<tr><td>Maximize Clicks</td></tr>
<tr><td>Maximize Conversions</td></tr>
<tr><td>Target CPA</td></tr>
<tr><td rowspan='2'>Display Method</td><td>Display ads evenly over time</td></tr>
<tr><td>Display ads as quickly as possible</td></tr>
<tr><td rowspan='3'>Devices</td><td>PC / Tablet</td></tr>
<tr><td>Smartphone</td></tr>
<tr><td>All</td></tr>
<tr><td rowspan='3'>How specified</td><td>Page feed</td></tr>
<tr><td>Entire domain</td></tr>
<tr><td>Entire domain and page feed</td></tr>
<tr><td rowspan='3'>Match Type</td><td>Broad match</td></tr>
<tr><td>Phrase match</td></tr>
<tr><td>Exact match</td></tr>
<tr><td rowspan='2'>Display Settings</td><td>On</td></tr>
<tr><td>Off</td></tr>
<tr><td rowspan='2'>Campaign Link Status</td><td>On</td></tr>
<tr><td>Off</td></tr>
<tr><td rowspan='2'>Target Users</td><td>All Users</td></tr>
<tr><td>Users on the List</td></tr>
<tr><td rowspan='4'>Target List Type</td><td>Default Target List</td></tr>
<tr><td>Ruled Target List</td></tr>
<tr><td>Logical Target List</td></tr>
<tr><td>Custom Target  List</td></tr>
<tr><td rowspan='2'>Reach Storage Status</td><td>Open</td></tr>
<tr><td>Closed</td></tr>
<tr><td rowspan='2'>Owner</td><td>Owner</td></tr>
<tr><td>Shared</td></tr>
<tr><td rowspan='2'>Shared</td><td>Paused Sharing</td></tr>
<tr><td>Active Sharing</td></tr>
<tr><td rowspan='3'>Campaign Type</td><td>Standard</td></tr>
<tr><td>Mobile app download</td></tr>
<tr><td>Dynamic Ads for Search</td></tr>
<tr><td rowspan='2'>OS</td><td>iOS</td></tr>
<tr><td>Android</td></tr>
<tr><td rowspan='2'>Visitor</td><td>All visitors</td></tr>
<tr><td>Specified visitors</td></tr>
<tr><td rowspan='2'>Date Specific</td><td>Specific date</td></tr>
<tr><td>Non specific date</td></tr>
<tr><td rowspan='49'>Agency Location</td><td>Hokkaido</td></tr>
<tr><td>Aomori</td></tr>
<tr><td>Iwate</td></tr>
<tr><td>Miyagi</td></tr>
<tr><td>Akita</td></tr>
<tr><td>Yamagata</td></tr>
<tr><td>Fukushima</td></tr>
<tr><td>Ibaraki</td></tr>
<tr><td>Tochigi</td></tr>
<tr><td>Gunma</td></tr>
<tr><td>Saitama</td></tr>
<tr><td>Chiba</td></tr>
<tr><td>Tokyo</td></tr>
<tr><td>Kanagawa</td></tr>
<tr><td>Niigata</td></tr>
<tr><td>Toyama</td></tr>
<tr><td>Ishikawa</td></tr>
<tr><td>Fukui</td></tr>
<tr><td>Yamanashi</td></tr>
<tr><td>Nagano</td></tr>
<tr><td>Gifu</td></tr>
<tr><td>Shizuoka</td></tr>
<tr><td>Aichi</td></tr>
<tr><td>Mie</td></tr>
<tr><td>Shiga</td></tr>
<tr><td>Kyoto</td></tr>
<tr><td>Osaka</td></tr>
<tr><td>Hyogo</td></tr>
<tr><td>Nara</td></tr>
<tr><td>Wakayama</td></tr>
<tr><td>Tottori</td></tr>
<tr><td>Shimane</td></tr>
<tr><td>Okayama</td></tr>
<tr><td>Hiroshima</td></tr>
<tr><td>Yamaguchi</td></tr>
<tr><td>Tokushima</td></tr>
<tr><td>Kagawa</td></tr>
<tr><td>Ehime</td></tr>
<tr><td>Kochi</td></tr>
<tr><td>Fukuoka</td></tr>
<tr><td>Saga</td></tr>
<tr><td>Nagasaki</td></tr>
<tr><td>Kumamoto</td></tr>
<tr><td>Oita</td></tr>
<tr><td>Miyazaki</td></tr>
<tr><td>Kagoshima</td></tr>
<tr><td>Okinawa</td></tr>
<tr><td>Outside Japan</td></tr>
<tr><td>N/A</td></tr>
<tr><td rowspan='49'>Advertiser Location</td><td>Hokkaido</td></tr>
<tr><td>Aomori</td></tr>
<tr><td>Iwate</td></tr>
<tr><td>Miyagi</td></tr>
<tr><td>Akita</td></tr>
<tr><td>Yamagata</td></tr>
<tr><td>Fukushima</td></tr>
<tr><td>Ibaraki</td></tr>
<tr><td>Tochigi</td></tr>
<tr><td>Gunma</td></tr>
<tr><td>Saitama</td></tr>
<tr><td>Chiba</td></tr>
<tr><td>Tokyo</td></tr>
<tr><td>Kanagawa</td></tr>
<tr><td>Niigata</td></tr>
<tr><td>Toyama</td></tr>
<tr><td>Ishikawa</td></tr>
<tr><td>Fukui</td></tr>
<tr><td>Yamanashi</td></tr>
<tr><td>Nagano</td></tr>
<tr><td>Gifu</td></tr>
<tr><td>Shizuoka</td></tr>
<tr><td>Aichi</td></tr>
<tr><td>Mie</td></tr>
<tr><td>Shiga</td></tr>
<tr><td>Kyoto</td></tr>
<tr><td>Osaka</td></tr>
<tr><td>Hyogo</td></tr>
<tr><td>Nara</td></tr>
<tr><td>Wakayama</td></tr>
<tr><td>Tottori</td></tr>
<tr><td>Shimane</td></tr>
<tr><td>Okayama</td></tr>
<tr><td>Hiroshima</td></tr>
<tr><td>Yamaguchi</td></tr>
<tr><td>Tokushima</td></tr>
<tr><td>Kagawa</td></tr>
<tr><td>Ehime</td></tr>
<tr><td>Kochi</td></tr>
<tr><td>Fukuoka</td></tr>
<tr><td>Saga</td></tr>
<tr><td>Nagasaki</td></tr>
<tr><td>Kumamoto</td></tr>
<tr><td>Oita</td></tr>
<tr><td>Miyazaki</td></tr>
<tr><td>Kagoshima</td></tr>
<tr><td>Okinawa</td></tr>
<tr><td>Outside Japan</td></tr>
<tr><td>N/A</td></tr>
<tr><td rowspan='2'>Automatic Charge</td><td>Off</td></tr>
<tr><td>On</td></tr>
<tr><td rowspan='2'>Display Settings (Internal)</td><td>Off</td></tr>
<tr><td>On</td></tr>
<tr><td rowspan='2'>Read only</td><td>Off</td></tr>
<tr><td>On</td></tr>
<tr><td rowspan='2'>Edit</td><td>Off</td></tr>
<tr><td>On</td></tr>
<tr><td rowspan='2'>Admin</td><td>Off</td></tr>
<tr><td>On</td></tr>
<tr><td rowspan='2'>Alert (Conversion Only Analytics)</td><td>Off</td></tr>
<tr><td>On</td></tr>
<tr><td rowspan='2'>Alert (Editorial)</td><td>Off</td></tr>
<tr><td>On</td></tr>
<tr><td rowspan='2'>Alert (Billing)</td><td>Off</td></tr>
<tr><td>On</td></tr>
<tr><td rowspan='2'>Active Flag</td><td>Off</td></tr>
<tr><td>On</td></tr>
<tr><td rowspan='2'>Status</td><td>On</td></tr>
<tr><td>Off</td></tr>
<tr><td rowspan='5'>Objective of Conversion Tracking</td><td>Others</td></tr>
<tr><td>Page Access</td></tr>
<tr><td>Sales</td></tr>
<tr><td>Application</td></tr>
<tr><td>Sales Promotion</td></tr>
<tr><td rowspan='4'>Page Format</td><td>html</td></tr>
<tr><td>chtml</td></tr>
<tr><td>xhtml(Mobile Phone)</td></tr>
<tr><td>wml</td></tr>
<tr><td rowspan='2'>Page Security Level</td><td>HTTP</td></tr>
<tr><td>HTTPS</td></tr>
<tr><td rowspan='4'>Conversion Type</td><td>Web Page</td></tr>
<tr><td>Click to Call</td></tr>
<tr><td>App</td></tr>
<tr><td>Import</td></tr>
<tr><td rowspan='2'>Counting Type</td><td>Many per click</td></tr>
<tr><td>One per click</td></tr>
<tr><td rowspan='2'>for Auto Bidding</td><td>Include</td></tr>
<tr><td>Exclude</td></tr>
<tr><td rowspan='3'>Action you''d like to track</td><td>App Download (from Google play)</td></tr>
<tr><td>App First Open</td></tr>
<tr><td>In-App Action</td></tr>
<tr><td rowspan='2'>Display Settings (InterestMatch)</td><td>On</td></tr>
<tr><td>Off</td></tr>
<tr><td rowspan='3'>Advanced Location Options</td><td>Location of user</td></tr>
<tr><td>Location included in search query, Location of interest</td></tr>
<tr><td>Location of user, Location included in search query, Location of interest</td></tr>
<tr><td rowspan='2'>Advanced Location Options Excluded</td><td>Location of user</td></tr>
<tr><td>Location of user, Location included in search query, Location of interest</td></tr>
<tr><td rowspan='1'>Focus Device</td><td>Smartphone</td></tr>
<tr><td rowspan='2'>Position (Target position in search results)</td><td>First Page</td></tr>
<tr><td>Top of First Page</td></tr>
<tr><td rowspan='2'>Bid Adjustment Method (Target position in search results)</td><td>Manual Bidding</td></tr>
<tr><td>Full Auto</td></tr>
<tr><td rowspan='2'>Limit by Budget (Target position in search results)</td><td>Increase</td></tr>
<tr><td>Not increase</td></tr>
<tr><td rowspan='2'>Low Quality Keyword (Target position in search results)</td><td>Increase</td></tr>
<tr><td>Not increase</td></tr>

</table>
