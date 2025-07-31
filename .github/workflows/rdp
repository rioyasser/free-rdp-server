name: RDP

on: [workflow_dispatch]

jobs:
  build:
    runs-on: windows-latest
    steps:
      - name: Download ngrok
        run: |
          Invoke-WebRequest https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-stable-windows-amd64.zip -OutFile ngrok.zip
          Expand-Archive ngrok.zip
          ./ngrok.exe authtoken YOUR_AUTH_TOKEN

      - name: Enable RDP
        run: |
          net user kamel123 MyStrong123 /add
          net localgroup administrators kamel123 /add
          Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server' -Name 'fDenyTSConnections' -Value 0
          Enable-NetFirewallRule -DisplayGroup "Remote Desktop"
          ./ngrok.exe tcp 3389
