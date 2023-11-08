### React: Text Append

Create a Text Append module as shown below:

There is a reusable component in the module named TextField:

- It renders a `<label>` and an `<input>` elements.
- It receives 2 props:
  - labelText - The text to be rendered in `<label>` element.
  - onChange - The event handler onChange function to be called on `<input>` element change.

The module must have the following functionalities:

- It renders 2 TextField components. The first is used for the first text, and the second is for the second text.
- As values are entered in the text fields, concatenate the texts, separated by a space, and render the result inside `<label data-testid="final-text">`.
  The following data-testid attributes are required in the component for the tests to pass:
- The final appended text label: 'final-text'
- The div containing first TextField component: 'first-text'
- The div containing second TextField component: 'second-text'
- Inside the TextField component:
  - label element: 'label'
  - input element: 'input'
    Please note that the component has these data- testid attributes for test cases, certain classes and ids for rendering purposes. They should not be changed.

### Solution

Lol, my solution doesn't match this problem because the codebase shown is different from this one. So I just went with the general logic for the issue shown. I guess hackerrank's testing system was glitching at that time, but I've faced this issue a lot.

#### Dropdown/index.jsx

```jsx
/* ... */
<select data-testid="dropdown" defaultValue={labelText} onChange={onChange}>
  {/* Do not remove this default option as this is needed in testing */}
  <option value={labelText} key={labelText} disabled>
    {labelText}
  </option>
  {options.map((option, index) => (
    <option key={index} value={option}>
      {option}
    </option>
  ))}
</select>
/* ... */
```

#### App.jsx

```jsx
/* ... */
<div data-testid="country-options">
  <Dropdown
    options={countryOptions}
    labelText={"Select Country"}
    onChange={(e) => setCountry(e.target.value)}
  />
</div>
<div data-testid="language-options">
  <Dropdown
    options={languageOptions}
    labelText={"Select Language"}
    onChange={(e) => setLanguage(e.target.value)}
  />
</div>
/* ... */
```
