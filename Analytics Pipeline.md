Company: LainSoft

Genre/Tags:  MMO, Turn-based, PvE, In-Game transactions

Active Players:  ~15,000 ( Players with activity occurring within the last 30 days )
<br>
<br>
<br>
<br>
1.0	Analytics
<br>
<br>
    1.1	Overview  <br>
    1.2	Data Ingestion & Transfer <br>
    1.3	Data Storage  <br>
    1.4	Data Processing & Analysis  <br>
    1.5	Visualization <br>
    1.6	Example & Explanation <br>
<br>
<br>
<br>
<br>
1.1	Overview  ---------------------------------------------------------------------------------------------------------------------------------------------
<br>
<br>
  LainSoft expresses the desire to transfer their current analytics solution to AWS. This includes analysis of strictly game-related data such as 
  the average time a player spends fighting a boss enemy in-game or non-Identifiable/Unique user information such as the event itself of a player
  engaging in a digital transaction. Their current team does not have the capacity to perform complex or time-sensitive analytics tasks. They would
  like for cost to primarily be controlled by their real-time needs or desires. They average 15,000 active players currently but have hundreds of thousands 
  registered to the game whose historical data will still be retained and utilized.
<br>
<br>
<br>
<br>
1.2	Data Ingestion & Transfer -----------------------------------------------------------------------------------------------------------------------------
<br>
<br>
1. Kinesis Data Stream
<br> 

    * Utilize a Kinesis Agent to send data from existing backend
    * Can automatically encrypt data as it enters a stream
    * Billing is charged for each shard at an hourly rate, PUT payload unit is charged at a per million rate
    * A shard is the base throughput unit for Kinesis Data Stream
<br>
2. Kinesis Data Firehouse
<br>

    * Can automatically scale to handle ingestion of data in response to active players
    * Billing only occurs for data that is transmitted through Kinesis Data Firehose
    * Can be used to transfer data to a Data Lake built on AWS utilizing S3
<br>
<br>
3. Kinesis Data Analytics
<br>

    * Can automatically scale to handle ingestion of data in response to active players
    * Analyze data while streaming for real-time use by employees
    * Billing is based on the average number of KPUs
        * Kinesis Processing Unit is defined as memory, computing, and networking  assigned to the data stream
<br>
<br>
<br>
<br>
1.3	Data Storage  -----------------------------------------------------------------------------------------------------------------------------------------
<br>
<br>
1. Data Lake implementation on AWS
<br>
<br>
  a. Ease of use benefits
<br>

    * Composed of non-relational data ( raw Data ) and relational data ( defined/schema )
    * Non-relational data doesn’t require specific tailoring to be collected
    * Can be collected from a wide variety of sources
    * Can run analytics without transferring data to a different system and utilize preferred platforms 
<br>
	b. Analytical Advantages
<br>

    * Machine Learning
    * Data enters in real-time
    * Predict specific outcomes
    * Utilize data to react to potential outcomes
<br>
<br>
2. AWS S3
<br>

    * Unlimited scale which can support unknown growth of the game
    * Capable of holding unstructured data which is utilized for Machine Learning
    * Support for different storage types with regard to frequency of access or importance
<br>
<br>
3. AWS Storage Gateway
<br>

    * Extend on-premises data into AWS to alleviate storage cost and increase retainability of player data
    * Hold historical data for potential hundreds of thousands of subscribed players who may not be active
<br>
<br>
4. AWS Direct Connect
<br>

    * Establish private connectivity to AWS and provide multiple avenues to ensure security of data
    * Increase reliability and throughput to respond to random events
<br>
<br>
<br>
<br>
1.4	Data Processing & Analysis  ---------------------------------------------------------------------------------------------------------------------------
<br>
<br>
1. Amazon RedShift
<br>

    * Can support the unstructured data that is fed into it
        * Will integrate easily with the Data Lake
    * Can utilize RedShift Spectrum to run queries without the need for extensive ETL
        * Will accommodate the need for analytics to be handled without large time or team investment
    * Can be used to store gameplay related data and non-Identifiable data obtained from players
    * Petabyte-scale ensures that storage needs will be met for the foreseeable future
    * Billing occurs per-second according to the node type and number of nodes in the cluster and can be changed to 
    accommodate storage as the player count grows
    * Billing will also occur for the number of bytes that RedShift Spectrum scans
<br>
<br>
<br>
<br>
1.5	Data Visualization  -----------------------------------------------------------------------------------------------------------------------------------
<br>
<br>
1. Amazon CloudWatch
<br>

    * Aide in a more seamless migration to AWS by having utilization information from the various AWS tools available 
    in a central area in a visual interface
    * Highly Customizable to meet the needs of the team as they evolve
    * Integrated with SNS to notify team members of specific events
<br>
<br>
2. Amazon QuickSight
<br>	

    * Allows team members to create dashboards specific to data they choose
    * Can provide Machine Learning insights for predictions
    * Highly customizable and interactive
    * Support for automatic delivery of reports based on data it receives
    * Billing is based on pay-per-session for users who are not the creators of the dashboard
<br>
<br>
<br>
<br>
1.6	Example & Explanation --------------------------------------------------------------------------------------------------------------------------------
<br>
<br>
Data entering in real-time allows LainSoft to respond to analytics quickly. This is crucial due to the MMO nature of the game as opposed to a 
single-player experience. Analytics indicating trends that negatively affect the game, such as cheating based on data suggesting a player is doing 
damage substantially above what should be feasible could spread within the community through various media platforms within 24 hours and present a
challenge to implement a solution as the number of players impacted spans the entire active community. For this same reason, the need to predict
outcomes for other types of scenarios such as monetization is also crucial.
<br>
<br>
According to the needs of LainSoft Kinesis Data Streams was chosen for its ability to serve as the point of entry to their new analytics pipeline 
and feed into Kinesis Data Analytics and Kinesis Data Firehouse. These methods of data ingestion can handle analyzation of the data, decreasing the 
load on their team and also are only charged in regard to their specific wants or active use. The inclusion of a Data Lake on AWS will also largely 
decrease the workload of their team as services such as S3 offer seemingly unlimited storage, avoiding data silos, while being integrated with their
existing infrastructure through Storage Gateway and DirectConnect to ensure their analytics remain private and also offer support for both
non-relational data and relational data. This ensures that neither storage nor the formatting of data will be a concern for their team. Amazon
RedShift further supports this choice and will likely reduce their cost as they scale its performance to their needs. Finally, Amazon CloudWatch 
and QuickSight will greatly reduce the effort required by their live team to respond to analytics with real-time notification and concise visualized 
data.
<br>
<br>
Ex. A new boss is announced for the game that requires users to be at a certain level defined by their gear. Typically, LainSoft sees an increase of
digital transactions involving an item that allows users to fast-track improvements to their gear following these announcements as presented by historical 
data within their Data Lake. Across all sources, data enters via Kinesis Data Streams into Kinesis Data Analytics, indicating this is not the case for 
this specific announcement based on the current number of purchases. However, through Machine Learning done on this data and historical data within
Amazon RedShift, it is suggested that a discount on these digital transactions could remedy this issue as it has in the past. Further use of Machine
Learning suggests a variety of different discount options. LainSoft implements a 20% discount on purchases and within the next 12 hours, see a healthy
increase in purchases they deem profitable based on the discount suggested.
