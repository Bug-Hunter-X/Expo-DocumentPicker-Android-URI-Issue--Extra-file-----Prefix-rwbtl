# Expo DocumentPicker Android URI Issue

This repository demonstrates a bug in Expo's DocumentPicker API on Android. The issue involves an extra `file:///` prefix being added to the URI returned by `DocumentPicker.getDocumentAsync`, causing subsequent attempts to read the file using `RNFS.readFile` to fail.

## Bug Description

When selecting a file using `DocumentPicker.getDocumentAsync` on Android, the returned URI sometimes includes an extra `file:///` prefix. This invalid URI then prevents the file from being accessed using libraries like `RNFS`.

## Reproduction

1. Clone this repository.
2. Run the project on an Android emulator or device.
3. Select a file using the DocumentPicker.
4. Observe the error in the console when trying to read the file.

## Solution

The solution involves checking the URI for the extra prefix and removing it before attempting to read the file. The corrected code is provided in `bugSolution.js`.

## Additional Notes

This issue may be related to specific Android versions or configurations.  More investigation might be necessary to determine the root cause.