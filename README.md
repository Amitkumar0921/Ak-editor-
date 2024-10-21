# Ak-editor-
Ak editor 
import React, { useState } from 'react';
import { View, Button, Image, StyleSheet } from 'react-native';
import ImagePicker from 'react-native-image-picker';

export default function App() {
  const [image, setImage] = useState(null);

  const selectImage = () => {
    ImagePicker.showImagePicker({}, (response) => {
      if (response.uri) {
        setImage(response.uri);
      }
    });
  };

  return (
    <View style={styles.container}>
      {image && <Image source={{ uri: image }} style={styles.image} />}
      <Button title="Select Image" onPress={selectImage} />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
  },
  image: {
    width: 300,
    height: 300,
    margin: 20,
  },
});
import React, { useState } from 'react';
import { View, Button, StyleSheet } from 'react-native';
import ImagePicker from 'react-native-image-picker';
import { Grayscale } from 'react-native-image-filter-kit';

export default function App() {
  const [image, setImage] = useState(null);

  const selectImage = () => {
    ImagePicker.showImagePicker({}, (response) => {
      if (response.uri) {
        setImage(response.uri);
      }
    });
  };

  return (
    <View style={styles.container}>
      {image && (
        <Grayscale>
          <Image source={{ uri: image }} style={styles.image} />
        </Grayscale>
      )}
      <Button title="Select Image" onPress={selectImage} />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
  },
  image: {
    width: 300,
    height: 300,
    margin: 20,
  },
});
