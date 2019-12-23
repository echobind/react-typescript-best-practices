# React-TypeScript Best Practices

Our suggested best practices when using React with TypeScript.

---

**Table of Contents**
* [Components](#components)
* [Props](#props)
* [Hooks](#hooks)
* [FAQ](#faq)
  * [Contributing](#contributing)
  * [License](#license)
  * [Contact](#contact)
* [License](#license)

---

### Components

We prefer to use **function expressions** beceause the syntax you use with them makes it easier to read compared to function declarations. 

```typescript
// ✅ written as a function expression
const ComponentExample: React.FC = () => <h1>My Website Heading</h1>
```

✅ Keep your types/interfaces collocated with your components, unless you need to break them out.

### Props

Opt for `types` over `interfaces` when declaring your component props ([unless you're authoring a library](https://github.com/typescript-cheatsheets/react-typescript-cheatsheet#types-or-interfaces))

```typescript
type Props = {
 /** The background color */
 color?: string;
 /** The text to show inside */
 text: string;
}

const Button: React.FC<Props> = ({ color = 'blue', text }) => (
 <button style={{ backgroundColor: color }}>{text}</button>
)
```

✅ Prefer destructuring props in function parameter

✅ Use ES6 default values

✅ Document your props 


### Hooks

Use a generic when you need to initialize a hook with a `null`-ish value. 

```typescript
type User = {
  /** The user's email address */
  email: string;
  /** The user's ID */
  id: string;
}
const [user, setUser] = useState<User | null>(null);
```

## FAQ

Some questions you might have around using React with TypeScript. 

### How do I type a `ChangeEvent`?

If you're working with a form, you'll want to use `React.ChangeEvent`. Here's an example:
```typescript
function onChange(e: React.ChangeEvent<HTMLInputElement>) {
  //... setValue(e.target.value)
}
```

### What does "X" mean in the `tsconfig.json`?

The `tsconfig.json` has many options, all of which you can learn about here in the [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/compiler-options.html).

### Where should I look if I want to dive deeper?

One of the best places to dive deeper into this subject is the community guide [`react-typescript-cheatsheet`](https://github.com/typescript-cheatsheets/react-typescript-cheatsheet).


## License

MIT
