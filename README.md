# exc_bad_access_demo

A new project has EXC_BAD_ACCESS crash.

## Creation steps

1、Create a new project through Android Studio, the platforms supports Android and iOS.

2、Add firebase_crashlytics library

```yaml
  firebase_crashlytics: ^4.0.3
```

3、Use Admob mediation ads and add Vungle ads

```yaml
  google_mobile_ads: ^5.1.0
  gma_mediation_liftoffmonetize: ^1.0.0
```

Configure Admob ID in Info.plist（The ID below is the Admob test ID）

```
    <key>GADApplicationIdentifier</key>
    <string>ca-app-pub-3940256099942544~1458002511</string>
```

4、Add audioplayers library

```
audioplayers: ^6.0.0
```

5、Play Audio

```dart
final player = AudioPlayer();
player.play(AssetSource("audio.mp3"));

```

## Crash

Audio crashes after playing for a while on iOS devices.

The crash information is as follows:

```
* thread #1, queue = 'com.apple.main-thread', stop reason = EXC_BAD_ACCESS (code=1, address=0x0)
    frame #0: 0x00000001bdd5881c libswiftCore.dylib`swift::SubstGenericParametersFromMetadata::SubstGenericParametersFromMetadata(swift::TargetMetadata<swift::InProcess> const*) + 24
libswiftCore.dylib`swift::SubstGenericParametersFromMetadata::SubstGenericParametersFromMetadata:
->  0x1bdd5881c <+24>: ldr    x9, [x1]
    0x1bdd58820 <+28>: cmp    x9, #0x7ff
    0x1bdd58824 <+32>: csel   w9, wzr, w9, hi
    0x1bdd58828 <+36>: cmp    w9, #0x202
Target 0: (Runner) stopped.
Lost connection to device.
```
