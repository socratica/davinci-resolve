# DaVinci Resolve Scripting API Documentation

## Resolve Class

### Methods

```python
Fusion() ⟶ Fusion
# Returns the Fusion object. Starting point for Fusion scripts.

GetMediaStorage() ⟶ MediaStorage
# Returns the media storage object to query and act on media locations.

GetProjectManager() ⟶ ProjectManager
# Returns the project manager object for currently open database.

OpenPage(pageName) ⟶ bool
# Switches to indicated page in DaVinci Resolve.
# Input can be one of ("media", "cut", "edit", "fusion", "color", "fairlight", "deliver").

GetCurrentPage() ⟶ str
# Returns the page currently displayed in the main window.
# Returned value can be one of ("media", "cut", "edit", "fusion", "color", "fairlight", "deliver", None).

GetProductName() ⟶ str
# Returns product name.

GetVersion() ⟶ list
# Returns list of product version fields in [major, minor, patch, build, suffix] format.

GetVersionString() ⟶ str
# Returns product version in "major.minor.patch[suffix].build" format.

LoadLayoutPreset(presetName) ⟶ bool
# Loads UI layout from saved preset named 'presetName'.

UpdateLayoutPreset(presetName) ⟶ bool
# Overwrites preset named 'presetName' with current UI layout.

ExportLayoutPreset(presetName, presetFilePath) ⟶ bool
# Exports preset named 'presetName' to path 'presetFilePath'.

DeleteLayoutPreset(presetName) ⟶ bool
# Deletes preset named 'presetName'.

SaveLayoutPreset(presetName) ⟶ bool
# Saves current UI layout as a preset named 'presetName'.

ImportLayoutPreset(presetFilePath, presetName=None) ⟶ bool
# Imports preset from path 'presetFilePath'.
# The optional argument 'presetName' specifies how the preset shall be named.
# If not specified, the preset is named based on the filename.

Quit() ⟶ None
# Quits the Resolve App.

ImportRenderPreset(presetPath) ⟶ bool
# Import a preset from presetPath (string) and set it as current preset for rendering.

ExportRenderPreset(presetName, exportPath) ⟶ bool
# Export a preset to a given path (string) if presetName(string) exists.

ImportBurnInPreset(presetPath) ⟶ bool
# Import a data burn in preset from a given presetPath (string).

ExportBurnInPreset(presetName, exportPath) ⟶ bool
# Export a data burn in preset to a given path (string) if presetName (string) exists.

GetKeyframeMode() ⟶ keyframeMode
# Returns the currently set keyframe mode (int).
# Refer to section 'Keyframe Mode information' below for details.

SetKeyframeMode(keyframeMode) ⟶ bool
# Returns True when 'keyframeMode' (enum) is successfully set.
# Refer to section 'Keyframe Mode information' below for details.
```

---

## ProjectManager Class

### Methods

```python
ArchiveProject(projectName, filePath, isArchiveSrcMedia=True, isArchiveRenderCache=True, isArchiveProxyMedia=False) ⟶ bool
# Archives project to provided file path with the configuration as provided by the optional arguments.

CreateProject(projectName) ⟶ Project
# Creates and returns a project if projectName (string) is unique, and None if it is not.

DeleteProject(projectName) ⟶ bool
# Deletes the project in the current folder if not currently loaded.

LoadProject(projectName) ⟶ Project
# Loads and returns the project with name = projectName (string) if there is a match found, and None if there is no matching project.

GetCurrentProject() ⟶ Project
# Returns the currently loaded Resolve project.

SaveProject() ⟶ bool
# Saves the currently loaded project with its own name. Returns True if successful.

CloseProject(project) ⟶ bool
# Closes the specified project without saving.

CreateFolder(folderName) ⟶ bool
# Creates a folder if folderName (string) is unique.

DeleteFolder(folderName) ⟶ bool
# Deletes the specified folder if it exists. Returns True in case of success.

GetProjectListInCurrentFolder() ⟶ list
# Returns a list of project names in the current folder.

GetFolderListInCurrentFolder() ⟶ list
# Returns a list of folder names in the current folder.

GotoRootFolder() ⟶ bool
# Opens the root folder in the database.

GotoParentFolder() ⟶ bool
# Opens the parent folder of the current folder in the database if the current folder has a parent.

GetCurrentFolder() ⟶ str
# Returns the current folder name.

OpenFolder(folderName) ⟶ bool
# Opens the folder under the given name.

ImportProject(filePath, projectName=None) ⟶ bool
# Imports a project from the file path provided with the given project name, if any. Returns True if successful.

ExportProject(projectName, filePath, withStillsAndLUTs=True) ⟶ bool
# Exports the project to the provided file path, including stills and LUTs if withStillsAndLUTs is True (enabled by default). Returns True in case of success.

RestoreProject(filePath, projectName=None) ⟶ bool
# Restores a project from the file path provided with the given project name, if any. Returns True if successful.

GetCurrentDatabase() ⟶ dict
# Returns a dictionary (with keys 'DbType', 'DbName' and optional 'IpAddress') corresponding to the current database connection.

GetDatabaseList() ⟶ list
# Returns a list of dictionary items (with keys 'DbType', 'DbName' and optional 'IpAddress') corresponding to all the databases added to Resolve.

SetCurrentDatabase(dbInfo) ⟶ bool
# Switches the current database connection to the database specified by the keys below, and closes any open project.
# 'DbType': 'Disk' or 'PostgreSQL' (string)
# 'DbName': database name (string)
# 'IpAddress': IP address of the PostgreSQL server (string, optional key - defaults to '127.0.0.1')

CreateCloudProject(cloudSettings) ⟶ Project
# Creates and returns a cloud project.
# 'cloudSettings': Check 'Cloud Projects Settings' subsection below for more information.

ImportCloudProject(filePath, cloudSettings) ⟶ bool
# Returns True if importing the cloud project is successful; False otherwise.
# 'filePath': String; filePath of the file to import
# 'cloudSettings': Check 'Cloud Projects Settings' subsection below for more information.

RestoreCloudProject(folderPath, cloudSettings) ⟶ bool
# Returns True if restoring the cloud project is successful; False otherwise.
# 'folderPath': String; path of the folder to restore
# 'cloudSettings': Check 'Cloud Projects Settings' subsection below for more information.
```

---

## Project Class

### Methods

```python
GetMediaPool() ⟶ MediaPool
# Returns the Media Pool object.

GetTimelineCount() ⟶ int
# Returns the number of timelines currently present in the project.

GetTimelineByIndex(idx) ⟶ Timeline
# Returns the timeline at the given index, 1 <= idx <= project.GetTimelineCount().

GetCurrentTimeline() ⟶ Timeline
# Returns the currently loaded timeline.

SetCurrentTimeline(timeline) ⟶ bool
# Sets the given timeline as the current timeline for the project. Returns True if successful.

GetGallery() ⟶ Gallery
# Returns the Gallery object.

GetName() ⟶ str
# Returns the project name.

SetName(projectName) ⟶ bool
# Sets the project name if the given projectName (string) is unique.

GetPresetList() ⟶ list
# Returns a list of presets and their information.

SetPreset(presetName) ⟶ bool
# Sets the preset by the given presetName (string) into the project.

AddRenderJob() ⟶ str
# Adds a render job based on current render settings to the render queue. Returns a unique job id (string) for the new render job.

DeleteRenderJob(jobId) ⟶ bool
# Deletes the render job for the input job id (string).

DeleteAllRenderJobs() ⟶ bool
# Deletes all render jobs in the queue.

GetRenderJobList() ⟶ list
# Returns a list of render jobs and their information.

GetRenderPresetList() ⟶ list
# Returns a list of render presets and their information.

StartRendering(jobId1, jobId2, ...) ⟶ bool
# Starts rendering jobs indicated by the input job ids.

StartRendering([jobIds...], isInteractiveMode=False) ⟶ bool
# Starts rendering jobs indicated by the input job ids.
# The optional "isInteractiveMode", when set, enables error feedback in the UI during rendering.

StartRendering(isInteractiveMode=False) ⟶ bool
# Starts rendering all queued render jobs.
# The optional "isInteractiveMode", when set, enables error feedback in the UI during rendering.

StopRendering() ⟶ None
# Stops any current render processes.

IsRenderingInProgress() ⟶ bool
# Returns True if rendering is in progress.

LoadRenderPreset(presetName) ⟶ bool
# Sets a preset as the current preset for rendering if presetName (string) exists.

SaveAsNewRenderPreset(presetName) ⟶ bool
# Creates a new render preset by the given name if presetName (string) is unique.

SetRenderSettings(settings) ⟶ bool
# Sets the given settings for rendering. Settings is a dict, with support for the keys:
# Refer to "Looking up render settings" section for information for supported settings.

GetRenderJobStatus(jobId) ⟶ dict
# Returns a dict with job status and completion percentage of the job by the given jobId (string).

GetSetting(settingName) ⟶ str
# Returns the value of the project setting (indicated by settingName, string). Check the section below for more information.

SetSetting(settingName, settingValue) ⟶ bool
# Sets the project setting (indicated by settingName, string) to the value (settingValue, string). Check the section below for more information.

GetRenderFormats() ⟶ dict
# Returns a dict (format -> file extension) of available render formats.

GetRenderCodecs(renderFormat) ⟶ dict
# Returns a dict (codec description -> codec name) of available codecs for the given render format (string).

GetCurrentRenderFormatAndCodec() ⟶ dict
# Returns a dict with the currently selected format 'format' and render codec 'codec'.

SetCurrentRenderFormatAndCodec(format, codec) ⟶ bool
# Sets the given render format (string) and render codec (string) as options for rendering.

GetCurrentRenderMode() ⟶ int
# Returns the render mode: 0 - Individual clips, 1 - Single clip.

SetCurrentRenderMode(renderMode) ⟶ bool
# Sets the render mode. Specify renderMode = 0 for Individual clips, 1 for Single clip.

GetRenderResolutions(format, codec) ⟶ list
# Returns a list of resolutions applicable for the given render format (string) and render codec (string).
# Returns a full list of resolutions if no argument is provided.
# Each element in the list is a dictionary with 2 keys "Width" and "Height".

RefreshLUTList() ⟶ bool
# Refreshes LUT List.

GetUniqueId() ⟶ str
# Returns a unique ID for the project item.

InsertAudioToCurrentTrackAtPlayhead(mediaPath, startOffsetInSamples, durationInSamples) ⟶ bool
# Inserts the media specified by mediaPath (string) with startOffsetInSamples (int) and durationInSamples (int) at the playhead on a selected track on the Fairlight page.
# Returns True if successful, otherwise False.

LoadBurnInPreset(presetName) ⟶ bool
# Loads user-defined data burn in preset for the project when supplied presetName (string). Returns True if successful.

ExportCurrentFrameAsStill(filePath) ⟶ bool
# Exports the current frame as still to the supplied filePath. filePath must end in a valid export file format.
# Returns True if successful, otherwise False.

GetColorGroupsList() ⟶ list
# Returns a list of all group objects in the timeline.

AddColorGroup(groupName) ⟶ ColorGroup
# Creates a new ColorGroup. groupName must be a unique string.

DeleteColorGroup(colorGroup) ⟶ bool
# Deletes the given color group and sets clips to ungrouped.
```

## MediaStorage Class

### Methods

```python
GetMountedVolumeList() ⟶ list
# Returns a list of folder paths corresponding to mounted volumes displayed in Resolve’s Media Storage.

GetSubFolderList(folderPath) ⟶ list
# Returns a list of folder paths in the given absolute folder path.

GetFileList(folderPath) ⟶ list
# Returns a list of media and file listings in the given absolute folder path.
# Note that media listings may be logically consolidated entries.

RevealInStorage(path) ⟶ bool
# Expands and displays the given file/folder path in Resolve’s Media Storage.

AddItemListToMediaPool(item1, item2, ...) ⟶ list
# Adds specified file/folder paths from Media Storage into the current Media Pool folder.
# Input is one or more file/folder paths. Returns a list of the MediaPoolItems created.

AddItemListToMediaPool([items...]) ⟶ list
# Adds specified file/folder paths from Media Storage into the current Media Pool folder.
# Input is an array of file/folder paths. Returns a list of the MediaPoolItems created.

AddItemListToMediaPool([{itemInfo}, ...]) ⟶ list
# Adds a list of itemInfos specified as a dict of "media", "startFrame" (int), "endFrame" (int) from Media Storage into the current Media Pool folder.
# Returns a list of the MediaPoolItems created.

AddClipMattesToMediaPool(MediaPoolItem, [paths], stereoEye) ⟶ bool
# Adds specified media files as mattes for the specified MediaPoolItem.
# StereoEye is an optional argument for specifying which eye to add the matte to for stereo clips ("left" or "right").
# Returns True if successful.

AddTimelineMattesToMediaPool([paths]) ⟶ list
# Adds specified media files as timeline mattes in the current media pool folder.
# Returns a list of created MediaPoolItems.
```

## MediaPool Class

### Methods

```python
GetRootFolder() ⟶ Folder
# Returns root Folder of Media Pool.

AddSubFolder(folder, name) ⟶ Folder
# Adds a new subfolder under the specified Folder object with the given name.

RefreshFolders() ⟶ bool
# Updates the folders in collaboration mode.

CreateEmptyTimeline(name) ⟶ Timeline
# Adds a new timeline with the given name.

AppendToTimeline(clip1, clip2, ...) ⟶ list
# Appends specified MediaPoolItem objects in the current timeline.
# Returns the list of appended TimelineItems.

AppendToTimeline([clips]) ⟶ list
# Appends specified MediaPoolItem objects in the current timeline.
# Returns the list of appended TimelineItems.

AppendToTimeline([{clipInfo}, ...]) ⟶ list
# Appends a list of clipInfos specified as a dict of "mediaPoolItem", "startFrame" (int), "endFrame" (int), (optional) "mediaType" (int; 1 - Video only, 2 - Audio only), "trackIndex" (int), and "recordFrame" (int).
# Returns the list of appended TimelineItems.

CreateTimelineFromClips(name, clip1, clip2, ...) ⟶ Timeline
# Creates a new timeline with the specified name, and appends the specified MediaPoolItem objects.

CreateTimelineFromClips(name, [clips]) ⟶ Timeline
# Creates a new timeline with the specified name, and appends the specified MediaPoolItem objects.

CreateTimelineFromClips(name, [{clipInfo}]) ⟶ Timeline
# Creates a new timeline with the specified name, appending the list of clipInfos specified as a dict of "mediaPoolItem", "startFrame" (int), "endFrame" (int), "recordFrame" (int).

ImportTimelineFromFile(filePath, importOptions={}) ⟶ Timeline
# Creates a timeline based on parameters within the given file (AAF/EDL/XML/FCPXML/DRT/ADL/OTIO) and optional importOptions dict, with support for the keys:
# "timelineName": string, specifies the name of the timeline to be created. Not valid for DRT import.
# "importSourceClips": bool, specifies whether source clips should be imported, True by default. Not valid for DRT import.
# "sourceClipsPath": string, specifies a filesystem path to search for source clips if the media is inaccessible in their original path and if "importSourceClips" is True.
# "sourceClipsFolders": list of Media Pool folder objects to search for source clips if the media is not present in the current folder and if "importSourceClips" is False. Not valid for DRT import.
# "interlaceProcessing": bool, specifies whether to enable interlace processing on the imported timeline being created. Valid only for AAF import.

DeleteTimelines([timeline]) ⟶ bool
# Deletes specified timelines in the media pool.

GetCurrentFolder() ⟶ Folder
# Returns the currently selected Folder.

SetCurrentFolder(Folder) ⟶ bool
# Sets the current folder by the given Folder.

DeleteClips([clips]) ⟶ bool
# Deletes specified clips or timeline mattes in the media pool.

ImportFolderFromFile(filePath, sourceClipsPath="") ⟶ bool
# Returns True if import from the given DRB filePath is successful, False otherwise.
# sourceClipsPath is a string that specifies a filesystem path to search for source clips if the media is inaccessible in their original path, empty by default.

DeleteFolders([subfolders]) ⟶ bool
# Deletes specified subfolders in the media pool.

MoveClips([clips], targetFolder) ⟶ bool
# Moves specified clips to the target folder.

MoveFolders([folders], targetFolder) ⟶ bool
# Moves specified folders to the target folder.

GetClipMatteList(MediaPoolItem) ⟶ list
# Gets mattes for the specified MediaPoolItem, as a list of paths to the matte files.

GetTimelineMatteList(Folder) ⟶ list
# Gets mattes in the specified Folder, as a list of MediaPoolItems.

DeleteClipMattes(MediaPoolItem, [paths]) ⟶ bool
# Deletes mattes based on their file paths for the specified MediaPoolItem. Returns True on success.

RelinkClips([MediaPoolItem], folderPath) ⟶ bool
# Updates the folder location of specified media pool clips with the specified folder path.

UnlinkClips([MediaPoolItem]) ⟶ bool
# Unlinks specified media pool clips.

ImportMedia([items...]) ⟶ list
# Imports specified file/folder paths into the current Media Pool folder. Input is an array of file/folder paths.
# Returns a list of the MediaPoolItems created.

ImportMedia([{clipInfo}]) ⟶ list
# Imports file path(s) into the current Media Pool folder as specified in the list of clipInfo dict.
# Returns a list of the MediaPoolItems created.
# Each clipInfo gets imported as one MediaPoolItem unless 'Show Individual Frames' is turned on.
# Example: ImportMedia([{"FilePath":"file_%03d.dpx", "StartIndex":1, "EndIndex":100}]) would import clip "file_[001-100].dpx".

ExportMetadata(fileName, [clips]) ⟶ bool
# Exports metadata of specified clips to 'fileName' in CSV format.
# If no clips are specified, all clips from the media pool will be used.

GetUniqueId() ⟶ str
# Returns a unique ID for the media pool.

CreateStereoClip(LeftMediaPoolItem, RightMediaPoolItem) ⟶ MediaPoolItem
# Takes in two existing media pool items and creates a new 3D stereoscopic media pool entry, replacing the input media in the media pool.
```

## Folder Class

### Methods

```python
GetClipList() ⟶ list
# Returns a list of clips (items) within the folder.

GetName() ⟶ str
# Returns the media folder name.

GetSubFolderList() ⟶ list
# Returns a list of subfolders in the folder.

GetIsFolderStale() ⟶ bool
# Returns true if the folder is stale in collaboration mode, false otherwise.

GetUniqueId() ⟶ str
# Returns a unique ID for the media pool folder.

Export(filePath) ⟶ bool
# Returns true if export of DRB folder to filePath is successful, false otherwise.

TranscribeAudio() ⟶ bool
# Transcribes audio of the MediaPoolItems within the folder and nested folders.
# Returns True if successful; False otherwise.

ClearTranscription() ⟶ bool
# Clears audio transcription of the MediaPoolItems within the folder and nested folders.
# Returns True if successful; False otherwise.
```

## MediaPoolItem Class

### Methods

```python
GetName() ⟶ str
# Returns the clip name.

GetMetadata(metadataType=None) ⟶ str | dict
# Returns the metadata value for the key 'metadataType'.
# If no argument is specified, a dict of all set metadata properties is returned.

SetMetadata(metadataType, metadataValue) ⟶ bool
# Sets the given metadata to metadataValue (string). Returns True if successful.

SetMetadata(metadata) ⟶ bool
# Sets the item metadata with the specified 'metadata' dict. Returns True if successful.

GetMediaId() ⟶ str
# Returns the unique ID for the MediaPoolItem.

AddMarker(frameId, color, name, note, duration, customData) ⟶ bool
# Creates a new marker at the given frameId position with the specified marker information.
# 'customData' is optional and helps to attach user-specific data to the marker.

GetMarkers() ⟶ dict
# Returns a dict (frameId -> {information}) of all markers and dicts with their information.
# Example of output format: {96.0: {'color': 'Green', 'duration': 1.0, 'note': '', 'name': 'Marker 1', 'customData': ''}, ...}
# In the above example - there is one 'Green' marker at offset 96 (position of the marker).

GetMarkerByCustomData(customData) ⟶ dict
# Returns marker {information} for the first matching marker with the specified customData.

UpdateMarkerCustomData(frameId, customData) ⟶ bool
# Updates customData (string) for the marker at the given frameId position.
# CustomData is not exposed via UI and is useful for scripting developers to attach any user-specific data to markers.

GetMarkerCustomData(frameId) ⟶ str
# Returns the customData string for the marker at the given frameId position.

DeleteMarkersByColor(color) ⟶ bool
# Deletes all markers of the specified color from the media pool item. "All" as an argument deletes all color markers.

DeleteMarkerAtFrame(frameNum) ⟶ bool
# Deletes the marker at the specified frame number from the media pool item.

DeleteMarkerByCustomData(customData) ⟶ bool
# Deletes the first matching marker with the specified customData.

AddFlag(color) ⟶ bool
# Adds a flag with the specified color (string).

GetFlagList() ⟶ list
# Returns a list of flag colors assigned to the item.

ClearFlags(color) ⟶ bool
# Clears the flag of the specified color if one exists. An "All" argument is supported and clears all flags.

GetClipColor() ⟶ str
# Returns the item color as a string.

SetClipColor(colorName) ⟶ bool
# Sets the item color based on the colorName (string).

ClearClipColor() ⟶ bool
# Clears the item color.

GetClipProperty(propertyName=None) ⟶ str | dict
# Returns the property value for the key 'propertyName'.
# If no argument is specified, a dict of all clip properties is returned.

SetClipProperty(propertyName, propertyValue) ⟶ bool
# Sets the given property to propertyValue (string).

LinkProxyMedia(proxyMediaFilePath) ⟶ bool
# Links proxy media located at the path specified by the argument 'proxyMediaFilePath' with the current clip.
# 'proxyMediaFilePath' should be an absolute clip path.

UnlinkProxyMedia() ⟶ bool
# Unlinks any proxy media associated with the clip.

ReplaceClip(filePath) ⟶ bool
# Replaces the underlying asset and metadata of the MediaPoolItem with the specified absolute clip path.

GetUniqueId() ⟶ str
# Returns a unique ID for the media pool item.

TranscribeAudio() ⟶ bool
# Transcribes audio of the MediaPoolItem. Returns True if successful; False otherwise.

ClearTranscription() ⟶ bool
# Clears audio transcription of the MediaPoolItem. Returns True if successful; False otherwise.

GetAudioMapping() ⟶ str (json formatted)
# Returns a string with the MediaPoolItem's audio mapping information.
# Check the 'Audio Mapping' section below for more information.
```

---

## Timeline Class

### Methods

```python
GetName() ⟶ str
# Returns the timeline name.

SetName(timelineName) ⟶ bool
# Sets the timeline name if timelineName (string) is unique. Returns True if successful.

GetStartFrame() ⟶ int
# Returns the frame number at the start of the timeline.

GetEndFrame() ⟶ int
# Returns the frame number at the end of the timeline.

SetStartTimecode(timecode) ⟶ bool
# Sets the start timecode of the timeline to the string 'timecode'.
# Returns True when the change is successful, false otherwise.

GetStartTimecode() ⟶ str
# Returns the start timecode for the timeline.

GetTrackCount(trackType) ⟶ int
# Returns the number of tracks for the given track type ("audio", "video" or "subtitle").

AddTrack(trackType, subTrackType) ⟶ bool
# Adds a track of trackType ("video", "subtitle", "audio").
# Optional argument subTrackType is used for "audio" trackType.
# subTrackType can be one of {"mono", "stereo", "5.1", "5.1film", "7.1", "7.1film", "adaptive1", ... , "adaptive24"}.
# subTrackType defaults to 'mono' if skipped and track type is ‘audio’.

AddTrack(trackType, newTrackOptions) ⟶ bool
# Adds a track of trackType ("video", "subtitle", "audio").
# Optional newTrackOptions = {'audioType': same as subTrackType above, 'index': 1 <= index <= GetTrackCount(trackType)}.
# 'audioType' defaults to 'mono' if skipped and track type is ‘audio’.
# 'index' if skipped (or if value not in bounds) appends the track.

DeleteTrack(trackType, trackIndex) ⟶ bool
# Deletes a track of trackType ("video", "subtitle", "audio") and given trackIndex.
# 1 <= trackIndex <= GetTrackCount(trackType).

SetTrackEnable(trackType, trackIndex, Bool) ⟶ bool
# Enables/Disables a track with given trackType and trackIndex.
# trackType is one of {"audio", "video", "subtitle"}.
# 1 <= trackIndex <= GetTrackCount(trackType).

GetIsTrackEnabled(trackType, trackIndex) ⟶ bool
# Returns True if the track with given trackType and trackIndex is enabled, and False otherwise.
# trackType is one of {"audio", "video", "subtitle"}.
# 1 <= trackIndex <= GetTrackCount(trackType).

SetTrackLock(trackType, trackIndex, Bool) ⟶ bool
# Locks/Unlocks a track with given trackType and trackIndex.
# trackType is one of {"audio", "video", "subtitle"}.
# 1 <= trackIndex <= GetTrackCount(trackType).

GetIsTrackLocked(trackType, trackIndex) ⟶ bool
# Returns True if the track with given trackType and trackIndex is locked, and False otherwise.
# trackType is one of {"audio", "video", "subtitle"}.
# 1 <= trackIndex <= GetTrackCount(trackType).

DeleteClips([timelineItems], Bool) ⟶ bool
# Deletes specified TimelineItems from the timeline, performing ripple delete if the second argument is True.
# The second argument is optional (defaults to False).

SetClipsLinked([timelineItems], Bool) ⟶ bool
# Links or unlinks the specified TimelineItems depending on the second argument.

GetItemListInTrack(trackType, index) ⟶ list
# Returns a list of timeline items on that track (based on trackType and index).
# 1 <= index <= GetTrackCount(trackType).

AddMarker(frameId, color, name, note, duration, customData) ⟶ bool
# Creates a new marker at the given frameId position with the specified marker information.
# 'customData' is optional and helps to attach user-specific data to the marker.

GetMarkers() ⟶ dict
# Returns a dict (frameId -> {information}) of all markers and dicts with their information.
# Example: {96.0: {'color': 'Green', 'duration': 1.0, 'note': '', 'name': 'Marker 1', 'customData': ''}, ...}
# In the above example - there is one 'Green' marker at offset 96 (position of the marker).

GetMarkerByCustomData(customData) ⟶ dict
# Returns marker {information} for the first matching marker with the specified customData.

UpdateMarkerCustomData(frameId, customData) ⟶ bool
# Updates customData (string) for the marker at the given frameId position.
# CustomData is not exposed via UI and is useful for scripting developers to attach any user-specific data to markers.

GetMarkerCustomData(frameId) ⟶ str
# Returns the customData string for the marker at the given frameId position.

DeleteMarkersByColor(color) ⟶ bool
# Deletes all timeline markers of the specified color.
# An "All" argument is supported and deletes all timeline markers.

DeleteMarkerAtFrame(frameNum) ⟶ bool
# Deletes the timeline marker at the given frame number.

DeleteMarkerByCustomData(customData) ⟶ bool
# Deletes the first matching marker with the specified customData.

ApplyGradeFromDRX(path, gradeMode, item1, item2, ...) ⟶ bool
# Loads a still from the given file path (string) and applies grade to Timeline Items with gradeMode (int):
# 0 - "No keyframes", 1 - "Source Timecode aligned", 2 - "Start Frames aligned".

ApplyGradeFromDRX(path, gradeMode, [items]) ⟶ bool
# Loads a still from the given file path (string) and applies grade to Timeline Items with gradeMode (int):
# 0 - "No keyframes", 1 - "Source Timecode aligned", 2 - "Start Frames aligned".

GetCurrentTimecode() ⟶ str
# Returns a string timecode representation for the current playhead position on Cut, Edit, Color, Fairlight, and Deliver pages.

SetCurrentTimecode(timecode) ⟶ bool
# Sets the current playhead position from input timecode on Cut, Edit, Color, Fairlight, and Deliver pages.

GetCurrentVideoItem() ⟶ item
# Returns the current video timeline item.

GetCurrentClipThumbnailImage() ⟶ dict
# Returns a dict (keys "width", "height", "format" and "data") with data containing raw thumbnail image data (RGB 8-bit image data encoded in base64 format) for current media in the Color Page.
# An example of how to retrieve and interpret thumbnails is provided in 6_get_current_media_thumbnail.py in the Examples folder.

GetTrackName(trackType, trackIndex) ⟶ str
# Returns the track name for the track indicated by trackType ("audio", "video" or "subtitle") and index.
# 1 <= trackIndex <= GetTrackCount(trackType).

SetTrackName(trackType, trackIndex, name) ⟶ bool
# Sets the track name (string) for the track indicated by trackType ("audio", "video" or "subtitle") and index.
# 1 <= trackIndex <= GetTrackCount(trackType).

DuplicateTimeline(timelineName) ⟶ Timeline
# Duplicates the timeline and returns the created timeline, with the (optional) timelineName, on success.

CreateCompoundClip([timelineItems], clipInfo={}) ⟶ TimelineItem
# Creates a compound clip of input timeline items with an optional clipInfo map: {"startTimecode" : "00:00:00:00", "name" : "Compound Clip 1"}.
# It returns the created timeline item.

CreateFusionClip([timelineItems]) ⟶ TimelineItem
# Creates a Fusion clip of input timeline items.
# It returns the created timeline item.

ImportIntoTimeline(filePath, importOptions={}) ⟶ bool
# Imports timeline items from an AAF file and optional importOptions dict into the timeline, with support for the keys:
# "autoImportSourceClipsIntoMediaPool": bool, specifies if source clips should be imported into the media pool, True by default.
# "ignoreFileExtensionsWhenMatching": bool, specifies if file extensions should be ignored when matching, False by default.
# "linkToSourceCameraFiles": bool, specifies if link to source camera files should be enabled, False by default.
# "useSizingInfo": bool, specifies if sizing information should be used, False by default.
# "importMultiChannelAudioTracksAsLinkedGroups": bool, specifies if multi-channel audio tracks should be imported as linked groups, False by default.
# "insertAdditionalTracks": bool, specifies if additional tracks should be inserted, True by default.
# "insertWithOffset": str, specifies insert with offset value in timecode format - defaults to "00:00:00:00", applicable if "insertAdditionalTracks" is False.
# "sourceClipsPath": str, specifies a filesystem path to search for source clips if the media is inaccessible in their original path and if "ignoreFileExtensionsWhenMatching" is True.
# "sourceClipsFolders": str, list of Media Pool folder objects to search for source clips if the media is not present in current folder.

Export(fileName, exportType, exportSubtype) ⟶ bool
# Exports timeline to 'fileName' as per input exportType & exportSubtype format.
# Refer to section "Looking up timeline export properties" for information on the parameters.

GetSetting(settingName) ⟶ str
# Returns value of timeline setting (indicated by settingName : string). Check the section below for more information.

SetSetting(settingName, settingValue) ⟶ bool
# Sets timeline setting (indicated by settingName : string) to the value (settingValue : string). Check the section below for more information.

InsertGeneratorIntoTimeline(generatorName) ⟶ TimelineItem
# Inserts a generator (indicated by generatorName : string) into the timeline.

InsertFusionGeneratorIntoTimeline(generatorName) ⟶ TimelineItem
# Inserts a Fusion generator (indicated by generatorName : string) into the timeline.

InsertFusionCompositionIntoTimeline() ⟶ TimelineItem
# Inserts a Fusion composition into the timeline.

InsertOFXGeneratorIntoTimeline(generatorName) ⟶ TimelineItem
# Inserts an OFX generator (indicated by generatorName : string) into the timeline.

InsertTitleIntoTimeline(titleName) ⟶ TimelineItem
# Inserts a title (indicated by titleName : string) into the timeline.

InsertFusionTitleIntoTimeline(titleName) ⟶ TimelineItem
# Inserts a Fusion title (indicated by titleName : string) into the timeline.

GrabStill() ⟶ GalleryStill
# Grabs still from the current video clip. Returns a GalleryStill object.

GrabAllStills(stillFrameSource) ⟶ list
# Grabs stills from all the clips of the timeline at 'stillFrameSource' (1 - First frame, 2 - Middle frame).
# Returns the list of GalleryStill objects.

GetUniqueId() ⟶ str
# Returns a unique ID for the timeline.

CreateSubtitlesFromAudio(autoCaptionSettings={}) ⟶ bool
# Creates subtitles from audio for the timeline.
# Takes in an optional dictionary autoCaptionSettings. Check 'Auto Caption Settings' subsection below for more information.
# Returns True on success, False otherwise.

DetectSceneCuts() ⟶ bool
# Detects and makes scene cuts along the timeline. Returns True if successful, False otherwise.

ConvertTimelineToStereo() ⟶ bool
# Converts timeline to stereo. Returns True if successful; False otherwise.

GetNodeGraph() ⟶ Graph
# Returns the timeline's node graph object.

AnalyzeDolbyVision(timelineItems=[], analysisType=None) ⟶ bool
# Analyzes Dolby Vision on clips present on the timeline. Returns True if analysis start is successful; False otherwise.
# If timelineItems is empty, analysis is performed on all items. Else, analysis is performed on timelineItems only.
# Set analysisType to resolve.DLB_BLEND_SHOTS for blend setting.
```

---

## TimelineItem Class

### Methods

```python
GetName() ⟶ str
# Returns the item name.

GetDuration() ⟶ int
# Returns the item duration.

GetEnd() ⟶ int
# Returns the end frame position on the timeline.

GetFusionCompCount() ⟶ int
# Returns the number of Fusion compositions associated with the timeline item.

GetFusionCompByIndex(compIndex) ⟶ FusionComp
# Returns the Fusion composition object based on the given index.
# 1 <= compIndex <= timelineItem.GetFusionCompCount()

GetFusionCompNameList() ⟶ list
# Returns a list of Fusion composition names associated with the timeline item.

GetFusionCompByName(compName) ⟶ FusionComp
# Returns the Fusion composition object based on the given name.

GetLeftOffset() ⟶ int
# Returns the maximum extension by frame for the clip from the left side.

GetRightOffset() ⟶ int
# Returns the maximum extension by frame for the clip from the right side.

GetStart() ⟶ int
# Returns the start frame position on the timeline.

SetProperty(propertyKey, propertyValue) ⟶ bool
# Sets the value of property "propertyKey" to value "propertyValue".
# Refer to "Looking up Timeline item properties" for more information.

GetProperty(propertyKey=None) ⟶ int | dict
# Returns the value of the specified key.
# If no key is specified, the method returns a dictionary (Python) or table (Lua) for all supported keys.

AddMarker(frameId, color, name, note, duration, customData) ⟶ bool
# Creates a new marker at the given frameId position with the specified marker information.
# 'customData' is optional and helps to attach user-specific data to the marker.

GetMarkers() ⟶ dict
# Returns a dict (frameId -> {information}) of all markers and dicts with their information.
# Example: a value of {96.0: {'color': 'Green', 'duration': 1.0, 'note': '', 'name': 'Marker 1', 'customData': ''}, ...}
# indicates a single green marker at clip offset 96.

GetMarkerByCustomData(customData) ⟶ dict
# Returns marker {information} for the first matching marker with the specified customData.

UpdateMarkerCustomData(frameId, customData) ⟶ bool
# Updates customData (string) for the marker at the given frameId position.
# CustomData is not exposed via UI and is useful for scripting developers to attach any user-specific data to markers.

GetMarkerCustomData(frameId) ⟶ str
# Returns the customData string for the marker at the given frameId position.

DeleteMarkersByColor(color) ⟶ bool
# Deletes all markers of the specified color from the timeline item.
# "All" as an argument deletes all color markers.

DeleteMarkerAtFrame(frameNum) ⟶ bool
# Deletes the marker at the specified frame number from the timeline item.

DeleteMarkerByCustomData(customData) ⟶ bool
# Deletes the first matching marker with the specified customData.

AddFlag(color) ⟶ bool
# Adds a flag with the given color (string).

GetFlagList() ⟶ list
# Returns a list of flag colors assigned to the item.

ClearFlags(color) ⟶ bool
# Clears the flags of the specified color.
# An "All" argument is supported to clear all flags.

GetClipColor() ⟶ str
# Returns the item color as a string.

SetClipColor(colorName) ⟶ bool
# Sets the item color based on the colorName (string).

ClearClipColor() ⟶ bool
# Clears the item color.

AddFusionComp() ⟶ FusionComp
# Adds a new Fusion composition associated with the timeline item.

ImportFusionComp(path) ⟶ FusionComp
# Imports a Fusion composition from the given file path by creating and adding a new composition for the item.

ExportFusionComp(path, compIndex) ⟶ bool
# Exports the Fusion composition based on the given index to the path provided.

DeleteFusionCompByName(compName) ⟶ bool
# Deletes the named Fusion composition.

LoadFusionCompByName(compName) ⟶ FusionComp
# Loads the named Fusion composition as the active composition.

RenameFusionCompByName(oldName, newName) ⟶ bool
# Renames the Fusion composition identified by oldName.

AddVersion(versionName, versionType) ⟶ bool
# Adds a new color version for a video clip based on versionType (0 - local, 1 - remote).

GetCurrentVersion() ⟶ dict
# Returns the current version of the video clip.
# The returned value will have the keys versionName and versionType (0 - local, 1 - remote).

DeleteVersionByName(versionName, versionType) ⟶ bool
# Deletes a color version by name and versionType (0 - local, 1 - remote).

LoadVersionByName(versionName, versionType) ⟶ bool
# Loads a named color version as the active version.
# versionType: 0 - local, 1 - remote.

RenameVersionByName(oldName, newName, versionType) ⟶ bool
# Renames the color version identified by oldName and versionType (0 - local, 1 - remote).

GetVersionNameList(versionType) ⟶ list
# Returns a list of all color versions for the given versionType (0 - local, 1 - remote).

GetMediaPoolItem() ⟶ MediaPoolItem
# Returns the media pool item corresponding to the timeline item if one exists.

GetStereoConvergenceValues() ⟶ dict
# Returns a dict (offset -> value) of keyframe offsets and respective convergence values.

GetStereoLeftFloatingWindowParams() ⟶ dict
# For the LEFT eye -> returns a dict (offset -> dict) of keyframe offsets and respective floating window params.
# Value at a particular offset includes the left, right, top, and bottom floating window values.

GetStereoRightFloatingWindowParams() ⟶ dict
# For the RIGHT eye -> returns a dict (offset -> dict) of keyframe offsets and respective floating window params.
# Value at a particular offset includes the left, right, top, and bottom floating window values.

ApplyArriCdlLut() ⟶ bool
# Applies ARRI CDL and LUT. Returns True if successful, False otherwise.

SetCDL(CDL_map) ⟶ bool
# Keys of map are: "NodeIndex", "Slope", "Offset", "Power", "Saturation", where 1 <= NodeIndex <= total number of nodes.

AddTake(mediaPoolItem, startFrame=None, endFrame=None) ⟶ bool
# Adds mediaPoolItem as a new take. Initializes a take selector for the timeline item if needed.
# By default, the full clip extents are added. startFrame (int) and endFrame (int) are optional arguments used to specify the extents.

GetSelectedTakeIndex() ⟶ int
# Returns the index of the currently selected take, or 0 if the clip is not a take selector.

GetTakesCount() ⟶ int
# Returns the number of takes in take selector, or 0 if the clip is not a take selector.

GetTakeByIndex(idx) ⟶ dict
# Returns a dict (keys "startFrame", "endFrame" and "mediaPoolItem") with take info for the specified index.

DeleteTakeByIndex(idx) ⟶ bool
# Deletes a take by index, 1 <= idx <= number of takes.

SelectTakeByIndex(idx) ⟶ bool
# Selects a take by index, 1 <= idx <= number of takes.

FinalizeTake() ⟶ bool
# Finalizes take selection.

CopyGrades(tgtTimelineItems) ⟶ bool
# Copies the current node stack layer grade to the same layer for each item in tgtTimelineItems.
# Returns True if successful.

SetClipEnabled(enabled) ⟶ bool
# Sets clip enabled status based on the argument (True/False).

GetClipEnabled() ⟶ bool
# Gets clip enabled status.

UpdateSidecar() ⟶ bool
# Updates the sidecar file for BRAW clips or RMD file for R3D clips.

GetUniqueId() ⟶ str
# Returns a unique ID for the timeline item.

LoadBurnInPreset(presetName) ⟶ bool
# Loads user-defined data burn-in preset for clip when supplied presetName (string).
# Returns True if successful.

CreateMagicMask(mode) ⟶ bool
# Returns True if magic mask was created successfully, False otherwise.
# mode can be "F" (forward), "B" (backward), or "BI" (bidirectional).

RegenerateMagicMask() ⟶ bool
# Returns True if magic mask was regenerated successfully, False otherwise.

Stabilize() ⟶ bool
# Returns True if stabilization was successful, False otherwise.

SmartReframe() ⟶ bool
# Performs Smart Reframe. Returns True if successful, False otherwise.

GetNodeGraph(layerIdx=None) ⟶ Graph
# Returns the clip's node graph object at layerIdx (int, optional).
# Returns the first layer if layerIdx is skipped.
# 1 <= layerIdx <= project.GetSetting("nodeStackLayers").

GetColorGroup() ⟶ ColorGroup
# Returns the clip's color group if one exists.

AssignToColorGroup(ColorGroup) ⟶ bool
# Returns True if TiItem is successfully assigned to the given ColorGroup.
# ColorGroup must be an existing group in the current project.

RemoveFromColorGroup() ⟶ bool
# Returns True if the TiItem is successfully removed from the ColorGroup it is in.

ExportLUT(exportType, path) ⟶ bool
# Exports LUTs from tiItem referring to value passed in 'exportType' (enum) for LUT size.
# Saves generated LUT in the provided 'path' (string). 'path' should include the intended file name.
# If an empty or incorrect extension is provided, the appropriate extension (.cube/.vlt) will be appended at the end of the path.

GetLinkedItems() ⟶ list
# Returns a list of linked timeline items.

GetTrackTypeAndIndex() ⟶ list
# Returns a list of two values that correspond to the TimelineItem's trackType (string) and trackIndex (int) respectively.
# trackType is one of {"audio", "video", "subtitle"}.
# 1 <= trackIndex <= Timeline.GetTrackCount(trackType).
```
## Gallery Class

### Methods

```python
GetAlbumName(galleryStillAlbum) ⟶ str
# Returns the name of the GalleryStillAlbum object 'galleryStillAlbum'.

SetAlbumName(galleryStillAlbum, albumName) ⟶ bool
# Sets the name of the GalleryStillAlbum object 'galleryStillAlbum' to 'albumName'.

GetCurrentStillAlbum() ⟶ GalleryStillAlbum
# Returns the current album as a GalleryStillAlbum object.

SetCurrentStillAlbum(galleryStillAlbum) ⟶ bool
# Sets the current album to the GalleryStillAlbum object 'galleryStillAlbum'.

GetGalleryStillAlbums() ⟶ list
# Returns the gallery albums as a list of GalleryStillAlbum objects.
```

## GalleryStillAlbum Class

### Methods

```python
GetStills() ⟶ list
# Returns the list of GalleryStill objects in the album.

GetLabel(galleryStill) ⟶ str
# Returns the label of the GalleryStill object 'galleryStill'.

SetLabel(galleryStill, label) ⟶ bool
# Sets the new 'label' to the GalleryStill object 'galleryStill'.

ImportStills(filePaths) ⟶ bool
# Imports GalleryStill from each filePath in the filePaths list.
# Returns True if at least one still is imported successfully, False otherwise.

ExportStills(galleryStill, folderPath, filePrefix, format) ⟶ bool
# Exports a list of GalleryStill objects 'galleryStill' to directory 'folderPath',
# with filename prefix 'filePrefix', using file format 'format'.
# Supported formats: dpx, cin, tif, jpg, png, ppm, bmp, xpm, drx.

DeleteStills(galleryStill) ⟶ bool
# Deletes the specified list of GalleryStill objects 'galleryStill'.
```

## GalleryStill Class

### Description

This class does not provide any API functions but the object type is used by functions in other classes.

## Graph Class

### Methods

```python
GetNumNodes() ⟶ int
# Returns the number of nodes in the graph.

SetLUT(nodeIndex, lutPath) ⟶ bool
# Sets a LUT on the node mapping the node index provided.
# 1 <= nodeIndex <= self.GetNumNodes().
# The lutPath can be an absolute path or a relative path (based off custom LUT paths or the master LUT path).
# The operation is successful for valid LUT paths that Resolve has already discovered (see Project.RefreshLUTList).

GetLUT(nodeIndex) ⟶ str
# Gets the relative LUT path based on the node index provided.
# 1 <= nodeIndex <= total number of nodes.

GetNodeLabel(nodeIndex) ⟶ str
# Returns the label of the node at nodeIndex.

GetToolsInNode(nodeIndex) ⟶ list
# Returns toolsList (list of strings) of the tools used in the node indicated by the given nodeIndex (int).

SetNodeEnabled(nodeIndex, isEnabled) ⟶ bool
# Sets the node at the given nodeIndex (int) to isEnabled (bool).
# 1 <= nodeIndex <= self.GetNumNodes().
```

## ColorGroup Class

### Methods

```python
GetName() ⟶ str
# Returns the name (string) of the ColorGroup.

SetName(groupName) ⟶ bool
# Renames the ColorGroup to groupName (string).

GetClipsInTimeline(Timeline=CurrTimeline) ⟶ list
# Returns a list of TimelineItem that are in the ColorGroup in the given Timeline.
# Timeline defaults to the Current Timeline if not specified.

GetPreClipNodeGraph() ⟶ Graph
# Returns the ColorGroup Pre-clip graph.

GetPostClipNodeGraph() ⟶ Graph
# Returns the ColorGroup Post-clip graph.
```

## Keyframe Mode Information

This section covers additional notes for the functions `Resolve.GetKeyframeMode()` and `Resolve.SetKeyframeMode(keyframeMode)`.

### `keyframeMode` Enums

`keyframeMode` can be one of the following enums:

- `resolve.KEYFRAME_MODE_ALL` ⟶ 0
- `resolve.KEYFRAME_MODE_COLOR` ⟶ 1
- `resolve.KEYFRAME_MODE_SIZING` ⟶ 2

**Description:**

- Integer values returned by `Resolve.GetKeyframeMode()` will correspond to the enums above.

## Cloud Projects Settings

This section covers additional notes for the functions `ProjectManager:CreateCloudProject`, `ProjectManager:ImportCloudProject`, and `ProjectManager:RestoreCloudProject`.

### `cloudSettings` Dict

All three functions take in a `{cloudSettings}` dictionary, which includes the following keys:

- `resolve.CLOUD_SETTING_PROJECT_NAME`: `str`, `["" by default]`
- `resolve.CLOUD_SETTING_PROJECT_MEDIA_PATH`: `str`, `["" by default]`
- `resolve.CLOUD_SETTING_IS_COLLAB`: `bool`, `[False by default]`
- `resolve.CLOUD_SETTING_SYNC_MODE`: `syncMode` (see below), `[resolve.CLOUD_SYNC_PROXY_ONLY by default]`
- `resolve.CLOUD_SETTING_IS_CAMERA_ACCESS`: `bool`, `[False by default]`

### `syncMode` Values

`syncMode` can be one of the following values:

- `resolve.CLOUD_SYNC_NONE`
- `resolve.CLOUD_SYNC_PROXY_ONLY`
- `resolve.CLOUD_SYNC_PROXY_AND_ORIG`

### Requirements

- All three functions (`ProjectManager:CreateCloudProject`, `ProjectManager:ImportCloudProject`, and `ProjectManager:RestoreCloudProject`) require `resolve.CLOUD_SETTING_PROJECT_MEDIA_PATH` to be defined.
- `ProjectManager:CreateCloudProject` also requires `resolve.CLOUD_SETTING_PROJECT_NAME` to be defined.

## Looking up Project and Clip Properties

This section covers additional notes for the functions `Project:GetSetting`, `Project:SetSetting`, `Timeline:GetSetting`, `Timeline:SetSetting`, `MediaPoolItem:GetClipProperty`, and `MediaPoolItem:SetClipProperty`. These functions are used to get and set properties that are otherwise available to the user through the Project Settings and the Clip Attributes dialogs.

### Key-Value Pair Format

The functions follow a key-value pair format, where each property is identified by a key (the `settingName` or `propertyName` parameter) and possesses a value (typically a text value). Keys and values are designed to be easily correlated with parameter names and values in the Resolve UI. Explicitly enumerated values for some parameters are listed below.

Some properties may be read-only—these include intrinsic clip properties like the date created or sample rate, and properties that can be disabled in specific application contexts (e.g., custom colorspaces in an ACES workflow, or output sizing parameters when behavior is set to match the timeline).

### Getting Values

Invoke `Project:GetSetting`, `Timeline:GetSetting`, or `MediaPoolItem:GetClipProperty` with the appropriate property key. To get a snapshot of all queryable properties (keys and values), you can call `Project:GetSetting`, `Timeline:GetSetting`, or `MediaPoolItem:GetClipProperty` without parameters (or with a `NoneType` or a blank property key). Using specific keys to query individual properties will be faster. Note that getting a property using an invalid key will return a trivial result.

### Setting Values

Invoke `Project:SetSetting`, `Timeline:SetSetting`, or `MediaPoolItem:SetClipProperty` with the appropriate property key and a valid value. When setting a parameter, please check the return value to ensure the success of the operation. You can troubleshoot the validity of keys and values by setting the desired result from the UI and checking property snapshots before and after the change.

### Enumerated Project Properties

#### `superScale`
- The property value is an enumerated integer between `0` and `4` with these meanings:
  - `0 = Auto`
  - `1 = No scaling`
  - `2`, `3`, and `4` represent the Super Scale multipliers `2x`, `3x`, and `4x`.
- For the super scale multiplier `2x Enhanced`, exactly four arguments must be passed as outlined below. If fewer than four arguments are passed, it will default to `2x`.

**Affects:**
- `x = Project:GetSetting('superScale')` and `Project:SetSetting('superScale', x)`
- For `2x Enhanced`: `Project:SetSetting('superScale', 2, sharpnessValue, noiseReductionValue)`, where `sharpnessValue` is a float in the range `[0.0, 1.0]` and `noiseReductionValue` is a float in the range `[0.0, 1.0]`.

#### `timelineFrameRate`
- The property value is one of the frame rates available to the user in project settings under the "Timeline frame rate" option.
- Drop Frame can be configured for supported frame rates by appending the frame rate with `"DF"`, e.g., `"29.97 DF"` will enable drop frame and `"29.97"` will disable drop frame.

**Affects:**
- `x = Project:GetSetting('timelineFrameRate')` and `Project:SetSetting('timelineFrameRate', x)`

### Enumerated Clip Properties

#### `Super Scale`
- The property value is an enumerated integer between `1` and `4` with these meanings:
  - `1 = No scaling`
  - `2`, `3`, and `4` represent the Super Scale multipliers `2x`, `3x`, and `4x`.
- For the super scale multiplier `2x Enhanced`, exactly four arguments must be passed as outlined below. If fewer than four arguments are passed, it will default to `2x`.

**Affects:**
- `x = MediaPoolItem:GetClipProperty('Super Scale')` and `MediaPoolItem:SetClipProperty('Super Scale', x)`
- For `2x Enhanced`: `MediaPoolItem:SetClipProperty('Super Scale', 2, sharpnessValue, noiseReductionValue)`, where `sharpnessValue` is a float in the range `[0.0, 1.0]` and `noiseReductionValue` is a float in the range `[0.0, 1.0]`.

#### `Cloud Sync`
- The property value is an enumerated integer that corresponds to one of the following enums:
  - `resolve.CLOUD_SYNC_DEFAULT` ⟶ `-1`
  - `resolve.CLOUD_SYNC_DOWNLOAD_IN_QUEUE` ⟶ `0`
  - `resolve.CLOUD_SYNC_DOWNLOAD_IN_PROGRESS` ⟶ `1`
  - `resolve.CLOUD_SYNC_DOWNLOAD_SUCCESS` ⟶ `2`
  - `resolve.CLOUD_SYNC_DOWNLOAD_FAIL` ⟶ `3`
  - `resolve.CLOUD_SYNC_DOWNLOAD_NOT_FOUND` ⟶ `4`
  - `resolve.CLOUD_SYNC_UPLOAD_IN_QUEUE` ⟶ `5`
  - `resolve.CLOUD_SYNC_UPLOAD_IN_PROGRESS` ⟶ `6`
  - `resolve.CLOUD_SYNC_UPLOAD_SUCCESS` ⟶ `7`
  - `resolve.CLOUD_SYNC_UPLOAD_FAIL` ⟶ `8`
  - `resolve.CLOUD_SYNC_UPLOAD_NOT_FOUND` ⟶ `9`

## Audio Mapping

This section covers the output for `mpItem.GetAudioMapping()`.

### Example Scenario

This example assumes an `mpItem` that has audio from its embedded source and from two other clips that are linked to it. The audio clip attributes of this `mpItem` will show 3 tracks.

Assume that:

- **(A)** The embedded track is of format/type 'stereo' (2 channels).
- **(B)** Linked clip 1 track is of format/type '7.1' (8 channels).
- **(C)** Linked clip 2 track is '5.1' (6 channels).

Assume that the format/type was not changed further.

### Output

`mpItem.GetAudioMapping()` returns a string of the form:

```python
{
  "embedded_audio_channels": 2,                 # Total number of embedded channels across all tracks
  "linked_audio": {                             # A list of only linked audio information
    "1": {                                      # Same as (B) above
      "channels": 8,
      "path": FILE_PATH
    },
    "2": {                                      # Same as (C) above
      "channels": 6,
      "path": FILE_PATH
    }
  },
  "track_mapping": {                            # Listing of all the tracks. Output here will match what is seen in the audio clip attributes menu on the UI.
    "1": {
      "channel_idx": [0, 3],                    # Channel index '0' indicates that the channel is muted; in this case, channel index '3' will correspond to the first channel of (B)
      "type": "Stereo"                          # The length of the 'channel_idx' list will always correspond to the number of channels the format specified in 'type' will allow.
                                                # In this case, 'Stereo' allows 2 channels and so the length of the 'channel_idx' list is 2.
    },
    "2": {
      "channel_idx": [3, 4, 5, 6, 7, 8, 9, 10], # Channel indices here are following the default for (B)
      "type": "7.1"
    },
    "3": {
      "channel_idx": [0, 0, 0, 1, 15, 16],      # The first three channels for this track are muted; The next channel is the first channel of (A), and the final 2 follow the default for (C)
      "type": "5.1"
    }
  }
}
```


## Auto Caption Settings

This section covers the supported settings for the method `Timeline.CreateSubtitlesFromAudio({autoCaptionSettings})`.

### `autoCaptionSettings` Dictionary

The parameter setting is a dictionary containing the following keys:

- `resolve.SUBTITLE_LANGUAGE`: `languageID` (see below), `[resolve.AUTO_CAPTION_AUTO by default]`
- `resolve.SUBTITLE_CAPTION_PRESET`: `presetType` (see below), `[resolve.AUTO_CAPTION_SUBTITLE_DEFAULT by default]`
- `resolve.SUBTITLE_CHARS_PER_LINE`: `int`, Number between `1` and `60` inclusive `[42 by default]`
- `resolve.SUBTITLE_LINE_BREAK`: `lineBreakType` (see below), `[resolve.AUTO_CAPTION_LINE_SINGLE by default]`
- `resolve.SUBTITLE_GAP`: `int`, Number between `0` and `10` inclusive `[0 by default]`

**Note:** The default values for some keys may change based on values defined for other keys, as per the UI.

**Example:**
If the following dictionary is supplied:

```python
CreateSubtitlesFromAudio({
    resolve.SUBTITLE_LANGUAGE = resolve.AUTO_CAPTION_KOREAN,
    resolve.SUBTITLE_CAPTION_PRESET = resolve.AUTO_CAPTION_NETFLIX
})
```

The default value for `resolve.SUBTITLE_CHARS_PER_LINE` will be `16` instead of `42`.

### `languageID` Values

- `resolve.AUTO_CAPTION_AUTO`
- `resolve.AUTO_CAPTION_DANISH`
- `resolve.AUTO_CAPTION_DUTCH`
- `resolve.AUTO_CAPTION_ENGLISH`
- `resolve.AUTO_CAPTION_FRENCH`
- `resolve.AUTO_CAPTION_GERMAN`
- `resolve.AUTO_CAPTION_ITALIAN`
- `resolve.AUTO_CAPTION_JAPANESE`
- `resolve.AUTO_CAPTION_KOREAN`
- `resolve.AUTO_CAPTION_MANDARIN_SIMPLIFIED`
- `resolve.AUTO_CAPTION_MANDARIN_TRADITIONAL`
- `resolve.AUTO_CAPTION_NORWEGIAN`
- `resolve.AUTO_CAPTION_PORTUGUESE`
- `resolve.AUTO_CAPTION_RUSSIAN`
- `resolve.AUTO_CAPTION_SPANISH`
- `resolve.AUTO_CAPTION_SWEDISH`

### `presetType` Values

- `resolve.AUTO_CAPTION_SUBTITLE_DEFAULT`
- `resolve.AUTO_CAPTION_TELETEXT`
- `resolve.AUTO_CAPTION_NETFLIX`

### `lineBreakType` Values

- `resolve.AUTO_CAPTION_LINE_SINGLE`
- `resolve.AUTO_CAPTION_LINE_DOUBLE`

## Looking up Render Settings

This section covers the supported settings for the method `SetRenderSettings({settings})`.

### `settings` Dictionary

The parameter setting is a dictionary containing the following keys:

- `"SelectAllFrames"`: `bool` (when set to `True`, the settings `MarkIn` and `MarkOut` are ignored)
- `"MarkIn"`: `int`
- `"MarkOut"`: `int`
- `"TargetDir"`: `str`
- `"CustomName"`: `str`
- `"UniqueFilenameStyle"`: `int` (`0` for Prefix, `1` for Suffix)
- `"ExportVideo"`: `bool`
- `"ExportAudio"`: `bool`
- `"FormatWidth"`: `int`
- `"FormatHeight"`: `int`
- `"FrameRate"`: `float` (examples: `23.976`, `24`)
- `"PixelAspectRatio"`: `str` (for SD resolution: `"16_9"` or `"4_3"`) (for other resolutions: `"square"` or `"cinemascope"`)
- `"VideoQuality"`: Possible values for the current codec (if applicable):
  - `0` (`int`) - Sets quality to automatic
  - `[1 -> MAX]` (`int`) - Sets input bit rate
  - `["Least", "Low", "Medium", "High", "Best"]` (`str`) - Sets input quality level
- `"AudioCodec"`: `str` (example: `"aac"`)
- `"AudioBitDepth"`: `int`
- `"AudioSampleRate"`: `int`
- `"ColorSpaceTag"`: `str` (example: `"Same as Project"`, `"AstroDesign"`)
- `"GammaTag"`: `str` (example: `"Same as Project"`, `"ACEScct"`)
- `"ExportAlpha"`: `bool`
- `"EncodingProfile"`: `str` (example: `"Main10"`) - Can only be set for H.264 and H.265.
- `"MultiPassEncode"`: `bool` - Can only be set for H.264.
- `"AlphaMode"`: `int` (`0` for Premultiplied, `1` for Straight) - Can only be set if `"ExportAlpha"` is `True`.
- `"NetworkOptimization"`: `bool` - Only supported by QuickTime and MP4 formats.


## Looking up Timeline Export Properties

This section covers the parameters for the argument `Export(fileName, exportType, exportSubtype)`.

### `exportType` Constants

`exportType` can be one of the following constants:

- `resolve.EXPORT_AAF`
- `resolve.EXPORT_DRT`
- `resolve.EXPORT_EDL`
- `resolve.EXPORT_FCP_7_XML`
- `resolve.EXPORT_FCPXML_1_8`
- `resolve.EXPORT_FCPXML_1_9`
- `resolve.EXPORT_FCPXML_1_10`
- `resolve.EXPORT_HDR_10_PROFILE_A`
- `resolve.EXPORT_HDR_10_PROFILE_B`
- `resolve.EXPORT_TEXT_CSV`
- `resolve.EXPORT_TEXT_TAB`
- `resolve.EXPORT_DOLBY_VISION_VER_2_9`
- `resolve.EXPORT_DOLBY_VISION_VER_4_0`
- `resolve.EXPORT_DOLBY_VISION_VER_5_1`
- `resolve.EXPORT_OTIO`
- `resolve.EXPORT_ALE`
- `resolve.EXPORT_ALE_CDL`

### `exportSubtype` Enums

`exportSubtype` can be one of the following enums:

- `resolve.EXPORT_NONE`
- `resolve.EXPORT_AAF_NEW`
- `resolve.EXPORT_AAF_EXISTING`
- `resolve.EXPORT_CDL`
- `resolve.EXPORT_SDL`
- `resolve.EXPORT_MISSING_CLIPS`

**Notes:**

- `exportSubtype` is a required parameter for `resolve.EXPORT_AAF` and `resolve.EXPORT_EDL`. For the rest of the `exportType`, `exportSubtype` is ignored.
- When `exportType` is `resolve.EXPORT_AAF`, valid `exportSubtype` values are `resolve.EXPORT_AAF_NEW` and `resolve.EXPORT_AAF_EXISTING`.
- When `exportType` is `resolve.EXPORT_EDL`, valid `exportSubtype` values are `resolve.EXPORT_CDL`, `resolve.EXPORT_SDL`, `resolve.EXPORT_MISSING_CLIPS`, and `resolve.EXPORT_NONE`.

**Note:** Replace `'resolve.'` when using the constants above if a different Resolve class instance name is used.


## Unsupported `exportType` Types

Starting with DaVinci Resolve 18.1, the following export types are not supported:

- `resolve.EXPORT_FCPXML_1_3`
- `resolve.EXPORT_FCPXML_1_4`
- `resolve.EXPORT_FCPXML_1_5`
- `resolve.EXPORT_FCPXML_1_6`
- `resolve.EXPORT_FCPXML_1_7`


## Looking up Timeline Item Properties

This section covers additional notes for the functions `TimelineItem:SetProperty` and `TimelineItem:GetProperty`. These functions are used to get and set the properties mentioned below.

### Supported Keys and Accepted Values

- **"Pan"**: Floating point values from `-4.0*width` to `4.0*width`
- **"Tilt"**: Floating point values from `-4.0*height` to `4.0*height`
- **"ZoomX"**: Floating point values from `0.0` to `100.0`
- **"ZoomY"**: Floating point values from `0.0` to `100.0`
- **"ZoomGang"**: Boolean value
- **"RotationAngle"**: Floating point values from `-360.0` to `360.0`
- **"AnchorPointX"**: Floating point values from `-4.0*width` to `4.0*width`
- **"AnchorPointY"**: Floating point values from `-4.0*height` to `4.0*height`
- **"Pitch"**: Floating point values from `-1.5` to `1.5`
- **"Yaw"**: Floating point values from `-1.5` to `1.5`
- **"FlipX"**: Boolean value for flipping horizontally
- **"FlipY"**: Boolean value for flipping vertically
- **"CropLeft"**: Floating point values from `0.0` to `width`
- **"CropRight"**: Floating point values from `0.0` to `width`
- **"CropTop"**: Floating point values from `0.0` to `height`
- **"CropBottom"**: Floating point values from `0.0` to `height`
- **"CropSoftness"**: Floating point values from `-100.0` to `100.0`
- **"CropRetain"**: Boolean value for the "Retain Image Position" checkbox
- **"DynamicZoomEase"**: A value from the following constants:
  - `DYNAMIC_ZOOM_EASE_LINEAR = 0`
  - `DYNAMIC_ZOOM_EASE_IN`
  - `DYNAMIC_ZOOM_EASE_OUT`
  - `DYNAMIC_ZOOM_EASE_IN_AND_OUT`
- **"CompositeMode"**: A value from the following constants:
  - `COMPOSITE_NORMAL = 0`
  - `COMPOSITE_ADD`
  - `COMPOSITE_SUBTRACT`
  - `COMPOSITE_DIFF`
  - `COMPOSITE_MULTIPLY`
  - `COMPOSITE_SCREEN`
  - `COMPOSITE_OVERLAY`
  - `COMPOSITE_HARDLIGHT`
  - `COMPOSITE_SOFTLIGHT`
  - `COMPOSITE_DARKEN`
  - `COMPOSITE_LIGHTEN`
  - `COMPOSITE_COLOR_DODGE`
  - `COMPOSITE_COLOR_BURN`
  - `COMPOSITE_EXCLUSION`
  - `COMPOSITE_HUE`
  - `COMPOSITE_SATURATE`
  - `COMPOSITE_COLORIZE`
  - `COMPOSITE_LUMA_MASK`
  - `COMPOSITE_DIVIDE`
  - `COMPOSITE_LINEAR_DODGE`
  - `COMPOSITE_LINEAR_BURN`
  - `COMPOSITE_LINEAR_LIGHT`
  - `COMPOSITE_VIVID_LIGHT`
  - `COMPOSITE_PIN_LIGHT`
  - `COMPOSITE_HARD_MIX`
  - `COMPOSITE_LIGHTER_COLOR`
  - `COMPOSITE_DARKER_COLOR`
  - `COMPOSITE_FOREGROUND`
  - `COMPOSITE_ALPHA`
  - `COMPOSITE_INVERTED_ALPHA`
  - `COMPOSITE_LUM`
  - `COMPOSITE_INVERTED_LUM`
- **"Opacity"**: Floating point value from `0.0` to `100.0`
- **"Distortion"**: Floating point value from `-1.0` to `1.0`
- **"RetimeProcess"**: A value from the following constants:
  - `RETIME_USE_PROJECT = 0`
  - `RETIME_NEAREST`
  - `RETIME_FRAME_BLEND`
  - `RETIME_OPTICAL_FLOW`
- **"MotionEstimation"**: A value from the following constants:
  - `MOTION_EST_USE_PROJECT = 0`
  - `MOTION_EST_STANDARD_FASTER`
  - `MOTION_EST_STANDARD_BETTER`
  - `MOTION_EST_ENHANCED_FASTER`
  - `MOTION_EST_ENHANCED_BETTER`
  - `MOTION_EST_SPEED_WARP_BETTER`
  - `MOTION_EST_SPEED_WARP_FASTER`
- **"Scaling"**: A value from the following constants:
  - `SCALE_USE_PROJECT = 0`
  - `SCALE_CROP`
  - `SCALE_FIT`
  - `SCALE_FILL`
  - `SCALE_STRETCH`
- **"ResizeFilter"**: A value from the following constants:
  - `RESIZE_FILTER_USE_PROJECT = 0`
  - `RESIZE_FILTER_SHARPER`
  - `RESIZE_FILTER_SMOOTHER`
  - `RESIZE_FILTER_BICUBIC`
  - `RESIZE_FILTER_BILINEAR`
  - `RESIZE_FILTER_BESSEL`
  - `RESIZE_FILTER_BOX`
  - `RESIZE_FILTER_CATMULL_ROM`
  - `RESIZE_FILTER_CUBIC`
  - `RESIZE_FILTER_GAUSSIAN`
  - `RESIZE_FILTER_LANCZOS`
  - `RESIZE_FILTER_MITCHELL`
  - `RESIZE_FILTER_NEAREST_NEIGHBOR`
  - `RESIZE_FILTER_QUADRATIC`
  - `RESIZE_FILTER_SINC`
  - `RESIZE_FILTER_LINEAR`

### Additional Notes

- Values beyond the range will be clipped.
- `width` and `height` are the same as the UI max limits.

### Passing Arguments

- The arguments can be passed as a key-value pair or grouped together into a dictionary (for Python) or table (for Lua) and passed as a single argument.
- Getting the values for keys that use constants will return the number corresponding to the constant.


## ExportLUT Notes

This section covers additional notes for `TimelineItem.ExportLUT(exportType, path)`.

### Supported `exportType` Values

The supported values for `exportType` (enum) are:

- `resolve.EXPORT_LUT_17PTCUBE`
- `resolve.EXPORT_LUT_33PTCUBE`
- `resolve.EXPORT_LUT_65PTCUBE`
- `resolve.EXPORT_LUT_PANASONICVLUT`


## Deprecated Resolve API Functions

The following API functions are deprecated.

### ProjectManager

```python
GetProjectsInCurrentFolder() ⟶ dict
# Returns a dict of project names in the current folder.

GetFoldersInCurrentFolder() ⟶ dict
# Returns a dict of folder names in the current folder.
```

### Project

```python
GetPresets() ⟶ dict
# Returns a dict of presets and their information.

GetRenderJobs() ⟶ dict
# Returns a dict of render jobs and their information.

GetRenderPresets() ⟶ dict
# Returns a dict of render presets and their information.
```

### MediaStorage

```python
GetMountedVolumes() ⟶ dict
# Returns a dict of folder paths corresponding to mounted volumes displayed in Resolve’s Media Storage.

GetSubFolders(folderPath) ⟶ dict
# Returns a dict of folder paths in the given absolute folder path.

GetFiles(folderPath) ⟶ dict
# Returns a dict of media and file listings in the given absolute folder path. Note that media listings may be logically consolidated entries.

AddItemsToMediaPool(item1, item2, ...) ⟶ dict
# Adds specified file/folder paths from Media Storage into the current Media Pool folder. Input is one or more file/folder paths. Returns a dict of the MediaPoolItems created.

AddItemsToMediaPool([items...]) ⟶ dict
# Adds specified file/folder paths from Media Storage into the current Media Pool folder. Input is an array of file/folder paths. Returns a dict of the MediaPoolItems created.
```

### Folder

```python
GetClips() ⟶ dict
# Returns a dict of clips (items) within the folder.

GetSubFolders() ⟶ dict
# Returns a dict of subfolders in the folder.
```

### MediaPoolItem

```python
GetFlags() ⟶ dict
# Returns a dict of flag colors assigned to the item.
```

### Timeline

```python
GetItemsInTrack(trackType, index) ⟶ dict
# Returns a dict of Timeline items on the video or audio track (based on trackType) at the specified index.
```

### TimelineItem

```python
GetFusionCompNames() ⟶ dict
# Returns a dict of Fusion composition names associated with the timeline item.

GetFlags() ⟶ dict
# Returns a dict of flag colors assigned to the item.

GetVersionNames(versionType) ⟶ dict
# Returns a dict of version names by provided versionType: 0 - local, 1 - remote.

GetNumNodes() ⟶ int
# Returns the number of nodes in the current graph for the timeline item.

SetLUT(nodeIndex, lutPath) ⟶ bool
# Sets LUT on the node mapping the node index provided, 1 <= nodeIndex <= total number of nodes.
# The lutPath can be an absolute path, or a relative path (based off custom LUT paths or the master LUT path).
# The operation is successful for valid LUT paths that Resolve has already discovered (see Project.RefreshLUTList).

GetLUT(nodeIndex) ⟶ str
# Gets the relative LUT path based on the node index provided, 1 <= nodeIndex <= total number of nodes.

GetNodeLabel(nodeIndex) ⟶ str
# Returns the label of the node at nodeIndex.
```

## Unsupported Resolve API Functions

The following API (functions and parameters) are no longer supported. Use job IDs instead of indices.

### Project

```python
StartRendering(index1, index2, ...) ⟶ Bool
# Please use unique job IDs (string) instead of indices.

StartRendering([idxs...]) ⟶ Bool
# Please use unique job IDs (string) instead of indices.

DeleteRenderJobByIndex(idx) ⟶ Bool
# Please use unique job IDs (string) instead of indices.

GetRenderJobStatus(idx) ⟶ dict
# Please use unique job IDs (string) instead of indices.

GetSetting and SetSetting ⟶ dict
# The settingName 'videoMonitorUseRec601For422SDI' is now replaced with 'videoMonitorUseMatrixOverrideFor422SDI' and 'videoMonitorMatrixOverrideFor422SDI'.
# The settingName 'perfProxyMediaOn' is now replaced with 'perfProxyMediaMode' which takes values: 0 - disabled, 1 - when available, 2 - when source not available.
```
