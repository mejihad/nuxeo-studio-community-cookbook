# Social Security Number Display

![SSN](ssn.png)

## Description

Elements that show/hide the value of a field holding a social security number.

## Usage

Elements that show/hide the value of a field holding a social security number:

* In a _read_ layout, use `nuxeo-se-ssn-read`:
  * The value is obfuscated (********* instead of the clear value)
  * A button allows for toggling the display (display the value or the "*")
    * Once displayed, it automatically hides the value after 8 seconds
  * `administrators` and users members of `allowedGroups` can see the widget. Others see nothing (not even ******)

* In an _edit_ layout, use `nuxeo-se-ssn-edit`:
  * The inoput type is `password` by default
  * A button allows for toggling the type to `text`

## Installation

### Studio Designer

* Install the content in the `ui` folder as Resources in Designer
* Import it in the custom bundle generated by Designer (`nuxeo-{YOUR_PROJECT_ID}-custom-bundle.html`). For example, if you dropped the `ssn` folder in `ui`, add the following line to the bundle:

```
<link rel="import" href="ssn/nuxeo-se-ssn-read.html">
<link rel="import" href="ssn/nuxeo-se-ssn-edit">
```

## Configuration

Just use the element and its required attributes: `document` and `ssnField`. To allow non admin users to see the value, also use `allowedGroups`. The later must be passed as JSON, which means double quotes inside, single quote outside:

```
. . . other elements and widgets . . .

<nuxeo-se-ssn-read document="[[document]]"
                   ssn-field="person:ssn"
                   allowed-groups='["grp1","grp2","grp3"]'></nuxeo-se-ssn-read>

. . . other elements and widgets . . .
```
For nuxeo-se-ssn-read, an optional `hide-after` property can be set: The number of seconds to wait before hidding the value once it is showed (default value is 8 seconds)

:warning: **WARNING** When using the `edit` element, the caller must use the double binding notation to the document, `{{document}}`, to allow the `document` object to be modified in the parent element:

```
. . . other elements and widgets . . .

<nuxeo-se-ssn-edit document="{{document}}"
                   ssn-field="person:ssn"
                   allowed-groups='["grp1","grp2","grp3"]'></nuxeo-se-ssn-edit>

. . .
```

## Documentation Links

- [HOWTO: Create and Reuse a Custom Element](https://doc.nuxeo.com/nxdoc/how-to-create-and-reuse-custom-element/)
- [HOWTO: Customize Document Layouts](https://doc.nuxeo.com/nxdoc/web-ui-document-layouts/)
- [Web UI Layout Elements](https://doc.nuxeo.com/nxdoc/web-ui-layouts/)
