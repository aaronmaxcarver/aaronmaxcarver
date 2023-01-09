### projects
[chrt.com](https://chrt.com)

<!--
### essays
[aaronmaxcarver.com](https://aaronmaxcarver.com)
-->

### social
[linkedin.com/in/aaroncarver<br/>](https://linkedin.com/in/aaroncarver)
[youtube.com/aaroncarver<br/>](https://youtube.com/aaroncarver)
discord - aaroncarver#4627
facebook - *none*<br/>
insta - *none*<br/>
twitter - *none*<br/>


## Portfolio (DRAFT - 2022-12-11)

* This portfolio showcases my latest software development project, [CHRT.com](https://chrt.com)

### Product features
* CHRT.com is a performance journal for day traders. After a day of trading, a trader uploads a .csv or Excel file with their transaction data and chrt.com provides the trader with a variety of analytics about their trades
* To use the product, Sign Up at [chrt.com/signup](https://chrt.com/signup), then navigate to [chrt.com/journal](https://chrt.com/journal) and <<use the sample data file>> 

### "Productization"
* **Account security (authentication and authorization)**
  * Secure remote password (SRP) and multi-factor authentication (MFA) - <<>>
  * Attribute-based access control (ABAC) - <<>> 
* **Clickwrap agreement with audit trail, terms of service, privacy policy**
  * <<>>
* **Payments integration**
  * For live payments integration, Stripe's payments WebSocket feed would connect to AWS EventBridge. For each event resulting in a subscription, a Lambda function would use the Node.js AWS SDK client for Cognito to set a new timestamp value for the per-user custom claims relevant to subscriptions such as `custom:JournalSubscription`
  * These claims are already in use across the site by both API Gateway lambda validators and the temporary credentials used by the client-side AWS SDK. The claims can be viewed directly by decoding (such as with [jwt.io](https://jwt.io)) the `idToken` stored in localStorage after Sign In 

### Development
* I wrote all the code and designed the architecture
  * Frontend code is JavaScript, specifically JSX for React
  * Backend code is JavaScript running in the Node.js runtime environment
* Commercial-grade tooling is used for all build processes
 * <<GitHub, CodePipeline, etc.>>
 

*Click any image to display it "fullscreen" a new tab. The diagrams and descriptions are not exhaustive*
 
***

## (1 of 5) Frontend Deployment and Distribution

### Deployment
* Each merge to the `main` branch of the bundle repo on GitHub triggers the build process
* At the end of the build process, the new bundle 

### Bundle
* React.js Single Page Application
* variety of npm packages including [react-router](https://www.npmjs.com/package/react-router), <<>> 
<img width="2560" alt="Frontend" src="https://user-images.githubusercontent.com/59704103/206937582-4f32e336-23b9-4647-b01c-a4f5a56758ee.png">

***

## (2 of 5) Authentication Architecture
* The temporary credentials are used by the AWS JavaScript SDK to make direct requests to almost any AWS service (S3, DynamoDB, Aurora, etc.)
* The JWT is commonly used as the credential for authentication with API Gateway API endpoints which invoke Lamba functions, receive per-user IAM policies, and can be set to cache such policies for up to 3600s
* Custom attributes are useful for checking subscription claims which are set to unix timestamps 
<img width="2560" alt="Auth (2)" src="https://user-images.githubusercontent.com/59704103/206937423-162e3d52-8143-43e7-bfef-6c568df99de0.png">

***

## (3 of 5) Lambda CI/CD
<img width="2560" alt="Lambda CI/CD" src="https://user-images.githubusercontent.com/59704103/206937374-33f9ebcf-6486-43eb-9792-6b62e736ed13.png">

***

## (4 of 5) Data Service Architecture
<img width="2560" alt="Data" src="https://user-images.githubusercontent.com/59704103/206937276-8509154b-3e8b-423c-900d-251ef0b4dc67.png">

*** 

## (5 of 5) Journal Service Architecture
<img width="2560" alt="Journal" src="https://user-images.githubusercontent.com/59704103/206937198-c4b5a1e8-4147-440e-8779-78b626b5ff71.png">
