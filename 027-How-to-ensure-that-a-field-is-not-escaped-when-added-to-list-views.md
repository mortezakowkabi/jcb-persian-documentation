# HOW TO ENSURE THAT A FIELD IS NOT ESCAPED WHEN ADDED TO LIST VIEWS

* ### Example Extra styling In Fields
Occationally there is a need to add extra styling to a List View
Hi. Sometimes one would like to add extra styling like this [00:00:06](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m06s) The problem though is that by default all of these field values are being escaped. 

How is this kind of styling added to a field?

### Settings - Editing View - PHP Area

In the Job Order Admin View area, in PHP, [00:00:39](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m39s) there is a method called 'Add PHP(getitems Method - before translation fix & decryption)'. This happens before the translation fix or the decryption of any field. This is not the ideal place. 

### Settings Values In The Code - Add PHP Area

Usually this would be added after that was done, but in this case it was done before. [00:01:15](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m15s) A value is set up when 'danger' or 'warning' need to be applied, simply by using the getDate and modifying it by the danger time and the warning time from the job tracking configuration values. This is a configuration field that has been added to the component and it's names are: 'warning time' and 'danger time' where the default is 3 weeks, 1 week. This is the dates that is going to be used.<<<<<<<<<<<<<<<<<<<<<<<<<


 

### Looping Through Data Till Target Found - Adding Styling

I then look through the data and when I identify [00:01:49](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m49s) data that is actually part of the target. I add this value to it. That then intern turns this red. The next one is I check the dates. Depending on its values I again add some HTML value [00:02:19](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m19s) to the date, and I use a custom method in a helper class call fancyDate, where I convert the default sequel date to a better date or a better looking date, 2nd of April or something. The problem is though, [00:02:39](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m39s) if you do this and you compile your component, add items, go look at it, you'd see that it actually escapes those values and it prints it out like you see it over here. It prints out that around the value(see video). [00:02:59](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m59s) 

### Preventing The Escape Info

That's obviously not what you'd like and the reason why it does that, because all values are being escaped. Now there is a way to stop that from being from happening. That is really what this tutorial is about. To show you how to prevent that escaping. The value we have here is to create date, as well as the job status. I'm going to go in, I'm still in the [00:03:31](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m31s) back end of the component, Job order. 

### Field Adding Escape=False To Code

And I'm going to go to the fields, I'm going to scroll down to Job status. I'm going to open it. While I having it open and I can scroll down [00:04:09](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m09s) way at the bottom you see I added this little line escape= "false". So you would simply add this line. When component builder compiles, in the body of the component where that field is loaded, it will tell the escape method not to escape it, [00:04:37](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m37s) that it would then display the html instead of printing it out. That is really what it's all about. Maybe it have a lot of explanation for such a simple thing. But I can tell you what if you can't do that, it's quite frustrating. Because sometimes you would like to give some indication with some HTML upon the value, this feature actually allows that. Like you could see here we were able to add a nice button around these dates. And as well as adding some colour to these words. [00:05:15](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m15s) That is a quick demonstration of how to make use of the not escape method or concept when it comes to list views around the field values. If you have any questions please don't hesitate to let me know. 