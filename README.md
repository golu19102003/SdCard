![Screenshot 2025-05-25 123536](https://github.com/user-attachments/assets/fb95dce7-8a1e-490e-b01c-6d83baa80271)
![Screenshot 2025-05-25 123525](https://github.com/user-attachments/assets/2dc5b59c-b2e2-4e9d-8959-068b72ed5f17)
![Screenshot 2025-05-25 123515](https://github.com/user-attachments/assets/e988dc54-e774-4e9f-96af-4ad4a27248f5)

## SD Card Android Studio App Using Java – Detailed README Description
**Overview**
This Android application demonstrates how to read from and write data to the SD card (external storage) using Java in Android Studio. The app provides a simple interface for users to input text, save it to a file on the SD card, retrieve the saved data, and clear the input field. This project is ideal for beginners looking to understand file operations and external storage handling in Android[1][6].

**Features**
- Write user input to a text file on the SD card.
- Read content from the text file and display it in the app.
- Clear the input field.
- Basic error handling with user feedback via Toast messages.

**Project Structure**
- **MainActivity.java**: Contains all logic for UI interaction and file operations.
- **activity_main.xml**: Layout file with EditText and three Buttons (Write, Read, Clear).

**How It Works**
- The app uses Android’s `File` and `FileOutputStream` classes to write data, and `FileInputStream` and `BufferedReader` to read data from the SD card.
- The file is typically stored at `/sdcard/myfile.txt`. The app checks for file existence and handles exceptions to notify the user if any error occurs.
- Permissions for reading and writing to external storage must be declared in the AndroidManifest.xml file.

**Permissions**
To access the SD card, add the following permissions to your `AndroidManifest.xml`:
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE"/>
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>

*Note: For Android 10 (API level 29) and above, you may need to handle scoped storage or request legacy storage access.*

**Basic Usage**
1. Launch the app.
2. Enter text in the input field.
3. Tap **Write** to save the text to the SD card.
4. Tap **Read** to load and display the text from the SD card.
5. Tap **Clear** to empty the input field.

**Code Snippet (Core Logic)**

// Writing to SD card
File f = new File("/sdcard/myfile.txt");
f.createNewFile();
FileOutputStream fout = new FileOutputStream(f);
fout.write(message.getBytes());
fout.close();

// Reading from SD card
FileInputStream fin = new FileInputStream(f);
BufferedReader br = new BufferedReader(new InputStreamReader(fin));
String line, buf = "";
while ((line = br.readLine()) != null) {
    buf += line;
}
e1.setText(buf);
br.close();
fin.close();

**Error Handling**
- The app displays Toast messages for successful operations and errors, such as file not found or permission issues.

**Requirements**
- Android Studio installed.
- Android device or emulator with SD card/emulated external storage.
- Minimum SDK version as per your project needs.

**References**
- For more details on external storage and file operations, see the [Android Developer documentation].
