# baitapthuchanh2
import 'package:flutter/material.dart';

void main() {
  runApp(MaterialApp(home: EmailCheckApp()));
}

class EmailCheckApp extends StatefulWidget {
  @override
  _EmailCheckAppState createState() => _EmailCheckAppState();
}

class _EmailCheckAppState extends State<EmailCheckApp> {
  
  final emailController = TextEditingController();

  String message = '';

  void checkEmail() {
    String email = emailController.text.trim();

    if (email.isEmpty) {
      setState(() {
        message = 'Email không hợp lệ';
      });
    } else if (!email.contains('@')) {
      setState(() {
        message = 'Email không đúng định dạng';
      });
    } else {
      setState(() {
        message = 'Bạn đã nhập email hợp lệ';
      });
    }
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Thực hành 02')),
      body: Padding(
        padding: EdgeInsets.all(20),
        child: Column(
          children: [
           
            TextField(
              controller: emailController,
              decoration: InputDecoration(labelText: 'Email'),
            ),
            SizedBox(height: 20),
            ElevatedButton(
              onPressed: checkEmail,
              child: Text('Kiểm tra'),
            ),
            SizedBox(height: 20),
            Text(
              message,
              style: TextStyle(
                  color: Colors.red, fontWeight: FontWeight.bold, fontSize: 16),
            )
          ],
        ),
      ),
    );
  }
}
