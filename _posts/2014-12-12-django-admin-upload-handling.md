---
layout: post
title: Django admin file upload handling
---

In a Django project I recently worked on I was looking for a way to add the ability to upload data through the admin interface, at which point it would be processed and added to the database. Everything I could find online involved editing the admin interface; however, there is an easier way!

Create a model representing the type of data upload you want – for example, `DataFile` – and give it a `FileField`. We then override the `save` method, which controls saving a model in the database, and is automatically invoked when a model is created in the admin interface.

In your `models.py`:

{% highlight python %}
class DataFile(models.Model):
    data = models.FileField()

    def save(self, *args, **kwargs):
        super(DataFile, self).save(*args, **kwargs)
        filename = self.data.url
        # Do anything you'd like with the data in filename
{% endhighlight %}

The first line in save saves the file model in the database. `filename` will then contain the path of the file in the file system (the location is controlled by the [`MEDIA_ROOT` Django setting](https://docs.djangoproject.com/en/dev/ref/settings/#media-root)). You can then, for example, parse the data into models and populate the database with them.

In your `admin.py` add `admin.site.register(DataFile)`. It will now be added to the admin interface. The 'Add' page will have a basic upload form:

![Django file upload screen]({{ site.url }}/assets/django_file_upload.png)

After clicking 'Save', the data will be uploaded and control handed over to the save method of `DataFile`.
