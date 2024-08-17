We now move all images in the examples/step*/doc/*png to the homepage and link
to the online images. They are located at
https://svnhp.dealii.org/trunk/homepage/images/steps/developer/*

All images are supposed to have the format step-*/doc/step*.png (note the
prefix!).


To move images from inside the steps (this needs to be done on occasion
because they are typically developed with images in the svn) you can do the
following:

cd deal.II/examples
ls step-*/doc/step*.png

cp step-*/doc/step*.png /path/to/homepage/images/steps/developer/
svn rm step-*/doc/step*.png
sed -i 's#@image html \(step.*png\)#<img src="http://www.dealii.org/images/steps/developer/\1" alt="">#g' step-*/doc/*.dox
sed -i 's#@image html "\(step.*png\)"#<img src="http://www.dealii.org/images/steps/developer/\1" alt="">#g' step-*/doc/*.dox

#now commit in /path/to/homepage/images/steps/developer/

#check the diffs that it worked

svn ci -m "moved images online from tutorial steps"





Timo Heister, 2013/2/22
