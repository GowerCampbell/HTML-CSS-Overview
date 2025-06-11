
# Building Forms Guide for Web Design

HTML forms collect user input, from simple search queries to complex applications, styled with CSS and processed with server-side languages like PHP.

## Initializing a Form
The `<form>` element wraps all form controls, using `action` (URL for data submission) and `method` (HTTP method, typically `get` or `post`).
```html
<form action="/login" method="post">
  ...
</form>
```

## Text Fields & Textareas
### Text Fields
The `<input>` element with a `type` attribute collects text-based data. The `name` attribute is submitted with the input data.
```html
<input type="text" name="username">
```
HTML5 input types include:
- `color`, `date`, `datetime`, `email`, `month`, `number`, `range`, `search`, `tel`, `time`, `url`, `week`.
```html
<input type="date" name="birthday">
<input type="time" name="game-time">
<input type="email" name="email-address">
<input type="url" name="website">
<input type="number" name="cost">
<input type="tel" name="phone-number">
```

### Textarea
The `<textarea>` element captures multi-line text, with `cols` (width in characters) and `rows` (height in lines) for sizing.
```html
<textarea name="comment" cols="30" rows="4">Add your comment here</textarea>
```

## Multiple Choice Inputs & Menus
### Radio Buttons
Allow single selection from a group, using `<input type="radio">` with the same `name` attribute.
```html
<input type="radio" name="day" value="Friday" checked> Friday
<input type="radio" name="day" value="Saturday"> Saturday
<input type="radio" name="day" value="Sunday"> Sunday
```

### Checkboxes
Allow multiple selections, using `<input type="checkbox">`.
```html
<input type="checkbox" name="day" value="Friday" checked> Friday
<input type="checkbox" name="day" value="Saturday"> Saturday
<input type="checkbox" name="day" value="Sunday"> Sunday
```

### Drop-Down Lists
Use `<select>` and `<option>` elements for a compact list of options.
```html
<select name="day">
  <option value="Friday" selected>Friday</option>
  <option value="Saturday">Saturday</option>
  <option value="Sunday">Sunday</option>
</select>
```
- `multiple` attribute allows multiple selections.
```html
<select name="day" multiple>
  <option value="Friday" selected>Friday</option>
  <option value="Saturday">Saturday</option>
  <option value="Sunday">Sunday</option>
</select>
```

## Form Buttons
Submit form data with `<input type="submit">` or `<button>`.
```html
<input type="submit" name="submit" value="Send">
<button name="submit"><strong>Send Us</strong> a Message</button>
```

## Other Inputs
### Hidden Input
Stores data not visible to users but included in form submission.
```html
<input type="hidden" name="tracking-code" value="abc-123">
```

### File Input
Allows file uploads.
```html
<input type="file" name="file">
```
- Custom styling requires JavaScript.

## Organizing Form Elements
### Label
The `<label>` element provides accessible captions, linked via the `for` attribute to an input’s `id`.
```html
<label for="username">Username</label>
<input type="text" name="username" id="username">
```
Alternatively, wrap controls directly.
```html
<label>
  <input type="radio" name="day" value="Friday" checked> Friday
</label>
```

### Fieldset
Groups related controls and labels, styled with CSS (e.g., borders).
```html
<fieldset>
  <label>
    Username
    <input type="text" name="username">
  </label>
  <label>
    Password
    <input type="password" name="password">
  </label>
</fieldset>
```

### Legend
Provides a caption for a `<fieldset>`.
```html
<fieldset>
  <legend>Login</legend>
  <label>
    Username
    <input type="text" name="username">
  </label>
  <label>
    Password
    <input type="password" name="password">
  </label>
</fieldset>
```

## Form & Input Attributes
### Disabled
Disables interaction with a control or `<fieldset>`.
```html
<label>
  Username
  <input type="text" name="username" disabled>
</label>
```

### Placeholder
Displays a hint that disappears on focus.
```html
<label>
  Email Address
  <input type="email" name="email-address" placeholder="name@domain.com">
</label>
```

### Required
Ensures a control has a value before submission, with browser validation for specific types (e.g., `email`).
```html
<label>
  Email Address
  <input type="email" name="email-address" required>
</label>
```
- Style with `:optional` and `:required` pseudo-classes.

### Additional Attributes
- `accept`, `autocomplete`, `autofocus`, `formaction`, `formenctype`, `formmethod`, `formnovalidate`, `formtarget`, `max`, `maxlength`, `min`, `pattern`, `readonly`, `selectionDirection`, `step`.

## Login Form Example
```html
<form>
  <fieldset class="account-info">
    <label>
      Username
      <input type="text" name="username">
    </label>
    <label>
      Password
      <input type="password" name="password">
    </label>
  </fieldset>
  <fieldset class="account-action">
    <input class="btn" type="submit" name="submit" value="Login">
    <label>
      <input type="checkbox" name="remember"> Stay signed in
    </label>
  </fieldset>
</form>
```
```css
*,
*:before,
*:after {
  box-sizing: border-box;
}
form {
  border: 1px solid #c6c7cc;
  border-radius: 5px;
  font: 14px/1.4 "Helvetica Neue", Helvetica, Arial, sans-serif;
  overflow: hidden;
  width: 240px;
}
fieldset {
  border: 0;
  margin: 0;
  padding: 0;
}
input {
  border-radius: 5px;
  font: 14px/1.4 "Helvetica Neue", Helvetica, Arial, sans-serif;
  margin: 0;
}
.account-info {
  padding: 20px 20px 0 20px;
}
.account-info label {
  color: #395870;
  display: block;
  font-weight: bold;
  margin-bottom: 20px;
}
.account-info input {
  background: #fff;
  border: 1px solid #c6c7cc;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.1);
  color: #636466;
  padding: 6px;
  margin-top: 6px;
  width: 100%;
}
.account-action {
  background: #f0f0f2;
  border-top: 1px solid #c6c7cc;
  padding: 20px;
}
.account-action .btn {
  background: linear-gradient(#49708f, #293f50);
  border: 0;
  color: #fff;
  cursor: pointer;
  font-weight: bold;
  float: left;
  padding: 8px 16px;
}
.account-action label {
  color: #7c7c80;
  font-size: 12px;
  float: left;
  margin: 10px 0 0 20px;
}
```

## Summary
- **Form Structure**: Use `<form>` with `action` and `method` to collect user input.
- **Inputs**: `<input>` for text, radio, checkboxes, file, and hidden data; `<textarea>` for multi-line text; `<select>` for drop-downs.
- **Buttons**: `<input type="submit">` or `<button>` to submit data.
- **Organization**: Use `<label>`, `<fieldset>`, and `<legend>` for accessibility and structure.
- **Attributes**: `disabled`, `placeholder`, `required`, and more enhance functionality and validation.
