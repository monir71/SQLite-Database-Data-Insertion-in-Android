Helper method addData() of MyDBHelper class: 
```
public class MyDBHelper extends SQLiteOpenHelper {

    private static final String DATABASE_NAME = "contacts";
    private static final int DATABASE_VERSION = 1;
    private static final String TABLE_NAME = "contact";
    private static final String KEY_ID = "id";
    private static final String KEY_NAME = "name";
    private static final String KEY_CONTACT = "contact_no";

    public MyDBHelper(Context context) {
        super(context, DATABASE_NAME, null, DATABASE_VERSION);
    }

    @Override
    public void onCreate(SQLiteDatabase db) {
        db.execSQL("CREATE TABLE " + TABLE_NAME + "(" + KEY_ID + " INTEGER PRIMARY KEY AUTOINCREMENT, "
                + KEY_NAME + " TEXT NOT NULL, " + KEY_CONTACT + " TEXT NOT NULL)");
    }

    @Override
    public void onUpgrade(SQLiteDatabase db, int oldVersion, int newVersion) {

    }

    public void addData(String name, String phone)
    {
        SQLiteDatabase db = this.getWritableDatabase();
        ContentValues values = new ContentValues();
        values.put(KEY_NAME, name);
        values.put(KEY_CONTACT, phone);
        db.insert(TABLE_NAME, null, values);
    }
}
```
And finally in MainActivity.java
```
            MyDBHelper myDBHelper = new MyDBHelper(this);
            myDBHelper.addData("Md Moniruzzaman", "01710389323");
```
