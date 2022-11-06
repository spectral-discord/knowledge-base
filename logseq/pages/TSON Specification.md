{{embed ((3ac6d6f3-0cb8-4b0e-95b2-869c6cf69d12)) }}
| Key | Alternatives | Type | Examples |
|-|-|-|-|
| tuning systems | tunings | Array <Object> | See the [tuning systems specification](((62911960-76e1-4cb8-81a7-ee92fc8019b8))) |
| spectra | | Array <Object> | See the [spectra specification](((6291b083-cb55-4961-8a93-e977afd6dc98))) |
| sets | | Array <Object> | See the [sets specification](((6291b0c2-024a-45e7-86dc-4d149993c94e))) |
- ## Tuning Systems
    id:: 62911960-76e1-4cb8-81a7-ee92fc8019b8
    collapsed:: true
    - {{embed ((13fe4f0a-b40a-4b39-aad0-392b0e75d2e1))}}
        | Key | Type | Examples |
        |-|-|-|
        | name | String | `Slendro`, `5-limit`, `My Tuning` |
        | description | String | `A description might be nice to add` |
        | id | String | `1`, `My Tuning`, `63113f49-888a-4948-b896-b7448242a854` |
        | scales | Array <Object> | See the [scales specification](((629122d9-4089-4ca0-80af-bf8540b22d82))) |
        An `id` must be defined, and it must be a unique value that isn't used by any other tuning systems.
        
        The only other required parameters are the [reference](((632cd327-c00a-41e2-9a4c-e99fb6fde7c9))) object and the [notes](((62918617-11a6-4911-abd6-d068605aaa73))) array.
    - ## Scales
        id:: 629122d9-4089-4ca0-80af-bf8540b22d82
        collapsed:: true
        - {{embed ((6296869a-0c5b-487b-af9c-dfca96eacf1d))}} 
            The only required parameter is `notes`.
            | Key | Alternatives | Type | Examples |
            |-|-|-|-|
            | reference | | Object | See the [reference specification](((632cd327-c00a-41e2-9a4c-e99fb6fde7c9))) |
            | [repeat ratio](((6291924c-5500-456e-9cca-6a138f6e16c6))) | repeat | [Expression](((629146bc-6e1e-4a00-b2a0-5c205cfb23c6))), Number | `3^(7/3)`, `2.1` |
            | [max frequency](((6291bc28-1b8c-4517-b0b8-d8a6d001ce91))) | max, maximum | String, Number | `666 Hz`, `20000` |
            | [min frequency](((6296c474-695c-450e-9ecb-d0c2fac4ad30))) | min, minimum | String, Number | `66.6 Hz`, `20.0` |
            | notes | | Array<[Expression](((629146bc-6e1e-4a00-b2a0-5c205cfb23c6))), Object> | See the [notes specification](((62918617-11a6-4911-abd6-d068605aaa73))) |
            | [spectrum](((62f2aa52-4de4-4e95-8e5a-a90fa4f99e4e))) | | String | `7`, `My Spectrum` |
    - ## Reference
        id:: 632cd327-c00a-41e2-9a4c-e99fb6fde7c9
        collapsed:: true
        - Because the scale's notes are defined as ratios relative to a [root](((62919617-9d52-416c-be4f-c72edbbbda0f))), a [reference frequency](((62919254-679c-4edd-aacc-105fc45c85b2))) is used to map real frequency values onto each of the notes.
            
            See the ((9ca5419f-19dc-4ba9-a131-4b3891639697)) section for more info and examples!
            | Key | Type | Examples |
            |-|-|-|-|
            | [frequency](((62918b58-f893-48c9-b530-4102f7f3c173))) | String, Number | `440 Hz`, `500` |
            | [note](((62919243-8c47-4050-b49c-ca654d73e36b))) | String | `A#`, `Dax`, `7` |
            {{embed ((4899ac1f-4ff7-4a70-815f-19fcac761588))}}
    - ## Notes
        id:: 62918617-11a6-4911-abd6-d068605aaa73
        collapsed:: true
        - {{embed ((6291c175-343a-4c3b-9fc7-f20c479ddbef))}} 
            | Key | Alternatives | Type | Examples |
            |-|-|-|-|
            | [frequency ratio](((62918b58-f893-48c9-b530-4102f7f3c173))) | ratio | [Expression](((629146bc-6e1e-4a00-b2a0-5c205cfb23c6))) | `1.557`, `3^(1.3/13)` |
            | name | | String | `A#`, `Dax`, `7` |
            {{embed ((fe32a44a-6de1-4888-8d38-f33ba4a3187f))}}
- ## Spectra
    id:: 6291b083-cb55-4961-8a93-e977afd6dc98
    collapsed:: true
    - {{embed ((62f3497b-ac78-49d3-8971-12db0df8a53c))}}
        | Key | Alternatives | Type | Examples |
        |-|-|-|-|
        | name | | String | `Violin`, `Inharmonic #3` |
        | description | | String | `Some description` |
        | id | | String | `1`, `My Spectrum` |
        | partial distribution | partials | Array <Object> | See the [partials specification](((6324f256-bc97-443f-8c73-e16ece6d82f7))) |
        An `id` must be defined, and it must be a unique value that isn't used by any other spectra.
    - ## Partial Distribution
        id:: 6324f256-bc97-443f-8c73-e16ece6d82f7
        collapsed:: true
        - The **partials** array contains the spectrum's [partial distribution](((629bee65-cf76-4a03-a0e9-4862024c7d4e))).
            
            Each partial is represented by an object containing a [frequency ratio](((62918b58-f893-48c9-b530-4102f7f3c173))) and an [amplitude weight](((63111de0-f636-40c4-8c5f-da2c9164619b))).
            | Key | Alternatives | Type |
            |-|-|-|
            | frequency ratio | ratio | [Expression](((629146bc-6e1e-4a00-b2a0-5c205cfb23c6))) |
            | amplitude weight | weight | [Expression](((629146bc-6e1e-4a00-b2a0-5c205cfb23c6))) |
- ## Sets
    id:: 6291b0c2-024a-45e7-86dc-4d149993c94e
    collapsed:: true
    - {{embed ((63113e04-b1ed-4f89-b615-b012672760d2))}}
        | Key | Type | Examples |
        |-|-|-|-|
        | id | String | `7`,  `My Set`, `63113f49-888a-4948-b896-b7448242a854`|
        | name | String | `Composition 5` |
        | description | String | `Some description` |
        | members | Array <Object> | See the [set members specification](((63113f49-888a-4948-b896-b7448242a854))) |
        An `id` must be defined, and it must be a unique value that isn't used by any other sets.
    - ## Set Members
        id:: 63113f49-888a-4948-b896-b7448242a854
        collapsed:: true
        - Set members can reference a tuning system, a spectrum, or both.
            
            If both are defined, you can also provide a boolean, `override scale spectra`, which determines whether the spectrum defined in the set member should be used instead of any spectra that are declared in the tuning's scales.
            
            To include a spectrum or tuning in a set, the tuning or spectra must be defined in their respective arrays, and you must reference its `id` parameter, which must be a unique value.
            
            | Key | Alternatives | Type | Examples |
            |-|-|-|-|
            | tuning system | tuning | String | `1`, `My Special Tuning` |
            | spectrum | | String | `1`, `My Special Spectrum` |
            | override scale spectra | | Boolean | `true`, `false` |
- ## Example TSONs
    collapsed:: true
    - ```yaml
        Tuning Systems
        - name: 12edo
            scales
            - reference frequency: 440 hz
                repeat ratio: 2.0
                notes
                - frequency ratio: 1
                    name: A
                - ratio: 2^(1/12)
                    name: [ A#, Bb ]
                # etc...
        - name: JI - BP-edo
            scales
            - reference: 440
                repeat: 2
                max frequency: 880 hz
                notes
                - ratio: 3/2
                    name: ref
                - [ 4/3, 5/3 ]
                # etc...
            - reference: 880
                repeat: 3
                min: 880
                notes
                - 3^(1/13)
                # etc...
        
        Spectra
        - name: harmonic
            overtones
            - frequency ratio: 1
                amplitude weight: 1
            - ratio: 2
                weight: 1/2
            # etc...
            # TBD
            # - noise profile
        
        Instruments
        # TBD
        
        Sets
        # TBD
        ```