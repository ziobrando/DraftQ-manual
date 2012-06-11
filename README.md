#How does it works

### How to write an ebook in GitHub

GitHub is an excellent social coding platform, which let you watch, fork and pull git repositories. GitHub is really appreciated by developers because, it make easy to share your code. More than this, GitHub has the ability to parse and display markdown files as html page. [Markdown](http://daringfireball.net/projects/markdown/) it's an easy and fast markup language which is focused on content and semantic. Write your ebook in markdown, push it on your GitHub repository, and let the people comments: writing an ebook is this way, it's easy as you write code. DraftQ will do all the rest.

### How to import an ebook on DraftQ

DraftQ rely on the presence of two files on the repository: manifest and medatada.

Manifests is a file called **draftq.yml** which must be placed on the root of the repository.

Manifests use [YAML Syntax](http://www.yaml.org/spec/1.2/spec.html) to define the location of ebook's files (source files, cover and  metadata).

Metadata is a subset of Dublin Core standard for define ebook metadata (author, abrastact, etc...).

### Draftq.yml syntax

If you have an ebook repository and you want to add it to DraftQ, you must add a file called draftq.yml to your git repository.

![](https://github.com/ideatosrl/DraftQ/blob/master/public/images/sample-repo.png?raw=true)

DraftQ manifest let you define the structure of your ebook:

![](https://github.com/ideatosrl/DraftQ/blob/master/public/images/sample-manifest.png?raw=true)

Here is a sample code you can use as a template for draftq.yml

	--- # Document Root
	  sourceFiles: ['readme.md','en/redis.md']
	  cover: 'en/title.png'
	  metadata: 'en/metadata.xml'

**sourceFiles:** it represents the list of markdown files to import. You must specify them in the exact order. The sourceFiles value is defined as a [Yaml Generic Sequence](http://www.yaml.org/spec/1.2/spec.html#id2802662) and can be specified using both inline or block notation. sourceFiles is a mandatory field.

**cover:** it's an image file (.png|.jpg) to use as cover. Cover will be put on top of your ebook. Cover will be also used in the ebook splash page. If you don't have a cover just omit this line (optional).

**metadata:** the location of metadata file. Metadata is a mandatory field. For further information see the section below.

###Metadata
Metadata file contains information about your ebook, like title, author and abstract. It is represented as an xml document fragment and it support a subset of [Dublin Core Metadata Element Set](http://dublincore.org/documents/dces/).

```xml
<dc:title>The Little Redis Book</dc:title>
<dc:creator>Karl Seguin</dc:creator>
<dc:description>
<![CDATA[
Over the last couple years, the techniques and tools used for persisting and 
querying data have grown at an incredible pace. 
.....
]]>
</dc:description>
```

**dc:title:** The title of your ebook. Property is mandatory.

**dc:creator:** The main author of the ebook. Optional property.

**dc:description:** Description may include but is not limited to an abstract or a table of contents. Optional property.

Metadata file is called **metadata.xml** by convention, but you can choose a different name. Also you can place your metadata file wherever you want, and specify the location on your manifest file.