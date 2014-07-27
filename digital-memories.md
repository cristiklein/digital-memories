Principles
==========

We rely only on metadata to organise digital memories. Preferred formats are XMP, then EXIF. The following attributes are used:

1. `exif:DateTimeOriginal` to uniquely identify and sort the memory files;
2. `exif:SubSecTimeOriginal` to discriminate memory files, in case they were taken the very same second;
3. `exif:MakerNotes:SequenceNumber` to discriminate memory files, in case the previous is attribute unavailable (note that this is a proprietary attribute);
4. `xmp:label` to assign a memory file to a user-collection;
5. `xmp:DerivedFrom` to store the old full filename of the digital memory.

Commands
========

Commands useful to process digital memory files:

Audio
-----

* Convert "old" audios:
        
        for f in *.wav; do avconv -i "$f" -strict experimental "`basename "$f" .wav`.m4a"; done

Photo
-----

* Stitching Panoramas: `hugin`
* HDR rendering: `hugin_hdrmerge`
* Physically rotate: `exiftran -ai *.jpg`

Video
-----

* Convert "old" videos:
        
        for f in *.avi; do avconv -i "$f" -strict experimental -preset medium -ar 44100 "`basename "$f" .avi`.mp4"; done
		
  (`-ar 44100` is required because the audio codec requires a minimum sampling rate)

* Convert and rotate right "old" videos:
        
        for f in *.avi; do avconv -i "$f" -strict experimental -preset medium -ar 44100 -vf transpose=1 "`basename "$f" .avi`.mp4"; done

* Change container format:
        
        for f in *.avi; do avconv -i "$f" -c:v copy -c:a copy "`basename "$f" .avi`.mp4"; done

All
---

* Add labels: `exiftool -xmp:label="My label" *.jpg`
* Add title:
        
        for f in *.mp4; do exiftool "-xmp:title=`basename "$f" .mp4`" "$f"; done
		
* Add full filename as metadata:
        
        exiftool -r -overwrite_original '-DerivedFromFilePath<$directory/$filename' .
		
* Add one second to file:
		
        exiftool -alldates+="0:0:1" "filename.jpg"
        

