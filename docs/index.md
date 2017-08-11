---
layout: default
---

# [](#header-1)Training face landmark detector

This application helps to train your own face landmark detector. You can train your own face landmark detection by just providing the paths for
directory containing the images and files containing their corresponding face landmarks. As this landmark detector was originally trained on
[HELEN dataset](http://www.ifp.illinois.edu/~vuongle2/helen/), the training follows the format of data provided in HELEN dataset.

The dataset consists of .txt files whose first line contains the image name which then follows the annotations.
The format of the file containing annotations should be of following format :
       
>       /directory/images/abc.jpg
>       123.45,345.65
>       321.67,543.89
>       .... , ....
>       .... , ....
       
The above format is similar to HELEN dataset which is used for training the model.

```js
// Command to be typed for running the sample
./sample_train_landmark_detector -annotations=/home/sukhad/Downloads/code/trainset/ -config=config.xml -face_cascade=lbpcascadefrontalface.xml -model=trained_model.dat -width=460 -height=460
```

## [](#header-2)Description of training parameters

> * annotations a : (REQUIRED) Path to annotations txt file [example - /data/annotations.txt]
> * config c : (REQUIRED) Path to configuration xml file containing parameters for training.[ example - /data/config.xml]
> * model m :  (REQUIRED) Path to configuration xml file containing parameters for training.[ example - /data/model.dat]
> * width w : (OPTIONAL)  The width which you want all images to get to scale the annotations. Large images are slow to process [default = 460]
> * height h : (OPTIONAL) The height which you want all images to get to scale the annotations. Large images are slow to process [default = 460]
> * face_cascade f (REQUIRED) Path to the face cascade xml file which you want to use as a detector.

### [](#header-3)Header 3

```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# Ruby code with syntax highlighting
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

#### [](#header-4)Header 4

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

##### [](#header-5)Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### [](#header-6)Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![](https://assets-cdn.github.com/images/icons/emoji/octocat.png)

### Large image

![](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
