- ***TSON*** (Tuning-Spectrum Object Notation) is a YAML-based data format for describing musical tuning and sound spectrum information.
	-
	- #### Why another tuning file/data standard?
	  collapsed:: true
		- [Valid question.](((629168a2-5251-438a-983c-1c1a993aeaeb)))
		- Existing formats have too many limitations for modern software and microtonal practices...
		  collapsed:: true
			- Some sacrifice portability and manipulability for readability (SCL, TUN), while others are environment-specific or unreadable (MTS)
			- Each comes with some combination of limitations...
				- No reference frequencies
				- No pseudo-octaves/repetition ratios
				- No more than 12 notes per octave
				- Limits on how "detuned" a note can be
				- Not extensible
			- No standardizations or commonly used data structures exist for timbre/spectrum data or for pairing tunings and timbres
			- Most only allow notes to be defined in cents or just intonation ratios - reinforcing the dominance of 12-edo and harmonic timbres in music theory, research, and tech
		- TSON aims to address their shortcomings in a number of ways...
		  collapsed:: true
			- Readable without sacrificing portability and manipulability - YAML is readable and backwards-compatible with JSON... which is supported pretty much everywhere now
			- Compatible with existing tuning formats, yet extensible
			- Pitch ratios can be defined via numbers or expressions, preserving support for JI notation as well as cents, via `2^(cents / 1200)`
			- Unrecognized parameters won't break TSON interpretation, they'll just be ignored if not implemented
			- Able to contain timbre/spectrum data, multiple tunings and timbres per file, plus tuning-timbre pairings and sets
			- *Planned*: Instrument data (e.g. key layouts) and further timbre data structures (dynamic/reactive timbres, waveforms, and more)
		- Also, TSON is intended to be a focal point for an set of useful microtonal software...
		  collapsed:: true
			- *Coming Soon!*: [[TSONify]] - open-source packages/libraries for multiple languages with useful features for manipulating TSON data and supporting TSON in audio software
				- Conversion between TSON and existing microtonal formats
				- TSON data validation
				- Support for the use of variables in expressions for dynamic tunings, timbres, and instrument models
				- Multi-file aggregation and linking for timbre/tuning pairings and sequences
				- Integration with TonalHub for fetching and updating data hosted in TonalHub instances
				- Tools for including TSON support in your own software
				- And more...
			- *Coming Soon!*: [[TonalHub]] - open-source, self-hostable web app & API for archiving and creating tuning, spectrum, and instrument models
			  collapsed:: true
				- API and UI for archiving, fetching, and manipulating TSON data
				- TSON data model versioning
				- Tools for analyzing and developing tunings and timbres
				- And more...
- *Heads up:* TSON uses a number of terms that you might be unfamiliar with, or may have used differently in other contexts. Check out the [glossary]([[TSON Glossary]]) to see how they're used here!
- ## [Specification]([[TSON Specification]])
- ## [[Understanding and Using TSON]]
- ## Include TSON Support in Your Own Software
  collapsed:: true
	- Coming Soon (once [specifications]([[TSON Specification]]) and [[TSONify]] are further developed)