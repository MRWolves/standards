# MRAS Application Team Java Styleguide

## Google Standard

The MRAS Application Team Java standard is a slight modification of the [Google Java Standards](https://google.github.io/styleguide/javaguide.html).  Any rule not explicitly modified in this document defaults to that of the Google standard.

## Modifications

The following sections describe the differences between the MRAS Application Team Java standard and the Google style recommendations.  The section layout is identical to that of the Google style document, for ease of navigation.

### 3 Source File Structure

#### 3.3.1 Wildcard Imports Discouraged

Wildcard imports are not disallowed, but are strongly discouraged.  Exceptions are allowed for uses where there is both little/no risk of confusion regarding the source of a given definition *and* a substantial decrease in the number of imports.  For example, it is permissible to use a wildcard import to pull all the values of an enum into the static namespace, provided said values have sufficiently-unique names.

### 4 Formatting

####
