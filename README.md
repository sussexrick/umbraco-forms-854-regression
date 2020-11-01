# Umbraco Forms 8.5.4 regression

When used with TinyMCE, Umbraco Forms 8.5.4 appears to save the result of a failed server-side validation so that the error cannot be corrected. This is logged as [Issue #441 ](https://github.com/umbraco/Umbraco.Forms.Issues/issues/441).

This solution includes the same Umbraco code and config with Umbraco Forms 8.5.3 and Umbraco Forms 8.5.4. In both cases the admin user is `test@test.com` and the password is `testtesttest`.

## Steps to reproduce

1. In Visual Studio 2019 run up both applications and visit the home page, which contains an Umbraco Form with a short answer and a long answer field. Both are mandatory. The long answer has TinyMCE enabled.
2. Fill in the form and submit. It works.
3. Revisit the form. Fill in only the first field, the short answer, and submit. You will be told be server-side validation that the long answer field is required.
4. Fill in the long answer and submit. On Umbraco Forms 8.5.3 this works, but on 8.5.4 it doesn't. Even if you start the form again, this field seems to remain invalid until the end of your session.
