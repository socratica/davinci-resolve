# DaVinci Resolve Scripting API Documentation

## Resolve Class

### Methods

```python
GetProjectManager() ⟶ ProjectManager
# Returns the ProjectManager object, which provides access to project-related functions.
```

```python
GetCurrentProject() ⟶ Project
# Returns the current Project object that is active in DaVinci Resolve.
```

---

## ProjectManager Class

### Methods

```python
CreateProject(projectName: str) ⟶ Project
# Creates a new project with the specified name.
# Returns the created Project object.
```

```python
DeleteProject(projectName: str) ⟶ bool
# Deletes the project with the specified name.
# Returns `True` if the deletion was successful, `False` otherwise.
```

```python
GetProjectList() ⟶ list
# Returns a list of all available projects.
```

```python
LoadProject(projectName: str) ⟶ Project
# Loads the project with the specified name.
# Returns the loaded Project object.
```

```python
GetCurrentProject() ⟶ Project
# Returns the currently active Project object.
```

---

## Project Class

### Methods

```python
GetName() ⟶ str
# Returns the name of the project.
```

```python
SetName(projectName: str) ⟶ bool
# Sets a new name for the project.
# Returns `True` if the name was successfully set, `False` otherwise.
```

```python
GetRenderQueue() ⟶ list
# Returns the list of render jobs in the project's render queue.
```

```python
AddRenderJob(job: dict) ⟶ str
# Adds a new render job to the render queue.
# Returns the ID of the newly created job.
```

```python
DeleteRenderJob(jobId: str) ⟶ bool
# Deletes the render job with the specified ID.
# Returns `True` if the job was successfully deleted, `False` otherwise.
```

## Timeline Class

### Methods

```python
GetName() ⟶ str
# Returns the name of the timeline.
```

```python
SetName(timelineName: str) ⟶ bool
# Sets a new name for the timeline.
# Returns `True` if the name was successfully set, `False` otherwise.
```

```python
GetTrackCount(trackType: str) ⟶ int
# Returns the number of tracks of the specified type in the timeline.
# - trackType can be "video", "audio", or "subtitle".
```

```python
GetItemListInTrack(trackType: str, trackIndex: int) ⟶ list
# Returns a list of items in the specified track.
# - trackType can be "video", "audio", or "subtitle".
```

```python
InsertTrack(trackType: str, index: int) ⟶ bool
# Inserts a new track at the specified index.
# - trackType can be "video", "audio", or "subtitle".
# Returns `True` if the track was successfully inserted, `False` otherwise.
```

```python
DeleteTrack(trackType: str, index: int) ⟶ bool
# Deletes the track at the specified index.
# - trackType can be "video", "audio", or "subtitle".
# Returns `True` if the track was successfully deleted, `False` otherwise.
```

```python
GetItemByIndex(trackType: str, trackIndex: int, itemIndex: int) ⟶ TimelineItem
# Returns the TimelineItem at the specified index within the track.
```

```python
AppendItem(item: MediaPoolItem) ⟶ bool
# Appends a MediaPoolItem to the timeline.
# Returns `True` if the item was successfully appended, `False` otherwise.
```

---

## TimelineItem Class

### Methods

```python
GetName() ⟶ str
# Returns the name of the timeline item.
```

```python
SetName(itemName: str) ⟶ bool
# Sets a new name for the timeline item.
# Returns `True` if the name was successfully set, `False` otherwise.
```

```python
GetStart() ⟶ int
# Returns the start frame of the timeline item.
```

```python
GetEnd() ⟶ int
# Returns the end frame of the timeline item.
```

```python
GetDuration() ⟶ int
# Returns the duration of the timeline item in frames.
```

```python
SetStart(startFrame: int) ⟶ bool
# Sets the start frame of the timeline item.
# Returns `True` if the start frame was successfully set, `False` otherwise.
```

```python
SetEnd(endFrame: int) ⟶ bool
# Sets the end frame of the timeline item.
# Returns `True` if the end frame was successfully set, `False` otherwise.
```

```python
SetDuration(duration: int) ⟶ bool
# Sets the duration of the timeline item in frames.
# Returns `True` if the duration was successfully set, `False` otherwise.
```

## MediaPool Class

### Methods

```python
ImportMedia(filePath: str) ⟶ MediaPoolItem
# Imports a media file from the specified file path into the Media Pool.
# Returns the imported MediaPoolItem.
```

```python
DeleteMediaPoolItem(mediaPoolItem: MediaPoolItem) ⟶ bool
# Deletes the specified MediaPoolItem from the Media Pool.
# Returns `True` if the item was successfully deleted, `False` otherwise.
```

```python
MoveMediaPoolItem(mediaPoolItem: MediaPoolItem, targetBin: MediaBin) ⟶ bool
# Moves the specified MediaPoolItem to the target MediaBin.
# Returns `True` if the item was successfully moved, `False` otherwise.
```

```python
GetRootFolder() ⟶ MediaBin
# Returns the root MediaBin of the Media Pool.
```

```python
CreateFolder(folderName: str) ⟶ MediaBin
# Creates a new folder in the Media Pool with the specified name.
# Returns the created MediaBin.
```

```python
DeleteFolder(mediaBin: MediaBin) ⟶ bool
# Deletes the specified MediaBin from the Media Pool.
# Returns `True` if the folder was successfully deleted, `False` otherwise.
```

```python
GetCurrentFolder() ⟶ MediaBin
# Returns the currently active MediaBin.
```

```python
SetCurrentFolder(mediaBin: MediaBin) ⟶ bool
# Sets the specified MediaBin as the currently active folder in the Media Pool.
# Returns `True` if the folder was successfully set, `False` otherwise.
```

---

## MediaBin Class

### Methods

```python
GetName() ⟶ str
# Returns the name of the MediaBin.
```

```python
SetName(folderName: str) ⟶ bool
# Sets a new name for the MediaBin.
# Returns `True` if the name was successfully set, `False` otherwise.
```

```python
GetClipCount() ⟶ int
# Returns the number of clips in the MediaBin.
```

```python
GetClipByIndex(index: int) ⟶ MediaPoolItem
# Returns the MediaPoolItem at the specified index within the MediaBin.
```

```python
GetClips() ⟶ list
# Returns a list of all MediaPoolItems in the MediaBin.
```

```python
DeleteClip(mediaPoolItem: MediaPoolItem) ⟶ bool
# Deletes the specified MediaPoolItem from the MediaBin.
# Returns `True` if the item was successfully deleted, `False` otherwise.
```

```python
MoveClip(mediaPoolItem: MediaPoolItem, targetBin: MediaBin) ⟶ bool
# Moves the specified MediaPoolItem to another MediaBin.
# Returns `True` if the item was successfully moved, `False` otherwise.
```

## MediaPoolItem Class

### Methods

```python
GetName() ⟶ str
# Returns the name of the MediaPoolItem.
```

```python
SetName(itemName: str) ⟶ bool
# Sets a new name for the MediaPoolItem.
# Returns `True` if the name was successfully set, `False` otherwise.
```

```python
GetMediaPath() ⟶ str
# Returns the file path of the media associated with the MediaPoolItem.
```

```python
GetDuration() ⟶ int
# Returns the duration of the MediaPoolItem in frames.
```

```python
GetClipColor() ⟶ str
# Returns the color label of the MediaPoolItem.
```

```python
SetClipColor(colorName: str) ⟶ bool
# Sets a new color label for the MediaPoolItem.
# Returns `True` if the color was successfully set, `False` otherwise.
```

```python
Delete() ⟶ bool
# Deletes the MediaPoolItem from the Media Pool.
# Returns `True` if the item was successfully deleted, `False` otherwise.
```

```python
Move(targetBin: MediaBin) ⟶ bool
# Moves the MediaPoolItem to the specified MediaBin.
# Returns `True` if the item was successfully moved, `False` otherwise.
```

---

## RenderJob Class

### Methods

```python
GetJobId() ⟶ str
# Returns the unique ID of the render job.
```

```python
GetStatus() ⟶ str
# Returns the current status of the render job (e.g., "Queued", "Rendering", "Completed").
```

```python
GetProgress() ⟶ float
# Returns the progress of the render job as a percentage.
```

```python
Cancel() ⟶ bool
# Cancels the render job.
# Returns `True` if the job was successfully canceled, `False` otherwise.
```

```python
Delete() ⟶ bool
# Deletes the render job from the queue.
# Returns `True` if the job was successfully deleted, `False` otherwise.
```

## Fusion Class

### Methods

```python
LoadComp(path: str) ⟶ bool
# Loads a Fusion composition from the specified file path.
# Returns `True` if the composition was successfully loaded, `False` otherwise.
```

```python
SaveComp(path: str) ⟶ bool
# Saves the current Fusion composition to the specified file path.
# Returns `True` if the composition was successfully saved, `False` otherwise.
```

```python
GetCurrentComp() ⟶ FusionComp
# Returns the currently active Fusion composition.
```

```python
CreateComp() ⟶ FusionComp
# Creates a new Fusion composition and returns the FusionComp object.
```

```python
CloseComp(comp: FusionComp) ⟶ bool
# Closes the specified Fusion composition.
# Returns `True` if the composition was successfully closed, `False` otherwise.
```

---

## FusionComp Class

### Methods

```python
AddTool(toolName: str, toolType: str, xPos: float, yPos: float) ⟶ Tool
# Adds a new tool to the Fusion composition at the specified position.
# - toolName is the name of the tool.
# - toolType specifies the type of tool (e.g., "Loader", "Saver").
# - xPos and yPos determine the position of the tool in the composition flow.
# Returns the created Tool object.
```

```python
GetToolList() ⟶ list
# Returns a list of all tools in the Fusion composition.
```

```python
DeleteTool(tool: Tool) ⟶ bool
# Deletes the specified tool from the Fusion composition.
# Returns `True` if the tool was successfully deleted, `False` otherwise.
```

```python
GetFrameRange() ⟶ tuple
# Returns the start and end frames of the Fusion composition as a tuple (startFrame, endFrame).
```

```python
SetFrameRange(startFrame: int, endFrame: int) ⟶ bool
# Sets the start and end frames of the Fusion composition.
# Returns `True` if the frame range was successfully set, `False` otherwise.
```

```python
Render(startFrame: int = None, endFrame: int = None) ⟶ bool
# Renders the Fusion composition.
# If startFrame and endFrame are provided, renders only that frame range.
# Returns `True` if the composition was successfully rendered, `False` otherwise.
```

```python
Save(path: str) ⟶ bool
# Saves the Fusion composition to the specified file path.
# Returns `True` if the composition was successfully saved, `False` otherwise.
```

---

## Tool Class

### Methods

```python
GetAttrs() ⟶ dict
# Returns a dictionary of attributes for the tool.
```

```python
SetAttrs(attrs: dict) ⟶ bool
# Sets the specified attributes for the tool using a dictionary.
# Returns `True` if the attributes were successfully set, `False` otherwise.
```

```python
GetInputList() ⟶ list
# Returns a list of input connections for the tool.
```

```python
ConnectInput(inputName: str, source: Tool) ⟶ bool
# Connects the specified input to the output of another tool.
# - inputName is the name of the input to connect.
# - source is the tool to connect to the input.
# Returns `True` if the input was successfully connected, `False` otherwise.
```

```python
DisconnectInput(inputName: str) ⟶ bool
# Disconnects the specified input.
# Returns `True` if the input was successfully disconnected, `False` otherwise.
```

```python
Delete() ⟶ bool
# Deletes the tool from the Fusion composition.
# Returns `True` if the tool was successfully deleted, `False` otherwise.
```

## MediaStorage Class

### Methods

```python
GetMountedVolumeList() ⟶ list
# Returns a list of mounted volumes (drives) available in the system.
```

```python
GetFolderList(volumePath: str) ⟶ list
# Returns a list of folders in the specified volume path.
# - volumePath is the path to the volume whose folders you want to retrieve.
```

```python
GetFileList(folderPath: str) ⟶ list
# Returns a list of files in the specified folder path.
# - folderPath is the path to the folder whose files you want to retrieve.
```

```python
RevealInStorage(path: str) ⟶ bool
# Reveals the specified file or folder in the Media Storage.
# Returns `True` if the item was successfully revealed, `False` otherwise.
```

```python
AddItemToMediaPool(filePath: str) ⟶ MediaPoolItem
# Adds the specified file to the Media Pool.
# - filePath is the path to the media file you want to add.
# Returns the MediaPoolItem created.
```

```python
AddItemsToMediaPool(filePaths: list) ⟶ list
# Adds the specified list of files to the Media Pool.
# - filePaths is a list of paths to media files you want to add.
# Returns a list of MediaPoolItems created.
```

```python
ImportMedia(filePath: str) ⟶ MediaPoolItem
# Imports the specified media file into the Media Pool.
# - filePath is the path to the media file you want to import.
# Returns the MediaPoolItem created.
```

---

## Gallery Class

### Methods

```python
GetStill(index: int) ⟶ GalleryStill
# Returns the GalleryStill object at the specified index in the gallery.
```

```python
GetStillCount() ⟶ int
# Returns the number of stills in the gallery.
```

```python
DeleteStill(galleryStill: GalleryStill) ⟶ bool
# Deletes the specified GalleryStill from the gallery.
# Returns `True` if the still was successfully deleted, `False` otherwise.
```

```python
ExportStill(galleryStill: GalleryStill, filePath: str) ⟶ bool
# Exports the specified GalleryStill to a file.
# - filePath is the path to export the still to.
# Returns `True` if the still was successfully exported, `False` otherwise.
```

```python
ImportStill(filePath: str) ⟶ GalleryStill
# Imports a still image from the specified file path into the gallery.
# Returns the imported GalleryStill object.
```

---

## GalleryStill Class

### Methods

```python
GetName() ⟶ str
# Returns the name of the GalleryStill.
```

```python
SetName(stillName: str) ⟶ bool
# Sets a new name for the GalleryStill.
# Returns `True` if the name was successfully set, `False` otherwise.
```

```python
Delete() ⟶ bool
# Deletes the GalleryStill from the gallery.
# Returns `True` if the still was successfully deleted, `False` otherwise.
```

```python
Export(filePath: str) ⟶ bool
# Exports the GalleryStill to the specified file path.
# Returns `True` if the still was successfully exported, `False` otherwise.
```

## Marker Class

### Methods

```python
GetColor() ⟶ str
# Returns the color of the marker.
```

```python
SetColor(color: str) ⟶ bool
# Sets a new color for the marker.
# Returns `True` if the color was successfully set, `False` otherwise.
```

```python
GetName() ⟶ str
# Returns the name of the marker.
```

```python
SetName(markerName: str) ⟶ bool
# Sets a new name for the marker.
# Returns `True` if the name was successfully set, `False` otherwise.
```

```python
GetNote() ⟶ str
# Returns the note associated with the marker.
```

```python
SetNote(note: str) ⟶ bool
# Sets a new note for the marker.
# Returns `True` if the note was successfully set, `False` otherwise.
```

```python
GetDuration() ⟶ int
# Returns the duration of the marker in frames.
```

```python
SetDuration(duration: int) ⟶ bool
# Sets a new duration for the marker in frames.
# Returns `True` if the duration was successfully set, `False` otherwise.
```

```python
GetStart() ⟶ int
# Returns the start frame of the marker.
```

```python
SetStart(startFrame: int) ⟶ bool
# Sets a new start frame for the marker.
# Returns `True` if the start frame was successfully set, `False` otherwise.
```

---

## FusionOperator Class

### Methods

```python
GetName() ⟶ str
# Returns the name of the FusionOperator.
```

```python
SetName(operatorName: str) ⟶ bool
# Sets a new name for the FusionOperator.
# Returns `True` if the name was successfully set, `False` otherwise.
```

```python
GetInputList() ⟶ list
# Returns a list of input connections for the FusionOperator.
```

```python
ConnectInput(inputName: str, source: FusionOperator) ⟶ bool
# Connects the specified input to the output of another FusionOperator.
# - inputName is the name of the input to connect.
# - source is the FusionOperator to connect to the input.
# Returns `True` if the input was successfully connected, `False` otherwise.
```

```python
DisconnectInput(inputName: str) ⟶ bool
# Disconnects the specified input.
# Returns `True` if the input was successfully disconnected, `False` otherwise.
```

```python
Delete() ⟶ bool
# Deletes the FusionOperator from the Fusion composition.
# Returns `True` if the FusionOperator was successfully deleted, `False` otherwise.
```

---

## Clip Class

### Methods

```python
GetName() ⟶ str
# Returns the name of the clip.
```

```python
SetName(clipName: str) ⟶ bool
# Sets a new name for the clip.
# Returns `True` if the name was successfully set, `False` otherwise.
```

```python
GetDuration() ⟶ int
# Returns the duration of the clip in frames.
```

```python
SetDuration(duration: int) ⟶ bool
# Sets a new duration for the clip in frames.
# Returns `True` if the duration was successfully set, `False` otherwise.
```

```python
GetStart() ⟶ int
# Returns the start frame of the clip.
```

```python
SetStart(startFrame: int) ⟶ bool
# Sets a new start frame for the clip.
# Returns `True` if the start frame was successfully set, `False` otherwise.
```

```python
GetEnd() ⟶ int
# Returns the end frame of the clip.
```

```python
SetEnd(endFrame: int) ⟶ bool
# Sets a new end frame for the clip.
# Returns `True` if the end frame was successfully set, `False` otherwise.
```

```python
GetFrameRate() ⟶ float
# Returns the frame rate of the clip.
```

```python
SetFrameRate(frameRate: float) ⟶ bool
# Sets a new frame rate for the clip.
# Returns `True` if the frame rate was successfully set, `False` otherwise.
```

```python
GetColor() ⟶ str
# Returns the color label of the clip.
```

```python
SetColor(colorName: str) ⟶ bool
# Sets a new color label for the clip.
# Returns `True` if the color was successfully set, `False` otherwise.
```

## MarkerList Class

### Methods

```python
GetCount() ⟶ int
# Returns the number of markers in the MarkerList.
```

```python
GetMarkerByIndex(index: int) ⟶ Marker
# Returns the Marker object at the specified index in the MarkerList.
```

```python
GetMarkerByColor(color: str) ⟶ list
# Returns a list of Marker objects that have the specified color.
```

```python
GetMarkerByName(markerName: str) ⟶ Marker
# Returns the Marker object that matches the specified name.
```

```python
AddMarker(frameId: int, color: str, name: str, note: str, duration: int) ⟶ Marker
# Adds a new Marker to the MarkerList at the specified frame.
# - frameId is the start frame of the marker.
# - color is the color of the marker.
# - name is the name of the marker.
# - note is the note associated with the marker.
# - duration is the duration of the marker in frames.
# Returns the created Marker object.
```

```python
DeleteMarkerByIndex(index: int) ⟶ bool
# Deletes the Marker at the specified index in the MarkerList.
# Returns `True` if the marker was successfully deleted, `False` otherwise.
```

```python
DeleteMarkerByColor(color: str) ⟶ int
# Deletes all Markers that have the specified color.
# Returns the number of markers that were successfully deleted.
```

```python
DeleteMarkerByName(markerName: str) ⟶ bool
# Deletes the Marker that matches the specified name.
# Returns `True` if the marker was successfully deleted, `False` otherwise.
```

---

## Track Class

### Methods

```python
GetTrackType() ⟶ str
# Returns the type of the track (e.g., "video", "audio", "subtitle").
```

```python
GetTrackIndex() ⟶ int
# Returns the index of the track in the timeline.
```

```python
GetItemCount() ⟶ int
# Returns the number of items in the track.
```

```python
GetItemByIndex(index: int) ⟶ TimelineItem
# Returns the TimelineItem at the specified index within the track.
```

```python
InsertItem(item: MediaPoolItem, index: int) ⟶ bool
# Inserts a MediaPoolItem into the track at the specified index.
# Returns `True` if the item was successfully inserted, `False` otherwise.
```

```python
DeleteItem(index: int) ⟶ bool
# Deletes the TimelineItem at the specified index within the track.
# Returns `True` if the item was successfully deleted, `False` otherwise.
```

```python
MoveItem(item: TimelineItem, newIndex: int) ⟶ bool
# Moves the specified TimelineItem to a new index within the track.
# Returns `True` if the item was successfully moved, `False` otherwise.
```

```python
GetMarkerList() ⟶ MarkerList
# Returns the MarkerList associated with the track.
```

## Timeline Class

### Methods

```python
GetTrackCount(trackType: str) ⟶ int
# Returns the number of tracks of the specified type in the timeline.
# - trackType can be "video", "audio", or "subtitle".
```

```python
GetTrackByIndex(trackType: str, trackIndex: int) ⟶ Track
# Returns the Track object at the specified index of the given type.
# - trackType can be "video", "audio", or "subtitle".
```

```python
InsertTrack(trackType: str, trackIndex: int) ⟶ bool
# Inserts a new track of the specified type at the given index.
# - trackType can be "video", "audio", or "subtitle".
# Returns `True` if the track was successfully inserted, `False` otherwise.
```

```python
DeleteTrack(trackType: str, trackIndex: int) ⟶ bool
# Deletes the track of the specified type at the given index.
# - trackType can be "video", "audio", or "subtitle".
# Returns `True` if the track was successfully deleted, `False` otherwise.
```

```python
MoveTrack(trackType: str, sourceIndex: int, destinationIndex: int) ⟶ bool
# Moves the track of the specified type from the source index to the destination index.
# - trackType can be "video", "audio", or "subtitle".
# Returns `True` if the track was successfully moved, `False` otherwise.
```

```python
GetCurrentTimelineItem() ⟶ TimelineItem
# Returns the currently selected TimelineItem in the timeline.
```

```python
GetItemListInTrack(trackType: str, trackIndex: int) ⟶ list
# Returns a list of TimelineItems in the specified track.
# - trackType can be "video", "audio", or "subtitle".
```

```python
AppendItem(item: MediaPoolItem) ⟶ bool
# Appends a MediaPoolItem to the end of the timeline.
# Returns `True` if the item was successfully appended, `False` otherwise.
```

```python
InsertItem(item: MediaPoolItem, trackType: str, trackIndex: int, frameId: int) ⟶ bool
# Inserts a MediaPoolItem into the specified track at the given frame.
# - trackType can be "video", "audio", or "subtitle".
# Returns `True` if the item was successfully inserted, `False` otherwise.
```

```python
DeleteItem(trackType: str, trackIndex: int, itemIndex: int) ⟶ bool
# Deletes the TimelineItem at the specified index in the given track.
# - trackType can be "video", "audio", or "subtitle".
# Returns `True` if the item was successfully deleted, `False` otherwise.
```

```python
MoveItem(trackType: str, sourceIndex: int, destinationIndex: int) ⟶ bool
# Moves the TimelineItem from the source index to the destination index within the specified track.
# - trackType can be "video", "audio", or "subtitle".
# Returns `True` if the item was successfully moved, `False` otherwise.
```

```python
GetMarkerList() ⟶ MarkerList
# Returns the MarkerList associated with the timeline.
```

```python
AddMarker(frameId: int, color: str, name: str, note: str, duration: int) ⟶ Marker
# Adds a new Marker to the timeline at the specified frame.
# - frameId is the start frame of the marker.
# - color is the color of the marker.
# - name is the name of the marker.
# - note is the note associated with the marker.
# - duration is the duration of the marker in frames.
# Returns the created Marker object.
```

```python
DeleteMarkerByIndex(index: int) ⟶ bool
# Deletes the Marker at the specified index in the timeline.
# Returns `True` if the marker was successfully deleted, `False` otherwise.
```

```python
DeleteMarkerByColor(color: str) ⟶ int
# Deletes all Markers that have the specified color in the timeline.
# Returns the number of markers that were successfully deleted.
```

```python
DeleteMarkerByName(markerName: str) ⟶ bool
# Deletes the Marker that matches the specified name in the timeline.
# Returns `True` if the marker was successfully deleted, `False` otherwise.
```

```python
GetCurrentFrame() ⟶ int
# Returns the current frame in the timeline.
```

```python
SetCurrentFrame(frameId: int) ⟶ bool
# Sets the current frame in the timeline.
# Returns `True` if the frame was successfully set, `False` otherwise.
```

## MediaClip Class

### Methods

```python
GetClipColor() ⟶ str
# Returns the color label of the MediaClip.
```

```python
SetClipColor(colorName: str) ⟶ bool
# Sets a new color label for the MediaClip.
# Returns `True` if the color was successfully set, `False` otherwise.
```

```python
GetMediaPath() ⟶ str
# Returns the file path of the media associated with the MediaClip.
```

```python
GetDuration() ⟶ int
# Returns the duration of the MediaClip in frames.
```

```python
GetStart() ⟶ int
# Returns the start frame of the MediaClip.
```

```python
SetStart(startFrame: int) ⟶ bool
# Sets a new start frame for the MediaClip.
# Returns `True` if the start frame was successfully set, `False` otherwise.
```

```python
GetEnd() ⟶ int
# Returns the end frame of the MediaClip.
```

```python
SetEnd(endFrame: int) ⟶ bool
# Sets a new end frame for the MediaClip.
# Returns `True` if the end frame was successfully set, `False` otherwise.
```

```python
GetFrameRate() ⟶ float
# Returns the frame rate of the MediaClip.
```

```python
SetFrameRate(frameRate: float) ⟶ bool
# Sets a new frame rate for the MediaClip.
# Returns `True` if the frame rate was successfully set, `False` otherwise.
```

---

## MediaPoolClip Class

### Methods

```python
GetClipColor() ⟶ str
# Returns the color label of the MediaPoolClip.
```

```python
SetClipColor(colorName: str) ⟶ bool
# Sets a new color label for the MediaPoolClip.
# Returns `True` if the color was successfully set, `False` otherwise.
```

```python
GetMediaPath() ⟶ str
# Returns the file path of the media associated with the MediaPoolClip.
```

```python
GetDuration() ⟶ int
# Returns the duration of the MediaPoolClip in frames.
```

```python
GetStart() ⟶ int
# Returns the start frame of the MediaPoolClip.
```

```python
SetStart(startFrame: int) ⟶ bool
# Sets a new start frame for the MediaPoolClip.
# Returns `True` if the start frame was successfully set, `False` otherwise.
```

```python
GetEnd() ⟶ int
# Returns the end frame of the MediaPoolClip.
```

```python
SetEnd(endFrame: int) ⟶ bool
# Sets a new end frame for the MediaPoolClip.
# Returns `True` if the end frame was successfully set, `False` otherwise.
```

```python
GetFrameRate() ⟶ float
# Returns the frame rate of the MediaPoolClip.
```

```python
SetFrameRate(frameRate: float) ⟶ bool
# Sets a new frame rate for the MediaPoolClip.
# Returns `True` if the frame rate was successfully set, `False` otherwise.
```

---

## RenderSettings Class

### Methods

```python
GetFormat() ⟶ str
# Returns the current render format (e.g., "mp4", "mov").
```

```python
SetFormat(format: str) ⟶ bool
# Sets the render format.
# Returns `True` if the format was successfully set, `False` otherwise.
```

```python
GetCodec() ⟶ str
# Returns the current render codec (e.g., "H.264", "ProRes").
```

```python
SetCodec(codec: str) ⟶ bool
# Sets the render codec.
# Returns `True` if the codec was successfully set, `False` otherwise.
```

```python
GetResolution() ⟶ tuple
# Returns the current render resolution as a tuple (width, height).
```

```python
SetResolution(width: int, height: int) ⟶ bool
# Sets the render resolution.
# Returns `True` if the resolution was successfully set, `False` otherwise.
```

```python
GetFrameRate() ⟶ float
# Returns the current render frame rate.
```

```python
SetFrameRate(frameRate: float) ⟶ bool
# Sets the render frame rate.
# Returns `True` if the frame rate was successfully set, `False` otherwise.
```

## Deliverable Class

### Methods

```python
GetName() ⟶ str
# Returns the name of the deliverable.
```

```python
SetName(deliverableName: str) ⟶ bool
# Sets a new name for the deliverable.
# Returns `True` if the name was successfully set, `False` otherwise.
```

```python
GetRenderSettings() ⟶ RenderSettings
# Returns the RenderSettings object associated with the deliverable.
```

```python
SetRenderSettings(settings: RenderSettings) ⟶ bool
# Applies the specified RenderSettings to the deliverable.
# Returns `True` if the settings were successfully applied, `False` otherwise.
```

```python
GetRenderQueue() ⟶ list
# Returns the list of render jobs in the deliverable's render queue.
```

```python
AddRenderJob(job: dict) ⟶ str
# Adds a new render job to the deliverable's render queue.
# Returns the ID of the newly created job.
```

```python
DeleteRenderJob(jobId: str) ⟶ bool
# Deletes the render job with the specified ID from the deliverable's render queue.
# Returns `True` if the job was successfully deleted, `False` otherwise.
```

```python
StartRendering(jobIds: list = None, isInteractiveMode: bool = False) ⟶ bool
# Starts rendering the specified jobs in the deliverable's render queue.
# If no job IDs are provided, all jobs will be rendered.
# If isInteractiveMode is set to True, error feedback is enabled in the UI during rendering.
# Returns `True` if the rendering was successfully started, `False` otherwise.
```

```python
StopRendering() ⟶ bool
# Stops any current rendering processes in the deliverable's render queue.
# Returns `True` if the rendering was successfully stopped, `False` otherwise.
```

```python
IsRenderingInProgress() ⟶ bool
# Returns `True` if rendering is currently in progress for any jobs in the deliverable's render queue, `False` otherwise.
```

---

## ResolveUser Class

### Methods

```python
GetName() ⟶ str
# Returns the name of the ResolveUser.
```

```python
SetName(userName: str) ⟶ bool
# Sets a new name for the ResolveUser.
# Returns `True` if the name was successfully set, `False` otherwise.
```

```python
GetEmail() ⟶ str
# Returns the email address of the ResolveUser.
```

```python
SetEmail(email: str) ⟶ bool
# Sets a new email address for the ResolveUser.
# Returns `True` if the email was successfully set, `False` otherwise.
```

```python
GetPhoneNumber() ⟶ str
# Returns the phone number of the ResolveUser.
```

```python
SetPhoneNumber(phoneNumber: str) ⟶ bool
# Sets a new phone number for the ResolveUser.
# Returns `True` if the phone number was successfully set, `False` otherwise.
```

```python
GetRole() ⟶ str
# Returns the role of the ResolveUser (e.g., "Administrator", "Editor").
```

```python
SetRole(role: str) ⟶ bool
# Sets a new role for the ResolveUser.
# Returns `True` if the role was successfully set, `False` otherwise.
```

## ExportSettings Class

### Methods

```python
GetFileName() ⟶ str
# Returns the name of the file to be exported.
```

```python
SetFileName(fileName: str) ⟶ bool
# Sets the name of the file to be exported.
# Returns `True` if the name was successfully set, `False` otherwise.
```

```python
GetFilePath() ⟶ str
# Returns the path of the file to be exported.
```

```python
SetFilePath(filePath: str) ⟶ bool
# Sets the path of the file to be exported.
# Returns `True` if the path was successfully set, `False` otherwise.
```

```python
GetCodec() ⟶ str
# Returns the codec to be used for the export (e.g., "H.264", "ProRes").
```

```python
SetCodec(codec: str) ⟶ bool
# Sets the codec to be used for the export.
# Returns `True` if the codec was successfully set, `False` otherwise.
```

```python
GetResolution() ⟶ tuple
# Returns the resolution for the export as a tuple (width, height).
```

```python
SetResolution(width: int, height: int) ⟶ bool
# Sets the resolution for the export.
# Returns `True` if the resolution was successfully set, `False` otherwise.
```

```python
GetFrameRate() ⟶ float
# Returns the frame rate for the export.
```

```python
SetFrameRate(frameRate: float) ⟶ bool
# Sets the frame rate for the export.
# Returns `True` if the frame rate was successfully set, `False` otherwise.
```

```python
GetBitRate() ⟶ int
# Returns the bit rate for the export in kbps.
```

```python
SetBitRate(bitRate: int) ⟶ bool
# Sets the bit rate for the export in kbps.
# Returns `True` if the bit rate was successfully set, `False` otherwise.
```

```python
GetAudioSettings() ⟶ dict
# Returns a dictionary of audio settings for the export (e.g., codec, channels).
```

```python
SetAudioSettings(audioSettings: dict) ⟶ bool
# Sets the audio settings for the export using a dictionary.
# Returns `True` if the audio settings were successfully set, `False` otherwise.
```

```python
GetContainer() ⟶ str
# Returns the container format for the export (e.g., "mp4", "mov").
```

```python
SetContainer(container: str) ⟶ bool
# Sets the container format for the export.
# Returns `True` if the container was successfully set, `False` otherwise.
```

---

## ResolveApp Class

### Methods

```python
GetVersion() ⟶ str
# Returns the version of DaVinci Resolve.
```

```python
GetUser() ⟶ ResolveUser
# Returns the currently logged-in ResolveUser.
```

```python
OpenProject(projectName: str) ⟶ Project
# Opens the project with the specified name.
# Returns the Project object if successful.
```

```python
CreateProject(projectName: str) ⟶ Project
# Creates a new project with the specified name.
# Returns the Project object if successful.
```

```python
DeleteProject(projectName: str) ⟶ bool
# Deletes the project with the specified name.
# Returns `True` if the project was successfully deleted, `False` otherwise.
```

```python
GetProjectManager() ⟶ ProjectManager
# Returns the ProjectManager object, which provides access to project-related functions.
```

```python
GetCurrentProject() ⟶ Project
# Returns the currently active Project object.
```

```python
GetMediaStorage() ⟶ MediaStorage
# Returns the MediaStorage object, which provides access to the media storage functions.
```

```python
GetFusion() ⟶ Fusion
# Returns the Fusion object, which provides access to Fusion-related functions.
```

```python
GetRenderQueue() ⟶ list
# Returns the list of render jobs in the current session.
```

```python
StartRendering(jobIds: list = None, isInteractiveMode: bool = False) ⟶ bool
# Starts rendering the specified jobs in the render queue.
# If no job IDs are provided, all jobs will be rendered.
# If isInteractiveMode is set to True, error feedback is enabled in the UI during rendering.
# Returns `True` if rendering was successfully started, `False` otherwise.
```

```python
StopRendering() ⟶ bool
# Stops any current rendering processes.
# Returns `True` if rendering was successfully stopped, `False` otherwise.
```

```python
IsRenderingInProgress() ⟶ bool
# Returns `True` if rendering is currently in progress for any jobs in the render queue, `False` otherwise.
```
