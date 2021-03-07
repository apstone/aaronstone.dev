---
title: Showing intent in modern UIs
date: '2021-03-06T01:13:43.812Z'
---
![Showing Intent](./showing-intent.jpg)

As developers, it is easy to assume that your users will intuitively understand your application. When looking at something we built, it's obvious how it should behave because we created it. An "Add To Cart" button? Of course, it fires off a request to the /cart API to add an item. It also does a ton of business logic behind the scenes that can be slow on a slower network speed, resulting in the user sitting there wondering if the application is even working.
 
The application feels clunky, and users are now left guessing at what's going on. The experience sucks. As developers, we have the power to provide insight into our apps visually. We can expose intent throughout the UI by presenting meaningful feedback to the user. Exposing intent can be as simple as a progress spinner on a button, a loading bar, or even showing skeleton screens/content placeholders until sufficient data is available to render the screen.

Feedback feels good. This information helps the user determine if something has gone wrong, but it also just feels right. Your app appears more responsive when it can return instant feedback from a user's actions.

# Implementing this in React Native

React makes this easy. We can use state variables to track our current application state and use that to help inform the user of what is going on. Take the example button component below - the component takes a `loading` prop that can be used to toggling the buttons text to instead show a progress indicatior. This helps us show the user that their action was successful and that something is happening behind the scenes.

```ts
export const Button = ({text, action, loading = false}: ButtonProps) => (
  <TouchableOpacity onPress={action} style={styles.button} disabled={loading}>
    {loading ? (
      <ActivityIndicator color="#FFF" />
    ) : (
      <Text style={styles.text}>{text}</Text>
    )}
  </TouchableOpacity>
);

export default Button;
```
