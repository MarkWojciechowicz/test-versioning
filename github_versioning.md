```mermaid
graph TD
<<<<<<< HEAD
    subgraph API_Dev["API"]
        dev_branch["development 🔀
                    ihsi-api"]
        dev_branch2["development 🔀
                    Generates New Version
                    e.g. api_v1.4.0"]
        feature_branch["Feature 🔀
                        (IHSIDEV-1234)"]
        containter_reg["Containter
                        Registry
                        tagged 'api_v1.4.0'"]
        dev_branch -->|Checkout | feature_branch
        feature_branch -->|PR | dev_branch2
        dev_branch2 -->|Push |containter_reg
    end
    
    subgraph APP_Dev["Website"]
        dev_branch_app["development 🔀
                        ihsi-website"]
        dev_branch2_app["development 🔀
                    Generates New Version
                    e.g. app_v1.1.0"]
        feature_branch_app["Feature 🔀
                        (IHSIDEV-4567)"]
        containter_reg_app["Containter
                        Registry
                        tagged 'app_v1.1.0'"]
        dev_branch_app -->|Checkout | feature_branch_app
        feature_branch_app -->|PR | dev_branch2_app
        dev_branch2_app -->|Push |containter_reg_app
    end

    subgraph deployment["Deployment"]
        api_con["API Container
                Registry"]
        app_con["APP Container
                Registry"]
        ihsi_repo["ihsi-deployment (Repo)"]
        ihsi_change["sandbox_1:
                    &nbsp;&nbsp;&nbsp;api: api_v1.4.0
                    &nbsp;&nbsp;&nbsp;app: app_v1.1.0"]
        sandbox_1["sandbox_1 🖥"]
        style ihsi_change text-align:left

        ihsi_repo -->|"PR
                    to configure 
                    target" | ihsi_change
        ihsi_change --> api_con
        ihsi_change --> app_con
        api_con -->|Push api_v1.4.0 | sandbox_1
        app_con -->|Push app_v1.1.0 | sandbox_1

        api_con_to_dev["API Container
                Registry"]
        app_con_to_dev["APP Container
                Registry"]
        ihsi_repo_to_dev["ihsi-deployment (Repo)"]
        ihsi_change_to_dev["ihsi_dev:
                    &nbsp;&nbsp;&nbsp;api: latest
                    &nbsp;&nbsp;&nbsp;app: latest"]
        ihsi_dev_server["ihsi_dev 🖥"]
        style ihsi_change_to_dev text-align:left

        ihsi_repo_to_dev -->|"PR
                    to configure 
                    target" | ihsi_change_to_dev
        ihsi_change_to_dev --> api_con_to_dev
        ihsi_change_to_dev --> app_con_to_dev
        api_con_to_dev -->|Push api_v1.4.0 | ihsi_dev_server
        app_con_to_dev -->|Push app_v1.1.0 | ihsi_dev_server

    end



    API_Dev --- APP_Dev
    APP_Dev --> deployment
=======
    subgraph Local["Local"]
        A["Develop on Branch"]
        C["Github Action"]
        A -->|PR to main | C
        C -->|pushes| D["Container Registry"]
    end
    
    subgraph Development["Development"]
        E["studio-deployments Repo"]
        G["Development Server"]
        cd["Container Registry"]
        E -->|change SHA to Deploy| cd
        cd --> |pulls | G
    end
    
    subgraph Production["Production"]
        H["Create Github Release"]
        J["Production"]
        H -->|Publish | J
    end
    
    Local -->| | Development
    Development --> | | Production
>>>>>>> origin/main
```