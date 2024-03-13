# Deploying_Backend

**Deploying** means moving the backend from `localhost` to `internet`. Thus, making it accessible on internet. **AWS** is the most popular cloud, followed by **Azure**, **GCP**. 

Deploying **Backends are slightly trickier than Frontends**, since frontends are usually same(html, css, js) for user, but data is dynamic which is served by backend.

Two ways to deploy backends : 

- Basic/Easy Requires Manual Work
- Using CI/CD (Advance)


# 1st - Manual Deployment

---

Following are the steps to perform manual update/changes to server

1. SSH into machine
2. Pull your latest code `git pull origin {branch-name-main/master}`
3. Start the process `pm2 start` or Stop existing process `pm2 kill`
4. Re-build the code `Maybe have some new packages`
5. Re-run the code (pm2)

- Ignoring previously committed file in `.gitignore`
    
    ```jsx
    git rm --cached backend.pem
    ```
    

# 2nd - Automating via Bash Script

---

**Using Bash Script** : Writing all those manual command used in single file/script. Add this to `/home/ubuntu`  and to run `source ./deploy.sh`

# 3rd - Single Line Script via Local Machine

---

**One Command in local machine** : Still an extra command after pushing changes to github.

# 4th - GitHub Actions CD

---

Platforms similar to GitHub are GitLab, Bit Bucket, offers feature called **CD** (**Continuous Deployment**) which essentially allow us to create actions (similar to scripts) that auto deploys on commit to specific branch to repository.

Also to ensure that production ready code is commited or merged to main branch these version control platforms offer **CI** (**Continuous Integration**), involves running a series of **automated tests** when code is pushed to the main repository, but before it is merged or committed. 

[What is Continuous Integration?](https://youtu.be/_zCyLT33moA?si=17BAov5D-CnbTvLI)

In GitHub Repository, inside `.github/workflows/` create, `deploy-to-aws.yaml`