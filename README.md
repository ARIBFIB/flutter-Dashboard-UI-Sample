Here's the polished version with the logo size optimized for better readability and presentation:  

---

# 🌟 Toller Mini: Flutter Dashboard UI Sample  

<img src="https://github.com/user-attachments/assets/2a10ac5b-fe90-4f83-ab1f-e5e59e808584" alt="Toller Mini Logo" width="200" style="display: block; margin: 0 auto;" />  

---

## 🚀 Overview  
**Toller Mini** is a modern and sleek Flutter dashboard template that simplifies mobile application development. Designed for efficiency and aesthetics, this project serves as a perfect starting point for developers who aim to create stunning, user-friendly, and responsive interfaces with minimal effort.  

---

## ScreenShot
<img src="https://github.com/user-attachments/assets/e94c1a9d-6024-41f1-8d7c-a4bf1e650516" alt="Toller Mini Logo" width="300" height="800" style="display: block; margin: 0 auto;" />  



## 🎨 Features  

✨ **Responsive Design**  
Effortlessly adapts to all screen sizes, from mobile phones to tablets.  

🎯 **Customizable Widgets**  
Highly flexible and easy-to-modify components to fit your project requirements.  

🧭 **Intuitive Navigation**  
Simplified and user-friendly navigation ensures an optimal user experience.  

🛠️ **Clean Code Architecture**  
Well-structured and documented codebase that enhances readability and maintainability.  

🌈 **Interactive UI Elements**  
Engaging buttons, menus, and layouts that bring your application to life.  

---

## 📱 User Interface Highlights  

🌟 **Stylish Container Layouts**  
Beautifully crafted layouts that improve usability and visual appeal.  

💡 **Dynamic Interactions**  
Interactive elements to create a smooth and intuitive user experience.  

---

## 🚀 Getting Started  

Follow these simple steps to set up and run the application:  

1. **Clone the Repository**  
   ```bash  
   git clone https://github.com/your-username/toller-mini.git  
   ```  

2. **Navigate to the Project Directory**  
   ```bash  
   cd toller-mini  
   ```  

3. **Install Dependencies**  
   ```bash  
   flutter pub get  
   ```  

4. **Run the Application**  
   ```bash  
   flutter run  
   ```  

---

## 🌟 Contribution  

Contributions are welcome! If you’d like to enhance this project, feel free to open an issue or submit a pull request. Please ensure your contributions adhere to the guidelines in the `CONTRIBUTING.md` file.  

---

## 📜 License  

This project is licensed under the MIT License. See the `LICENSE` file for details.  

---

## 📞 Contact  

For any inquiries, suggestions, or feedback, feel free to reach out:  
📧 Email: [your-email@example.com](mailto:your-email@example.com)  
🌐 Portfolio: [your-portfolio-link.com](https://your-portfolio-link.com)  

---
Code 
```
import 'package:flutter/material.dart';
import 'package:url_launcher/url_launcher.dart';
import 'user_profile_page.dart';
import 'how_to_use_page.dart';
import 'add_device_page.dart';
import 'manual_control_page.dart'; // Ensure this imports the correct ManualControlPage
import 'scheduled_control_page.dart';
import 'login_page.dart';
import 'contact_us_page.dart'; // Import the new Contact Us page
import 'package:shared_preferences/shared_preferences.dart';

class MenuPage extends StatelessWidget {
  final Function toggleTheme;

  const MenuPage({super.key, required this.toggleTheme});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Menu'),
      ),
      body: ListView(
        children: [
          Divider(),
          ListTile(
            title: Text('User Profile'),
            onTap: () {
              Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const UserProfilePage()),
              );
            },
          ),
          Divider(),
          ExpansionTile(
            title: Text('Motor Control'),
            leading: Icon(Icons.control_camera),
            children: [
              ListTile(
                title: Text('Manual Control'),
                onTap: () {
                  Navigator.push(
                    context,
                    MaterialPageRoute(builder: (context) => ManualControlPage()), // No 'const'
                  );
                },
              ),
              ListTile(
                title: Text('Scheduled Control'),
                onTap: () {
                  Navigator.push(
                    context,
                    MaterialPageRoute(builder: (context) => const ScheduledControlPage()),
                  );
                },
              ),
            ],
          ),
          Divider(),
          ListTile(
            title: Text('Add a Device'),
            onTap: () {
              Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => AddDevicePage()),
              );
            },
            trailing: Icon(Icons.arrow_forward_ios),
          ),
          Divider(),
          ListTile(
            title: Text('How to Use/Install'),
            onTap: () {
              Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => HowToUsePage()),
              );
            },
            trailing: Icon(Icons.arrow_forward_ios),
          ),
          Divider(),
          ListTile(
            title: Text('Shop Now'),
            onTap: () => _launchURL('https://shop.demetronics.com/'),
            trailing: Icon(Icons.shop),
          ),
          Divider(),
          ListTile(
            title: Text('Contact Us'),
            onTap: () {
              Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const ContactUsPage()),
              );
            },
          ),
          Divider(),
          ListTile(
            title: Text('Logout'),
            onTap: () => _showLogoutDialog(context),
            trailing: Icon(Icons.exit_to_app),
          ),
        ],
      ),
    );
  }

  void _showLogoutDialog(BuildContext context) {
    showDialog(
      context: context,
      barrierDismissible: false,
      builder: (BuildContext context) {
        return AlertDialog(
          title: Text('Confirm Logout'),
          content: Text('Are you sure you want to logout?'),
          actions: <Widget>[
            TextButton(
              onPressed: () {
                Navigator.of(context).pop();
              },
              child: Text('Cancel'),
            ),
            TextButton(
              onPressed: () async {
                final prefs = await SharedPreferences.getInstance();
                await prefs.setBool('isLoggedIn', false);

                Navigator.of(context).pop();
                Navigator.pushReplacement(
                  context,
                  MaterialPageRoute(builder: (context) => const LoginPage()),
                );
              },
              child: Text('Logout'),
            ),
          ],
        );
      },
    );
  }

  Future<void> _launchURL(String url) async {
    final Uri uri = Uri.parse(url);
    if (await canLaunchUrl(uri)) {
      await launchUrl(uri);
    } else {
      throw 'Could not launch $url';
    }
  }
}

```
