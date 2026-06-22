### React Native

---

# 1. Foundations

---

---

## 1. What is React Native?

=> React Native allows you to build Android and iOS mobile apps using JavaScript and React.

## 2. Using React Native:

```
    <View>
      <Text>Hello</Text>
      <Button title="Click" />
    </View>
```

## 3. | React Web | React Native |

```
| React Web | React Native      |
| --------- | ----------------- |
| div       | View              |
| p, h1     | Text              |
| button    | Button            |
| CSS       | StyleSheet        |
| Browser   | Mobile App        |
| ReactDOM  | Native Components |
```

## 4. What is Expo?

=> Expo is a framework that makes React Native development easier.

## 5. Installation

```
npx create-expo-app@latest
npm run start
npm run reset-project
```

---

---

# 2. React Native Core Components

---

---

## 1. First React Native Component - app/index.js

```
    import { View, Text } from "react-native";

    export default function Home() {
      return (
        <View>
          <Text>Hello React Native!</Text>
        </View>
      );
    }
```

## 2. Text

```
    <Text>Hello World</Text>
```

## 3. View

```
    <View>
      <Text>Inside View</Text>
    </View>
```

## 4. Image

```
    import { Image } from "react-native";
```

```
    <Image
      source={{
        uri: "https://picsum.photos/200"
      }}
      style={{ width: 200, height: 200 }}
    />
```

## 5. Button

```
    <Button
      title="Click Me"
      onPress={() => alert("Clicked")}
    />
```

## 6. TextInput

```
    <TextInput
      placeholder="Enter name"
    />
```

## 7. ScrollView

```
    import { ScrollView } from "react-native";
```

```
    <ScrollView>
      <Text>Item 1</Text>
      <Text>Item 2</Text>
    </ScrollView>
```

## 8. Link

```
    import { Link } from "expo-router";
```

```
    <Link href={"/about"}>About Screen</Link>
```

---

---

# 3. Styling

---

---

## 1. No CSS files - Use StyleSheet.

```
    import { StyleSheet } from "react-native";

    const styles = StyleSheet.create({
      container: {
        flex: 1,
        backgroundColor: "#fff",
        justifyContent: "center",
        alignItems: "center"
      }
    });
```

```
    <View style={styles.container}>...</View>
    <View
      style={{
        flex: 1,
        flexDirection: "row"
      }}
    >
    ...
    </View>
```

---

---

# 4. Navigation

---

---

## 1. \_layout.tsx

```
    import { Stack } from "expo-router";

    export default function RootLayout() {
      return (
        <Stack>
          <Stack.Screen
            name="index"
            options={{ headerShown: true, title: "Home" }}
          />
          <Stack.Screen
            name="about"
            options={{ headerShown: true, title: "About" }}
          />
        </Stack>
      );
    }
```

```
    <Stack screenOptions={{ headerShown: false }}>...</Stack>
```

## 2. index.tsx

```
    import { Text, View, StyleSheet } from "react-native";
    import { Link } from "expo-router";

    export default function Index() {
      return (
        <View style={styles.container}>
          <Text>Edit app/index.tsx to edit this screen.</Text>
          <Link href="/about">Visit About Screen</Link>
        </View>
      );
    }

    const styles = StyleSheet.create({
      container: {
        flex: 1,
        backgroundColor: "#fff",
        justifyContent: "center",
        alignItems: "center",
      },
    });

```

## 3. about.tsx

```
    import { View, Text } from "react-native";
    import React from "react";

    const About = () => {
      return (
        <View>
          <Text>About Screen</Text>
        </View>
      );
    };

    export default About;
```

---

---

# 5. Tab Navigator

---

---

## 1. Folder Structure

```
app/
│
├── _layout.tsx
│
├── (tabs)/
│   ├── _layout.tsx
│   ├── index.tsx
│   ├── profile.tsx
│   └── settings.tsx
```

## 2. Root Layout - app/\_layout.tsx

```
    import { Stack } from "expo-router";

    export default function RootLayout() {
      return (
        <Stack>
          <Stack.Screen
            name="(tabs)"
            options={{ headerShown: false }}
          />
        </Stack>
      );
    }
```

## 3. Tab Layout - app/(tabs)/\_layout.tsx

```
    import { Tabs } from "expo-router";
    import { Ionicons } from "@expo/vector-icons";

    export default function TabsLayout() {
      return (
        <Tabs
          screenOptions={{
            headerShown: true,

            tabBarActiveTintColor: "tomato",
            tabBarInactiveTintColor: "gray",

            tabBarStyle: {
              position: "absolute",
              left: 15,
              right: 15,
              bottom: 0,

              backgroundColor: "#fff",
              borderTopWidth: 0,
              height: 75,

              shadowColor: "#000",
              shadowOffset: {
                width: 0,
                height: -3,
              },
              shadowOpacity: 0.1,
              shadowRadius: 3,
              elevation: 5,
            },
            tabBarLabelStyle: {
              fontSize: 12,
              fontWeight: "600",
            },
          }}
        >
          <Tabs.Screen
            name="index"
            options={{
              title: "Home",

              tabBarIcon: ({ focused, color, size }) => (
                <Ionicons
                  name={focused ? "home" : "home-outline"}
                  size={size}
                  color={color}
                />
              ),
            }}
          />

          <Tabs.Screen
            name="profile"
            options={{
              title: "Profile",

              tabBarIcon: ({ focused, color, size }) => (
                <Ionicons
                  name={focused ? "person" : "person-outline"}
                  size={size}
                  color={color}
                />
              ),
            }}
          />

          <Tabs.Screen
            name="settings"
            options={{
              title: "Settings",

              tabBarIcon: ({ focused, color, size }) => (
                <Ionicons
                  name={focused ? "settings" : "settings-outline"}
                  size={size}
                  color={color}
                />
              ),
            }}
          />
        </Tabs>
      );
    }
```

## 4. Home Screen - app/(tabs)/index.tsx

```
    import { View, Text, StyleSheet } from "react-native";

    export default function HomeScreen() {
      return (
        <View style={styles.container}>
          <Text style={styles.text}>Home Screen</Text>
        </View>
      );
    }

    const styles = StyleSheet.create({
      container: {
        flex: 1,
        justifyContent: "center",
        alignItems: "center",
      },
      text: {
        fontSize: 24,
        fontWeight: "bold",
      },
    });
```
