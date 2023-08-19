Hi there!

Usually when we're working with data in React Native we work with arrays, that are easier to use in flatlists. Modifying any data in an array is a computational complex operation, especially as the dataset grows, for instance, if we have an array of strings and we want to find one string that match, we would have to loop thought the array to find and remove it, so the larger the array, larger the time spent in this operation.

To fix the issue above, it's possible to use objects with unique identifiers, that would be easier and faster to manipulate the dataset.

So, who we can do it?

First of all, let's take a look at the following example:

```javascript
const App = () => {
  const [data] = useState([
    {
      name: "Joao",
      job: "Developer",
    },
    {
      name: "Maria",
      job: "CEO",
    },
  ])

  const _renderItem = ({ item }) => {
    return (
      <View style={styles.view}>
        <Text style={[styles.text, styles.titleText]}>{item?.name}</Text>
        <Text style={styles.text}>{item?.job}</Text>
      </View>
    )
  }

  const _keyExtractor = (item) => {
    return item.name
  }

  return (
    <SafeAreaView>
      <FlatList
        renderItem={_renderItem}
        data={data}
        keyExtractor={_keyExtractor}
      />
    </SafeAreaView>
  )
}
```

It will render the following screen:

![Screenshot of an android emulator, showing two blue cards, the first one has the text Joao Developer and the second One Maria CEO](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/iobw3nmgn56swlbjz6xq.png)

To convert it to use an object, we would have to change the data initialization and how the flatlist would use this data.

Starting with the initialization, we could use an unique identifier, in this case we will use the pattern user-x, where x is an integer, resulting in this new format:

```javascript
{
    'user-1': {
      name: 'Joao',
      job: 'Developer',
    },
    'user-2': {
      name: 'Maria',
      job: 'CEO',
    },
  }
```

Then, we should change the props for the flatlist, since we have an object and the data props expects an array we could use the Object.entries to have an array, for example if we had an object like this:

```javascript
const data = { "user-1": { name: "Maria" } }
```

Object.entries would return to us:

```javascript
;[["user-1", { name: "Maria" }]]
```

That result shows that we will also have to change the render item function, since the item received from the flatlist is now an array:

```js
const _renderItem = ({ item }) => {
  const [_, itemData] = item

  return (
    <View style={styles.view}>
      <Text style={[styles.text, styles.titleText]}>{itemData?.name}</Text>
      <Text style={styles.text}>{itemData?.job}</Text>
    </View>
  )
}
```

The complete code:

```javascript
const App = () => {
  const [data] = useState({
    "user-1": {
      name: "Joao",
      job: "Developer",
    },
    "user-2": {
      name: "Maria",
      job: "CEO",
    },
  })

  const _renderItem = ({ item }) => {
    const [_, itemData] = item

    return (
      <View style={styles.view}>
        <Text style={[styles.text, styles.titleText]}>{itemData?.name}</Text>
        <Text style={styles.text}>{itemData?.job}</Text>
      </View>
    )
  }

  const _keyExtractor = (item) => {
    const [key] = item

    return key
  }

  return (
    <SafeAreaView>
      <FlatList
        renderItem={_renderItem}
        data={Object.entries(data)}
        keyExtractor={_keyExtractor}
      />
    </SafeAreaView>
  )
}
```

## Benefits of using the object

As mentioned above, using an object would be better for performance, especially when modifying the data. For example, if this list had options to remove an item or add a new one, it would be faster to remove the data from the object considering that we already have identified it.
