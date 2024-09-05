#PD-risset

##Risset eternal accelerando
Jean-Claude Risset described an auditory illusion known as the "eternal accelerando", where, similar to Shepard tones in pitch, a rhythm can be structured and played back in a way that creates the perception of constant acceleration.

https://en.wikipedia.org/wiki/Jean-Claude_Risset#cite_note-5

https://pubs.aip.org/asa/jasa/article-abstract/80/3/961/680513/Pitch-and-rhythm-paradoxes-Comments-on-Auditory?redirectedFrom=fulltext

In his 2011 paper "Scheduling and composing with Risset eternal accelerando rhythms", Dan Stowell provided a solution for implementing eternal accelerandos on (rhythmic) audio samples.

https://www.semanticscholar.org/paper/Scheduling-and-composing-with-Risset-eternal-Stowell/df6a5bf9566d609b120fe06cd7c2541f6aea453c).

##Implementation for Pure Data
Risset Sampler is an implementation of the described eternal accelerando following Stowell's solution in Pure Data.

In risset_sampler.pd, play back rates and depending amplitude powers for 5 different streams are calculated using Stowell's formulas (2) and (3) - see pd sampleplayer sub patch. These streams are set up to play back the same drum loop sample to generate the eternal accelerando effect.

Observations, open issues and questions:
1. There is an uncertainty concerning the unit of parameter "b" (bandwidth of octaves). The observation is, that for the test audio samples, values < 1 work best to achieve the required auditory effect, there also seems to be a sweet spot around the value of 0.15 for the sample provided in this repository.
2. The duration of the metabar τ is currently calculated by multiplying the sample duration T by a factor > 1. Doubling the amount of bars in a given (fixed 4/4 * 2 bars length) test audio sample seem to yield the most convincing results. There's more clarification needed whether τ = T * 4 can be generalized.
3. Depending on "b", amplitude powers seem to become erratic in such way that values generated on (lower) streams are glued to 0.841 (due to the +/- π clipping and following calculations in p(r)). The general question regards the intended flexibility of the parameters (or whether they need to be determined/ fixed depending on the source sample).
