- *TSON* (Tuning-Spectrum Object Notation) is a YAML-based file format for storing musical tuning and timbre/spectrum data
	- ### Why another microtonal file standard?
	  collapsed:: true
		- [Valid question.](https://xkcd.com/927/)
		- Existing formats aren't equipped for modern xenharmonic/microtonal compositional frameworks and software practices...
		  collapsed:: true
			- Some sacrifice portability and manipulability for readability (SCL, TUN), while others are environment-specific or unreadable (MTS)
			- Each comes some combination of limitations...
			  collapsed:: true
				- No reference frequencies
				- No pseudo-octaves/repetition ratios
				- No more than 12 notes per octave
				- Limits on how "detuned" a note can be
				- Not extensible
			- No standardizations or commonly used data structures exist for timbre/spectrum data or for pairing tunings and timbres
			- Most only allow notes to be defined in cents or just intonation ratios - reinforcing the dominance of 12-edo and harmonic timbres in music theory, research, audio tech, and musical communication
		- TSON aims to address their shortcomings in a number of ways...
		  collapsed:: true
			- Readable without sacrificing portability and manipulability - YAML is readable and backwards-compatible with JSON... which is supported pretty much everywhere now
			- Compatible with existing tuning formats, yet extensible
			- Pitch ratios can be defined via either floats or expressions, preserving support for JI notation and cents, via `2^(cents / 1200)`
			- Unrecognized parameters won't break TSON interpretation, they'll just be ignored if not implemented
			- Able to contain timbre/spectrum data, multiple tunings and timbres per file, plus tuning-timbre groupings and sequences
			- *Planned*: Instrument data (e.g. key layouts) and further timbre data structures (dynamic/reactive timbres, waveforms, and more)
		- Also, TSON is intended to be a focal point for an set of useful microtonal software...
		  collapsed:: true
			- *Coming Soon!*: [[TSONify]] - open-source packages/libraries for multiple languages with useful features for working with TSON data (and hopefully aiding its adoption)
			  collapsed:: true
				- Conversion between TSON and existing microtonal formats
				- TSON data validation
				- Support for the use of variables in expressions for dynamic tunings, timbres, and instrument models
				- Multi-file aggregation and linking for timbre/tuning pairings and sequences
				- Integration with TonalHub for fetching and updating data hosted in TonalHub instances
				- Tools for including TSON support in your own software
				- And more...
			- *Coming Soon!*: [[TonalHub]] - open-source, self-hostable web app for archiving and working with tuning, timbre, and instrument models
			  collapsed:: true
				- API and UI for archiving, fetching, and manipulating TSON data
				- TSON data model versioning
				- Tools for analyzing and developing tunings and timbres
				- And more...
- ## Specification
	- Coming Soon
- ## Include TSON Support in Your Own Software
  collapsed:: true
	- Coming Soon
- ## Get Involved
  collapsed:: true
	- Coming Soon