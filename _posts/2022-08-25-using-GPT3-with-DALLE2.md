---
layout: post
title: Teaching GPT-3 to create interesting DALLE-2 prompts
subtitle: And trying to figure out its obsession with women
author: Petar
---

I recently got access to DALLE-2 and have been having a blast with it. There's been an explosion of [information and guides](https://dallery.gallery/) on how to construct good prompts for it. In some instances it appears to be almost formulaic -- this got me thinking -- can I teach GPT-3 to come up with funky prompts? 

I've got no idea how to construct good GPT-3 prompts, so if you want to [skip to end](#attempt-10), go ahead. Otherwise let's just get into it and see what this gives us:

#### Attempt 1: `Write a creative DALLE2 prompt`

> What would you do if you had the power to control time? If I had the power to control time, I would use it to fix all the mistakes I've ever made. I would go back and make sure I studied for that test I failed, or fix that relationship I ruined. I would spend more time with the people I love, and make sure to tell them how much I care about them. I would use my power to make the world a better place, and make sure that everyone had the chance to live a happy and fulfilling life.

Err, ok? Not even going to feed this to DALLE. I think the word `prompt` may have made it write a story instead. Let's try again:

#### Attempt 2: `Create 5 varied DALLE-2 prompts that use different styles and formats as well as a variety of scenery detail information and objects`

> 1. The DALLE-2 program has provided me with an opportunity to explore new scenery and learn about different cultures.
> 
> 2. DALLE-2 has allowed me to travel to some of the most beautiful places on earth and learn about their cultures and customs.
> 
> 3. The DALLE-2 program has given me a chance to see the world in a new light and learn about different cultures and customs.
> 
> 4. DALLE-2 has opened my eyes to new scenery and cultures, and I have learnt so much about different customs and beliefs.
> 
> 5. The DALLE-2 program has been an amazing experience that has allowed me to explore new scenery, learn about different cultures, > and see the world in a new light.

Ok, I was hoping GPT-3 would have an inkling of this type of task. Looks like we're going to have to get more specific.

#### Attempt 3

I came across a website (which I have now lost the link to), which specified a bunch of useful lists for creating DALLE-2 prompts. Let's use them as a template!

`Create 5 varied DALLE-2 prompts that use different styles and formats as well as a variety of scenery detail information and objects. Use the following template:`

`A [format] of [description] in the style of [style], [perspective]. You need to replace the parameters in the brackets. Use the following lists to choose from for each one:`

`format:`
`3D Render, Book Cover, Cartoon, Diagram, Glass, Illustration, Oil Painting, Painting, Photograph, Pixel Art, Portrait, Selfie, Sketch, Tattoo, Watercolor Painting`

`style:`
`Abstract, Anime, Art Deco, Art Nouveau, Banksy, Baroque, Bauhaus, Biopunk, Cubism, Cybernetic, Cyberpunk, Fractal, Gothic, Impressionism, Impressionist, Pop Art, Realism, Renaissance, Steampunk, Surrealism, Synthwave, Ukiyo-E, Vaporwave`

`perspective:`
`85Mm, Bokeh, Close Up, Dark Background, Drone, In The Distance, Landscape, Long Shot, Low Angle, On Canvas, Panoramic, White Background, Wide Angle`

`The description parameter needs to specify an object or subject performing an action, in some sort of scenery.`

> 1. A 3D Render of a cityscape in the style of Cyberpunk, Long Shot.
> 2. A Book Cover of a woman in the style of Art Nouveau, Close Up.
> 3. A Cartoon of a cat in the style of Anime, On Canvas.
> 4. A Diagram of a heart in the style of Gothic, White Background.
> 5. A Glass of water in the style of Impressionism, In the Distance.

Kind of getting there, but it's not very inventive. After about 10 more variations of the above, I couldn't get GPT-3 to produce anything new; it kind of got stuck in a loop. Let's try something more creative.

#### Attempt 4

`Come up with a brand new description of a painting or photograph, specifying the art style, the atmosphere, the framing of the subject, the lighting and the medium. Describe the subject.`

> This is a painting of a young woman in a white dress. She is standing in a garden, surrounded by flowers. The light is shining on her from the left, and she is looking towards the right. The painting is in a realistic style, and the colors are very bright.

That's more like it! Let's give it to DALLE. (I will remove the "This is" portion of the prompt)

<img src="/assets/images/gpt-dalle-examples/attempt4/woman1.png" /> | <img src="/assets/images/gpt-dalle-examples/attempt4/woman2.png" /> 
<img src="/assets/images/gpt-dalle-examples/attempt4/woman3.png" /> | <img src="/assets/images/gpt-dalle-examples/attempt4/woman4.png" /> 

Let's generate another prompt: 

> This painting depicts a beautiful summer day at the beach. The sun is shining and the waves are crashing onto the shore. The colors are very bright and vibrant. The subject is framed by the beach umbrellas and the palm trees. The medium is oil on canvas.

<img src="/assets/images/gpt-dalle-examples/attempt4/beach1.png" /> | <img src="/assets/images/gpt-dalle-examples/attempt4/beach2.png" /> 
<img src="/assets/images/gpt-dalle-examples/attempt4/beach3.png" /> | <img src="/assets/images/gpt-dalle-examples/attempt4/beach4.png" /> 

It completely forgot to specify the subject this time. I suppose there doesn't have to be one. It also chose to use the same description for the colours/vibe. 

At this point I noticed a mistake in my prompt. I've asked it for a painting or photograph -- then I ask it to specify an art style -- and at the end I ask it to specify the medium. Perhaps that's why it chose a painting both times? Let's try improving it.

#### Attempt 5

`Come up with an original description of a painting or photograph, specifying the subject, what they're doing, the atmosphere, the surroundings, the framing of the subject and the lighting`

> In this painting, a young woman is standing in a sun-drenched field of wildflowers. She is wearing a flowing white dress and has a bright red scarf tied around her waist. The woman's hair is blowing in the breeze and she has a serene look on her face. The painting has a warm, sunny feeling and the woman looks like she is in a state of bliss.

What's with the women GPT-3? 🤨 I regenerated the output 3 more times and it was more or less the same thing.

#### Attempt 6

`Come up with an original description of a scene, specifying the subject, what they're doing, the atmosphere, the surroundings. Decide whether this is a painting, a photograph or a 3D render.  Describe the framing of the subject and the lighting. If it's a painting decide the medium.`

> The subject is a young woman, standing in a forest clearing. She is looking up at the sky, with a sad expression on her face. The atmosphere is one of melancholy and longing. The forest is dark and shadowy, and the sunlight is filtering through the trees. The woman is framed by the trees, and the light is shining on her face. This is a painting, done in oils.

Seriously? C'mon, I even maxed out the randomness to 1 (was 0.75)! To make a long story short, I tried a few more generations. I played around with the "presence penalty", which affects the model's likelihood of bringing up new topics. Nonetheless, it kept focusing on women or young girls as the subject, occasionally choosing a boy or "itself" (I) as the subject.

It is clearly struggling with the medium because it almost always chooses a painting and appears to defer the decision I am asking of it by simply stating:

> This could be a painting, a photograph or a 3D render.

Let's try to fix that.

#### Attempt 7

`Come up with an original description of a [medium], specifying the subject, what they're doing, the atmosphere, the surroundings and the lighting. Replace [medium] with one of: photograph, painting, 3d render, sketch. If it's a photograph specify the film type and the lens. If it's a painting specify the style.`

> It's a photograph of a young woman, she's sitting on a bench in a park and she's looking at the camera with a smile. The light is soft and there's a bit of a breeze.
>
> It's a 3d render of a cityscape at night. The streets are empty and there's a light rain falling. The lights from the buildings and streetlights reflect off the wet pavement.
> 
> It's a sketch of a man in a suit. He's standing in an office with his hands in his pockets. The lighting is bright and there's a window behind him.

This time it gave me 3 outputs for the price of one, presumably because of the substitution instruction, though it did skip the painting for some reason. We've _kiiiiind_ of escaped the "woman loop". 

<img src="/assets/images/gpt-dalle-examples/attempt7/city.png" /> | <img src="/assets/images/gpt-dalle-examples/attempt7/man.png" /> 

Let's keep trying.

#### Attempt 8

`Come up with an original description of a scene, specifying the atmosphere, the surroundings and the lighting. Optionally specify a subject and tell me what they're doing. Tell me if this is a photograph, a painting, a 3d render or a sketch. If it's a photograph specify the film type and the lens. If it's a painting specify the style.`

> It's a painting, in the impressionist style. The scene is of a park in the early morning, with the sun just starting to peek over the trees. The light is soft and diffused, and the colors are muted. The grass is still damp with dew, and there are a few people walking around, enjoying the peace and quiet of the morning.

<img src="/assets/images/gpt-dalle-examples/attempt8/park.png" />

And once more:

> It's a beautiful sunny day and the sky is clear. The scene is of a young woman sitting on a bench in a park, reading a book. She's surrounded by trees and flowers, and the sun is shining down on her.

You gotta be shitting me. 

Let's take some steps back. I'll limit it to just photographs since I'm noticing that it's forgetting to mention some of the specifics I am asking it for, which is odd because I've seen examples of extremely long and convoluted instructions that people have given it and it follows them to the dot.

#### Attempt 9

`Come up with an original description of a photograph specifying the subject and what they're doing, the atmosphere, the surroundings and the lighting. Specify the film type and the lens.`

> In this photograph, the subject is a young woman standing in the middle of a road. She is looking to the left, away from the camera. The road is empty and there are trees on either side. The lighting is natural and the film type is color. The lens is a wide-angle lens.

AAAAAAH! STOP! 🤬

#### Attempt 10

`Come up with an original description of a photograph specifying a person and what they're doing, the atmosphere, the surroundings and the lighting. Specify the film type and the lens. Don't choose a woman as the subject`

> A young man in his early twenties is leaning against a wall on a sunny day. He is wearing a worn leather jacket and jeans. His hair is messy and his eyes are looking down. The background is a busy street with people walking by. The light is bright and harsh.
> 
> The film type is 35mm and the lens is a 50mm.

<img src="/assets/images/gpt-dalle-examples/attempt10/man.png" />

Well, if it's stupid and it works... You know, at this point it doesn't feel like it's headed in the right direction any more. Even if we escape the "woman loop", we still aren't producing enough creative variations. Let's revisit what we tried in Attempt 3 but change up the description parameter.

#### Final attempt...?

`Write a sentence using the following template:`

`A [format] of [scene] in the style of [style], [perspective]. You need to replace the parameters in the brackets. Use the following lists to choose from for each one:`

`format: ...`

`style: ...`

`perspective: ...`

`The scene parameter needs to specify an object or subject performing an action. Describe the scenery. Describe the mood and the lighting.`

> A 3D Render of a small girl in the style of Banksy, from a Low Angle perspective. The girl is drawn in black and white with a few strategic color splashes. She's standing in front of a dark background, with a single light source coming from the top left. The mood is playful and mischievous, with a hint of danger.

<img src="/assets/images/gpt-dalle-examples/attempt11/banksy_girl.png" />

You know, that's pretty good! Another one:

> A Photograph of a Girl in a Blue Dress, In the Distance. The girl is standing in a field of tall grass with a light breeze blowing her dress around her. The sun is setting in the background, casting a golden glow on everything.

<img src="/assets/images/gpt-dalle-examples/attempt11/woman_field.png" />

Noooooooooo, please god no! Hit it again!

> A painting of a sunset in the style of realism, wide angle. You can see the sun beginning to dip below the horizon, and the sky is a beautiful orange. The lighting is very warm, and the mood is peaceful.

<img src="/assets/images/gpt-dalle-examples/attempt11/sunset.png" />

> A photograph of a rose in the style of Impressionism, 85Mm. The rose is in a garden with ivy crawling up a white picket fence in the background. The lighting is bright and the mood is cheerful.

<img src="/assets/images/gpt-dalle-examples/attempt11/rose.png" />

Well, that's not so bad. But it's not great either. New generations are at least somewhat varied. 

There are clearly issues with this approach. The last example specifies an impressionistic _photograph_; clearly some of the combinations of styles and formats just don't make sense. I kind of hoped that GPT-3 would have a taller creative ceiling but perhaps it needs to be guided more. A lot of the generated prompts are pretty tame. I wanted lamas driving Ferraris in LA, not roses in gardens.

It's now 00:30 and I don't have the energy to create better prompts for my prompts, nor can I figure out GPT-3's obsession with women. 

And with my last few DALLE-2 credits, I leave you with...

<img src="/assets/images/gpt-dalle-examples/lamas1.png" />
*This took 5 attempts and I'm not even happy with it!*

<img src="/assets/images/gpt-dalle-examples/lamas2.png" /> | <img src="/assets/images/gpt-dalle-examples/lamas3.png" />
