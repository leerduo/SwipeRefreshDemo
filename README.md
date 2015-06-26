#添加下拉刷新
##使用SwipeRefreshLayout
```xml
<android.support.v4.widget.SwipeRefreshLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:id="@+id/swipe"
    tools:context=".MainActivity">

    <ListView
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:id="@+id/list" />

</android.support.v4.widget.SwipeRefreshLayout>
```
##ActionBar上增加刷新的动作
```xml
 <item
        android:id="@+id/refresh"
        android:title="刷新"
        app:showAsAction="always"
        />
```
#添加响应动作
##手指滑动
```java
 swipeRefreshLayout.setOnRefreshListener(new SwipeRefreshLayout.OnRefreshListener() {
            @Override
            public void onRefresh() {
                update();
            }
        });
```
```java
 private void update() {
        Toast.makeText(this,"刷新...",Toast.LENGTH_SHORT).show();
        swipeRefreshLayout.setRefreshing(false);
    }
```
##响应ActionBar的item
```java
  @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        // Inflate the menu; this adds items to the action bar if it is present.
        getMenuInflater().inflate(R.menu.menu_main, menu);
        return true;
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        // Handle action bar item clicks here. The action bar will
        // automatically handle clicks on the Home/Up button, so long
        // as you specify a parent activity in AndroidManifest.xml.
        int id = item.getItemId();

        //noinspection SimplifiableIfStatement
        if (id == R.id.refresh){
            swipeRefreshLayout.setRefreshing(true);
            update();
            return true;
        }
        if (id == R.id.action_settings) {
            return true;
        }

        return super.onOptionsItemSelected(item);
    }
```
TODO  源代码