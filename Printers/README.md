# Intune Policy – Secure Point and Print Configuration

This configuration profile is designed to manage **Point and Print Restrictions** via **Administrative Templates** in Microsoft Intune. It enhances printer security by allowing only approved servers and suppressing prompts during driver installation and updates.

---

## 🔧 Policy Configuration Summary

### Administrative Templates → Printers

| Setting Name                                               | State    | Value                         |
| ---------------------------------------------------------- | -------- | ----------------------------- |
| Limits print driver installation to Administrators         | Disabled |                               |
| Package Point and Print – Approved servers                 | Enabled  | `printserver.local`           |
| Point and Print Restrictions                               | Enabled  | See detailed values below     |
| Users can only point and print to machines in their forest | False    |                               |
| Users can only point and print to these servers            | True     | `printserver.local`           |
| Install driver prompt (new connection)                     | Enabled  | Do not show warning or prompt |
| Update driver prompt (existing connection)                 | Enabled  | Do not show warning or prompt |

---

### System → Device Installation → Device Installation Restrictions

| Setting Name                                                               | State   | Value                                                                                                                    |
| -------------------------------------------------------------------------- | ------- | ------------------------------------------------------------------------------------------------------------------------ |
| Allow installation of devices using drivers that match these setup classes | Enabled | `{4d36e979-e325-11ce-bfc1-08002be10318}, {4658ee7e-f050-11d1-b6bd-00c04fa372a7}, {1ed2bbf9-11f0-4084-b21f-ad83a8e6dcdc}` |

These GUIDs correspond to printer-related device classes, ensuring only approved printer drivers can be installed.

---

## 📅 How to Use

1. In the [Intune Admin Center](https://intune.microsoft.com), go to:
   `Devices` → `Configuration profiles` → `Import profile`
2. Upload the provided `.json` file.
3. Replace the FQDN `printserver.local` with your own print server.
4. Assign the profile to your target device group(s).

---
