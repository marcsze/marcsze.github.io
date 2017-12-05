---
layout: post
title: "Angst After a Job Interview"
date: 2017-12-03
tags: [scienceblog]
---

I have recently been interviewing for various jobs both in academia and industry. The process is pretty different for the two different sectors. In this blog post I want to focus on my experience with a specific job interview for industry, we shall call them GS. In the essence of transparency I did not get this job that I am about to talk about. I'm still on the fence as to whether this was a good or bad thing.  

It took some time to get through the company's first two interviews. After completing this process the third interview was a question on how I would analyze a specific data set. This seemed pretty straight forward enough and seemed like a reasonable question to ask about. 

The question that they asked me was the following:

*You have a set of 16S rRNA sequencing data from 100 Ulcerative Colitis patients. Stool samples were collected from flare as well as remission periods from each patient (total 200 samples). Describe how you would determine which bacterial features are associated with the remission period.*

The answer that I provided is below:

*Although it would be possible to choose to use a technique such as LEfSe to analyze this set of data I would instead opt to use the machine learning algorithm Random Forest. There are a few reasons for this choice. First, building a model with Random Forest will offer me future utility with the option to be able to test this model on other data sets moving forward. Second, Random Forest in many ways accounts for the interdependency of OTUs while LEfSe does not. Finally, using the mean decrease in accuracy (MDA) metric allows for an interpretation as to how important a specific OTU is to the model with the community accounted for. As a counter point LEfSe would not incorporate the whole community into its analysis pipeline but rather would look at each individual OTU in isolation versus the biological outcome of interest.*
 
*With the algorithm chosen I would use a similar approach as to a study that I recently undertook looking at the microbiota before and after treatment of colorectal cancer (https://www.biorxiv.org/content/early/2017/09/16/138222). The problem in which one is looking at, flares and remission in Ulcerative Colitis (UC), is similar in the sense that there is a before (unhealthy state) and a after (healthy state). I would build the model by first holding out a set percentage of samples (typically 20%). With the remaining samples (80% if 20% was held out) I would then run a random forest model with 10-fold cross validation in which I optimize the mtry hyperparameter (the number of OTUs that it will “try” before making a split) and then test this model on the held out 20%. I would do this 100 times to generate a range in which one could reasonably expect the true AUC to fall. From each iteration I would store the MDA for every OTU within the model and then rank the OTUs by their median. The OTUs with the highest median MDA across the 100 different runs would most likely be the most important OTUs with respect to differentiating between flares and remission.*
 
*The one downside to using the Random Forest method is that there is no defined cut-off by which one would choose the most important OTUs. One could use an arbitrary cut-off to limit the features of interest (e.g. top 10%) if other more specific downstream analysis needs to be done.*

They seemed happy with this answer and I thought this was going to be enough to demonstrate my knowledge base. But I was wrong. I had another follow up and another e-mail interview challenge. Not only was I going to be asked to analyze a data set in one week but I also had to create a presentation on it to be critiqued by 4-5 people. Now, as an active post doc, this is a lot of work to ask for when considering that I have my own projects that still need to get done during the week. Since I did not get the job I am pretty sure I did not spend enough time on this question set. I definitely could have done more but at the same time I am not being paid to analyze or find new questions for the company. First, here is the [GitHub repo](https://github.com/marcsze/gs_stuff) if you want to take a look at things. Here is the breakdown of my hours spent on the question.

* 1 hour reading the given paper
* 1 hour planning analysis
* 3 hours of code set up
* 1 hour for graphing the data
* 2 hours creating a presentation

So the total amount of time spent was 8 hours from start to finish. In that time I created a NMDS graph of the OTUs based on groups, generated a Random Forest model to classify groups using the microbiota, taxonomically classified OTUs based on the RDP, identified the most important OTUs to the model, and created two graphs to visualize the Random Forest data. 
I don't know how much time they want for me to spend on the question but hats off to the individual who got the position because I thought this would be more than enough. 

At the moment, my experience with industry job interviews have not been all that positive of an experience. Below are a summary so far of how things have gone:

* Johnson & Johnson Microbiota position (Straight up rejection)
* Merck Bioinformatics Position (Straight up rejection - Not the right fit and International)
* Nestle Microbiota Position, St. Louis (Straight up rejection)
* Nestle Microbiota Position, Lausanne (Rejected after 2nd Skype interview - No industry experience & metagenomics knowledge)
* Thermo-Fisher Bioinformatics Position (Job no longer exists)
* Insight Data Science Fellowship (Accepted - I declined the offer (might have been a mistake))


Although the academic interviews can be more gruelling and I haven't been any more successful in that regard either (0/2 on offers after an in person interview). I do enjoy them more due to the networking and interesting conversations that occur throughout the entire process.

In the end, I have been repeatedly told it isn't me, it is the "fit". I understand that this is an important intangible but it can definitely lead to the applicant feeling inadequate to some degree. As an example, take the Nestle job, it is impossible for me to get industry experience unless I am hired, so this becomes a little bit of a vicious circle. Additionally, no matter how much I know about the analysis of the [microbiota](https://www.ncbi.nlm.nih.gov/pubmed/?term=Marc+Sze), if I am not on a metagenomics manuscript I somehow am not skilled enough to know how to do it? Just because I'm not on a paper for metagenomics doesn't mean I don't know how to do it or understand it...

I think there really isn't a grand point to this post. I just needed somewhere to write down the angst that I am accumulating by going through an interview process that has no immediate end in sight. For those in a similar boat, I just keep telling myself, all I need is one...just one and all of this won't matter anymore. 

