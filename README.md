# Facebook-Campaign-Analysis
![How-to-Create-a-Social-Media-Marketing-Strategy-for-Your-Business](https://user-images.githubusercontent.com/92436079/225217596-bb3ea0d8-d46c-4854-975f-9f94e644f98a.jpg)


Social Media ad campaign is one of the best ways to market your business online.I performed exploratory data analysis for xyz company to help the marketing depertment get more insights on the facebook campaigns they have ben running.

[Data Source]( https://www.kaggle.com/code/joshuamiguelcruz/facebook-ad-campaign-eda/notebook)

The data used in this project is from an anonymous organisation’s social media ad campaign.

1.) ad_id: an unique ID for each ad.

2.) xyzcampaignid: an ID associated with each ad campaign of XYZ company.

3.) fbcampaignid: an ID associated with how Facebook tracks each campaign.

4.) age: age of the person to whom the ad is shown.

5.) gender: gender of the person to whim the add is shown

6.) interest: a code specifying the category to which the person’s interest belongs (interests are as mentioned in the person’s Facebook public profile).

7.) Impressions: the number of times the ad was shown.

8.) Clicks: number of clicks on for that ad.

9.) Spent: Amount paid by company xyz to Facebook, to show that ad.

10.) Total conversion: Total number of people who enquired about the product after seeing the ad.

11.) Approved conversion: Total number of people who bought the product after seeing the ad.

**OBJECTIVES**

The objectives of this analysis are:

1.To identify the top performing advertisements

2.Determine the demographics of people who bought the product

3.See how to improve the least performing advertisements based on the data

**DATA CLEANING**

**Checking Missing Values**

```sql
select ad_id 
from FacebookCampaign
where ad_id is null
```

![image](https://user-images.githubusercontent.com/130441998/236917330-3fde5b7d-9751-42f9-ab73-9ce6e77350ab.png)

+ No Missing Value

**Checking Duplicates**

```sql
select distinct ad_id from FaceBookCampaign
```

![image](https://user-images.githubusercontent.com/130441998/236918387-c8cb8d4e-d14f-4e57-9d7e-118bfa1bf0b0.png)

+ No Duplicates

**Manupulation of Data**

+ Manupulating xyz_Campaign_id column to represent the 3 campaign level from level 1 to 3 and updating the table

```sql
select distinct xyz_campaign_id,
CASE
when xyz_campaign_id=916 then 1
when xyz_campaign_id=936 then 2
when xyz_campaign_id=1178 then 3
end as CampaignCategory
from FacebookCampaign
```

```sql
update FaceBookCampaign set xyz_campaign_id=CASE
when xyz_campaign_id=916 then 1
when xyz_campaign_id=936 then 2
when xyz_campaign_id=1178 then 3
end
```

```sql
Select distinct xyz_campaign_id from FacebookCampaign
```

**Total Purchase per Campaign**

```sql
select xyz_campaign_id,sum(Approved_Conversion) as TotalApprovedConversion
from FacebookCampaign
group by xyz_campaign_id
order by TotalApprovedConversion desc
```


![image](https://user-images.githubusercontent.com/130441998/236924113-b6adeea5-55d4-4925-bf9d-252aae0180e9.png)
