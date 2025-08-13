import React, { useState, useRef, useEffect } from 'react';
import { View, Text, Button, StyleSheet, Animated } from 'react-native';

export default function App() {
  const [water, setWater] = useState(0);
  const [sun, setSun] = useState(0);

  // Animated value for plant size
  const plantSize = useRef(new Animated.Value(20)).current;

  // Animate plant size when water changes
  useEffect(() => {
    Animated.timing(plantSize, {
      toValue: 20 + water, // Plant grows as water increases
      duration: 500,
      useNativeDriver: false, // Can't use fontSize with native driver
    }).start();
  }, [water]);

  // Function to determine plant stage
  const getPlantStage = () => {
    const avg = (water + sun) / 2;
    if (avg < 20) return '🌱'; // seed
    if (avg < 50) return '🌿'; // sprout
    if (avg < 80) return '🪴'; // small plant
    return '🌳'; // tree
  };

  const resetPlant = () =>{
    setWater(0);
    setSun(0)
    plantSize.setValue(0);
  }

  return (
    <View style={styles.container}>
      <Text style={styles.header}>Welcome to Your Garden 🌸</Text>

      {/* Animated Plant Emoji */}
      <Animated.Text style={{ fontSize: plantSize }}>{getPlantStage()}</Animated.Text>

      <Text style={styles.levelText}>Water Level: {water}</Text>
      <Text style={styles.levelText}>Sunlight Level: {sun}</Text>

      <View style={styles.buttonContainer}>
        <Button
          title="Water me 💧"
          onPress={() => setWater(Math.min(water + 5, 100))}
        />
        <Button
          title="Give sunlight ☀️"
          onPress={() => setSun(Math.min(sun + 10, 100))}

        />
        <Button
title = "Reset 🌱"
color ="red"
onPress={resetPlant}

/>
      </View>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#f0f8ff',
    padding: 20,
  },
  header: {
    fontSize: 22,
    marginBottom: 20,
    fontWeight: 'bold',
  },
  levelText: {
    fontSize: 18,
    marginVertical: 5,
  },
  buttonContainer: {
    marginTop: 20,
    width: '60%',
    justifyContent: 'space-between',
    height: 100,
  },
});
