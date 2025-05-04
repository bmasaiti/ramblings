---
title: "How I prepared for the Vault Certified Operations Professional exam"
date: 2025-04-19T14:11:42+10:00
draft: true
---


I recently started a role where I work a lot with security products , one such products is Hashicorp Vault. HashiCorp Vault is an identity-based secrets and encryption management system. It provides encryption services that are gated by authentication and authorization methods to ensure secure, auditable and restricted access to secrets.

If you work in devops or security within large organisations , there is a high chance you have interacted or have had to manage implementations of secrets management , probably have used Hashicorp vault , It's almost the defacto platform for managing secrets and setting up zero trust security between intergrated systems that require access to each other .

As a rule of thumb, when I am learning something new and there is a defined measure of competency such as certification , I like to take that and include it in my learning process and that is the reason I took both the Vault Associate exam and the Vault Operations Professional exam . In this quick article , I am going to share the resources I used and how I used them to prepare for the both exams. 

** Vault Associate exam
Preparing for this exam was probably most exciting , and for a good reason . This was my first time getting to understand what Vault is and how it works, so everything I was coming across was completely new . I used mainly two resources , Vault Docs and Udemy.

1. Vault Docs: I started digging into Vault docs , but soon got overwhelmed and abandoned the docs , that's when I went to udemy .
2. Udemy : I found a course  by Bryn Krousen (he has one for Vault Profesisonal too ) , Very detailed and straight to the point course , especially for someone who needs an introduction to what Vault is about, This course comes also with a set of labs to get your hands dirty if you have not setup vault on your local machine or in cloud (I did both). I followed this course end to end over the course of one week, that's how much fun it was . At the end of the course , I went back to Vault website , in particular here. [vault associate exam prep]https://developer.hashicorp.com/vault/tutorials/associate-cert-003 .
3. I have no idea how i missed the exam prep initially , but once I came back to It simplified my learning so much , All I had to do was follow the tutorials against each exam objective. This gave me a lot of practice and confidence to take the exam at the end of the second week. During the exam , I felt like I was over prepared.

** Vault Profesional Operations Exam.
When it came to the Vault Professional exam , this was a very tricky one , but I am glad for all the over preparation I had done when I took the associate exam, It gave me a  good base to start from and allowed my to refine my preparation technique. 
For the Professional exam I took a different approach , I started off with the exam objectives , and did all the tutorials related to each exam objective , Here I spent quite some time , redoing all the practical tutorials . I deployed a vault 3 node cluster in aws , set it up with autoseal and used that as my main cluster.
1. Setup a 3 node cluster , (allowed me to understand how standby nodes work , vault writes , understood how to interpret vault operational logs.), I also used this cluster for most other tutorials, such as setting up secrets engines and auth methods. 
2. I created a 3 other single node clusters , that where more ephemeral , I used them and stopped the ec2 boxes when I was not using them . These single node clusters I used them for the following tutorials tasks:
    . Setting up vault agent and configuring agent templating , and agent auto auth
    . Setting up Perfomance Replication ( including fialing over and reversing back to the primary cluster)
    . Setting up Disaster recovery replication and failing over and back.
    . Practising initialising vault clusters manually , using shimir unseal/recovery keys 
I believe setting up and interacting with these clusters helped me a lot , particulary in identifying activities that are not easy to recover from when you make a mistake during exam.
3. Came back to udemy to do Bryn Krousen's course (At this point I nolonger needed much theory ) I focused mostly on the labs , targetting doing them within 20mins. This was great , helped me to pick up on some gotchas , such as you can't initialise with unseal keys if you're using auto unseal , It has to be recovery keys.

**The key take aways 
1. The Vault Professional Certification exam is mostly a practical exam, taken over 4 hours and it's not an easy certification.
2. I think Hashicorp really wants us to pass the exam , by laying out exactly what is likely to be in your exam through the exam objectices linked to practical toturials that will help you prepare . 
3. All the information you need is the documentation and tutorials on Vault website .
4. You're allowed to reference the docs and api docs during the exam.

**Tips for acing the exam.
1. Prepare ...go hard on it , doing all the available practical tutorials.
2. During the exam , if you're primarily using the cli , You may find it doesn't give you all the parameters you can supply to the command , in a case like this cross reference with api docs , the parameters are always named the same way. 
3. Know where to find stuff, Whilst Vault provides you with docs and api docs , You really must be familiar with both , such that during the exam you know exactly where to go to find what you're looking for , you don't want to lose time fumbling through docs.
4. Make a list of all the difficult labs/practical tutorials that give you grief , redo them several times until you gain confidence. 
5. Understand the activities that can make it very hard to get  back , for example if you are initialising vault and you get it wrong, Once initialised it's very fidgity trying to get undo your changes ,you literaly have to delete the vault db and start again , this can be tricky during exam and adds a more work for you. 
6. The exam env uses portainer container environment. Stay vigilant when logging into these containers(vault nodes) , if you login to the wrong one and perfom an operation on the wrong node it may mess up you exam irretrivably. ( I revoked a root token on the wrong node :) , Fortunately I was done with that node, but that also meant I couldnt run some commands to validate my work.) 
7. If you're like me and English is not your first language, I would say request for the extra 30 minutes, you may not need them but good to know you have them, this will bring your exam time to 4hrs 30 mins.
8. Because of the length of the exam , Do all you need to do to ensure your comfort . Visit the bathroom , drink a little bit of water .
9. You can request a 15min break during the exam (I didnt), the proctor will pause your exam during that 15min break.
10. If you have done all the practil tutorials a few times , you shouldn't have a problem clearing this exam , and you should be able to finish it within 3 hours. 
11. I intentionally am not talking about exam content here because all you need for that is here : [exam content][https://developer.hashicorp.com/vault/tutorials/ops-pro-cert/ops-pro-review]

One final thing ..... the tutorials and the rest of the vualt website content is not available during the exam. Only the official docs and API docs are available , During your practices make sure you are referencing only the docs and api docs. 
https://developer.hashicorp.com/vault/docs
https://developer.hashicorp.com/vault/api-docs
