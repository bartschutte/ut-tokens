---
title: Buttons
subtitle: "Buttons are useful to draw attention to a goal or action. Calls to actions within buttons should be explicit."
name: buttons
category: component-buttons
---
{{% banner %}}
For information about how to write button copy, check out the [typography]({{< ref "typography.md" >}}) page.
{{% /banner %}}

{{< example-group >}}
<h3 class="ut-section__headline">
  <a class="ut-section__link ut-table-of-contents__link">Playground 👩🏽‍🔬</a>
  </h3>
<div class="playground l-grid l-xl-col-2 l-h-gap-4x">
  <tk-button
    id="playgroundExample"
    class="l-v-center-child"
    alignment="center"
  >
    Send
  </tk-button>
  <tk-container
    id="buttonDescriptions"
    type="contained"
    size="standard"
    variant="standard"
  >
    <fieldset>
      <legend class="t-heavy">Alignment</legend>
      <tk-single-select-list
        inline
        selected="center"
        size="medium"
      ></tk-single-select-list>
      <hr class="form__rule" />
      <legend class="t-heavy">Size</legend>
      <tk-single-select-list
        inline
        selected="standard"
        size="medium"
      ></tk-single-select-list>
      <p description="compact">Used only when there is a need to conserve space.</p>
      <hr class="form__rule" />
      <legend class="t-heavy">Status</legend>
      <tk-single-select-list
        inline
        selected="ready"
        size="medium"
      ></tk-single-select-list>
      <hr class="form__rule" />
      <legend class="t-heavy">Type</legend>
      <tk-single-select-list
        inline
        selected="contained"
        size="medium"
      ></tk-single-select-list>
      <div class="button-type__description" description="contained">
        <p>Contained buttons have more emphasis, as they use a primary colour fill. A layout and/or container should contain a single prominent button that makes it clear that other buttons have less importance in the hierarchy. This high-emphasis button commands the most attention.</p>
        <p>Use contained buttons for high prioritized interactions as they should guide the user. Use only as stand-alone or in combination with outline or ghost buttons. Use sparingly, as overuse can cause confusion to a user.</p>
      </div>
      <div class="button-type__description" description="outline">
        <p>Outlined buttons are used for more emphasis than text buttons due to the stroke. Outline buttons are intended for general use buttons and actions like triggering popouts, filtering and sharing actions, when a number of buttons have the same priority but none of them are more important than the others.</p>
        <p>This is typically the most appropriate button type because of its neutral visual weight. Also use outline buttons for low prioritized interactions that need to be available for the user (e.g. Back, Cancel). Use only in combination with primary or highlight buttons.</p>
      </div>
      <div class="button-type__description" description="ghost">
        <p>Ghost buttons have the same spacing and alignment rules as other buttons, however they are the most minimal visually. This allows them to be used alongside buttons when a low priority action is required, the element is placed alongside buttons, or when a tap target area should be considered.</p>
        <p>Ghost buttons are typically used for less important actions. Use ghost buttons for very low prioritized interactions as they draw little attention from the user. Use only in combination with other ghost buttons or primary buttons. Note: Ghost buttons are meant to be used for interactions, they are not links.</p>
      </div>
      <hr class="form__rule" />
      <legend class="t-heavy">Variant</legend>
      <tk-single-select-list
        inline
        selected="standard"
        size="medium"
      ></tk-single-select-list>
      <p description="destructive">When a user attempts a potentially destructive action we use red to warn them of the potential risk involved with completing such an action.</p>
    </fieldset>
  </tk-container>
</div>
<script>
  document.addEventListener("DOMContentLoaded", () => setRadioOptions());
  const example = document.getElementById('playgroundExample');
  const buttonDescriptions = document.getElementById('buttonDescriptions');

  const setRadioOptions = () => {
    const radioGroups = document.getElementsByTagName('tk-single-select-list');
    radioGroups[0].options = [
      { "label": "Auto", "value": "auto" },
      { "label": "Center", "value": "center" },
      { "label": "Leading", "value": "leading" },
      { "label": "Trailing", "value": "trailing" },
    ];
    radioGroups[1].options = [
      { "label": "Standard", "value": "standard" },
      { "label": "Compact", "value": "compact" },
    ];
    radioGroups[2].options = [
      { "label": "Ready", "value": "ready" },
      { "label": "Disabled", "value": "disabled" },
      { "label": "Loading", "value": "loading" },
    ];
    radioGroups[3].options = [
      { "label": "Contained", "value": "contained" },
      { "label": "Outline", "value": "outline" },
      { "label": "Ghost", "value": "ghost" },
    ];
    radioGroups[4].options = [
      { "label": "Standard", "value": "standard" },
      { "label": "Destructive", "value": "destructive" },
    ];

    radioGroups[0].addEventListener('checked', (event) => {
      setButtonAttributeAndDescription(event.detail, 'alignment');
    });

    radioGroups[1].addEventListener('checked', (event) => {
      setButtonAttributeAndDescription(event.detail, 'size');
    });

    radioGroups[2].addEventListener('checked', (event) => {
      setButtonAttributeAndDescription(event.detail, 'status');
      setStatusContent(event.detail);
    });

    radioGroups[3].addEventListener('checked', (event) => {
      setButtonAttributeAndDescription(event.detail, 'type');
    });

    radioGroups[4].addEventListener('checked', (event) => {
      setButtonAttributeAndDescription(event.detail, 'variant');
    });
  }

  const setStatusContent = (eventDetail) => {
    switch (eventDetail) {
      case 'loading':
        return example.innerText = 'Sending';
      case 'disabled':
        return example.innerText = 'Sent';
      default:
        return example.innerText = 'Send';
    }
  }

  const setButtonAttributeAndDescription = (eventDetail, source) => {
    buttonDescriptions.setAttribute(source, eventDetail);
    return example.setAttribute(source, eventDetail);
  }
</script>
{{< /example-group >}}

{{< example-group >}}
{{< example-output exampleTitle="Defaults" fullHeight="true" >}}
  <tk-button
    alignment="center"
    size="standard"
    status="ready"
    type="contained"
    variant="standard"
  >
    Example
  </tk-button>
{{< /example-output >}}
{{< /example-group >}}

{{< usage >}}
  {{% usage-positive %}}
  - Limit the number of contained buttons per page
  - Keep content within buttons clear, concise, actionable and no longer than 40 characters
  - Group like-sized buttons
  {{% /usage-positive %}}

  {{% usage-negative %}}
  - Wrap `TkButton` in an `<a>` or `<button>`
  - Use contained and destructive buttons together
  - Write button text that is greater than 40 characters
  - Use other colors for button link
  - Put default buttons next to compact buttons
  {{% /usage-negative %}}
{{< /usage >}}
{{< example-group >}}

{{< example-output exampleTitle="Submit" fullHeight="true" >}}
  <form action="http://www.google.com" id="formId">
    <tk-button
      action-type="submit"
      form="formId">
      Submit
    </tk-button>
  </form>
{{< /example-output >}}
{{< /example-group >}}

{{< example-group >}}
{{< example-output exampleTitle="Text + Icon" >}}
<tk-button type="outline">
  Locked feature
  <tk-icon class="ml-2x" name="lock" size="small"></tk-icon>
</tk-button>
<hr class="horizontal-rule" />
<tk-button
  type="outline"
>
  <tk-icon class="mr-2x" name="play" size="small"></tk-icon>
  10:03
</tk-button>
{{< /example-output >}}

{{% description %}}
Occasionally, an icon helps provide necessary context to an action. For example, we use a lock icon to visibly communicate to a customer that a feature or flow is unavailable.

For video play buttons that utilize preview images, use the `tk-poster-play` component that can be found [here]({{< ref "poster-play.md" >}}).
{{% /description %}}
{{< /example-group >}}

{{< example-group >}}
{{< example-output exampleTitle="Icon only" >}}
<button type="button" class="btn--icon-only">
  <tk-icon name="search" size="medium"></tk-icon>
  <span class="sr-only">Screen Reader text</span>
</button>
<button type="button" class="btn--icon-square">
  <tk-icon name="search" size="medium"></tk-icon>
  <span class="sr-only">Screen Reader text</span>
</button>
{{< /example-output >}}

{{% description %}}
Some buttons use only icons to convey actions. This is used for commonly known actions like search. **Note:** a web component version of this doesn't exist yet…hang tight!
{{% /description %}}
{{< /example-group >}}

{{< usage >}}
  {{% usage-positive %}}
  - Ensure the action of the button matches the icon of the button
  - Ensure buttons with locks are clickable
  - Place locks after a string of text.
  - Set the `status` Prop to `disabled` when applicable.
  - Only show locks when the feature or flow relevant to the user is blocked.
  {{% /usage-positive %}}

  {{% usage-negative %}}
  - Add lock icons without context
  - Add more than one lock to a button
  - Use icons for complex actions
  {{% /usage-negative %}}
{{< /usage >}}

{{< example-group >}}
{{< example-output exampleTitle="Inverse" fullHeight="true">}}
<button class="btn--inverse mb-2x">Button inverse</button>
<button class="btn--inverse active">Button inverse</button>
{{< /example-output >}}

{{% description %}}
This style of button is used as a toggle to select one or more options. Button Inverse should always have a `.input--hidden:checked + .btn--inverse` applied to one of the options. For buttons that require more text, use `.btn--multiline` with this class.
{{% /description %}}
{{< /example-group >}}

{{< example-group >}}
{{< example-output exampleTitle="Stacking utils" fullHeight="true">}}
<div class="l-flex l-flex-wrap">
  <tk-button class="mb-2x btn-md-block mr-lg-1x">Contained</tk-button>
  <tk-button class="mb-2x btn-md-block mr-lg-1x" type="outline">Outline</tk-button>
  <tk-button class="mb-2x btn-md-block" type="ghost">Ghost</tk-button>
</div>
{{< /example-output >}}
{{% description %}}
For times when buttons are next to each other on larger screens, but need to stack at smaller screens, we have classes to stack them. Use `btn-md-block` for screens stacking at medium screensizes and use `btn-sm-block` for stacking at small screensizes.
{{% /description %}}
{{< /example-group >}}

{{< example-group >}}
{{< example-output exampleTitle="Group" fullHeight="true">}}
<div class="btn-group">
  <tk-button class="mr-2x" type="outline">Cancel</tk-button>
  <tk-button>Send</tk-button>
</div>
{{< /example-output >}}

{{% description %}}
When two or more buttons need to be next to each other. Commonly used in [modals]({{< ref "modals" >}}).
{{% /description %}}
{{< /example-group >}}

{{< usage >}}
  {{% usage-positive %}}
  - Have clear actions for grouped buttons
  {{% /usage-positive %}}

  {{% usage-negative %}}
  - Use three or more buttons in a group without a good reason
  {{% /usage-negative %}}
{{< /usage >}}

{{% accessibility %}}
- Receives `:focus`
- Buttons without content or a name should have `aria-label` such as icons.
{{% /accessibility %}}

{{< example-group >}}
{{< example-output exampleTitle="Radio Button Group">}}
<div class="radio-btn-group">
  <label class="radio-btn-group__label">
    <input class="input--hidden" type="radio" name="radio-group-name-here-1" checked="checked">
    <span class="btn--inverse">Draco Malfoy</span>
  </label>
  <label class="radio-btn-group__label">
    <input disabled class="input--hidden" type="radio" name="radio-group-name-here-1">
    <span class="btn--inverse">Vincent Crabbe</span>
  </label>
  <label class="radio-btn-group__label">
    <input class="input--hidden" type="radio" name="radio-group-name-here-1">
    <span class="btn--inverse">Gregory Goyle</span>
  </label>
</div>
{{< /example-output >}}

  {{% description %}}
  This pattern allows customers to toggle between multiple options to make a selection. The default state should always have an item selected. Only one item in the group can be selected at a time. This is used as a secondary option for [single-select-list]({{< ref "single-select-list" >}}).
  {{% /description %}}
{{< /example-group >}}

{{< usage >}}
  {{% usage-positive %}}
  - Ensure one Radio Button Group item is selected
  - Provide clear copy with each radio selection
  {{% /usage-positive %}}

  {{% usage-negative %}}
  - Allow more than one radio button group to be selected at a time
  {{% /usage-negative %}}
{{< /usage >}}

{{% accessibility %}}
- Receives `:focus`
- Groups of `radio` buttons should share the same `:name`
{{% /accessibility %}}
