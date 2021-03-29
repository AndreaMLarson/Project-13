# Kibana

## Exploring Kibana

1. Start by adding the sample web log data to Kibana.

    - You can import it by clicking **Try our sample data**.

        ![](Images/Welcome.png)

    - Or you can import it from the homepage by clicking on **Load a data set and a Kibana dashboard** under **Add sample data**.

        ![](Images/add-data.png)

    - Click **Add Data** under the **Sample Web Logs** data pane.

        ![](Images/sampledata.png)

    - Click **View Data** to pull up the dashboard.

        ![](Images/view-data.png)

2. Answer the following questions:

    - In the last 7 days, how many unique visitors were located in India?

       - **Example Answer:** 252

        ![](Kibana/Images/unique visitors.png)


    - In the last 24 hours, of the visitors from China, how many were using Mac OSX?

       - **Example Answer:** 66

        ![](Kibana/Images/cn mac osx.png)

    - In the last 2 days, what percentage of visitors received 404 errors? How about 503 errors?

        - **Example Answer:** 404: 6.667% and 503: 13.333%
      On 3/27 2.10% of visitors reached a 404 error and 2.10% reached a 503 error  
       ![](Kibana/Images/status-3-27.png)
       On 3/28 from 12:00am to 4:00am 2.63% visitors received a 404 error
        ![](Kibana/Images/status-3-28-0-4.png)
      On 3/28 from 4:00am to 8:00am 6.32% of visitors reached a 404 error and 3.79% of users reached a 503 error
        ![](Kibana/Images/status-3-28-4-8.png)
      On 3/28 from 8:00am to 12:00pm 5.12% of users reached a 404 error and 2.56 reached a 503 error
        ![](Kibana/Images/status-3-28-8-12.png)
      On 3/28 from 12:00pm to 12:00am visitors did not receive any errors
        ![](Kibana/Images/status-3-28-12-24.png)

    - In the last 7 days, what country produced the majority of the traffic on the website?

        - **Example Answer:** United States

          ![](Kibana/Images/traffic-majority.png)

          - Of the traffic that's coming from that country, what time of day had the highest amount of activity?

              - **Example Answer:** 12 p.m. and 1 p.m. (hours 12 and 13)
          ![](Images/most-traffic2.png)

    - List all the types of downloaded files that have been identified for the last 7 days, along with a short description of each file type (use Google if you aren't sure about a particular file type).

        - **Example Answer:**

            - **gz:** `.gz` files are compressed files created using the gzip compression utility.

            - **css:** `.css` files can help define font, size, color, spacing, border and location of HTML information on a webpage. They are downloaded with their `.html` counterparts and rendered by the browser.

            - **zip:** A lossless compression format. A `.zip` file may contain one or more files or directories that have been compressed.

            - **deb:** A file with the `.deb` file extension is a Debian (Linux) Software Package file. These files are installed when using the `apt` package manager.

            - **rpm:** `.rpm` file formats are a Red Hat Software Package file. RPM stands for Red Hat Package Manager.

         ![](Kibana/Images/downloaded-files.png)

3. Look at the chart that shows Unique Visitors Vs. Average Bytes.

    ![](Kibana/Images/users-vs-bytes.png)

    - Locate the time frame in the last 7 days with the most amount of bytes (activity).

    - In your own words, is there anything that seems potentially strange about this activity?

        **Example Answer:** (Your results may be different.) In our example, it seems strange that _4_ visitors are using a number of bytes that is considerably higher than all other usage.

         ![](Kibana/Images/usage.png)

4. Filter the data by this event.

     ![](Kibana/Images/event-details.pngg)

    - What is the timestamp for this event?

        - **Example Answer:** The time filter shows Mar 25, 2021 @ 16:55:00:0 -> March 25, 2021 17:00:00.0

    - What kind of file was downloaded?

       - **Example Answer:** A gz file


    - From what country did this activity originate?

        - **Example Answer:** North America


    - What HTTP response codes were encountered by this visitor?

        - **Example Answer:** 200 OK


5. Switch over to the Kibana Discover page to see more details about this activity.

    - What is the source IP address of this activity?

        - **Example Answer:** `1.145.31.121`

    - What are the geo coordinates of this activity?

        - **Example Answer:** `{ lat": 28.28980556, "lon": -81.43708333 }`

    - What OS was the source machine running?

        - **Example Answer:** Windows 8

    - What is the full URL that was accessed?

        - **Example Answer:** https://artifacts.elastic.co/downloads/beats/metricbeat/metricbeat-6.3.2-i686.rpm

    - From what website did the visitor's traffic originate?

        - **Example Answer:** http://www.elastic-elastic-elastic.com/success/aleksandr-serebrov


6. Finish your investigation with a short overview of your insights.

    - What do you think the user was doing?

        - **Example Answer:** This event appears to be a user downloading a Linux package from the website being monitored.

    - Was the file they downloaded malicious? If not, what is the file used for?

        - Linux packages aren't typically malicious, but they could be. Depending on the website, this could be harmless traffic from a sysadmin performing an update.

    - Was there anything that seems suspicious about this activity?
    - Is any of the traffic you inspected potentially outside of compliance guidelines?

        - **Example Answer:** The main concern is the referral link from a user, no main concerns in this instance

          -  This user could be further monitored for additional activities that may seem suspicious.
