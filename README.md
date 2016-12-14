# android7.0-PopupWindow-showAsDropDown
##最近华为已经推出了android7.0正式版,可以直接更新,我的项目出现了一些问题,关于PopupWindow的showAsDropDown(view)
在7.0(24)之前没有问题
在7.0,在popupwindow为全屏时，不能在view的下方显示而是全部遮挡
##解决法官法如下:
```
if (Build.VERSION.SDK_INT < 24) {
            showAsDropDown(v);
        } else {
            // 适配 android 7.0
            int[] location = new int[2];
            v.getLocationOnScreen(location);
            int x = location[0];
            int y = location[1];
            //view的位置+view的高度
            showAtLocation(v, Gravity.NO_GRAVITY, 0, y + v.getHeight());
        }
```        
