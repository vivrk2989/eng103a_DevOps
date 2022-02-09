## S3 aervice in AWS

![Image Link](https://github.com/vivrk2989/eng103a_DevOps/blob/main/Images/S3%20Diagram.png)

Simple Storage Service (Amazon S3) is an object storage service that offers industry-leading scalability, data availability, security, and performance. Customers of all sizes and industries can use Amazon S3 to store and protect any amount of data for a range of use cases, such as data lakes, websites, mobile applications, backup and restore, archive, enterprise applications, IoT devices, and big data analytics.

### Benefits
1. Globally available
2. Can store anything
3. Used for Disaster Recovery (DR)
4. Can apply CRUD(Create, Read, Update and Delete) actions

### S3 Storage classes
- Standard: Can acess data anytime
- Glacier - non-urgent/Infrequent data access (Pay less compared to standard)

### Logging into the s3 bucket service

1. SSH into your AWS machine using `ssh -i "filename.pem" ubuntu@............eu.west-1.compute.amazonaws.com`
2. update and upgrade using `sudo apt update -y` and `sudo apt upgrade -y`
3. To install python, use `sudo apt install python3-pip`
4. check the version of python using `python --version`
5. By deafult 2.x version of python is installed. But we require atleast 3.x to work 
6. Use `alias python=python3.7` to install the required version
7. Then use `sudo pip3 install awscli`
8. Now to get into the S3, use `aws configure`
9. And this will ask for your aws access key id, your aws secret access key, region - `eu-west-1` and language - `json`
10. Once you are in, you can see the directories in s3 using `aws s3 ls`

### Commands in S3
- To make a bucket, use `aws s3 mb s3://name-of-the-bucket` . Note - Make sure you dont use underscore while naming a bucket. It will give errors.
- This bucket can be used to store data which can be accessed or used globally.
- use `sudo nano filename.txt` to create a text file. 
- To move the above file into the bucket, use `aws s3 cp filename.txt s3://name-of-the-S3-Bucket`
- Now an object `filename.txt` will be created in our bucket. We can utilize the data in the bucket using the `Object URL` but you cant access it now as we still need to provide permissions to access the file. 
- To utilize the data which is available globally, we need to set some permission using the `Permissions` tab inside the bucket of our aws console.
- Here, we have the option to make this data available for public access and authenticated users group. Make it `Read` on both the places and this will allow us to see the contents within the file we moved to the bucket.
- We can delete the test file we created using `sudo rm filename.txt`
- `ls` it to check if this works. 

### Moving data from s3 to our EC2 Instance

- Use `aws s3 cp s3://name-of-the-S3-Bucket/filename.txt ~`. This will download the file from s3 bucket to our EC" instance. Test this using `ls` .

### Deleting the S3 Bucket
- use `aws s3 rm s3://name-of-the-S3-Bucket --recursive` . This will delete all the files/data within the bucket.
- Now use `aws s3 rb s3://name-of-the-S3-Bucket` to delete the empty bucket

### CRUD Task

- Install boto3 using `pip install boto3` . Boto3 is an AWS `software developemtn kit` for python.
- Now create a python script that does CRUD for our data in aws using `sudo nano filename.py`
#### Let's automate the CRUD procedure 
1. In the python script we created type the following commands:
```
import boto3 # Imports the boto3 package we installed

bucket_name = input("What is the name of your S3 bucket?\n") # Creating a bucket name

location = {'LocationConstraint': "eu-west-1"} # Restricting it to just europe west region

s3 = boto3.resource('s3')
# the Resource() accepts the AWS service name as a parameter. By providing 's3' inside resource(), we can use it to perform operations on s3 objects.

print("For the CRUD operations of your choice, input mb for making bucket, up for uploading file, dl for downloading file, de for deleting file from s3 and rb to delete the bucket", ex to exit)

operation = [mb, up, dl, de, rb]

while true:
    action = input("Type of CRUD: ")

    if action not in operation:
        print("You have entered an invalid operation. Please enter a valid operation)
        continue
    elif action == "mb":
        s3.create_bucket(Bucket=bucket_name, CreateBucketConfiguration=location)
    elif action == "up":
        name_of_file = input("Name of file you like to upload: ")
        name_of_file_in_bucket = input("Name you would like to assign to the file being uploaded: ")
        s3.upload_file("name_of_file", "bucket_name", "name_of_file_in_bucket")
    elif action == "dl":
        name_of_file = input("Name of file you like to download: ")
        name_of_file_in_destination = input("Name you would like to assign to the file being downloaded: ")
        s3.download_file("bucket_name", "name_of_file", "name_of_file_in_destination")
    elif action == "de":
        name_of_file = input("Name of file you like to delete: ")
        s3.Object("bucket_name", "name_of_file").delete()
    elif action == "rb":
        s3.Bucket(bucket_name).delete()
    elif action == "ex":
        print("Successfully exited!")
        break
        print("You are in! you can use the required operations")
        
```
2. Run the script using `python3 filename.py`

  