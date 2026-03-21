# Advanced AWS – Week 6

## Homework Day 1 – Intro to Serverless AWS

---
##Lamda Function

```
export const handler = async (event) => {
  console.log("Incoming event:", JSON.stringify(event));

  // TODO implement
  const response = {
    statusCode: 200,
    headers: {
      "Content-Type": "application/json"
    },
    body: JSON.stringify({
      message: "Hello from Lambda!",
      path: event?.rawPath ?? null,
      method: event?.requestContext?.http?.method ?? null,
      time: new Date().toISOString()
    })
  };

  return response;
};

```


Students must submit a short Markdown file (or Google Docs) with:

## A) Proof Screenshots

1. Lambda function list showing `lv4-week6-hello`
   <img width="1133" height="252" alt="image" src="https://github.com/user-attachments/assets/1325a5f2-3b9e-430a-baa7-12d1472be311" />

3. Lambda test result showing success
   <img width="1360" height="292" alt="image" src="https://github.com/user-attachments/assets/ece14a31-c4a0-4795-8f89-63c36cf5f28a" />

5. API Gateway HTTP API page showing:  
   - route `GET /hello`
     <img width="461" height="487" alt="image" src="https://github.com/user-attachments/assets/e3f79e09-e7a5-481a-a222-7792e5853b93" />

   - invoke URL
     <img width="644" height="225" alt="image" src="https://github.com/user-attachments/assets/aa7b7a00-7d2f-498b-b253-4a259820cc6c" />
 
6. Postman request + response (200)
   <img width="893" height="252" alt="image" src="https://github.com/user-attachments/assets/81213c6d-d6f1-4c1d-a87f-dbd845a2d620" />

7. CloudWatch log stream with the "Incoming event" line
   <img width="490" height="27" alt="image" src="https://github.com/user-attachments/assets/bdf78335-3ec9-44d0-a482-e0261530dddb" />


---

## B) Concept Questions

1. In one paragraph: What problem does API Gateway solve that Lambda alone does not?
   API Gateway lets people actually access your Lambda through a URL. Lambda just runs code, but API Gateway handles the HTTP requests (like GET and POST) and routes them to the right function.
3. Why does the Lambda proxy response require `statusCode`, `headers`, and string `body`?
   Lambda proxy responses need statusCode, headers, and a string body because API Gateway requires that format to send an HTTP response correctly.
5. What are the free-tier headline limits for:
   - API Gateway HTTP APIs: about 1 million requests per month 
   - Lambda requests/comput: 1 million requests per month + 400,000 GB-seconds of compute time per month
     
## Homework Day 2 - Advanced Serverless AWS

## Part A — Build proof (screenshots)

1. API Gateway routes list showing all 5 routes:
   - GET /items
   - POST /items
   - GET /items/{id}
   - PUT /items/{id}
   - DELETE /items/{id}

     <img width="459" height="335" alt="image" src="https://github.com/user-attachments/assets/d31ca015-7973-4d26-9079-f566cc9cefd7" />

     <img width="443" height="336" alt="image" src="https://github.com/user-attachments/assets/9f42ce8f-3d6f-4c5a-8642-8003c34f76e2" />



2. Integrations screen showing which Lambda is attached to which route
   <img width="973" height="473" alt="image" src="https://github.com/user-attachments/assets/66861800-424c-443d-ac1b-9525f67768ab" />


4. Lambda A and Lambda B "Monitor → CloudWatch logs" showing request logs
   <img width="704" height="437" alt="image" src="https://github.com/user-attachments/assets/588cf05f-5b14-4aa1-bd6b-b913a0e254a6" />

   <img width="629" height="541" alt="image" src="https://github.com/user-attachments/assets/a666ff66-a09d-46e4-b3cb-35a7f657edd5" />




# Part B — Postman proof (screenshots)

4. Postman GET /items response
   <img width="463" height="277" alt="image" src="https://github.com/user-attachments/assets/a5538711-2d95-4018-934b-1782369ecf4b" />


6. Postman POST /items response (201)
   <img width="647" height="306" alt="image" src="https://github.com/user-attachments/assets/722654bb-844c-435f-b097-f1cc6c54f695" />



# Part C — Concept questions (short)

6. Why can’t we rely on in-memory storage in Lambda for persistence?
   Because Lambda functions don’t stick around. They spin up, do their job, and can disappear anytime. So if you save something in memory, it might be gone the next time your code runs.

8. What is a "route" in HTTP API Gateway, and what are its two parts?
   A route in HTTP API Gateway is basically how a request gets matched to your code. It consists of the HTTP method and the path.

10. What does CORS configuration in HTTP API do, and what headers are required for preflight?
    CORS in HTTP API controls whether a browser is allowed to call your API from another origin. It basically tells the browser if the request should be allowed or blocked.

    Access-Control-Allow-Origin, Access-Control-Allow-Methods, and Access-Control-Allow-Headers
