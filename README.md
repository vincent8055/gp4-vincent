# gp4-vincent

Workflow push to different branches


Deploy to dev branch (on push from local)

![Screenshot 2023-09-04 at 12 26 53 AM](https://github.com/vincent8055/gp4-vincent/assets/127754761/15539a1a-f34a-4586-bf1a-2bc2e0ea047b)
PS: this can be up to dev

Deploy to prod (after pull request)
![Screenshot 2023-09-04 at 12 25 20 AM](https://github.com/vincent8055/gp4-vincent/assets/127754761/2e83e5dc-148c-4125-91c2-d2587577b7e1)

I am also able to get the name of the branch (dev)

![Screenshot 2023-09-04 at 12 28 58 AM](https://github.com/vincent8055/gp4-vincent/assets/127754761/ebc97738-0af1-413a-b161-78adb07220ac)

![Screenshot 2023-09-04 at 12 29 56 AM](https://github.com/vincent8055/gp4-vincent/assets/127754761/be58d531-c81c-476b-b116-d1e7e81af7f3)

However, you will notice that it failed to deploy.  This is because I tried to use this variable (GIT_BRANCH) to determine the service name in the serverless.yml ie ```Gp4-env-${env.GIT_BRANCH}``` --> Gp4-env-dev .  This will not work as I found out that in Serverless framework, ```service``` cannot work with environment variables.  

Options is we leave it as is, or we create different serveless.yml files for each environment ie serverless-dev.yml and serverless-prod.yml to determine the different service name.

