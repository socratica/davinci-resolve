## Resolve methods
```python
DeleteLayoutPreset(presetName) ⟶ bool
ExportBurnInPreset(presetName, exportPath) ⟶ bool
ExportLayoutPreset(presetName, presetFilePath) ⟶ bool
ExportRenderPreset(presetName, exportPath) ⟶ bool
Fusion() ⟶ Fusion
GetCurrentPage() ⟶ str
GetKeyframeMode() ⟶ keyframeMode
GetMediaStorage() ⟶ MediaStorage
GetProductName() ⟶ str
GetProjectManager() ⟶ ProjectManager
GetVersion() ⟶ list
GetVersionString() ⟶ str
ImportBurnInPreset(presetPath) ⟶ bool
ImportLayoutPreset(presetFilePath, presetName=None) ⟶ bool
ImportRenderPreset(presetPath) ⟶ bool
LoadLayoutPreset(presetName) ⟶ bool
OpenPage(pageName) ⟶ bool
Quit() ⟶ None
SaveLayoutPreset(presetName) ⟶ bool
SetKeyframeMode(keyframeMode) ⟶ bool
UpdateLayoutPreset(presetName) ⟶ bool
```

## ProjectManager methods
```python
ArchiveProject(projectName, filePath, isArchiveSrcMedia=True, isArchiveRenderCache=True, isArchiveProxyMedia=False) ⟶ bool
CloseProject(project) ⟶ bool
CreateCloudProject(cloudSettings) ⟶ Project
CreateFolder(folderName) ⟶ bool
CreateProject(projectName) ⟶ Project
DeleteFolder(folderName) ⟶ bool
DeleteProject(projectName) ⟶ bool
ExportProject(projectName, filePath, withStillsAndLUTs=True) ⟶ bool
GetCurrentDatabase() ⟶ dict
GetCurrentFolder() ⟶ str
GetCurrentProject() ⟶ Project
GetDatabaseList() ⟶ list
GetFolderListInCurrentFolder() ⟶ list
GetProjectListInCurrentFolder() ⟶ list
GotoParentFolder() ⟶ bool
GotoRootFolder() ⟶ bool
ImportCloudProject(filePath, cloudSettings) ⟶ bool
ImportProject(filePath, projectName=None) ⟶ bool
LoadProject(projectName) ⟶ Project
OpenFolder(folderName) ⟶ bool
RestoreCloudProject(folderPath, cloudSettings) ⟶ bool
RestoreProject(filePath, projectName=None) ⟶ bool
SaveProject() ⟶ bool
SetCurrentDatabase(dbInfo) ⟶ bool
```

## Project methods
```python
AddColorGroup(groupName) ⟶ ColorGroup
AddRenderJob() ⟶ str
DeleteAllRenderJobs() ⟶ bool
DeleteColorGroup(colorGroup) ⟶ bool
DeleteRenderJob(jobId) ⟶ bool
ExportCurrentFrameAsStill(filePath) ⟶ bool
GetColorGroupsList() ⟶ list
GetCurrentRenderFormatAndCodec() ⟶ dict
GetCurrentRenderMode() ⟶ int
GetCurrentTimeline() ⟶ Timeline
GetGallery() ⟶ Gallery
GetMediaPool() ⟶ MediaPool
GetName() ⟶ str
GetPresetList() ⟶ list
GetRenderCodecs(renderFormat) ⟶ dict
GetRenderFormats() ⟶ dict
GetRenderJobList() ⟶ list
GetRenderJobStatus(jobId) ⟶ dict
GetRenderPresetList() ⟶ list
GetRenderResolutions(format, codec) ⟶ list
GetSetting(settingName) ⟶ str
GetTimelineByIndex(idx) ⟶ Timeline
GetTimelineCount() ⟶ int
GetUniqueId() ⟶ str
InsertAudioToCurrentTrackAtPlayhead(mediaPath, startOffsetInSamples, durationInSamples) ⟶ bool
IsRenderingInProgress() ⟶ bool
LoadBurnInPreset(presetName) ⟶ bool
LoadRenderPreset(presetName) ⟶ bool
RefreshLUTList() ⟶ bool
SaveAsNewRenderPreset(presetName) ⟶ bool
SetCurrentRenderFormatAndCodec(format, codec) ⟶ bool
SetCurrentRenderMode(renderMode) ⟶ bool
SetCurrentTimeline(timeline) ⟶ bool
SetName(projectName) ⟶ bool
SetPreset(presetName) ⟶ bool
SetRenderSettings(settings) ⟶ bool
SetSetting(settingName, settingValue) ⟶ bool
StartRendering(isInteractiveMode=False) ⟶ bool
StartRendering(jobId1, jobId2, ...) ⟶ bool
StartRendering([jobIds...], isInteractiveMode=False) ⟶ bool
StopRendering() ⟶ None
```

## MediaStorage methods
```python
AddClipMattesToMediaPool(MediaPoolItem, [paths], stereoEye) ⟶ bool
AddItemListToMediaPool(item1, item2, ...) ⟶ list
AddItemListToMediaPool([items...]) ⟶ list
AddItemListToMediaPool([{itemInfo}, ...]) ⟶ list
AddTimelineMattesToMediaPool([paths]) ⟶ list
GetFileList(folderPath) ⟶ list
GetMountedVolumeList() ⟶ list
GetSubFolderList(folderPath) ⟶ list
RevealInStorage(path) ⟶ bool
```

## MediaPool methods
```python
AddSubFolder(folder, name) ⟶ Folder
AppendToTimeline(clip1, clip2, ...) ⟶ list
AppendToTimeline([clips]) ⟶ list
AppendToTimeline([{clipInfo}, ...]) ⟶ list
CreateEmptyTimeline(name) ⟶ Timeline
CreateStereoClip(LeftMediaPoolItem, RightMediaPoolItem) ⟶ MediaPoolItem
CreateTimelineFromClips(name, clip1, clip2, ...) ⟶ Timeline
CreateTimelineFromClips(name, [clips]) ⟶ Timeline
CreateTimelineFromClips(name, [{clipInfo}]) ⟶ Timeline
DeleteClipMattes(MediaPoolItem, [paths]) ⟶ bool
DeleteClips([clips]) ⟶ bool
DeleteFolders([subfolders]) ⟶ bool
DeleteTimelines([timeline]) ⟶ bool
ExportMetadata(fileName, [clips]) ⟶ bool
GetClipMatteList(MediaPoolItem) ⟶ list
GetCurrentFolder() ⟶ Folder
GetRootFolder() ⟶ Folder
GetTimelineMatteList(Folder) ⟶ list
GetUniqueId() ⟶ str
ImportFolderFromFile(filePath, sourceClipsPath="") ⟶ bool
ImportMedia([items...]) ⟶ list
ImportMedia([{clipInfo}]) ⟶ list
ImportTimelineFromFile(filePath, importOptions={}) ⟶ Timeline
MoveClips([clips], targetFolder) ⟶ bool
MoveFolders([folders], targetFolder) ⟶ bool
RefreshFolders() ⟶ bool
RelinkClips([MediaPoolItem], folderPath) ⟶ bool
SetCurrentFolder(Folder) ⟶ bool
UnlinkClips([MediaPoolItem]) ⟶ bool
```

## Folder methods
```python
ClearTranscription() ⟶ bool
Export(filePath) ⟶ bool
GetClipList() ⟶ list
GetIsFolderStale() ⟶ bool
GetName() ⟶ str
GetSubFolderList() ⟶ list
GetUniqueId() ⟶ str
TranscribeAudio() ⟶ bool
```

## MediaPoolItem methods
```python
AddFlag(color) ⟶ bool
AddMarker(frameId, color, name, note, duration, customData) ⟶ bool
ClearClipColor() ⟶ bool
ClearFlags(color) ⟶ bool
ClearTranscription() ⟶ bool
DeleteMarkerAtFrame(frameNum) ⟶ bool
DeleteMarkerByCustomData(customData) ⟶ bool
DeleteMarkersByColor(color) ⟶ bool
GetAudioMapping() ⟶ str (json formatted)
GetClipColor() ⟶ str
GetClipProperty(propertyName=None) ⟶ str | dict
GetFlagList() ⟶ list
GetMarkerByCustomData(customData) ⟶ dict
GetMarkerCustomData(frameId) ⟶ str
GetMarkers() ⟶ dict
GetMediaId() ⟶ str
GetMetadata(metadataType=None) ⟶ str | dict
GetName() ⟶ str
GetUniqueId() ⟶ str
LinkProxyMedia(proxyMediaFilePath) ⟶ bool
ReplaceClip(filePath) ⟶ bool
SetClipColor(colorName) ⟶ bool
SetClipProperty(propertyName, propertyValue) ⟶ bool
SetMetadata(metadataType, metadataValue) ⟶ bool
SetMetadata(metadata) ⟶ bool
TranscribeAudio() ⟶ bool
UnlinkProxyMedia() ⟶ bool
UpdateMarkerCustomData(frameId, customData) ⟶ bool
```

## Timeline methods
```python
AddMarker(frameId, color, name, note, duration, customData) ⟶ bool
AddTrack(trackType, newTrackOptions) ⟶ bool
AddTrack(trackType, subTrackType) ⟶ bool
AnalyzeDolbyVision(timelineItems=[], analysisType=None) ⟶ bool
ApplyGradeFromDRX(path, gradeMode, [items]) ⟶ bool
ApplyGradeFromDRX(path, gradeMode, item1, item2, ...) ⟶ bool
ConvertTimelineToStereo() ⟶ bool
CreateCompoundClip([timelineItems], clipInfo={}) ⟶ TimelineItem
CreateFusionClip([timelineItems]) ⟶ TimelineItem
CreateSubtitlesFromAudio(autoCaptionSettings={}) ⟶ bool
DeleteClips([timelineItems], Bool) ⟶ bool
DeleteMarkerAtFrame(frameNum) ⟶ bool
DeleteMarkerByCustomData(customData) ⟶ bool
DeleteMarkersByColor(color) ⟶ bool
DeleteTrack(trackType, trackIndex) ⟶ bool
DetectSceneCuts() ⟶ bool
DuplicateTimeline(timelineName) ⟶ Timeline
Export(fileName, exportType, exportSubtype) ⟶ bool
GetCurrentClipThumbnailImage() ⟶ dict
GetCurrentTimecode() ⟶ str
GetCurrentVideoItem() ⟶ item
GetEndFrame() ⟶ int
GetIsTrackEnabled(trackType, trackIndex) ⟶ bool
GetIsTrackLocked(trackType, trackIndex) ⟶ bool
GetItemListInTrack(trackType, index) ⟶ list
GetMarkerByCustomData(customData) ⟶ dict
GetMarkerCustomData(frameId) ⟶ str
GetMarkers() ⟶ dict
GetName() ⟶ str
GetNodeGraph() ⟶ Graph
GetSetting(settingName) ⟶ str
GetStartFrame() ⟶ int
GetStartTimecode() ⟶ str
GetTrackCount(trackType) ⟶ int
GetTrackName(trackType, trackIndex) ⟶ str
GetUniqueId() ⟶ str
GrabAllStills(stillFrameSource) ⟶ list
GrabStill() ⟶ GalleryStill
ImportIntoTimeline(filePath, importOptions={}) ⟶ bool
InsertFusionCompositionIntoTimeline() ⟶ TimelineItem
InsertFusionGeneratorIntoTimeline(generatorName) ⟶ TimelineItem
InsertFusionTitleIntoTimeline(titleName) ⟶ TimelineItem
InsertGeneratorIntoTimeline(generatorName) ⟶ TimelineItem
InsertOFXGeneratorIntoTimeline(generatorName) ⟶ TimelineItem
InsertTitleIntoTimeline(titleName) ⟶ TimelineItem
SetClipsLinked([timelineItems], Bool) ⟶ bool
SetCurrentTimecode(timecode) ⟶ bool
SetName(timelineName) ⟶ bool
SetSetting(settingName, settingValue) ⟶ bool
SetStartTimecode(timecode) ⟶ bool
SetTrackEnable(trackType, trackIndex, Bool) ⟶ bool
SetTrackLock(trackType, trackIndex, Bool) ⟶ bool
SetTrackName(trackType, trackIndex, name) ⟶ bool
UpdateMarkerCustomData(frameId, customData) ⟶ bool
```

## TimelineItem
```python
AddFlag(color) ⟶ bool
AddFusionComp() ⟶ FusionComp
AddMarker(frameId, color, name, note, duration, customData) ⟶ bool
AddTake(mediaPoolItem, startFrame=None, endFrame=None) ⟶ bool
AddVersion(versionName, versionType) ⟶ bool
ApplyArriCdlLut() ⟶ bool
AssignToColorGroup(ColorGroup) ⟶ bool
ClearClipColor() ⟶ bool
ClearFlags(color) ⟶ bool
CopyGrades(tgtTimelineItems) ⟶ bool
CreateMagicMask(mode) ⟶ bool
DeleteFusionCompByName(compName) ⟶ bool
DeleteMarkerAtFrame(frameNum) ⟶ bool
DeleteMarkerByCustomData(customData) ⟶ bool
DeleteMarkersByColor(color) ⟶ bool
DeleteTakeByIndex(idx) ⟶ bool
DeleteVersionByName(versionName, versionType) ⟶ bool
ExportFusionComp(path, compIndex) ⟶ bool
ExportLUT(exportType, path) ⟶ bool
FinalizeTake() ⟶ bool
GetClipColor() ⟶ str
GetClipEnabled() ⟶ bool
GetCurrentVersion() ⟶ dict
GetDuration() ⟶ int
GetEnd() ⟶ int
GetFlagList() ⟶ list
GetFusionCompByIndex(compIndex) ⟶ FusionComp
GetFusionCompByName(compName) ⟶ FusionComp
GetFusionCompCount() ⟶ int
GetFusionCompNameList() ⟶ list
GetLeftOffset() ⟶ int
GetLinkedItems() ⟶ list
GetMarkerByCustomData(customData) ⟶ dict
GetMarkerCustomData(frameId) ⟶ str
GetMarkers() ⟶ dict
GetMediaPoolItem() ⟶ MediaPoolItem
GetName() ⟶ str
GetNodeGraph(layerIdx=None) ⟶ Graph
GetProperty(propertyKey=None) ⟶ int | dict
GetRightOffset() ⟶ int
GetSelectedTakeIndex() ⟶ int
GetStart() ⟶ int
GetStereoConvergenceValues() ⟶ dict
GetStereoLeftFloatingWindowParams() ⟶ dict
GetStereoRightFloatingWindowParams() ⟶ dict
GetTakeByIndex(idx) ⟶ dict
GetTakesCount() ⟶ int
GetTrackTypeAndIndex() ⟶ list
GetUniqueId() ⟶ str
GetVersionNameList(versionType) ⟶ list
ImportFusionComp(path) ⟶ FusionComp
LoadBurnInPreset(presetName) ⟶ bool
LoadFusionCompByName(compName) ⟶ FusionComp
RegenerateMagicMask() ⟶ bool
RemoveFromColorGroup() ⟶ bool
RenameFusionCompByName(oldName, newName) ⟶ bool
RenameVersionByName(oldName, newName, versionType) ⟶ bool
ReplaceClip(filePath) ⟶ bool
SelectTakeByIndex(idx) ⟶ bool
SetCDL(CDL_map) ⟶ bool
SetClipColor(colorName) ⟶ bool
SetClipEnabled(enabled) ⟶ bool
SetProperty(propertyKey, propertyValue) ⟶ bool
SmartReframe() ⟶ bool
Stabilize() ⟶ bool
TranscribeAudio() ⟶ bool
UpdateMarkerCustomData(frameId, customData) ⟶ bool
UpdateSidecar() ⟶ bool
```

## Gallery methods
```python
GetAlbumName(galleryStillAlbum) ⟶ str
GetCurrentStillAlbum() ⟶ GalleryStillAlbum
GetGalleryStillAlbums() ⟶ list
SetAlbumName(galleryStillAlbum, albumName) ⟶ bool
SetCurrentStillAlbum(galleryStillAlbum) ⟶ bool
```

## GalleryStillAlbum methods
```python
DeleteStills(galleryStill) ⟶ bool
ExportStills(galleryStill, folderPath, filePrefix, format) ⟶ bool
GetLabel(galleryStill) ⟶ str
GetStills() ⟶ list
ImportStills(filePaths) ⟶ bool
SetLabel(galleryStill, label) ⟶ bool
```

## Graph methods
```python
GetLUT(nodeIndex) ⟶ str
GetNodeLabel(nodeIndex) ⟶ str
GetNumNodes() ⟶ int
GetToolsInNode(nodeIndex) ⟶ list
SetLUT(nodeIndex, lutPath) ⟶ bool
SetNodeEnabled(nodeIndex, isEnabled) ⟶ bool
```

## ColorGroup methods
```python
GetClipsInTimeline(Timeline=CurrTimeline) ⟶ list
GetName() ⟶ str
GetPostClipNodeGraph() ⟶ Graph
GetPreClipNodeGraph() ⟶ Graph
SetName(groupName) ⟶ bool
```