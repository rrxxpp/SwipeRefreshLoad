# SwipeRefreshLoad
Modify from Demievil/SwipeRefreshLayout  and  dodola/MetaballLoading,Thanks

从SwipeRefreshLayout和MetaballLoading 合并过来的，主要是修改了SwipeRefreshLayout的上拉加载，没加载的时候隐藏footer，把MetaballLoading放到了footer里。
不会传gif，下demo吧
## Demo ##
[Download apk](/demo.apk)

## Screenshot ##
![png](/1.png)
![png](/2.png)
![png](/3.png)
![png](/4.png)


## Thanks ##

modify from

1.
https://github.com/dodola/MetaballLoading

2.
https://github.com/Demievil/SwipeRefreshLayout


## How to Use ##



<com.demievil.library.RefreshLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/swipe_container"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <ListView
        android:id="@+id/list"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="#FFFFFF"
        android:dividerHeight="1px"
        android:footerDividersEnabled="false"
        tools:listitem="@layout/list_item" />
</com.demievil.library.RefreshLayout>




 mRefreshLayout = (RefreshLayout) findViewById(R.id.swipe_container);
        mListView = (ListView) findViewById(R.id.list);


        mRefreshLayout.setChildView(mListView);

        initAdapter();
        mListView.setAdapter(mAdapter);

        mRefreshLayout.setColorSchemeResources(R.color.google_blue,
                R.color.google_green,
                R.color.google_red,
                R.color.google_yellow);


        //使用SwipeRefreshLayout的下拉刷新监听
        //use SwipeRefreshLayout OnRefreshListener
        mRefreshLayout.setOnRefreshListener(new RefreshLayout.OnRefreshListener() {
            @Override
            public void onRefresh() {
                simulateFetchingData();
            }
        });


        //使用自定义的RefreshLayout加载更多监听
        //use customed RefreshLayout OnLoadListener
        mRefreshLayout.setOnLoadListener(new RefreshLayout.OnLoadListener() {
            @Override
            public void onLoad() {
                simulateLoadingData();
            }
        });






