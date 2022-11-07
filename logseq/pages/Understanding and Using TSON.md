- TSON is designed to hold [Tuning Systems](((62911960-76e1-4cb8-81a7-ee92fc8019b8))), [Spectra](((6291b083-cb55-4961-8a93-e977afd6dc98))), and [Sets](((6291b0c2-024a-45e7-86dc-4d149993c94e)))
  id:: 636856ee-ac51-4ebf-ad27-81aab0759717
  
  At the top level, TSON is just arrays of each.
- ### Tuning Systems and Scales
  collapsed:: true
	- In TSON, tuning systems are made of [scales](((629122d9-4089-4ca0-80af-bf8540b22d82))), and scales are made of [notes](((62918617-11a6-4911-abd6-d068605aaa73))).
	  id:: 17e6ebb8-5570-4191-b7e4-06f9f5e616a9
	- Scales are functional and generative in the sense that notes are defined in relation to a [root](((62919617-9d52-416c-be4f-c72edbbbda0f))), and a [reference frequency](((62919254-679c-4edd-aacc-105fc45c85b2))) is used to generate real frequency values for all of the notes.
		- *Example*
		  collapsed:: true
			- ```yaml
			  Tuning System
			    - scales
			      - reference frequency: 100 hz
			        notes
			          - 1			# 100 hz
			          - 1.3		# 130 hz
			          - 1.5		# 150 hz
			          - 1.75		# 175 hz
			  ```
	- If using multiple scales in a tuning system, the scales can overlap so that their notes are interlaced.
		- *Example*
		  collapsed:: true
			- ```yaml
			  Tuning System
			    - scales
			      - reference frequency: 100 hz
			        notes
			          - 1			# 100 hz
			          - 1.5		# 150 hz
			          - 1.75		# 175 hz
			  
			      - reference frequency: 80 hz
			        notes
			          - 1 		# 80 hz
			          - 1.5		# 120 hz
			          - 2			# 160 hz
			          - 2.5		# 200 hz
			  ```
- ### Scale Parameters
  collapsed:: true
	- Scales can be made to repeat at a given ratio to the [root](((62919617-9d52-416c-be4f-c72edbbbda0f))) - the [repeat ratio](((6291924c-5500-456e-9cca-6a138f6e16c6))) then becomes the new root. This happens in both directions along the frequency spectrum - both increasing and decreasing in pitch.
		- *Example*
		  collapsed:: true
			- ```yaml
			  Tuning System
			    - scales
			      - reference frequency: 100 hz
			        repeat ratio: 2
			        notes
			          - 1			# ... 50 hz, 100 hz, 200 hz, 400 hz ...
			          - 1.5		# ... 75 hz, 150 hz, 300 hz, 600 hz ...
			          - 1.75		# ... 87.5 hz, 175 hz, 350 hz, 700 hz ...
			  ```
	- By providing [minimum](((6296c474-695c-450e-9ecb-d0c2fac4ad30))) and [maximum](((6291bc28-1b8c-4517-b0b8-d8a6d001ce91))) frequencies for a scale, you can limit the frequency range that notes will be generated for. This way, you can prevent overlapping scales.
		- *Example*
		  collapsed:: true
			- ```yaml
			  Tuning System
			    - scales
			      - reference: 100 hz
			        min: 300 hz
			        repeat: 2.0
			        notes
			          - 1.0		# 400 hz, 800 hz, 1600 hz, 3200 hz ...
			          - 1.5		# 300 hz, 600 hz, 1200 hz, 2400 hz ...
			          - 1.75		# 350 hz, 700 hz, 1400 hz, 2800 hz ...
			      - reference: 80
			        max: 300
			        repeat: 2.5
			        notes
			          - 1			# ... 32 hz, 80 hz, 200 hz
			          - 1.5		# ... 48 hz, 120 hz, 300 hz
			          - 2			# ... 64 hz, 160 hz
			  ```
	- If a repeat ratio is provided but min/max values are not, the scale could be repeated to cover any frequency range (whether toward $$\infty$$, the infinite regression of the asymptote at $$0$$, or both).
	- If a [note](((62919243-8c47-4050-b49c-ca654d73e36b))) is not provided in the reference object, the reference frequency will be set to the scale's root (ie, ratio `1.0`) that note [frequency ratios](((62918b58-f893-48c9-b530-4102f7f3c173))) are based on.
	  id:: 410b981c-9936-40f4-938b-c2efebb12c06
		- *Warning:* If a note with a frequency ratio of `1` is not defined, then a note will not exist there, nor at repeat intervals. If a reference note isn't defined either, then the scale's notes will be centered around a root and reference pitch that doesn't exist as a note.
		  
		  This may be desirable for some tunings, but many tunings will need a note with a frequency ratio of  `1`.
	- An optional [spectrum](((62f2aa52-4de4-4e95-8e5a-a90fa4f99e4e))) parameter can be provided as well, which must reference the ID of a spectrum that's defined in the `spectra` array.
		- This is intended to enable different scales within the same tuning system to be used with different spectra, enabling multi-scale as well as multi-spectra tuning systems.
- ### Notes
  collapsed:: true
	- The only requirement for a note is a [frequency ratio](((62918b58-f893-48c9-b530-4102f7f3c173))), which can be defined using either a number (integer or float) or a valid [expression](((629146bc-6e1e-4a00-b2a0-5c205cfb23c6))) that resolves to a real number greater than zero.
	  id:: c5c4a7b2-3770-4bb3-8838-de1cc5f4d862
	- While it's probably desirable for notes to be sorted by frequency ratio, it's not a requirement. Software that implements TSON (such as the [[TSONify]] SDKs) will sort the notes when needed.
	- While note names are optional, they're required for using a specific note as a scale's [reference note](((62919243-8c47-4050-b49c-ca654d73e36b))).
	  id:: 2145325a-8257-46f3-9c23-422d9c4ba285
		- If a note doesn't need a note name, you can just supply a number or expression strings as entries in the notes array, rather than objects.
		- Because TSON is written in YAML (a superset of JSON), you can even use bracket notation!
	- *Example*
	  collapsed:: true
		- ```yaml
		  # The two scales below are the same
		  #
		  # This is a valid, if minimal, TSON file
		  
		  Tuning Systems
		    - scales
		        - notes: [ 1, 1.5^(1/4), 1.5^(2/4), 1.5^(3/4) ]
		          reference frequency: 100
		        - notes
		            - ratio: 1.5^(1/4)
		              name: B
		            - 1.5^(3/4)
		            - 1
		            - 1.5^(2/4)
		          reference frequency: 100
		  ```
- ### Spectra and Partial Distributions
  collapsed:: true
	- [Spectra](((62f2aa52-4de4-4e95-8e5a-a90fa4f99e4e))) are used to store various information that can be used to recreate a sound or tone. This could be an instrument tone or virtually any sound.
	  {{embed ((62f3497b-755b-44c8-8a08-30d90eef5453))}}
	- Techniques such as additive synthesis or spectral modelling synthesis can be used with this data to recreate the sound described by this data.
	- {{embed ((62f3497b-5de1-4bd2-9d5c-2185c8957281))}}
	- Partial distributions store information about various partials (aka overtones) that comprise a sound. Typically, they are used to store the most prominent partials in a sound, but there isn't a limit to the number of partial that can be stored.
	- Partials are represented by a [frequency ratio](((62918b58-f893-48c9-b530-4102f7f3c173))) (similar to the frequency ratios of notes) and an [amplitude weight](((63111de0-f636-40c4-8c5f-da2c9164619b))) (similar to the frequency ratios of notes).
		- Amplitude weights define the relative power of a partial, compared to the other partials in the distribution. Ie, given two partials, the partial with the larger value for its amplitude weight will be louder than the partial with a smaller amplitude.
		- Typically, the amplitude weights in a partial distribution will be normalized so that they sum to `1.0`. Thus, amplitude weights determine how each partial will comprise the sound's overall loudness when combined.
		- Amplitude weights do not, however, determine the overall loudness of the sound. A partial distribution with a given set of amplitude weights can be used to represent very quiet as well as very loud sounds. The relative loudness between partials would be consistent, though.