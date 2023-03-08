Below are the Qt structures of most styled components of Mumble which you should greatly benefit from when making more complex skins for Mumble. All the structures are based on the XML formatted .UI files from the Mumble source code. For your convenience, the classes are in black and their names are in <i style="color:#090">italic green</i>. Each element should be formatted correctly for use in your QSS file when copied. For more information, see [[Skinning]].

Example:
<code>
 /* Change the "Custom Servers" (or the first) tab on the Connect Dialog */
 QDialog#ConnectDialog QWidget#tab {
   background: black;
   color: white;
 }
 
 /* Change the first tab on the ACL Editor and Connect Dialog */
 QWidget#tab {
   background: black;
   color: white;
 }
</code>

Structure based on git commit  [cb267a3](https://github.com/mumble-voip/mumble/commit/cb267a3606c8f65bf81961f121a6d9977692262f). (Parsed: 2016-02-11 02:02:37 GMT)


## ACL Editor (ACLEditor.ui) 

Source:  [cb267a3/src/mumble/ACLEditor.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/ACLEditor.ui)

* QDialog<i style="color:#fff">#</i><i style="color:#090">ACLEditor</i>
** QVBoxLayout
*** QTabWidget<i style="color:#fff">#</i><i style="color:#090">qtwTab</i>
**** QWidget<i style="color:#fff">#</i><i style="color:#090">qwChannel</i>
***** QFormLayout<i style="color:#fff">#</i><i style="color:#090">formLayout</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qlChannelDescription</i>
****** RichTextEditor<i style="color:#fff">#</i><i style="color:#090">rteChannelDescription</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qlChannelPassword</i>
****** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qleChannelPassword</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qlChannelPosition</i>
****** QSpinBox<i style="color:#fff">#</i><i style="color:#090">qsbChannelPosition</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qlChannelMaxUsers</i>
****** QSpinBox<i style="color:#fff">#</i><i style="color:#090">qsbChannelMaxUsers</i>
****** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbChannelTemporary</i>
****** QHBoxLayout<i style="color:#fff">#</i><i style="color:#090">qwChannelProperties</i>
******* QLineEdit<i style="color:#fff">#</i><i style="color:#090">qleChannelName</i>
******* QLabel<i style="color:#fff">#</i><i style="color:#090">qlChannelID</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qlChannelName</i>
**** QWidget<i style="color:#fff">#</i><i style="color:#090">qwGroups</i>
***** QVBoxLayout
****** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbGroups</i>
******* QHBoxLayout
******** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbGroupList</i>
******** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbGroupAdd</i>
******** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbGroupRemove</i>
******** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbGroupInherit</i>
******** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbGroupInheritable</i>
******** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbGroupInherited</i>
****** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbGroupMembers</i>
******* QGridLayout
******** QLabel<i style="color:#fff">#</i><i style="color:#090">qliGroupAdd</i>
******** QLabel<i style="color:#fff">#</i><i style="color:#090">qliGroupInherit</i>
******** QListWidget<i style="color:#fff">#</i><i style="color:#090">qlwGroupAdd</i>
******** QListWidget<i style="color:#fff">#</i><i style="color:#090">qlwGroupRemove</i>
******** QListWidget<i style="color:#fff">#</i><i style="color:#090">qlwGroupInherit</i>
******** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbGroupAdd</i>
******** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbGroupAddAdd</i>
******** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbGroupRemove</i>
******** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbGroupRemoveAdd</i>
******** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbGroupAddRemove</i>
******** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbGroupRemoveRemove</i>
******** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbGroupInheritRemove</i>
******** QLabel<i style="color:#fff">#</i><i style="color:#090">qliGroupRemove</i>
**** QWidget<i style="color:#fff">#</i><i style="color:#090">qwACL</i>
***** QHBoxLayout<i style="color:#fff">#</i><i style="color:#090">horizontalLayout</i>
****** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">qlVerticalACL</i>
******* QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbACLs</i>
******** QGridLayout
********* QListWidget<i style="color:#fff">#</i><i style="color:#090">qlwACLs</i>
********* QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbACLInherit</i>
********* QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbACLUp</i>
********* QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbACLDown</i>
********* QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbACLAdd</i>
********* QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbACLRemove</i>
******* QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbACLapply</i>
******** QHBoxLayout<i style="color:#fff">#</i><i style="color:#090">horizontalLayout_2</i>
********* QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbACLApplySubs</i>
********* QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbACLApplyHere</i>
******* QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbACLugroup</i>
******** QGridLayout
********* QLabel<i style="color:#fff">#</i><i style="color:#090">qliACLGroup</i>
********* QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbACLGroup</i>
********* QLabel<i style="color:#fff">#</i><i style="color:#090">qliACLUser</i>
********* QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbACLUser</i>
****** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbACLpermissions</i>
*** QDialogButtonBox<i style="color:#fff">#</i><i style="color:#090">qdbbButtons</i>

## ASIO Input (ASIOInput.ui) 

Source:  [cb267a3/src/mumble/ASIOInput.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/ASIOInput.ui)

* QWidget<i style="color:#fff">#</i><i style="color:#090">ASIOConfig</i>
** QVBoxLayout
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbDeviceSelection</i>
**** QHBoxLayout
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliDevice</i>
***** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbDevice</i>
***** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbQuery</i>
***** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbConfig</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbCapabilities</i>
**** QGridLayout
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliName</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlName</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliBuffers</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlBuffers</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbChannels</i>
**** QHBoxLayout
***** QVBoxLayout
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qliMic</i>
****** QListWidget<i style="color:#fff">#</i><i style="color:#090">qlwMic</i>
***** QVBoxLayout
****** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbAddMic</i>
****** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbRemMic</i>
***** QVBoxLayout
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qliUnused</i>
****** QListWidget<i style="color:#fff">#</i><i style="color:#090">qlwUnused</i>
***** QVBoxLayout
****** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbAddSpeaker</i>
****** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbRemSpeaker</i>
***** QVBoxLayout
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qliSpeakers</i>
****** QListWidget<i style="color:#fff">#</i><i style="color:#090">qlwSpeaker</i>

## Audio Input (AudioInput.ui) 

Source:  [cb267a3/src/mumble/AudioInput.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/AudioInput.ui)

* QWidget<i style="color:#fff">#</i><i style="color:#090">AudioInput</i>
** QVBoxLayout
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbInterfaces</i>
**** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliSystem</i>
***** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbSystem</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliDevice</i>
***** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbDevice</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbExclusive</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliEcho</i>
***** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbEcho</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbTransmission</i>
**** QGridLayout
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliTransmit</i>
***** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbTransmit</i>
***** QStackedWidget<i style="color:#fff">#</i><i style="color:#090">qswTransmit</i>
****** QWidget<i style="color:#fff">#</i><i style="color:#090">qwPTT</i>
******* QGridLayout
******** QLabel<i style="color:#fff">#</i><i style="color:#090">qliDoublePush</i>
******** QLabel<i style="color:#fff">#</i><i style="color:#090">qlDoublePush</i>
******** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbPushWindow</i>
******** QSlider<i style="color:#fff">#</i><i style="color:#090">qsDoublePush</i>
******** QLabel<i style="color:#fff">#</i><i style="color:#090">qliPTTHold</i>
******** QLabel<i style="color:#fff">#</i><i style="color:#090">qlPTTHold</i>
******** QSlider<i style="color:#fff">#</i><i style="color:#090">qsPTTHold</i>
****** QWidget<i style="color:#fff">#</i><i style="color:#090">qwVAD</i>
******* QGridLayout
******** QHBoxLayout
********* QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbAmplitude</i>
********* QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbSNR</i>
******** QLabel<i style="color:#fff">#</i><i style="color:#090">qliTransmitHold</i>
******** QSlider<i style="color:#fff">#</i><i style="color:#090">qsTransmitHold</i>
******** QLabel<i style="color:#fff">#</i><i style="color:#090">qlTransmitHold</i>
******** AudioBar<i style="color:#fff">#</i><i style="color:#090">abSpeech</i>
******** QLabel<i style="color:#fff">#</i><i style="color:#090">qliTransmitMin</i>
******** QSlider<i style="color:#fff">#</i><i style="color:#090">qsTransmitMin</i>
******** QLabel<i style="color:#fff">#</i><i style="color:#090">qliTransmitMax</i>
******** QSlider<i style="color:#fff">#</i><i style="color:#090">qsTransmitMax</i>
****** QWidget<i style="color:#fff">#</i><i style="color:#090">qwContinuous</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbCompression</i>
**** QGridLayout
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliQuality</i>
***** QSlider<i style="color:#fff">#</i><i style="color:#090">qsQuality</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlQuality</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliFrames</i>
***** QSlider<i style="color:#fff">#</i><i style="color:#090">qsFrames</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlFrames</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlBitrate</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbAudio</i>
**** QGridLayout
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliNoise</i>
***** QSlider<i style="color:#fff">#</i><i style="color:#090">qsNoise</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlNoise</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliAmp</i>
***** QSlider<i style="color:#fff">#</i><i style="color:#090">qsAmp</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlAmp</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbMisc</i>
**** QGridLayout<i style="color:#fff">#</i><i style="color:#090">_2</i>
***** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbPushClickBrowseOff</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlPushClickOff</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlPushClickOn</i>
***** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbPushClickPreview</i>
***** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbPushClickReset</i>
***** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbPushClickBrowseOn</i>
***** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qlePushClickPathOn</i>
***** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qlePushClickPathOff</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbPushClick</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliIdle</i>
***** QHBoxLayout<i style="color:#fff">#</i><i style="color:#090">horizontalLayout</i>
****** QSpinBox<i style="color:#fff">#</i><i style="color:#090">qsbIdle</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qlIdle</i>
****** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbIdleAction</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlIdle2</i>

## Audio Output (AudioOutput.ui) 

Source:  [cb267a3/src/mumble/AudioOutput.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/AudioOutput.ui)

* QWidget<i style="color:#fff">#</i><i style="color:#090">AudioOutput</i>
** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbInterfaces</i>
**** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout_3</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliSystem</i>
***** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbSystem</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliDevice</i>
***** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbDevice</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbExclusive</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbPositional</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbOutput</i>
**** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliJitter</i>
***** QSlider<i style="color:#fff">#</i><i style="color:#090">qsJitter</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlJitter</i>
***** QSlider<i style="color:#fff">#</i><i style="color:#090">qsVolume</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliVolume</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlVolume</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliDelay</i>
***** QSlider<i style="color:#fff">#</i><i style="color:#090">qsDelay</i>
***** QSlider<i style="color:#fff">#</i><i style="color:#090">qsOtherVolume</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlDelay</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlOtherVolume</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliOtherVolume</i>
***** QHBoxLayout<i style="color:#fff">#</i><i style="color:#090">horizontalLayout</i>
****** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbAttenuateOthers</i>
****** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbAttenuateOthersOnTalk</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbAdvancedAttenuation</i>
**** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_3</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbOnlyAttenuateSameOutput</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbAttenuateLoopbacks</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbPrioritySpeaker</i>
**** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_2</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbAttenuateUsersOnPrioritySpeak</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbVolume</i>
**** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout_2</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbHeadphones</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliMinDistancce</i>
***** QSlider<i style="color:#fff">#</i><i style="color:#090">qsMinDistance</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlMinDistance</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliMaxDistancce</i>
***** QSlider<i style="color:#fff">#</i><i style="color:#090">qsMaxDistance</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlMaxDistance</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliMaxDistVolume</i>
***** QSlider<i style="color:#fff">#</i><i style="color:#090">qsMaxDistVolume</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlMaxDistVolume</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliBloom</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlBloom</i>
***** QSlider<i style="color:#fff">#</i><i style="color:#090">qsBloom</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbLoopback</i>
**** QGridLayout
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliPacketDelay</i>
***** QSlider<i style="color:#fff">#</i><i style="color:#090">qsPacketDelay</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlPacketDelay</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliPacketLoss</i>
***** QSlider<i style="color:#fff">#</i><i style="color:#090">qsPacketLoss</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlPacketLoss</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliLoopback</i>
***** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbLoopback</i>

## Audio Stats (AudioStats.ui) 

Source:  [cb267a3/src/mumble/AudioStats.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/AudioStats.ui)

* QDialog<i style="color:#fff">#</i><i style="color:#090">AudioStats</i>
** QVBoxLayout
*** QHBoxLayout
**** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbInput</i>
***** QGridLayout
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qliMicLevel</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qlMicLevel</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qliSpeakerLevel</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qlSpeakerLevel</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qliSignalLevel</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qlSignalLevel</i>
**** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbSignal</i>
***** QGridLayout
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qliMicVolume</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qlMicVolume</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qliMicSNR</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qlMicSNR</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qliSpeechProb</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qlSpeechProb</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbConfiguration</i>
**** QGridLayout
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliBitrate</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlBitrate</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliDoublePush</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlDoublePush</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliSpeech</i>
***** AudioBar<i style="color:#fff">#</i><i style="color:#090">abSpeech</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbSpectrum</i>
**** QVBoxLayout
***** AudioNoiseWidget<i style="color:#fff">#</i><i style="color:#090">anwNoise</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbEcho</i>
**** QVBoxLayout
***** AudioEchoWidget<i style="color:#fff">#</i><i style="color:#090">aewEcho</i>

## Audio Wizard (AudioWizard.ui) 

Source:  [cb267a3/src/mumble/AudioWizard.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/AudioWizard.ui)

* QWizard<i style="color:#fff">#</i><i style="color:#090">AudioWizard</i>
** CompletablePage<i style="color:#fff">#</i><i style="color:#090">qwpIntro</i>
*** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">label</i>
** CompletablePage<i style="color:#fff">#</i><i style="color:#090">qwpDevice</i>
*** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_2</i>
**** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbInput</i>
***** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout_2</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qliInputText</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qliInput</i>
****** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbInput</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qliInputDevice</i>
****** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbInputDevice</i>
****** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbEcho</i>
**** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbOutput</i>
***** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qliOutputText</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qliOutput</i>
****** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbOutput</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qliOutputDevice</i>
****** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbOutputDevice</i>
****** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbPositional</i>
****** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbAttenuateOthers</i>
** CompletablePage<i style="color:#fff">#</i><i style="color:#090">qwpDeviceTuning</i>
*** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout_3</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">qliDeviceTuningText</i>
**** QSlider<i style="color:#fff">#</i><i style="color:#090">qsOutputDelay</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">qlOutputDelay</i>
** CompletablePage<i style="color:#fff">#</i><i style="color:#090">qwpVolume</i>
*** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_3</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">qliVolumeTuningText</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">qliVolumeTuningTextHC</i>
**** AudioBar<i style="color:#fff">#</i><i style="color:#090">abAmplify</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">qliAmpTuningText</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">qliAmpTuningTextHC</i>
**** QSlider<i style="color:#fff">#</i><i style="color:#090">qsMaxAmp</i>
**** QHBoxLayout<i style="color:#fff">#</i><i style="color:#090">horizontalLayout_2</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbHighContrast</i>
** CompletablePage<i style="color:#fff">#</i><i style="color:#090">qwpTrigger</i>
*** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout_4</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">qliVADText</i>
**** QHBoxLayout<i style="color:#fff">#</i><i style="color:#090">horizontalLayout</i>
***** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrPTT</i>
***** ShortcutKeyWidget<i style="color:#fff">#</i><i style="color:#090">skwPTT</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">qlTalkIcon</i>
**** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrSNR</i>
**** QWidget<i style="color:#fff">#</i><i style="color:#090">qwVAD</i>
***** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_6</i>
****** AudioBar<i style="color:#fff">#</i><i style="color:#090">abVAD</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qliVadTuningText</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qliVadTuningTextHC</i>
****** QSlider<i style="color:#fff">#</i><i style="color:#090">qsVAD</i>
**** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrAmplitude</i>
** CompletablePage<i style="color:#fff">#</i><i style="color:#090">qwpSettings</i>
*** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_9</i>
**** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbQuality</i>
***** QFormLayout<i style="color:#fff">#</i><i style="color:#090">formLayout</i>
****** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbQualityLow</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qlQualityLow</i>
****** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbQualityBalanced</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qlQualityBalanced</i>
****** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbQualityUltra</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qlQualityUltra</i>
****** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbQualityCustom</i>
****** QLabel<i style="color:#fff">#</i><i style="color:#090">qlQualityCustom</i>
**** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbNotifications</i>
***** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_10</i>
****** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbNotificationTTS</i>
****** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbNotificationSounds</i>
****** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbNotificationCustom</i>
** CompletablePage<i style="color:#fff">#</i><i style="color:#090">qwpPositional</i>
*** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_5</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">qliPositionalText</i>
**** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbHeadphone</i>
**** QGraphicsView<i style="color:#fff">#</i><i style="color:#090">qgvView</i>
** CompletablePage<i style="color:#fff">#</i><i style="color:#090">qwpDone</i>
*** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_4</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">qlDone</i>
**** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbUsage</i>

## Ban Editor (BanEditor.ui) 

Source:  [cb267a3/src/mumble/BanEditor.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/BanEditor.ui)

* QDialog<i style="color:#fff">#</i><i style="color:#090">BanEditor</i>
** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout_2</i>
*** QDialogButtonBox<i style="color:#fff">#</i><i style="color:#090">qbbButtons</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbBanList</i>
**** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout</i>
***** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qleSearch</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlUser</i>
***** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qleUser</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlIP</i>
***** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qleIP</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlMask</i>
***** QSpinBox<i style="color:#fff">#</i><i style="color:#090">qsbMask</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlReason</i>
***** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qleReason</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlStart</i>
***** QDateTimeEdit<i style="color:#fff">#</i><i style="color:#090">qdteStart</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlEnd</i>
***** QDateTimeEdit<i style="color:#fff">#</i><i style="color:#090">qdteEnd</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliHash</i>
***** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qleHash</i>
***** QListWidget<i style="color:#fff">#</i><i style="color:#090">qlwBans</i>
***** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbAdd</i>
***** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbUpdate</i>
***** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbRemove</i>
***** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbClear</i>

## Certificate Wizard (Cert.ui) 

Source:  [cb267a3/src/mumble/Cert.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/Cert.ui)

* QWizard<i style="color:#fff">#</i><i style="color:#090">Certificates</i>
** QWizardPage<i style="color:#fff">#</i><i style="color:#090">qwpWelcome</i>
*** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">qlIntroText</i>
**** CertView<i style="color:#fff">#</i><i style="color:#090">cvWelcome</i>
**** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbQuick</i>
**** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbCreate</i>
**** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbImport</i>
**** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbExport</i>
** CompletablePage<i style="color:#fff">#</i><i style="color:#090">qwpImport</i>
*** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">qlImportText</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">qlImportFile</i>
**** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qleImportFile</i>
**** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbImportFile</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">qlPassword</i>
**** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qlePassword</i>
**** CertView<i style="color:#fff">#</i><i style="color:#090">cvImport</i>
** QWizardPage<i style="color:#fff">#</i><i style="color:#090">qwpReplace</i>
*** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout_2</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">qlReplace</i>
**** CertView<i style="color:#fff">#</i><i style="color:#090">cvCurrent</i>
**** CertView<i style="color:#fff">#</i><i style="color:#090">cvNew</i>
** CompletablePage<i style="color:#fff">#</i><i style="color:#090">qwpExport</i>
*** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout_4</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">qlExport</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">qlExportFile</i>
**** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qleExportFile</i>
**** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbExportFile</i>
**** CertView<i style="color:#fff">#</i><i style="color:#090">cvExport</i>
** CompletablePage<i style="color:#fff">#</i><i style="color:#090">qwpNew</i>
*** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout_3</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">qlNewText</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">qlName</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">qlEmail</i>
**** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qleEmail</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">qlError</i>
**** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qleName</i>
** QWizardPage<i style="color:#fff">#</i><i style="color:#090">qwpFinish</i>
*** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_2</i>
**** QLabel<i style="color:#fff">#</i><i style="color:#090">qlFinishText</i>

## Config Dialog (ConfigDialog.ui) 

Source:  [cb267a3/src/mumble/ConfigDialog.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/ConfigDialog.ui)

* QDialog<i style="color:#fff">#</i><i style="color:#090">ConfigDialog</i>
** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout</i>
*** QListWidget<i style="color:#fff">#</i><i style="color:#090">qlwIcons</i>
*** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbExpert</i>
*** QHBoxLayout<i style="color:#fff">#</i><i style="color:#090">horizontalLayout</i>
**** QDialogButtonBox<i style="color:#fff">#</i><i style="color:#090">pageButtonBox</i>
**** QDialogButtonBox<i style="color:#fff">#</i><i style="color:#090">dialogButtonBox</i>
*** QStackedWidget<i style="color:#fff">#</i><i style="color:#090">qswPages</i>

## Connect Dialog (ConnectDialog.ui) 

Source:  [cb267a3/src/mumble/ConnectDialog.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/ConnectDialog.ui)

* QDialog<i style="color:#fff">#</i><i style="color:#090">ConnectDialog</i>
** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout</i>
*** ServerView<i style="color:#fff">#</i><i style="color:#090">qtwServers</i>
*** QDialogButtonBox<i style="color:#fff">#</i><i style="color:#090">qdbbButtonBox</i>

## Edit Server (ConnectDialogEdit.ui) 

Source:  [cb267a3/src/mumble/ConnectDialogEdit.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/ConnectDialogEdit.ui)

* QDialog<i style="color:#fff">#</i><i style="color:#090">ConnectDialogEdit</i>
** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout</i>
*** QLabel<i style="color:#fff">#</i><i style="color:#090">qliServer</i>
*** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qleServer</i>
*** QLabel<i style="color:#fff">#</i><i style="color:#090">qliPort</i>
*** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qlePort</i>
*** QLabel<i style="color:#fff">#</i><i style="color:#090">qliUsername</i>
*** QLabel<i style="color:#fff">#</i><i style="color:#090">qliPassword</i>
*** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qleUsername</i>
*** QDialogButtonBox<i style="color:#fff">#</i><i style="color:#090">qdbbButtonBox</i>
*** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qlePassword</i>
*** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbShowPassword</i>
*** QLabel<i style="color:#fff">#</i><i style="color:#090">qliName</i>
*** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qleName</i>

## Shortcuts (GlobalShortcut.ui) 

Source:  [cb267a3/src/mumble/GlobalShortcut.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/GlobalShortcut.ui)

* QWidget<i style="color:#fff">#</i><i style="color:#090">GlobalShortcut</i>
** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout</i>
*** QWidget<i style="color:#fff">#</i><i style="color:#090">qwWarningContainer</i>
**** QVBoxLayout
***** QWidget<i style="color:#fff">#</i><i style="color:#090">qwMacWarning</i>
****** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_4</i>
******* QLabel<i style="color:#fff">#</i><i style="color:#090">label</i>
******* QHBoxLayout<i style="color:#fff">#</i><i style="color:#090">horizontalLayout_2</i>
******** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbOpenAccessibilityPrefs</i>
******** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbSkipWarning</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbShortcuts</i>
**** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_3</i>
***** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_2</i>
****** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbEnableGlobalShortcuts</i>
****** QTreeWidget<i style="color:#fff">#</i><i style="color:#090">qtwShortcuts</i>
***** QHBoxLayout<i style="color:#fff">#</i><i style="color:#090">horizontalLayout</i>
****** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbAdd</i>
****** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbRemove</i>

## Whisper Target (GlobalShortcutTarget.ui) 

Source:  [cb267a3/src/mumble/GlobalShortcutTarget.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/GlobalShortcutTarget.ui)

* QDialog<i style="color:#fff">#</i><i style="color:#090">GlobalShortcutTarget</i>
** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout</i>
*** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbUsers</i>
*** QStackedWidget<i style="color:#fff">#</i><i style="color:#090">qswStack</i>
**** QWidget<i style="color:#fff">#</i><i style="color:#090">qwChannelPage</i>
***** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_2</i>
****** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbChannel</i>
******* QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_3</i>
******** QTreeWidget<i style="color:#fff">#</i><i style="color:#090">qtwChannels</i>
******** QHBoxLayout<i style="color:#fff">#</i><i style="color:#090">horizontalLayout</i>
********* QLabel<i style="color:#fff">#</i><i style="color:#090">qlGroup</i>
********* QLineEdit<i style="color:#fff">#</i><i style="color:#090">qleGroup</i>
******** QHBoxLayout<i style="color:#fff">#</i><i style="color:#090">horizontalLayout_2</i>
********* QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbLinks</i>
********* QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbChildren</i>
**** QWidget<i style="color:#fff">#</i><i style="color:#090">qwUserPage</i>
***** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout</i>
****** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbUser</i>
******* QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout_2</i>
******** QListWidget<i style="color:#fff">#</i><i style="color:#090">qlwUsers</i>
******** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbUser</i>
******** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbAdd</i>
******** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbRemove</i>
*** QDialogButtonBox<i style="color:#fff">#</i><i style="color:#090">qbbButtons</i>
*** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbChannel</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbModifiers</i>
**** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_4</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbForceCenter</i>

## LCD (LCD.ui) 

Source:  [cb267a3/src/mumble/LCD.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/LCD.ui)

* QWidget<i style="color:#fff">#</i><i style="color:#090">LCDConfig</i>
** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_2</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbDevices</i>
**** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout</i>
***** QTreeWidget<i style="color:#fff">#</i><i style="color:#090">qtwDevices</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbViews</i>
**** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliMinColWidth</i>
***** QSlider<i style="color:#fff">#</i><i style="color:#090">qsMinColWidth</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlMinColWidth</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliSplitterWidth</i>
***** QSlider<i style="color:#fff">#</i><i style="color:#090">qsSplitterWidth</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlSplitterWidth</i>

## Log (Log.ui) 

Source:  [cb267a3/src/mumble/Log.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/Log.ui)

* QWidget<i style="color:#fff">#</i><i style="color:#090">LogConfig</i>
** QVBoxLayout
*** QTreeWidget<i style="color:#fff">#</i><i style="color:#090">qtwMessages</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbTTS</i>
**** QGridLayout
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlVolume</i>
***** QSlider<i style="color:#fff">#</i><i style="color:#090">qsVolume</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlThreshold</i>
***** QSpinBox<i style="color:#fff">#</i><i style="color:#090">qsbThreshold</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbReadBackOwn</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbWhisper</i>
**** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbWhisperFriends</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbMaxBlocks</i>
**** QGridLayout<i style="color:#fff">#</i><i style="color:#090">_2</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlMaxBlocks</i>
***** QSpinBox<i style="color:#fff">#</i><i style="color:#090">qsbMaxBlocks</i>

## Look Config (LookConfig.ui) 

Source:  [cb267a3/src/mumble/LookConfig.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/LookConfig.ui)

* QWidget<i style="color:#fff">#</i><i style="color:#090">LookConfig</i>
** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout_4</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbLookFeel</i>
**** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout</i>
***** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbLanguage</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliTheme</i>
***** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbTheme</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbShowTransmitModeComboBox</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbHighContrast</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliLanguage</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlThemesDirectory</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbTray</i>
**** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbHideTray</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbStateInTray</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbApplication</i>
**** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout_3</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliAlwaysOnTop</i>
***** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbAlwaysOnTop</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbShowContextMenuInMenuBar</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbAskOnQuit</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbChannel</i>
**** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout_2</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliChannelDrag</i>
***** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbChannelDrag</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliExpand</i>
***** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbExpand</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbUsersTop</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbShowUserCount</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbChatBarUseSelection</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbFilterHidesEmptyChannels</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbLayout</i>
**** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayoutLayout</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlLHybrid</i>
***** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbLHybrid</i>
***** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbLCustom</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlLCustom</i>
***** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbLStacked</i>
***** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbLClassic</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlLClassic</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlLStacked</i>

## Main Window (MainWindow.ui) 

Source:  [cb267a3/src/mumble/MainWindow.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/MainWindow.ui)

* QMainWindow<i style="color:#fff">#</i><i style="color:#090">MainWindow</i>
** UserView<i style="color:#fff">#</i><i style="color:#090">qtvUsers</i>
** QMenuBar<i style="color:#fff">#</i><i style="color:#090">menubar</i>
*** QMenu<i style="color:#fff">#</i><i style="color:#090">qmConfig</i>
*** QMenu<i style="color:#fff">#</i><i style="color:#090">qmHelp</i>
*** QMenu<i style="color:#fff">#</i><i style="color:#090">qmServer</i>
*** QMenu<i style="color:#fff">#</i><i style="color:#090">qmSelf</i>
** QDockWidget<i style="color:#fff">#</i><i style="color:#090">qdwLog</i>
*** LogTextBrowser<i style="color:#fff">#</i><i style="color:#090">qteLog</i>
** QDockWidget<i style="color:#fff">#</i><i style="color:#090">qdwChat</i>
*** ChatbarTextEdit<i style="color:#fff">#</i><i style="color:#090">qteChat</i>
** QToolBar<i style="color:#fff">#</i><i style="color:#090">qtIconToolbar</i>

## Network Config (NetworkConfig.ui) 

Source:  [cb267a3/src/mumble/NetworkConfig.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/NetworkConfig.ui)

* QWidget<i style="color:#fff">#</i><i style="color:#090">NetworkConfig</i>
** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_2</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbConnection</i>
**** QVBoxLayout
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbTcpMode</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbQoS</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbAutoReconnect</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbAutoConnect</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbSuppressIdentity</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbProxy</i>
**** QGridLayout
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlType</i>
***** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbType</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlHostname</i>
***** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qleHostname</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlPort</i>
***** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qlePort</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlUsername</i>
***** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qleUsername</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlPassword</i>
***** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qlePassword</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbMisc</i>
**** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_3</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbImageDownload</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbServices</i>
**** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbAutoUpdate</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbPluginUpdate</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbUsage</i>

## Overlay (Overlay.ui) 

Source:  [cb267a3/src/mumble/Overlay.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/Overlay.ui)

* QWidget<i style="color:#fff">#</i><i style="color:#090">OverlayConfig</i>
** QVBoxLayout
*** QStackedWidget<i style="color:#fff">#</i><i style="color:#090">qswOverlayPage</i>
**** QWidget<i style="color:#fff">#</i><i style="color:#090">qwOverlayConfig</i>
***** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_4</i>
****** QWidget<i style="color:#fff">#</i><i style="color:#090">widget</i>
******* QHBoxLayout<i style="color:#fff">#</i><i style="color:#090">horizontalLayout_9</i>
******** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbOptions</i>
********* QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_15</i>
********** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbEnable</i>
********** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_14</i>
*********** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbLoadPreset</i>
*********** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbSavePreset</i>
*********** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbUninstall</i>
******** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgpFps</i>
********* QHBoxLayout<i style="color:#fff">#</i><i style="color:#090">horizontalLayout_8</i>
********** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_9</i>
*********** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbShowFps</i>
*********** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbShowTime</i>
*********** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbFpsFont</i>
*********** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbFpsColor</i>
********** QGraphicsView<i style="color:#fff">#</i><i style="color:#090">qgvFpsPreview</i>
****** QTabWidget<i style="color:#fff">#</i><i style="color:#090">qtwSetup</i>
******* QWidget<i style="color:#fff">#</i><i style="color:#090">qwLayoutTab</i>
******** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_13</i>
********* QGraphicsView<i style="color:#fff">#</i><i style="color:#090">qgvView</i>
******* QWidget<i style="color:#fff">#</i><i style="color:#090">qwExceptions</i>
******** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_16</i>
********* QHBoxLayout<i style="color:#fff">#</i><i style="color:#090">horizontalLayout_2</i>
********** QLabel<i style="color:#fff">#</i><i style="color:#090">qlExcListType</i>
********** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbBlacklist</i>
********** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbWhitelist</i>
********* QStackedWidget<i style="color:#fff">#</i><i style="color:#090">qswBlackWhiteList</i>
********** QWidget<i style="color:#fff">#</i><i style="color:#090">qwBlack</i>
*********** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_2</i>
************ QLabel<i style="color:#fff">#</i><i style="color:#090">qlBlackDesc</i>
************ QListWidget<i style="color:#fff">#</i><i style="color:#090">qlwBlacklist</i>
********** QWidget<i style="color:#fff">#</i><i style="color:#090">qwWhite</i>
*********** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_3</i>
************ QLabel<i style="color:#fff">#</i><i style="color:#090">qlWhiteDesc</i>
************ QListWidget<i style="color:#fff">#</i><i style="color:#090">qlwWhitelist</i>
********* QHBoxLayout<i style="color:#fff">#</i><i style="color:#090">horizontalLayout</i>
********** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbAdd</i>
********** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbRemove</i>
**** QWidget<i style="color:#fff">#</i><i style="color:#090">qwOverlayInstall</i>
***** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_5</i>
****** QGroupBox<i style="color:#fff">#</i><i style="color:#090">groupBox</i>
******* QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_11</i>
******** QFormLayout<i style="color:#fff">#</i><i style="color:#090">formLayout</i>
********* QLabel<i style="color:#fff">#</i><i style="color:#090">qlInstallIcon</i>
********* QLabel<i style="color:#fff">#</i><i style="color:#090">qlInstallText</i>
******** QHBoxLayout<i style="color:#fff">#</i><i style="color:#090">horizontalLayout_4</i>
********* QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbInstall</i>
**** QWidget<i style="color:#fff">#</i><i style="color:#090">qwOverlayUpgrade</i>
***** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_7</i>
****** QGroupBox<i style="color:#fff">#</i><i style="color:#090">groupBox_2</i>
******* QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_12</i>
******** QFormLayout<i style="color:#fff">#</i><i style="color:#090">formLayout_4</i>
********* QLabel<i style="color:#fff">#</i><i style="color:#090">qlUpgradeIcon</i>
********* QLabel<i style="color:#fff">#</i><i style="color:#090">qlUpgradeText</i>
******** QHBoxLayout<i style="color:#fff">#</i><i style="color:#090">horizontalLayout_6</i>
********* QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbUpgrade</i>

## Overlay Editor (OverlayEditor.ui) 

Source:  [cb267a3/src/mumble/OverlayEditor.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/OverlayEditor.ui)

* QDialog<i style="color:#fff">#</i><i style="color:#090">OverlayEditor</i>
** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbState</i>
**** QHBoxLayout<i style="color:#fff">#</i><i style="color:#090">horizontalLayout</i>
***** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbPassive</i>
***** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbTalking</i>
***** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbWhisper</i>
***** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbShout</i>
*** QGraphicsView<i style="color:#fff">#</i><i style="color:#090">qgvView</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbZoom</i>
**** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout</i>
***** QSlider<i style="color:#fff">#</i><i style="color:#090">qsZoom</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbElements</i>
**** QHBoxLayout<i style="color:#fff">#</i><i style="color:#090">horizontalLayout_2</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbAvatar</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbUser</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbChannel</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbMutedDeafened</i>
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbBox</i>
*** QDialogButtonBox<i style="color:#fff">#</i><i style="color:#090">qdbbBox</i>

## PA Audio Config (PAAudioConfig.ui) 

Source:  [cb267a3/src/mumble/PAAudioConfig.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/PAAudioConfig.ui)

<b style="color:red">Sorry, this file is no longer available.</b>
## PTT Button Widget (PTTButtonWidget.ui) 

Source:  [cb267a3/src/mumble/PTTButtonWidget.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/PTTButtonWidget.ui)

* QWidget<i style="color:#fff">#</i><i style="color:#090">qwPTTButtonWidget</i>
** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout</i>
*** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbPushToTalk</i>

## Plugins (Plugins.ui) 

Source:  [cb267a3/src/mumble/Plugins.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/Plugins.ui)

* QWidget<i style="color:#fff">#</i><i style="color:#090">PluginConfig</i>
** QVBoxLayout
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbOptions</i>
**** QVBoxLayout
***** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbTransmit</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbPlugins</i>
**** QVBoxLayout
***** QTreeWidget<i style="color:#fff">#</i><i style="color:#090">qtwPlugins</i>
***** QHBoxLayout
****** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbReload</i>
****** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbAbout</i>
****** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbConfig</i>

## Rich Text Editor (RichTextEditor.ui) 

Source:  [cb267a3/src/mumble/RichTextEditor.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/RichTextEditor.ui)

* QTabWidget<i style="color:#fff">#</i><i style="color:#090">RichTextEditor</i>
** QWidget<i style="color:#fff">#</i><i style="color:#090">qwRich</i>
*** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout_2</i>
**** QToolBar<i style="color:#fff">#</i><i style="color:#090">qtbToolBar</i>
**** RichTextHtmlEdit<i style="color:#fff">#</i><i style="color:#090">qteRichText</i>
** QWidget<i style="color:#fff">#</i><i style="color:#090">qwPlain</i>
*** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout</i>
**** QPlainTextEdit<i style="color:#fff">#</i><i style="color:#090">qptePlainText</i>

## Rich Text Editor Link (RichTextEditorLink.ui) 

Source:  [cb267a3/src/mumble/RichTextEditorLink.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/RichTextEditorLink.ui)

* QDialog<i style="color:#fff">#</i><i style="color:#090">RichTextEditorLink</i>
** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout</i>
*** QLabel<i style="color:#fff">#</i><i style="color:#090">qlUrl</i>
*** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qleUrl</i>
*** QLabel<i style="color:#fff">#</i><i style="color:#090">qlText</i>
*** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qleText</i>
*** QDialogButtonBox<i style="color:#fff">#</i><i style="color:#090">buttonBox</i>

## Text Message (TextMessage.ui) 

Source:  [cb267a3/src/mumble/TextMessage.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/TextMessage.ui)

* QDialog<i style="color:#fff">#</i><i style="color:#090">TextMessage</i>
** QVBoxLayout
*** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout</i>
**** RichTextEditor<i style="color:#fff">#</i><i style="color:#090">rteMessage</i>
*** QCheckBox<i style="color:#fff">#</i><i style="color:#090">qcbTreeMessage</i>
*** QDialogButtonBox<i style="color:#fff">#</i><i style="color:#090">qbbButtons</i>

## Tokens (Tokens.ui) 

Source:  [cb267a3/src/mumble/Tokens.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/Tokens.ui)

* QDialog<i style="color:#fff">#</i><i style="color:#090">Tokens</i>
** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout</i>
*** QListWidget<i style="color:#fff">#</i><i style="color:#090">qlwTokens</i>
*** QHBoxLayout
**** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbAdd</i>
**** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbRemove</i>
*** QDialogButtonBox<i style="color:#fff">#</i><i style="color:#090">qbbButtons</i>

## Change your comment (UserEdit.ui) 

Source:  [cb267a3/src/mumble/UserEdit.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/UserEdit.ui)

* QDialog<i style="color:#fff">#</i><i style="color:#090">UserEdit</i>
** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout_2</i>
*** QDialogButtonBox<i style="color:#fff">#</i><i style="color:#090">qbbButtons</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbUserList</i>
**** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout</i>
***** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbRename</i>
***** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbRemove</i>
***** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qlSearch</i>
***** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbInactive</i>
***** QSpinBox<i style="color:#fff">#</i><i style="color:#090">qsbInactive</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlInactive</i>
***** QTreeView<i style="color:#fff">#</i><i style="color:#090">qtvUserList</i>

## User Information (UserInformation.ui) 

Source:  [cb267a3/src/mumble/UserInformation.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/UserInformation.ui)

* QDialog<i style="color:#fff">#</i><i style="color:#090">UserInformation</i>
** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbConnection</i>
**** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliVersion</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlVersion</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliOS</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlOS</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliCertificate</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlCertificate</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliAddress</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlAddress</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliCELT</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlCELT</i>
***** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbCertificate</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliOpus</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlOpus</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbPing</i>
**** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout_2</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliPingCount</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliPingAvg</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliPingVar</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliTCP</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlTCPCount</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlTCPAvg</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlTCPVar</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliUDP</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlUDPCount</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlUDPAvg</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlUDPVar</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbUDP</i>
**** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout_3</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliGood</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliLate</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliLost</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliResync</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliFromClient</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlFromGood</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlFromLate</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlFromLost</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlFromResync</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliToClient</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlToGood</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlToLate</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlToLost</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlToResync</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliLatePercent</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliLostPercent</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlFromLatePercent</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlToLatePercent</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlFromLostPercent</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlToLostPercent</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbBandwidth</i>
**** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout_4</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliTime</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlTime</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qliBandwidth</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlBandwidth</i>

## UserLocalVolumeDialog.ui 

Source:  [cb267a3/src/mumble/UserLocalVolumeDialog.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/UserLocalVolumeDialog.ui)

* QDialog<i style="color:#fff">#</i><i style="color:#090">UserLocalVolumeDialog</i>
** QGridLayout
*** QSlider<i style="color:#fff">#</i><i style="color:#090">qsUserLocalVolume</i>
*** QDialogButtonBox<i style="color:#fff">#</i><i style="color:#090">qbbUserLocalVolume</i>
*** QSpinBox<i style="color:#fff">#</i><i style="color:#090">qsbUserLocalVolume</i>
*** QLabel<i style="color:#fff">#</i><i style="color:#090">qlUserLocalVolume</i>

## Recorder (VoiceRecorderDialog.ui) 

Source:  [cb267a3/src/mumble/VoiceRecorderDialog.ui](https://github.com/mumble-voip/mumble/blob/cb267a3606c8f65bf81961f121a6d9977692262f/src/mumble/VoiceRecorderDialog.ui)

* QDialog<i style="color:#fff">#</i><i style="color:#090">VoiceRecorderDialog</i>
** QGridLayout<i style="color:#fff">#</i><i style="color:#090">gridLayout_2</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbControl</i>
**** QHBoxLayout<i style="color:#fff">#</i><i style="color:#090">horizontalLayout_2</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlTime</i>
***** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbStart</i>
***** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbStop</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbMode</i>
**** QVBoxLayout<i style="color:#fff">#</i><i style="color:#090">verticalLayout</i>
***** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbDownmix</i>
***** QRadioButton<i style="color:#fff">#</i><i style="color:#090">qrbMultichannel</i>
*** QGroupBox<i style="color:#fff">#</i><i style="color:#090">qgbOutput</i>
**** QFormLayout<i style="color:#fff">#</i><i style="color:#090">formLayout</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlOutputFormat</i>
***** QComboBox<i style="color:#fff">#</i><i style="color:#090">qcbFormat</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlTargetDirectory</i>
***** QLabel<i style="color:#fff">#</i><i style="color:#090">qlFilename</i>
***** QHBoxLayout<i style="color:#fff">#</i><i style="color:#090">qhblTargetDirectory</i>
****** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qleTargetDirectory</i>
****** QPushButton<i style="color:#fff">#</i><i style="color:#090">qpbTargetDirectoryBrowse</i>
***** QLineEdit<i style="color:#fff">#</i><i style="color:#090">qleFilename</i>


