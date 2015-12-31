# Espresso Contributions for Realm 
Currently this library only contains the `RealmRecyclerViewActions` class that enables developers to write Espresso tests using [RealmRecyclerView](https://github.com/thorbenprimke/realm-recyclerview). 

`RealmRecyclerView` does not subclass `RecyclerView` but includes it in another view. These RecyclerViewActions help with testing when using the `RealmRecyclerView`. 

## Example

Assume your layout looks like this: 

```xml 
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
                xmlns:tools="http://schemas.android.com/tools"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                xmlns:app="http://schemas.android.com/apk/res-auto"
                android:paddingLeft="@dimen/activity_horizontal_margin"
                android:paddingRight="@dimen/activity_horizontal_margin"
                android:paddingTop="@dimen/activity_vertical_margin"
                android:paddingBottom="@dimen/activity_vertical_margin"
                tools:showIn="@layout/activity_main"
                tools:context=".MainActivityFragment">

    <co.moonmonkeylabs.realmrecyclerview.RealmRecyclerView
        android:id="@+id/main_task_list"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:rrvIsRefreshable="true"
        app:rrvLayoutType="LinearLayout"
        app:rrvEmptyLayoutId="@layout/empty_view"
        />


</RelativeLayout>
```

Let's also assume you have a number of items that are added to your RecyclerView and you need to write an Espresso test to scroll to a particular location before performing assertions. 
Here's how you'd do that: 

```java
// Scroll to the tenth item in the RealmRecyclerView where R.id.main_task_list is the id
// of the RealmRecyclerView
onView(withId(R.id.main_task_list)).perform(RealmRecyclerViewActions.scrollToPosition(10));
// more assertions ...
```

## License
```
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

Included dependencies are:
RealmRecyclerView (https://github.com/thorbenprimke/realm-recyclerview)
Realm (https://github.com/realm/realm-java)
SuperSLiM/Tonic Artos (https://github.com/TonicArtos/SuperSLiM)
```