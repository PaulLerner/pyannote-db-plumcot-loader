:warning: Work in progress :warning:  

Should work with `pyannote.database` `custom` branch

# pyannote.db.plumcot loader

Please refer to [pyannote.db.plumcot](https://github.com/PaulLerner/pyannote-db-plumcot/) for complete documentation.

Usage :

```python
from pyannote.database import get_protocol 

protocol=get_protocol('TheOffice.SpeakerDiarization.0') 
first_file = next(protocol.test())

# if you properly setup database.yml
transcription_doc = first_file['transcription']
entity_doc = first_file['entity']

# else...
from plumcot_loader.loader import AlignedLoader
from plumcot_loader.loader import CsvLoader
entity="/path/to/pyannote-db-plumcot/Plumcot/data/TheOffice/annotated_transcripts/merge_{uri}.csv".format(uri=first_file['uri'])
transcription= "/path/to/pyannote-db-plumcot/Plumcot/data/TheOffice/forced-alignment/{uri}.aligned".format(uri=first_file['uri'])
alignedLoader=AlignedLoader(transcription)
transcription_doc=alignedLoader(first_file)
first_file['transcription']=transcription_doc
csvLoader=CsvLoader(entity)
entity_doc=csvLoader(first_file)
```
