```
import 'package:flutter/material.dart';
import 'package:flutter_cached_pdfview/flutter_cached_pdfview.dart';
import 'package:go_router/go_router.dart';
import 'package:polystox_app_v2/widgets/polystox_colors.dart';

class ViewPdfFromUrlScreen extends StatelessWidget {
  static const String route = "ViewPdfFromUrlScreen";
  final String url;
  String? appBarTitle;
  ViewPdfFromUrlScreen({super.key, required this.url, this.appBarTitle});

  @override

  Widget build(BuildContext context) {
    double screenWidth = MediaQuery.of(context).size.width;
    double screenHeight = MediaQuery.of(context).size.height;
    return Scaffold(
      appBar: AppBar(
        backgroundColor: PolystoxColors.white,
        flexibleSpace: Container(
          decoration: BoxDecoration(
            color: PolystoxColors.white,
            boxShadow: [
              BoxShadow(
                offset: const Offset(4, 6),
                blurRadius: 20,
                color: PolystoxColors.primaryBlack.withOpacity(0.1),
              ),
            ],
          ),
        ),
        elevation: 0,
        scrolledUnderElevation: 0,
        automaticallyImplyLeading: false,
        leading: IconButton(
          icon: Icon(Icons.arrow_back_ios_new_rounded,
              color: PolystoxColors.deepNavy, size: 18),
          onPressed: () {
            GoRouter.of(context).pop(true);
          },
        ),
        titleSpacing: -8,
        title: Text(
          appBarTitle ?? "PDF Preview",
          style: TextStyle(
            color: PolystoxColors.deepNavy,
            fontSize: 18,
            fontWeight: FontWeight.w400,
          ),
        ),
      ),
      body: SizedBox(
        height: screenHeight,
        width: screenWidth,
        child: PDF().cachedFromUrl(
          url,
          key: UniqueKey(),
          placeholder: (progress) => Center(child: Text('$progress %')),
          errorWidget: (error) => Center(child: Text(error.toString())),
        ),
      ),
    );
  }
}
```