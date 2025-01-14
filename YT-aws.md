# serverless VS non serverless Architecture

# non serverless Architecture
- Only have to take care of the code and the infrastructure both for eg.
    - API = REST | GRAPHQL [we have this api]
    - AWS >>> EC2 [virtual machine with 2gb ram and 500gb storage] >> Execute the code in >>> ASG [auto-scaling-group expand 6gb ram and 1000gb storage]
    - billing perhour basis as application keep running 24 /7
    - EC2 [virtual machine]
        - setup the OS
        - Ram
        - storage
        - configurations 
        - upscale, downscale

# Serverless

- Only have to take care of the code and the infrastructure is not in our hand.
    - AWS Lambda
    - now AWS will decide the RAM, OS, Storage, upscale, downscale
    - billing = rate per invocation when the traffice is zero there is no charge applicable.
    - Application keep start and stop on the basis of usage.
    - if n num of invocation or n num of user uses the api then [n * rate] will be the charge.
    
