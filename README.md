# Tailscale on WSL2

- Tasks on WSL2

  1. Install Tailscale on WSL2 (Ubuntu 20.04)

     ```shell
     curl -fsSL https://pkgs.tailscale.com/stable/ubuntu/focal.gpg | sudo apt-key add -
     curl -fsSL https://pkgs.tailscale.com/stable/ubuntu/focal.list | sudo tee /etc/apt/sources.list.d/tailscale.list
     sudo apt-get update
     sudo apt-get install tailscale
     ```

  1. Start Tailscale daemon

     ```shell
     sudo tailscaled
     ```

  1. Let WSL2 to join the Tailscale network

     ```shell
     sudo tailscale up
     ```

- Tasks on Windows 10

  1. Configure Task Scheduler to start Tailscale on statrup

     1. open Task Scheduler

        ![open Task Scheduler](./images/tailscale_TaskScheduler_01.png "Task Scheduler")

     1. click `Create Task`

        ![Create Task](./images/tailscale_TaskScheduler_02.png "Create Task")

     1. click `Triggers`

        ![Triggers](./images/tailscale_TaskScheduler_03.png "Triggers")

     1. click `New`

        ![new Trigger](./images/tailscale_TaskScheduler_04.png "new Trigger")

     1. click `Begin the Task`

        ![click Begin the Task](./images/tailscale_TaskScheduler_05.png "click Begin the Task")

     1. select `At log on`

        ![select At log on](./images/tailscale_TaskScheduler_06.png "select At log on")

     1. save the Trigger

        ![save Trigger](./images/tailscale_TaskScheduler_07.png "save Trigger")

     1. click `Actions`

        ![Actions](./images/tailscale_TaskScheduler_08.png "Actions")

     1. click `New`

        ![new Action](./images/tailscale_TaskScheduler_09.png "new Action")

     1. create and save a new `Action`

        ![Actions](./images/tailscale_TaskScheduler_10.png "Actions")

        - Program/script:
          - `wsl` or `C:\Windows\System32\wsl.exe`
        - Add arguments:
          - `-u root tailscaled` or `-u root /usr/sbin/tailscaled`

        ![Actions](./images/tailscale_TaskScheduler_11.png "Actions")

     1. click `General`

        ![General](./images/tailscale_TaskScheduler_12.png "General")

     1. configure the task settings

        - Name:
          - any name you would like
        - Security options
          - select `Run whether user in logged on or not`
          - check `Run with highest privileges`
        - Hidden:
          - check `Hidden`
        - Configure for:
          - select `Windows 10`

        ![General](./images/tailscale_TaskScheduler_13.png "General")

     1. Done!

        ![Done!](./images/tailscale_TaskScheduler_14.png "Done!")
