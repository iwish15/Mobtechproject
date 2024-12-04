import React, { useState } from 'react';
import { View, Text, TextInput, Button, StyleSheet, TouchableOpacity, Image, ScrollView, FlatList } from 'react-native';
import { NavigationContainer } from '@react-navigation/native';
import { createStackNavigator } from '@react-navigation/stack';
import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';
import Ionicons from 'react-native-vector-icons/Ionicons';

const LoginScreen = ({ navigation }) => (
  <View style={styles.container}>
    <View style={styles.logoContainer}>
      <Image
        source={{ uri: 'https://cdn.iconscout.com/icon/premium/png-256-thumb/local-art-6781933-5558722.png' }}
        style={styles.logo}
      />
    </View>
    <Text style={styles.header}>Welcome to Local Art Finder</Text>
    <TextInput style={styles.input} placeholder="Enter your email" />
    <TextInput style={styles.input} placeholder="Enter your password" secureTextEntry />
    <TouchableOpacity style={styles.button} onPress={() => navigation.navigate('Home')}>
      <Text style={styles.buttonText}>Login</Text>
    </TouchableOpacity>
    <TouchableOpacity onPress={() => navigation.navigate('SignUp')}>
      <Text style={styles.link}>Create an Account</Text>
    </TouchableOpacity>
    <TouchableOpacity onPress={() => alert('Password recovery')}>
      <Text style={styles.link}>Forgot Password?</Text>
    </TouchableOpacity>
  </View>
);
const SignUpScreen = ({ navigation }) => (
  <View style={styles.container}>
    <Text style={styles.header}>Create an Account</Text>
    <TextInput style={styles.input} placeholder="Full Name" />
    <TextInput style={styles.input} placeholder="Enter your email" />
    <TextInput style={styles.input} placeholder="Create a password" secureTextEntry />
    <TextInput style={styles.input} placeholder="Confirm password" secureTextEntry />
    <TouchableOpacity
      style={styles.button}
      onPress={() => navigation.navigate('Home')}
    >
      <Text style={styles.buttonText}>Sign Up</Text>
    </TouchableOpacity>
    <TouchableOpacity onPress={() => navigation.navigate('Login')}>
      <Text style={styles.already}>Already have an account? Login</Text>
    </TouchableOpacity>
  </View>
);
const HomeScreen = ({ navigation }) => (
  <View style={styles.container}>
    <Text style={styles.header}>Discover Local Art</Text>
    <TextInput style={styles.searchbar} placeholder="Search for street art, galleries, or studios" />
    <TouchableOpacity style={styles.touchableButton} onPress={() => navigation.navigate('Map')}>
      <Text style={styles.buttonText}>Find Nearby Art</Text>
    </TouchableOpacity>
    <TouchableOpacity style={styles.touchableButton} onPress={() => alert('Top Art Picks')}>
      <Text style={styles.buttonText}>Top Art Picks in Your Area</Text>
    </TouchableOpacity>

    <FlatList
      horizontal
      data={[
        { title: 'Street Art', image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRn79BD8L2vTvAFU6QHqUAHWHcbr-U1zmkEKA&s' },
        { title: 'Galleries', image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQBveYyD_BZwjnKqU2eYdSkFkbfEIqToFRHJA&s' },
        { title: 'Studios', image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQR1kyUSYW15G33tt25YO5lthO0g8iSqgmAwg&s' },
      ]}
      renderItem={({ item }) => (
        <TouchableOpacity style={styles.categoryButton} onPress={() => alert(`You selected ${item.title}`)}>
          <Image source={{ uri: item.image }} style={styles.categoryImage} />
          <Text style={styles.categoryText}>{item.title}</Text>
        </TouchableOpacity>
      )}
      keyExtractor={(item) => item.title}
    />
  </View>
);
const MapScreen = ({ navigation }) => (
  <View style={styles.container}>
    <Image source={{ uri: 'https://user-images.githubusercontent.com/636156/46814671-db8e4280-cd3e-11e8-9af8-cf59e7698e7e.png' }} style={styles.mapImage} />
    <TouchableOpacity style={styles.button} onPress={() => navigation.navigate('ArtSpotDetails')}>
      <Text style={styles.buttonText}>View Art Spot Details</Text>
    </TouchableOpacity>
  </View>
);
const ArtSpotDetailsScreen = () => (
  <ScrollView style={styles.container}>
    <Text style={styles.header}>Art Spot Details</Text>
    <Image style={styles.imageCarousel} source={{ uri: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRD0TsQi7WG1TVFPAHbaDPXVjUyBe3ETf1VnQ&s' }} />
    <Text style={styles.myText}>"Wall of Dreams"</Text>
    <Text>Category: Street Art</Text>
    <Text>Artist: Ma. Clara</Text>
    <Text>Rating: ⭐⭐⭐⭐</Text>
    <Text>Description: Lorem ipsum dolor sit amet...</Text>
    <TouchableOpacity
          style={[styles.myButton, styles.rateButton]}
          onPress={() => Alert.alert('Rate this spot')}>
          <Text style={styles.buttonText}>Rate</Text>
        </TouchableOpacity>

        <TouchableOpacity
          style={[styles.myButton, styles.saveButton]}
          onPress={() => Alert.alert('Saved!')}>
          <Text style={styles.buttonText}>Save</Text>
        </TouchableOpacity>

        <TouchableOpacity
          style={[styles.myButton, styles.shareButton]}
          onPress={() => Alert.alert('Shared!')}>
          <Text style={styles.buttonText}>Share</Text>
        </TouchableOpacity>
  </ScrollView>
);
const ArtSpotComponent = () => {
  const [artSpots, setArtSpots] = useState([
    {
      name: 'Art Spot 1',
      category: 'Painting',
      artist: 'Ma. Clara',
      rating: 4.5,
      description: 'A beautiful painting',
      location: 'Cebu',
      image: { uri: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTwCi2Mu36uMI6q9Ca8ubqt7ACFFm3ia8bODA&s' },
    },
  ]);

  <TouchableOpacity onPress={() => handleDelete(index)} style={styles.deleteButton}>
  {/* You can use Ionicons or another suitable icon here */}
  <Ionicons name="trash-outline" size={20} color="red" style={styles.deleteIcon} />
</TouchableOpacity>


  return (
    <View style={styles.container}>
      <Text style={styles.header}>Saved Art Spots</Text>

      {artSpots.map((artSpot, index) => (
        <View key={index} style={styles.artSpot}>
          <TouchableOpacity onPress={() => handleDelete(index)} style={styles.deleteButton}>
            <Image source={{ uri: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ3ahgOYgQMph5ZLjxgYNQ4_iwSIjIceNkl8g&s'}} style={styles.deleteIcon} />
          </TouchableOpacity>

          <View style={styles.artSpotImage}>
            <Image source={artSpot.image} style={styles.image} />
          </View>

          <View style={styles.artSpotDetails}>
            <Text style={styles.artSpotName}>{artSpot.name}</Text>
            <Text style={styles.artSpotInfo}>Category: {artSpot.category}</Text>
            <Text style={styles.artSpotInfo}>Artist: {artSpot.artist}</Text>
            <Text style={styles.artSpotInfo}>Rating: {artSpot.rating}</Text>
            <Text style={styles.artSpotInfo}>Description: {artSpot.description}</Text>
            <Text style={styles.artSpotInfo}>Location: {artSpot.location}</Text>
          </View>
        </View>
      ))}
      </View>
  );
};
const ProfileScreen = ({ navigation }) => {
  const [name, setName] = useState('Deeana Ivory');
  const [email, setEmail] = useState('deeana.ivory@example.com');
  const [preferredArtTypes, setPreferredArtTypes] = useState(['Street Art', 'Galleries']);
  
  const savedArtSpots = [
    { id: '1', name: 'Spot 1', image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRn79BD8L2vTvAFU6QHqUAHWHcbr-U1zmkEKA&s', rating: 4 },
    { id: '2', name: 'Spot 2', image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQBveYyD_BZwjnKqU2eYdSkFkbfEIqToFRHJA&s', rating: 5 },
  ];

  const visitedArtSpots = [
    { id: '1', name: 'Spot A', image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQR1kyUSYW15G33tt25YO5lthO0g8iSqgmAwg&s', rating: 3 },
    { id: '2', name: 'Spot B', image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQR1kyUSYW15G33tt25YO5lthO0g8iSqgmAwg&s', rating: 4 },
  ];

  return (
    <ScrollView style={styles.container}>
      <Text style={styles.header}>Your Profile</Text>

      <View style={styles.profilePictureContainer}>
        <Image
          source={{ uri: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSysgd45_u1Nz4nEoAsF2nfUlR3qEyP-22vjaAqo0ZaBbKKBJziC439VEQfuIH4EJsVHfI&usqp=CAU' }} 
          style={styles.profileImage}
        />
      </View>
      <View style={styles.infoContainer}>
        <Text style={styles.infoHeader}>User Information</Text>

        <TextInput 
          style={styles.input} 
          placeholder="Full Name"
          value={name}
          onChangeText={(text) => setName(text)}
        />

        <TextInput 
          style={styles.input} 
          placeholder="Email"
          value={email}
          onChangeText={(text) => setEmail(text)}
        />

        <Text style={styles.infoText}>Preferred Art Types:</Text>
        <View style={styles.artTypesContainer}>
          {preferredArtTypes.map((artType, index) => (
            <Text key={index} style={styles.artTypeText}>{artType}</Text>
          ))}
        </View>
      </View>

      <View style={styles.activitySummaryContainer}>
        <Text style={styles.infoHeader}>Activity Summary</Text>

        <Text style={styles.infoText}>Saved Art Spots:</Text>
        <FlatList
          horizontal
          data={savedArtSpots}
          keyExtractor={(item) => item.id}
          renderItem={({ item }) => (
            <View style={styles.savedArtSpot}>
              <Image source={{ uri: item.image }} style={styles.savedArtImage} />
              <Text>{item.name}</Text>
              <Text>Rating: {item.rating} ⭐</Text>
            </View>
          )}
        />

        <Text style={styles.infoText}>Visited Art Spots:</Text>
        <FlatList
          horizontal
          data={visitedArtSpots}
          keyExtractor={(item) => item.id}
          renderItem={({ item }) => (
            <View style={styles.savedArtSpot}>
              <Image source={{ uri: item.image }} style={styles.savedArtImage} />
              <Text>{item.name}</Text>
              <Text>Rating: {item.rating} ⭐</Text>
            </View>
          )}
        />
      </View>

      <TouchableOpacity 
        style={styles.button}
        onPress={() => navigation.navigate('EditProfile')}
      >
        <Text style={styles.buttonText}>Edit Profile</Text>
      </TouchableOpacity>

      <TouchableOpacity 
        style={styles.button}
        onPress={() => alert('Logging out...')}
      >
        <Text style={styles.buttonText}>Log Out</Text>
      </TouchableOpacity>
    </ScrollView>
  );
};
const Tab = createBottomTabNavigator();
const TabNavigator = () => (
  <Tab.Navigator
    initialRouteName="Home"
    screenOptions={({ route }) => ({
      tabBarIcon: ({ focused, color, size }) => {
        let iconName;
        if (route.name === 'Home') {
          iconName = focused ? 'home' : 'home-outline';
        } else if (route.name === 'Nearby') {
          iconName = focused ? 'location' : 'location-outline';
        } else if (route.name === 'Saved') {
          iconName = focused ? 'star' : 'star-outline';
        } else if (route.name === 'Profile') {
          iconName = focused ? 'person' : 'person-outline';
        }

        return <Ionicons name={iconName} size={size} color={color} />;
      },
      tabBarActiveTintColor: 'black',
      tabBarInactiveTintColor: 'gray',
      tabBarStyle: {
        backgroundColor: 'lightblue',
        borderTopWidth: 0.5,
        elevation: 5,
        height: 60,
      },
      tabBarLabelStyle: {
        fontSize: 12,
        padding: 5,
      },
    })}
  >
    <Tab.Screen name="Home" component={HomeScreen}
    options={{
      headerStyle: {
        backgroundColor: 'lightblue'
      },
    }} />
    <Tab.Screen name="Nearby" component={MapScreen}
    options={{
      headerStyle: {
        backgroundColor: 'lightblue'
      },
    }} />
    <Tab.Screen name="Saved" component={ArtSpotComponent}
    options={{
      headerStyle: {
        backgroundColor: 'lightblue'
      },
    }} />
    <Tab.Screen name="Profile" component={ProfileScreen} 
    options={{
      headerStyle: {
        backgroundColor: 'lightblue'
      },
    }}/>

  </Tab.Navigator>
);

const Stack = createStackNavigator();
const App = () => (
  <NavigationContainer>
    <Stack.Navigator initialRouteName="Login">
      <Stack.Screen name=" " component={LoginScreen} />
      <Stack.Screen name="SignUp" component={SignUpScreen} />
      <Stack.Screen name="Home" component={TabNavigator} />
      <Stack.Screen name="Map" component={MapScreen} />
      <Stack.Screen name="ArtSpotDetails" component={ArtSpotDetailsScreen} />
    </Stack.Navigator>
  </NavigationContainer>
);

const styles = StyleSheet.create({
  container: {
    flex: 1,
    padding: 20,
    backgroundColor: '#fff',
  },
  header: {
    fontSize: 29,
    fontWeight: 'bold',
    justifyContent: 'center',
    alignContent: 'center',
    paddingBottom: 40,
  },
  input: {
    height: 40,
    borderColor: 'lightblue',
    borderWidth: 2,
    marginBottom: 10,
    paddingHorizontal: 15,
    marginVertical: 15,
    marginTop: 10,
  },
  searchbar: {
    borderColor: 'lightblue',
    borderWidth: 2,
    marginVertical: 10,
  },
  already: {
    paddingLeft: 80,
    marginVertical: 20,
  },
  touchableButton: {
    backgroundColor: 'pink',
    paddingVertical: 12,
    borderRadius: 5,
    marginBottom: 20,
    elevation: 5,
    shadowColor: '#000',
    shadowOffset: { width: 0, height: 4 },
    shadowOpacity: 0.8,
  },
  buttonText: {
    color: 'black',
    fontSize: 16,
    textAlign: 'center',
  },
  myText: {
    fontSize: 20,
    fontWeight: 'bold',
  },
  button: {
    padding: 10,
    backgroundColor: 'pink',
    borderRadius: 5,
    marginVertical: 5,
  },
  rateButton: {
    
  },
   myButton: {
    padding: 10,
    backgroundColor: 'pink',
    borderRadius: 5,
    marginVertical: 5,
    marginBottom: 30,
    
  },
  link: {
    color: 'black',
    marginVertical: 10,
    alignItems: 'center',
    paddingLeft: 115,
  },
  logoContainer: {
    alignItems: 'center',
    marginBottom: 20,
    marginTop: 60,
  },
  logo: {
    width: 100,
    height: 100,
    resizeMode: 'contain',
  },
  deleteButton: {

  },
  categoryButton: {
    padding: 10,
    backgroundColor: '#ddd',
    borderRadius: 5,
    marginRight: 10,
    alignItems: 'center',
  },
  categoryText: {
    fontSize: 16,
    marginTop: 5,
  },
  image: {
    width: 250,
    height: 200,
    borderRadius: 5,
    marginBottom: 10,

  },
  categoryImage: {
    width: 200,
    height: 200,
    resizeMode: 'contain',
  },
  mapImage: {
    flex: 1,
    width: '100%',
    height: 300,
  },
  imageCarousel: {
    height: 200,
    backgroundColor: '#eee',
    marginVertical: 10,
    borderRadius: 3,
  },
  profileImage: {
    width: 50,
    height: 50,
    borderRadius: 50,
    borderWidth: 2,
    borderColor: '#ccc',
  },
  infoContainer: {
    marginBottom: 20,
  },
  infoHeader: {
    fontSize: 18,
    fontWeight: 'bold',
    marginBottom: 10,
  },
  infoText: {
    fontSize: 16,
    marginVertical: 5,
  },
  deleteIcon: {
    width: 20,
    height: 20,
    alignItems: 'center',
    justifyContent: 'center',
    marginLeft: 300,
  },
  artTypesContainer: {
    flexDirection: 'row',
    flexWrap: 'wrap',
  },
  artTypeText: {
    backgroundColor: '#e0e0e0',
    borderRadius: 10,
    padding: 5,
    margin: 5,
  },
  activitySummaryContainer: {
    marginVertical: 20,
  },
  savedArtSpot: {
    alignItems: 'center',
    marginRight: 10,
  },
  savedArtImage: {
    width: 250,
    height: 250,
    borderRadius: 5,
    marginBottom: 5,
  },
  artSpotDetails: {

  },
  artSpotInfo: {
    fontSize: 16,
    marginVertical: 3,
    marginBottom: 5,
    marginTop: 10,

  },
});

export default App;
