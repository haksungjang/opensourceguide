# License compliant containers

### 2019-03-13

{% file src="../../.gitbook/assets/presented-slides-2020-3-11.pptx" %}

License compliant containers: Alexios presented the current state of work he has done in the context of license compliant containers. He showed a glossary of terms. The glossary is important, because it ensures that all are talking about the same things. After walking quickly through the glossary Alexios showed the different artifacts and the different distribution scenarios, which can happen. The artifacts Alexios talked about are:

1. Docker file
2. Docker layer
3. Docker image
4. Docker container

As they were also shown on our previous meeting \(see also attached slides for convenience\)

The distribution scenarios are:

1. Distributing a docker file
2. Distributing a docker layer
3. Distributing a docker image When distributing only a docker file the assumption is that the users can build the image on their own. Alexios said that a license as well as copyright ownership shall be present in all docker files. When pushing a layer to docker hub, care has to be taken what is contained in the layer. The recommendation is to provide only the minimum required elements, in order to keep the license compliance efforts as low as possible. Further Alexios said that squashing layers has to be avoided. Remark on pushing layers to docker hub. Docker hub checks whether the layer to be pushed is already published, if so this layer won't be published again. Other "container repos" might have a different behavior. Two options exist for making the source code available to the parts, which end up in a layer or image.
4. Integrate the source code directly in the layer or image and make it accessible
5. Create a "source code layer" or "source code image" and put it side by side to the binary layer or image.

   These options are similar to the options for providing the source code for GPL licensed binaries. In the end a layer or a container image is a binary.

After Alexios' presentation Karsten Klein gave an overview about their ways how they determine the ingredients of a container and how they generate the documentation of such ingredients.

Alexios and Karsten will make the presented slides available in our github repo

1. Next steps:

   Next meeting 25th of March the invitation will be send by Michael, since I will not be able to moderate the meeting

   Proposed Agenda:

2. Discussion of recommendations and best practices for license complaint containers         All

### 2019-03-18



### Best practices for license compliant containers

The following collection of "Dos" and "Don'ts" shall help to achieve license complaint containers, which is currently a major challenge, since the compliance process lacks behind technology. Like for the "traditional" development the compliance process for containers shall be fully integrated in the process of creating container layers or images. It is key to have persons in charge of compliance integrated in the process of creating the artifacts. This will save time and effort, compared to the situation when a build image or layer is transferred to the OSPO for license compliance analysis and work.

### Guiding Principles:

* Always publish only the minimal required artifacts. This can be in the easiest case the docker file, if this is not possible check whether it is enough to publish only a layer \(containing your application\). Publishing complete container images shall only be considered if the other options will not work.
* All the resulting compliance work, its effort and time needed has its origin in the docker file. Get involved in the creation process of the docker file right from the beginning
* Select carefully the docker repos you are using

### Docker file

### Dos for the docker file:

* Make the docker file REUSE conformant \(i.e. provide the license information for the docker file as well as a copyright string\)
* Use version pinning in your docker file. E.g. FROM abc:2.1.0
* Always "install" the minimal required set of packages, bear in mind that everything which will be published has to undergo the license compliance process
* Use multi stage builds.

### Don'ts for the docker file:

* Avoid squashing layers

### Docker layer

Some of best practices for docker layers have to be implemented in the docker file, which is the "make file" for docker layers and images.

### Dos for the docker layer:

* For every layer you publish make sure that it contains the "OSS disclosure document" and make sure that it can be accessed easily
* For every layer you publish make sure that it contains either the source code packages of the contained binaries or provide a "source code layer" along with the "binary layer" \(containing only the binaries and the OSS disclosure document\)

### Docker image

Like the best practices for creating docker layers some of best practices for docker images have to be implemented in the docker file, which is the "make file" for docker layers and images.

### Dos for the docker image:

* For every image you publish make sure that it contains the "OSS disclosure document" and make sure that it can be accessed easily
* For every image you publish make sure that it contains either the source code packages of the contained binaries or provide a "source code image" along with the "binary image" \(containing only the binaries and the OSS disclosure document\)

