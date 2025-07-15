# ⚛️ React Counter Component
Hi! 👋
This is a simple React class component that displays a counter with increment and delete actions.
It demonstrates key React lifecycle methods (componentDidUpdate, componentWillUnmount), props handling, and dynamic rendering.

# 📂 File
src/components/Counter.jsx (your code):

```
import React, { Component } from "react";

class Counter extends Component {
  componentDidUpdate(prevProps) {
    if (prevProps.counter.value !== this.props.counter.value) {
      // Example: Ajax calls when value changes
      console.log("Counter - Updated");
    }
  }

  componentWillUnmount() {
    console.log("Counter - Unmounted");
  }

  render() {
    console.log("Counter - Rendered");

    return (
      <div>
        <span className={this.getBadgeClasses()}>{this.formatCount()}</span>
        <button
          onClick={() => this.props.onIncrement(this.props.counter)}
          className="btn btn-secondary btn-sm"
        >
          Increment
        </button>
        <button
          onClick={() => this.props.onDelete(this.props.counter.id)}
          className="btn btn-danger btn-sm m-2"
        >
          Delete
        </button>
      </div>
    );
  }

  getBadgeClasses() {
    let classes = "badge m-2 badge-";
    classes += this.props.counter.value === 0 ? "warning" : "primary";
    return classes;
  }

  formatCount() {
    const { value: count } = this.props.counter;
    return count === 0 ? "Zero" : count;
  }
}
```

# export default Counter;
✨ Features

✅ Dynamic badge style — changes color when count is zero
✅ Increment button — calls onIncrement handler from parent
✅ Delete button — calls onDelete handler from parent
✅ Lifecycle methods:
    - componentDidUpdate – detects prop changes (e.g., value updates)
    - componentWillUnmount – cleanup logic when removed

# 🚀 Usage
This component expects the following props from a parent component:
    - counter: an object like { id: 1, value: 0 }
    - onIncrement: function to call when increment button is clicked
    - onDelete: function to call when delete button is clicked

Example parent:

```
<Counter
  key={counter.id}
  counter={counter}
  onIncrement={handleIncrement}
  onDelete={handleDelete}
/>
```

# 📌 Notes
    - State is not managed inside Counter—it relies on props.
    - Styling uses Bootstrap classes (btn, badge, etc.).
    - You can easily extend this component to add more buttons or styles.

# ✍️ Personal note
I built this Counter component to practice props, lifecycle methods, and event handling in React.
It’s reusable and can be plugged into any list of counters or similar UI. ✨