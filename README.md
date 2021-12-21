
# blajar-microservices

1. *Create a design system for a synchronous API microservice that collects and stores data from multiple website crawlers and multiple
third-party API services, which the API service must be able to handle
high-volume REST API calls from clients*

   ![alt text](https://github.com/ydesetiawan/blajar-microservices/blob/main/API_GATEWAY.drawio%20(1).png)

2. *Based on your design system for question 1, provide your solution to improve APIs response time for web crawler data collection.*

 -  **Added pagination to large payloads**  
 
    To solve the problem of relatively large response payloads we had to limit order history by adding pagination and provide JSON linking using hypermedia/Hateoas links for getting order line item details by making one more call with order ID as the key. This significantly reduced the payload size for customers with a long history of orders.

- **Added caching**
 
  We noticed 30% of the requests were the same for customer demographics within a 15 minutes period. The customer demographics don’t change frequently so we decided to add a caching  policy using the API Manager and reduced the capacity bottleneck of the Customer database by reducing the number of calls.

- **Deployed auto-scaling**

  We deployed the APIs within auto-scaling groups where it could scale between two and five instances depending on normal and peak times of the day.
