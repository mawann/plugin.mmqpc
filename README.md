# Mawan Moodle Quiz Password Changer

This plugin automatically updates all Quiz Passwords at set intervals, such as every 10 minutes, specifically for quizzes with a 6-digit numerical password. Exam supervisors can download the MMQPC app from Google Play to view the latest passwords.

Do you need an alternative plugin that is compatible with Google Authenticator and doesn't require an internet connection? [Click here](2fa/) to get it.

---

### How MMQPC Works

1. The admin installs the MMQPC Plugin.
2. The admin configures the settings in the following menu:
   * **Site Administration**
   * **Plugins**
   * **Local Plugins → Mawan Moodle Quiz Password Changer**
   
   Set the **Salt** and **Duration** values, then save the settings.
3. The quizzes are assigned a 6-digit numerical password, such as 111111 or 123456.
4. Exam supervisors install the **Moodle Quiz Password Changer** app, available on [Google Play](https://play.google.com/store/apps/details?id=appinventor.ai_mawan911.MMQPC).
5. When a quiz is active, the plugin automatically generates a new random 6-digit password at intervals set by the **Duration** parameter (e.g., every 10 minutes).
6. The exam supervisor checks the Moodle Quiz Password Changer app on their Android device. The screen will display the latest password. **No internet connection is required!** The token (password) is reliably displayed, even in closed rooms with poor internet signal.
7. The exam supervisor announces the password (token) displayed on their device, and students enter it on their devices.
8. Students begin the quiz.
9. If a student exits or is forced out of Moodle after the 11th minute, they cannot use the same password to re-enter because the plugin has already changed it. This mechanism is similar to the token system used in UNBK (Ujian Nasional Berbasis Komputer, which means Computer-Based National Examination in Indonesian).

> **Note:**  
> The Moodle admin must either:
> 1. Configure Moodle's `cron.php` to run every minute, or
> 2. Run it manually through the menu: Site administration → Server → Tasks → Scheduled Tasks → Send data to mawan.net server → Run now

### Standard Version Limitations

The standard version is free to use indefinitely but has the following limitations:

* You cannot change the **Salt**.
* You cannot adjust the token/password interval (**Duration**).

### What Are "Salt" and "Duration"?

**Salt:** A string that "seasons" the token (password) generated by the plugin. Just like different salts can alter the taste of food, different Salt values will generate different tokens. The Salt entered by the Moodle admin must match the Salt configured on the exam supervisor's phone. If the Salt values differ, the generated tokens will not match.

**Duration:** The interval, in minutes, at which the password changes. It is recommended to use a value that is a factor of 60, such as 1, 2, 3, 4, 5, 6, 10, 12, 15, 20, 30, or 60. For example, a Duration of 10 means the password changes every 10 minutes, specifically at 0, 10, 20, 30, 40, and 50 minutes past the hour.
