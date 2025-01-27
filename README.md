# MachineGuid Spoof Guide

Simple steps to manually spoof the `MachineGuid` in `HKLM\SOFTWARE\Microsoft\Cryptography`.

---

## **Using Command Prompt (CMD)**
1. **Run as Administrator**:  
   Right-click CMD > *Run as administrator*.

2. **Generate & Set New GUID**:  
   Paste this command:
   ```cmd
   for /f %g in ('powershell -command "[guid]::NewGuid().ToString()"') do reg add "HKLM\SOFTWARE\Microsoft\Cryptography" /v MachineGuid /t REG_SZ /d "%g" /f
   ```
   
## **Using PowerShell**
1. **Run as Administrator**:  
   Right-click PowerShell > *Run as administrator*.

2. **Generate & Set New GUID**:  
   Paste this command:
   ```powershell
   New-Guid | ForEach-Object { Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Cryptography" -Name "MachineGuid" -Value $_.Guid }
   ```

⚠️ **Note**:  
- Requires admin privileges.  
- Changing `MachineGuid` may affect software/services relying on it.  
- Use at your own risk.  
