# RealTimeDataProcessing-StreamService
# SWA Project Overview

Design a software system that allows the real-time participation and the real-time presentation of data from real-time data platforms.

- **Participation of Data**: Connect to the data platform of your choice, either by making a hook or regular request using the available API.
- **Data Structure**: Typically, the data is in JSON format. For instance, data from the [London Tube Schedule Update platform](https://ably.com/hub/ably-tfl/tube) looks like:
```json
{
  "current": "failed",
  "previous": "suspended",
  "reason": {
    "code": 40400,
    "statusCode": 401,
    "nonfatal": false,
    "href": "https://help.ably.io/error/40400"
  }
}

System Components
1. Real-time Data Input Service (RTDIS)
Connects to the data platform and fetches data.
Publishes received JSON data on Kafka Stream.
Each RTDIS has its unique topic.
Some platforms may require an API Key for data access.
Use free APIs when possible.
2. JSON Data Ripper Service (JDRS)
Processes the published JSON data.
Splits data into individual elements.
Publishes each element to its unique topic.
3. Presentation Service (PS)
Presents the time series of topic values.
Generates a CSV file with data values.
Note: Web applications can be designed using a microservices architecture.

Data Platforms: Teams can choose from these platforms or from Ably's Open Data Streaming Program.
Additional Requirements
Use MongoDB for microservices requiring data persistence.
Implement streaming with Kafka.
Implement logging and tracing.
Consider using a central Config Service for centralized configuration.
Progress Submission
Daily progress reports are to be submitted in Sakai. All team members must submit their individual reports.
