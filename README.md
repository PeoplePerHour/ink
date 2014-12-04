# Ink

Ink is a responsive email framework, used to make HTML emails look great on any client or device.  It includes a 12-column grid, as well as some simple UI elements for rapid prototyping.

Homepage:      http://zurb.com/ink<br />
Documentation: http://zurb.com/ink/docs.php<br />
Download:      http://zurb.com/ink/download.php

Ink is MIT-licensed and absolutely free to use. Ink wouldn't be possible without the support of the entire ZURB team, our friends and colleagues who gave feedback, and some luminaries who did some heavy lifting that we took advantage of (thanks guys).

# Repo Contents

* Base Source for CSS
* Docs
* Responsive Email Templates
* README, CONTRIBUTING and LICENSE

# ZURB

Ink was made by [ZURB](http://www.zurb.com), a product design company in Campbell, CA.

If Ink knocks your socks off the way we hope it does and you want more, why not check out [our jobs](http://www.zurb.com/talent)?

# Ink for PPH

PeoplePerHour has adopted Ink framework in order to get benefited by the responsive features of the framework.

#### Quick glossary

**compiled template:** An ink template compiled via *grunt assemble* and located at **/build/downloads/templates/pph/**

**converted template:** A compiled template that is passed to the inliner so that all styles are added to the html template as a value of a style attribute.

**inliner:** An online tool that parses an html document and copies all styles that correspond to each element in its style attribute. We use the inliner provied by Zurb [here](http://zurb.com/ink/inliner.php)

## PPH templates

All PPH related templates can be found in **/templates/pph** and have been organized in separate folders depending on their role.

### partials

The **partials** folder contain the html template of all re-usable elements across the PPH emails like the header, footer, pph signature, action buttons, header titles, fake post job form, hourlie tile etc. They can be included in any template by invoking:
```
{{> partial_filename }}
```

Below is the template of the pph signature template:
```
<div class="container-padding padding-bottom">
  <table>
      <tr>
          <td align="left">
              [[Top]]<br>
              [[Bottom]]
          </td>
      </tr>
  </table>
</div>
```

The partials are meant to be included in an email template and should never be passed directly to the inliner.

### basic

The **basic** folder contains html templates that:
- contain a full html page with head and body,
- include all required css files,
- include a single partial in their body.

Below is the template of the **sign** element that includes the **_pph_sign** partial (i.e the PPH signature we use in all emails).

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml">
<head>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
  <meta name="viewport" content="width=device-width"/>
  <style>{{>ink}}</style>
  <style>{{>pph-main}}</style>
  <style>{{>buttons}}</style>
</head>
<body>
{{> _pph-sign }}
</body>
</html>
```

After a basic template is compiled via *grunt assemble*, the compiled template found in **/build/downloads/templates/pph/** can by passed to an inliner.

Below you can see the basic template presented above, but compiled:
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
  <meta name="viewport" content="width=device-width"/>
  <style>/**********************************************
* Ink v1.0.5 - Copyright 2013 ZURB Inc        *
**********************************************/
/* ommitted for practical reasons */

/**
 * PPH CSS - omitted for practical reasons
 */
</style>
</head>
<body>
<div class="container-padding padding-bottom">
  <table>
      <tr>
          <td align="left">
              [[Top]]<br>
              [[Bottom]]
          </td>
      </tr>
  </table>
</div>
</body>
</html>
```

Finally, after the compiled template has been converted (i.e all styles have been placed inline in the template html), the contents of the <body> can be used in a PPH html template.

Below you can see the compiled template presented above, but converted:
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<!-- Inliner Build Version 4380b7741bb759d6cb997545f3add21ad48f010b -->
<html xmlns="http://www.w3.org/1999/xhtml" xmlns="http://www.w3.org/1999/xhtml">
<head>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
  <meta name="viewport" content="width=device-width" />
</head>
<body style="width: 100% !important; min-width: 100%; -webkit-text-size-adjust: 100%; -ms-text-size-adjust: 100%; color: #505050; font-family: Helvetica, Arial, sans-serif; font-weight: normal; text-align: left; line-height: 19px; font-size: 13px; background: #ededed; margin: 0; padding: 0;" bgcolor="#ededed">
<!-- HINT: Replace {sometext} with  after the template is passed to the inliner in order to use it a pph template -->
<div class="container-padding padding-bottom" style="padding: 0 15px 15px;">
    <table style="border-spacing: 0; border-collapse: collapse; vertical-align: top; text-align: left; padding: 0;">
      <tr style="vertical-align: top; text-align: left; padding: 0;" align="left">
        <td align="left" style="word-break: break-word; -webkit-hyphens: auto; -moz-hyphens: auto; hyphens: auto; border-collapse: collapse !important; vertical-align: top; text-align: left; color: #505050; font-family: Helvetica, Arial, sans-serif; font-weight: normal; line-height: 19px; font-size: 14px; margin: 0; padding: 0;" valign="top">
          [[Top]]<br />
          [[Bottom]]
        </td>
      </tr>
    </table>
  </div>
</body>
</html>
```

### demos

The **demos** folder contains html templates similar to the basic templates with the difference that they don't include a single partial but they comprise a full PPH email that is based on partials and is used for demonstration purposes.

Below is the template of a complete PPH email that contains an hourlie list:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />

    <style>{{>ink}}</style>
    <style>{{>pph-main}}</style>
    <style>{{>buttons}}</style>
    <style>{{>hourlies}}</style>
    <style>{{>jobs}}</style>
</head>
<body>
<table class="body">
  <tr>
      <td>
          <!-- BEGIN: Header -->
          {{> _header }}
          <!-- END: Header -->
          <!-- BEGIN: Main Content -->
          <table class="container bgWhite main-content">
              <tr>
                  <td>
                      <div class="container-padding padding-top">
                          <p>
                              Hey X,
                          </p>
                          <p>
                              This is some introductory text
                          </p>
                      </div>
                      <!-- BEGIN: Hourlie list -->
                      <table class="block-grid two-up">
                          <tr>
                              <td>
                                  {{> _hourlieTile }}
                              </td><td>
                                  {{> _hourlieTile }}
                              </td>
                          </tr>
                      </table>
                      <!-- END: Hourlie list -->
                      <!-- BEGIN: Browse offers button -->
                      <div class="container-padding buttons-container">
                          <center>
                          <table class="button small-button pph-btn pph-blue-btn pph-inverted-btn radius main-action">
                              <tr>
                                  <td>
                                      <a href="#">Browse Offers</a>
                                  </td>
                              </tr>
                          </table>
                          </center>
                      </div>
                      <!-- END: Browse offers button -->
                      <!-- BEGIN: Signature -->
                      {{> _pph-sign }}
                      <!-- END: Signature -->
                      <!-- BEGIN: Fake post job form -->
                      {{> _post-job-fake }}
                      <!-- END: Fake post job form -->
                  </td>
              </tr>
          </table>
          <!-- END: Main Content -->
          <!-- BEGIN: Footer -->
          {{> _footer }}
          <!-- END: Footer -->
      </td>
  </tr>
</table>
</body>
</html>
```

### mailchap

The **mailchap** folder contains mailchap related html templates.

**NOTICE:** At the moment these templates use the old email design, they need to be updated and use partials as well.
