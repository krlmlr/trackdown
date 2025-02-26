# trackdown (development version)

## trackdown 1.5.0

new feature `open` by @maelle

- allow to open the created document in a browser

## trackdown 1.4.0

- Trackdown now supports **Quarto**


- Allow custom Client API credentials. Developed from initial input by @maelle in PR https://github.com/ClaudioZandonella/trackdown/pull/38 
    - Review auth process for google APIs using trackdown_* functions (see trackdown_auth.R)
    - When changing trackdown app oauth force googledrive to use the same app credentials
    - Client APIs are checked in the following order:
      - TRACKDOWN_APP environment variabel indicating the the path to the JSON file with the own app credentials
      - Own app credentials specified via httr::oauth_app()
      - Use internal default trackdown app credentials
  
## trackdown 1.3.4

Highlight citation tags and equations when using `rich_text`

## trackdown 1.3.3

Fix issue indented code. Now it is correctly recognized.

## trackdown 1.3.2

Update privacy policy Trackdown R Package client API required scopes.  

## trackdown 1.3.1

Fix default `gfile` name in `render_file()` pull request #30 (by @mone27)

## trackdown 1.3.0

Introduce the `rich_text` feature and uses its own API credentials (see Issue #28)

- **`rich_text`.** Upload *rich* documents to Google Docs where important text that should not be changed is automatically highlighted (e.g., placeholders hiding the code, header of the document, code chunks, and in-line code). See [rich-text feature details]( https://claudiozandonella.github.io/trackdown/articles/trackdown-features.html#rich-text).
- **API Credentials.** Now, `trackdown` uses its own Goole API credentials (OAuth client ID and secret). See details on privacy policy at `vignette("trackdown-privacy-policy")` and [issue comment](https://github.com/ClaudioZandonella/trackdown/issues/28#issuecomment-1057195007).

## trackdown 1.2.1

Corrige output message pull request #29 (by @chainsawriot)

## trackdown 1.2.0

Introduce the `force` argument allowing users to skip confirm checks about overwriting documents (see Issue #27).

## trackdown 1.1.1 (CRAN release)

Fix issue encoding in Windows. Now trackdown does not assume `"UTF-8"` encoding but it relies on `"native.enc"`.

## trackdown 1.1.0

New features:
 
- Introduce (experimental) argument `rm_gcomments`in `download_file()` to automatically remove Google comments when downloading the file (See issue #25).   
- Introduce support for child `.Rmd` and `.Rnw` files (documents without headers).

Argument `hide_code = TRUE` can now be used regardless of whether the file contains header code and/or chunks or not. This fixed the issues #22 and #24.

## trackdown 1.0.2

Fix issue [#21](https://github.com/ClaudioZandonella/trackdown/issues/21)

## trackdown 1.0.1

Fix issue [#17](https://github.com/ClaudioZandonella/trackdown/issues/17) and issue [#19](https://github.com/ClaudioZandonella/trackdown/issues/19)

## trackdown 1.0.0 (CRAN release)

Initial CRAN release

Minor changes to fix cran checks:

- `googledrive` dependency set to (> 1.0.1) and `cli` (>= 3.0.0)
- use relative path to specify  `fixture` and `vcr_files` folders in unit-tests


## trackdown 0.1.1

Following the release of `googledrive` version 2.0.0 ([link](https://www.tidyverse.org/blog/2021/07/googledrive-2-0-0/)), on which `trackdown` is based to interact with Google Drive, we updated the internal functions. In particular:

- Set googledrive (>= 2.0.0) in the `Imports` field of the `DESCRIPTION` file.
- Substitute `team_drive_\*()` deprecated functions and `team_drive =` deprecated arguments with the new `shared_drive_*()` functions and `shared_drive = ` argument in all the `googledrive` functions used internally by `trackdown`.
- Remove `verbose = ` deprecated argument from the `googledrive` functions used internally by `trackdown`. Instead, the function `googledrive::local_drive_quiet()` is used.
- Update unit-tests


## trackdown 0.1.0

Stable version after the full revision of the package previously named `rmdrive`

The workflow follows the same idea as before, but there are several new features and changes. The main ones are:

- **File Supported**: Both `.Rmd` and `.Rnw` documents are supported
- **Hide Code**: Code in the header of the document (YAML header or LaTeX preamble) and code chunks can be removed from the document when uploading to Google Drive and will be automatically restored during download. This prevents collaborators from inadvertently making changes to the code which might corrupt the file and allows them to focus on the narrative text.
-  **Upload Output**: The actual output document (i.e., the rendered file) can be uploaded to Google Drive in conjunction with the `.Rmd` (or `.Rnw`) document. This helps collaborators to evaluate the overall layout (including figures and tables) and allows them to add comments to suggest and discuss changes.
- **API Speed**:  Now the upload to and download from Google Drive is faster.
-  **Documentation**: Rich e detailed documentation is available at https://ekothe.github.io/trackdown/
