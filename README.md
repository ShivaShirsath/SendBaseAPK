# Send App by itSelf
```java
// if black inside MainActivity
// if base.apk is not sending at upper versions
    if (Build.VERSION.SDK_INT >= 24) {
        try {
            Method m = StrictMode.class.getMethod("disableDeathOnFileUriExposure");
            m.invoke(null);
        } catch (Exception e) {
            Toast.makeText(MainActivity.this, e.getMessage(), Toast.LENGTH_LONG).show();
        }
    }		


// method declare outside MainActivity
	public void sendAppItself(Activity paramActivity) {
		try {
			paramActivity.startActivity(Intent.createChooser(new Intent(Intent.ACTION_SEND).setType("*/*").putExtra(Intent.EXTRA_STREAM, Uri.parse("file://" + paramActivity.getPackageManager().getApplicationInfo(paramActivity.getPackageName(), PackageManager.GET_META_DATA).publicSourceDir)), "Share it using"));
		} catch (Exception e) {
			Toast.makeText(this,e.getMessage(), Toast.LENGTH_LONG).show();
		}
	}
```
