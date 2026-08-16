# Add Resources

* To keep apps portable and secure, avoid hardcoding resource IDs.
* The user adding the resource must have the `Can manage` permission on the resource and the app

1. In the **App resources** section when you create or edit an app, click **+ Add resource**.
2. Select the resource type you want to add.
3. Set the permissions for the app service principal on the resource.
4. Assign a key to the resource, and reference that key in your `app.yaml` file.

*

    <figure><img src=".gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>
* Grant only the minimum required permissions to the app's service principal. For example:
  * Grant `CAN USE` on a SQL warehouse if the app only needs to run queries.
  * Grant `CAN QUERY` on a serving endpoint if the app only sends inference requests.
  * Grant `SELECT` or `MODIFY` on Unity Catalog tables based on the app’s data access needs
