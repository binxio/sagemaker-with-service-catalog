# sagemaker-with-service-catalog
How to create a self-service, on-demand Sagemaker for data analysts with AWS Service Catalog.


Follow these steps to get going:

1. Create a `PortfolioBucketName` S3 Bucket.

    aws s3 mb s3://sagemaker-with-service-catalog

2. Upload the product

    aws s3 cp products/ s3://sagemaker-with-service-catalog/products/ --recursive

3. Create the servicecatalog with cloudformation

    aws cloudformation create-stack --stack-name sagemaker-with-service-catalog --template-body file://portfolios/sagemaker-product.yml --parameters ParameterKey=SupportUrl,ParameterValue=https://binx.io ParameterKey=PortfolioBucketName,ParameterValue=sagemaker-with-service-catalog --capabilities CAPABILITY_IAM

4. Assume the newly created role.

e.g. https://signin.aws.amazon.com/switchrole?roleName=sagemaker-with-service-catalog-SagemakerRole-XXXXX

5. Start the Portfolio in AWS console

6. Enjoy you Sagemaker