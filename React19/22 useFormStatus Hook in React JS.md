
## Main Topics

- What is useFormStatus
    
- Example useFormStatus
    
- Make form handleSubmit form
```jsx
import { useFormStatus } from "react-dom";

// 1. The Child Component (Where the hook lives)
function SubmitButton() {
  const { pending } = useFormStatus();

  return (
    <button type="submit" disabled={pending}>
      {pending ? "Submitting..." : "Submit"}
    </button>
  );
}

// 2. The Parent Component (The Form)
export const FormStatusHook = () => {
  
  // This function represents your server action or async logic
  async function formAction(formData) {
    // Simulate a 2-second delay
    await new Promise((res) => setTimeout(res, 2000));
    
    const name = formData.get("username");
    console.log("Form submitted for:", name);
  }

  return (
    <div>
      {/* Use 'action' instead of 'onSubmit' for useFormStatus to work */}
      <form action={formAction}>
        <input type="text" name="username" placeholder="Enter Name" />
        <br />
        <br />
        <input type="password" name="password" placeholder="Enter Password" />
        <br />
        <br />
        
        {/* The hook MUST be inside a component nested in the form */}
        <SubmitButton />
      </form>
    </div>
  );
};
```