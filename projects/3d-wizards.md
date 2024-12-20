---
layout: project
type: project
image: img/3d-wizards/home.png
title: "3d-Wizards"
date: 2024
published: true
labels:
  - Javascript
  - Postgres
  - Html/CSS
  - GitHub
summary: "A store for 3d-Wizards company that my team developed in ICS 314."
---

3D-Wizards was my first experience working on a group coding project. The implementation involved taking an order from the store or a custom request, adding it to the cart, and then transferring it to a PostgreSQL database upon checkout. This site was deployed on Vercel and is still functional as of 12/19. My contribution to the project included designing and developing the custom order page and its associated features.

<img class="img-fluid" src="../img/3d-wizards/store.png">

The store features a functional search bar, and each item's blue link redirects to a separate page created by another team member.

Search for Product

```cpp

<h5 className="mt-4">Search</h5>
<form
  onSubmit={(e) => {
    e.preventDefault(); // Prevent page reload on Enter
  }}
>
  <div className="input-group">
    <input
      type="text"
      className="form-control"
      placeholder="Enter Product Name"
      value={searchTerm}
      aria-label="Search"
      onChange={(e) => setSearchTerm(e.target.value)} // Update search term
    />
    <button className="btn btn-dark" type="submit">
      Search
    </button>
  </div>
</form>

```

<img class="img-fluid" src="../img/3d-wizards/custom.png">

The custom order feature includes three parameters: request type, description, and material. A request type, description, and at least one material must be selected to add an entry to the database.

The request type and description were implemented by another team member, while I contributed by adding the material functionality and updating the submit button.

```cpp
{/* Material Buttons with Color Selectors */}
<div style={styles.materialButtons}>
  {materialKeys.map((material) => (
    <div key={material}>
      <button
        type="button"
        style={{
          ...styles.materialButton,
          backgroundColor: materialColors[material] || '#f5f5f5',
          color: materialColors[material] === 'black' ? 'white' : 'black',
        }}
        onClick={() => setSelectedMaterial(material)}
      >
        {material}
      </button>
      <select
        style={styles.dropdown}
        value={materialColors[material]}
        onChange={(e) => handleColorChange(material, e.target.value)}
      >
        <option value="">Select Color</option>
        {colors.map((color) => (
          <option key={color} value={color}>
            {color.charAt(0).toUpperCase() + color.slice(1)}
          </option>
        ))}
      </select>
    </div>
  ))}
</div>

```

The submit button dynamically changes color based on its state, implemented using CSS for styling and conditional logic to ensure proper functionality.

{% raw %}
```cpp
{/* CSS */}

submitButton: {
    width: '100%',
    padding: '12px',
    fontSize: '18px',
    borderRadius: '6px',
    border: '1px solid #ccc',
    backgroundColor: '#4CAF50',
    color: 'white',
    cursor: 'pointer',
},
disabledButton: {
    backgroundColor: '#ccc',
    cursor: 'not-allowed',
},


{/* Submit Button */}
<button
  type="submit"
  style={{
    ...styles.submitButton,
    ...(isFormValid ? {} : styles.disabledButton),
  }}
  disabled={!isFormValid}
>
  Submit
</button>

```
{% endraw %}
website link
https://3-d-wizards-inc-two.vercel.app/

Source: <a href="https://github.com/theVacay/vacay">theVacay/vacay</a>