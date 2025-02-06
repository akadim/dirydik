# Email Audit

Email Audit is a system used to audit all emails sent from within an organization. In the event of security incidents (such as leakage of sensitive information via emails), this system will be used by the organization's auditing department to retrieve and verify the emails of the concerning parties through its admin console.

# Instructions:

Development of an `Email Audit` system is currently in progress. Assume that this project is a real project and is being used in a production environment on a trial basis, since the features are not yet complete.

As the first assignment, two UI elements need to be implemented:

- The first one is called `RecipientsDisplay`, it is a table cell that is used to intelligently show email recipients inside the `AuditTable` component. This cell will trim recipients that are too long to display in the table.
- The second element is called `RecipientTooltip`, a tooltip-like component that will be used to display all of the email recipients, even ones that are trimmed in the table cell.

The task is to implement these UI elements in the `RecipientsDisplay` file within any of the included frameworks. Modifying or adding new props, re-ordering the recipients, and adding new or extra functionalities and features are not allowed in this assignment. Additionally, the component needs to be written in **Typescript**.

## `RecipientsDisplay`

Assume that an employee can send an email to many recipients. Due to the limited amount of space, the information has to be displayed well. The design team has come up with the following design specifications:

- If all the email addresses in the recipients list fit in the available space, display them as they are, delimited by a comma and space (e.g. `John.Smith@gmail.com, Jane.Smith@outlook.com`).
- If there is not enough space to display the entire recipients list, it must be trimmed. To prevent showing clipped email addresses that are hard to read, show only the portion of the recipients list that does fit. In other words, if the entirety of an email address does not fit, it must not be shown.
- If the recipients list has been trimmed (i.e. at least one email address is not shown), add `, ...` after the last email address shown. Furthermore, the rightmost end of the column must indicate the number of trimmed recipients with the provided `RecipientsBadge` component.
- A special case is given to the first recipient. If there is not enough space to fit even the first recipient's email address, the email address is allowed to be clipped with an ellipsis. If there is only one recipient, a badge must not be shown. If there is more than one recipient, the first recipient must be excluded from the number of trimmed recipients in the badge.
- This functionality should work on any screen size and when the screen is resized. For simplicity, this will only be tested in a recent version of a `Chromium` browser.
- For the element that holds the list of recipients, the `display` must be set to `flex` and the `align-items` property must be set to `center` to ensure alignment correctness.
- Do not modify or add new props to the `RecipientsBadge` component.
- Do not re-order the recipients.
- Do not add new/extra functionalities and features.

### `RecipientsDisplay` Examples

**Trim recipients that do not fit in the column. Show `, ...` after the last fitting recipient and a badge with `+N` at the end of the column.**

![Email trim example 1](Email%20trim%20example%201.svg)

**If there is not enough space to show the ellipsis and the extra space, trim that recipient as well.**

Incorrect:

![Email trim example 2A](Email%20trim%20example%202A.svg)

Correct:

![Email trim example 2B](Email%20trim%20example%202B.svg)

**If there is not enough space to show the first recipient, the badge should show the number of trimmed recipients excluding the first recipient, and the recipient should be truncated with an ellipsis only. If there is only one recipient, there should be no badge.**

Two recipients:

![Email trim example 3A](Email%20trim%20example%203A.svg)

One recipient:

![Email trim example 3B](Email%20trim%20example%203B.svg)

## `RecipientsTooltip`

Assume a use-case exists where the entirety of a recipient list must be made visible. The solution provided by the design team is to show the full list of the recipients at the **top right** corner of the viewport.

- The recipients list must be shown in a tooltip at the **top right** corner of the viewport.
- The tooltip must only be shown when the user hovers over a `RecipientsBadge` component.
- The tooltip must not be shown if the user is not hovering over a badge.
- The tooltip must display **`all of the email addresses in the recipients list, delimited by a comma and space`** (e.g. `John.Smith@gmail.com, Jane.Smith@outlook.com`).
- Assume that the viewport is wide enough to show the tooltip without any truncation.
- Do not create a new file, the tooltip must be located inside the `RecipientsDisplay` file.
- Do not re-order the recipients, display them as they are.
- Do not add new/extra functionalities and features.
- The tooltip should have the following styles:
  - Margin from the top right corner of the viewport is `8px`.
  - Padding top and bottom are `8px`.
  - Padding left and right are `16px`.
  - Background color is `#666`.
  - Text color is `#f0f0f0`.
  - Border radius is `24px`.
  - The `display` property must be set to `flex` and the `align-items` property must be set to `center` to ensure alignment correctness.

### `RecipientsTooltip` Examples

**An example format of showing the recipients list in the tooltip.**

```bash
a@test.example.com, b@test.example.com, c@test.example.com
```

**The example of margins for the recipients list.**

![Tooltip example 1](Tooltip%20example%201.png)

**The style example for recipients list in the tooltip.**

![Tooltip example 2](Tooltip%20example%202.png)

## Evaluation

We encourage you to closely follow the specified design and functionality requirements, as UI components will undergo screenshot comparison tests. Margins, padding, font sizes, and colors should match the provided specifications as closely as possible.

To help you match your submission with the expected results, we provide `Evaluation example [WxH].png` reference files. Note that the screenshots were created on Mac OS, so there may be slight differences on other operating systems.

In addition to automated screenshot comparisons, your code will be reviewed by human engineers. This review will focus on code quality, adherence to the project's coding standards, and the implementation's efficiency and maintainability. Writing clean, well-documented, and optimized code will be beneficial. By aiming to meet both the visual and code quality standards, you will increase the likelihood of your submission passing the evaluation process..

## Development

Install dependencies and then start in the development mode.

```bash
npm install
npm run dev
```

Navigate to the port that was displayed on the terminal. The app should be running after the development build is finished.

## Build

To generate production version:

```bash
npm run build
```

You can run the newly built app locally with `npm run preview`.

## Features

This project is in an early phase, so the features are not yet complete. At the moment, it will display mocked email data from `fake-data.ts` to simulate an API response. It also doesn't have any kind of pagination at the moment, but we plan to support it in the future, as well as allowing the user to set how many items to show per page.

Since checking date and time is crucial in an auditing process, table rows have alternating background colors between dates to make it easier to distinguish emails sent on different dates.

Our users are diverse and have many different device configurations, so we need to make sure the UI doesn't break when viewed at any screen size. However, since we haven't implemented a mobile version of the design yet, we understand that the information cannot be consumed well on very small screen sizes.
