# BetterPrefs

BetterPrefs is a replacement for Unity's PlayerPrefs that aims to add features that PlayerPrefs is lacking, such as support for multiple saves, save import/export and even more data types, such as booleans, Vector2s and Vector3s.

License: [MIT](https://opensource.org/licenses/MIT)

## Features

- **Multiple saves**: Save data can be saved to multiple files, and the user can switch between them.
- **Save import/export**: Save data can be imported and exported, which is very useful for sharing save data between different devices.
- **Cross-platform**: Save data can be saved to a file on the desktop, and loaded from a file on Android, etc. All platforms Unity supports can read the files in the same way.
- **Data types**: BetterPrefs supports more data types than Unity's PlayerPrefs, such as booleans, Vector2s and Vector3s.
- **Open source**: The source code is public, unlike Unity's PlayerPrefs.
- **More to come**: More features are coming soon, such as support for custom data types, custom serialization, and more.

## Getting Started

To start using BetterPrefs, you need to add the [BetterPrefs.cs](https://github.com/Carroted/BetterPrefs/blob/master/BetterPrefs.cs) script to your Unity project.

Once you'v added the script, you can use the BetterPrefs class to access your save data.

```csharp
BetterPrefs.Load(); // Loads the save data from the default save file, stored in Application.persistentDataPath + "/saves/game.sav" (can be changed in the script)

BetterPrefs.SetBool("MyBool", true);
BetterPrefs.SetInt("MyInt", 5);
BetterPrefs.SetFloat("MyFloat", 5.5f);
BetterPrefs.SetString("MyString", "Hello World!\nNewline supported!");
BetterPrefs.SetVector2("MyVector2", new Vector2(1.25f, 5.7f));
BetterPrefs.SetVector3("MyVector3", new Vector3(1.25f, 5.7f, 3.5f));

BetterPrefs.Save(); // Saves the data to the default save file, stored in Application.persistentDataPath + "/saves/game.sav" (can be changed in the script)
BetterPrefs.Save("/Backups/game.sav"); // Saves a backup of the data to the file "/Backups/game.sav"
```

Unlike PlayerPrefs, BetterPrefs lets you easily choose which save file to load and save to.

In the above example, we even create a backup of the data, so that if something goes wrong, we can still load the data we saved before.

BetterPrefs doesn't automatically save the data on quit due to Unity limitations (scripts that don't derive from MonoBehaviour can't access Unity's [OnApplicationQuit](https://docs.unity3d.com/ScriptReference/MonoBehaviour.OnApplicationQuit.html) event).

## Methods

- **BetterPrefs.Load()**: Loads the save data from the default save file.
- **BetterPrefs.Load(string path)**: Loads the save data from the specified file.
- **BetterPrefs.Save()**: Saves the data to the default save file.
- **BetterPrefs.Save(string path)**: Saves the data to the specified file.
- **BetterPrefs.SetBool(string key, bool value)**: Sets the value of the specified key to the specified boolean value.
- **BetterPrefs.SetInt(string key, int value)**: Sets the value of the specified key to the specified integer value.
- **BetterPrefs.SetFloat(string key, float value)**: Sets the value of the specified key to the specified float value.
- **BetterPrefs.SetString(string key, string value)**: Sets the value of the specified key to the specified string value.
- **BetterPrefs.SetVector2(string key, Vector2 value)**: Sets the value of the specified key to the specified Vector2 value.
- **BetterPrefs.SetVector3(string key, Vector3 value)**: Sets the value of the specified key to the specified Vector3 value.
- **BetterPrefs.GetBool(string key)**: Gets the value of the specified key as a boolean.
- **BetterPrefs.GetInt(string key)**: Gets the value of the specified key as an integer.
- **BetterPrefs.GetFloat(string key)**: Gets the value of the specified key as a float.
- **BetterPrefs.GetString(string key)**: Gets the value of the specified key as a string.
- **BetterPrefs.GetVector2(string key)**: Gets the value of the specified key as a Vector2.
- **BetterPrefs.GetVector3(string key)**: Gets the value of the specified key as a Vector3.
- **BetterPrefs.DeleteKey(string key)**: Deletes the specified key.
- **BetterPrefs.DeleteAll()**: Deletes all keys.
- **BetterPrefs.GetDate()**: Gets the `DateTime` of the currently loaded save file.
- **BetterPrefs.GetDate(string path)**: Gets the `DateTime` of the specified save file.
- **BetterPrefs.HasKey(string key)**: Checks if the specified key exists.

## Known Limitations

- Can't save on quit (can be done by a MonoBehaviour script, which should be better anyway, since it gives you more control over which save file to save and when)
- Escaped newlines (`\\n`) are turned into actual newlines (`\n`) when loading and saving, which can cause issues if you're trying to store \n and not an actual newline character.
- Needs a "split char" between type, key and value in the saves, which is automatically changed to a space when you try to use it in a string (`BetterPrefs.SetString`)

## About

BetterPrefs was released on May 21, 2022 by [Alex_Sour](https://github.com/Alex-Sour) under the [MIT license](https://opensource.org/licenses/MIT).