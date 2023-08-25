---
layout: post
title: "How to use ChatGPT to practice Spanish"
author: "Petar"
---

I've long wanted to be able to practice my Spanish by translating pieces of text. Trouble is, it's impossible to do so without someone fluent in Spanish there to correct my errors and explain them.

With ChatGPT (the free, 3.5, version) it finally feels possible. There are caveats of course, which I will mention.

### The entry prompt

> I want to practice my Spanish by translating things from English. Act as a Spanish tutor. Your task is to correct my translation and explain each correction. Provide me with a text in English that obeys the following:
>
> - consists of 4 to 5 sentences
> - includes at least 1 example that would require the subjunctive mood
> - includes a mix of past, present and future tenses (and variants thereof)
> - take inspiration, but do not limit yourself, from the following list of topics: weather, friends, politics, health culture, cooking, hobbies, nature, technology, business, family
>
> Respond in Spanish, apart from the text in English.

The last bullet point is important. If you don't direct ChatGPT it will almost always give you text about _vacations_. This fix isn't perfect, but it seems to be relatively varied so far and you can always use the "regenerate" feature to re-roll a topic.

The direction about the subjunctive mood is not necessary; it's just something _I_ want to practice. Similarly, the instruction for tenses is also up to you to modify but I think it helps vary the text (otherwise you get boring past-tense-only paragraphs).

#### Example output

> Por supuesto, estaré encantado de ayudarte. Aquí tienes el texto en inglés para que lo traduzcas al español:
>
> "Last night, my friends and I went to a cooking class to learn how to make traditional dishes from different cultures. The instructor suggested that we try our hand at making a spicy Mexican dish. While we were cooking, we talked about our favorite family recipes and shared stories about our childhood. Next week, we are planning a hiking trip to a nearby nature reserve. I hope the weather will be favorable and that we can enjoy the beauty of the outdoors."
>
> Por favor, traduce este texto al español y luego estaré aquí para revisar y corregir tu traducción, explicando cada corrección. ¡Buena suerte!

Notice that it has included a blend of the suggested topics, instead of remaining in one single topic. Some tweaking to that instruction may be required. Otherwise it has followed all other instructions correctly.

### The exit prompt

In a single reply you can include your translation and provide instructions for the correction.

There are some intentional mistakes in here to demonstrate the problems ChatGPT experiences... also don't judge my Spanish too much 😅

> Anoche, mis amisgos y yo fuimos a una clase de cocinar para aprender hacer platos tradicionales de culturas diferentes. El instructor sugerió que probamos hacer un picante plato de México. Como cocinamos, hablabamos sobre nuestras favoritas recetas de familia y compartimos cuentos de nuestro niñez. La proxima semana, planeamos una caminata a una reserva natural cerca. Espero que el tiempo sea favorable y que podamos disfrutar la belleza del aire libre.
>
> --
>
> Please correct all mistakes, including places where the sentence can be made more natural for a native Spanish (Spain) speaker. Ensure that I have used the correct tenses in all places and correct me if I haven't. Ensure not to highlight or explain things that are already correct. If there is a typo or a misued accent, highlight it but do not explain it. Explain the remaining corrections.

#### ChatGPT's reply:

_The emphasis is present in the original reply._

> ¡Muy bien! Has hecho un buen trabajo. Aquí están las correcciones y las explicaciones:
>
> "Anoche, mis **amigos** y yo fuimos a una clase de **cocina** para aprender **a hacer** platos tradicionales de **diferentes culturas**. El instructor **sugirió que intentáramos** hacer un **plato picante mexicano**. Mientras cocinábamos, hablábamos sobre nuestras **recetas familiares favoritas** y compartíamos cuentos de **nuestra infancia**. La próxima semana, **estamos planeando** una caminata a una reserva natural **cercana**. Espero que el tiempo sea favorable y que podamos disfrutar **de** la belleza del aire libre."
>
> Explicaciones:
>
> 1. "**amisgos**" - La palabra correcta es "**amigos**," que significa "friends."
>
> 2. "**clase de cocinar**" - Usamos "**clase de cocina**" para indicar "cooking class."
>
> 3. "**aprender hacer**" - Cambiamos "aprender hacer" a "**a aprender**" para usar la estructura correcta del infinitivo "to learn **to**."
>
> 4. "**platos tradicionales de culturas diferentes**" - Cambiamos "platos tradicionales de **diferentes culturas**" para que la descripción sea más clara.
>
> 5. "**sugerió que probamos hacer**" - Cambiamos "sugerió que probamos hacer" a "**sugirió que intentáramos**" para usar el subjuntivo y expresar una sugerencia.
>
> 6. "**picante plato de México**" - Cambiamos "picante plato de México" a "**plato picante mexicano**" para que la descripción > sea más natural.
>
> 7. "**favoritas recetas de familia**" - Cambiamos "favoritas recetas de familia" a "**recetas familiares favoritas**" para que el orden de las palabras sea correcto.
>
> 8. "**nuestro niñez**" - Cambiamos "nuestro niñez" a "**nuestra infancia**" para usar el sustantivo correcto.
>
> 9. "**estamos planeando**" - Cambiamos "planeamos" a "**estamos planeando**" para expresar una acción en progreso.
>
> 10. "**a una reserva natural cerca**" - Cambiamos "a una reserva natural **cerca**" para expresar la cercanía.
>
> 11. "**disfrutar la belleza del aire libre**" - Agregamos "**de**" antes de "**la belleza**" para indicar "enjoy the beauty **of** the outdoors."
>
> ¡Sigue practicando y mejorando tus habilidades en español! Si tienes más textos para traducir o preguntas, no dudes en decírmelo. Estoy aquí para ayudarte.

## Conclusion

I've been using this approach for a few weeks and overall I've been impressed by the replies it generates. I've checked a couple of the translations with my actual Spanish tutor and she agreed with 99% of the corrections.

There a few issues to note however:

- It's inconsitent in its own corrections. In the corrected text it gives: _"una reserva natural **cercana**"_ yet in the explanations it gives _"a una reserva natural **cerca**"_ which is the same as what I wrote!

- It highlights/corrects things without changing them. In its explanation it halluciantes reasons for the "correction". This didn't occur in the example I provided, but it's by far the most annoying mistake it makes.

- It still explains typos, despite being told not to. For instance, it highlighted and explained the mispelling (_amisgos_)

Despite this I still think it's a great way to practice my vocabulary in written form. Translating 4-5 sentences each morning has been a fun exercise, in addition to the rest of my practice routine.

I am still experimenting with the prompts, and with the recent addition of Custom Instructions I may not need to copy+paste the prompts each time.
