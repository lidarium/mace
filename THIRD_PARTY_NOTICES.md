# Third-Party Notices

**Mace — Proprietary Software**
Copyright (c) 2026 The individual author operating under Teralidarium Works. All rights reserved.

This application is proprietary and confidential. It is distributed under the
terms of the Mace End-User License Agreement (`EULA.md`) and the
proprietary license in `LICENSE`.

Mace links against the open-source packages listed below. Each package
remains subject to its own license. **All modules authored from scratch for this
application — the FastAPI backend, the Electron desktop shell, the React user
interface, the browser automation logic, and the Cloudflare deployment worker —
are proprietary and are not covered by any of the licenses below.**

## How to regenerate this file

```bash
# Python (backend)
backend/venv/bin/pip-licenses --format=markdown --order=license >> THIRD_PARTY_NOTICES.md

# JavaScript (frontend)
cd frontend && node ../tools/js-licenses.cjs >> THIRD_PARTY_NOTICES.md
```

Run this before every release. New dependencies carry new obligations.

## Summary

### Python backend — 160 packages

| License | Count |
|---|---|
| MIT (incl. "MIT License") | 77 |
| Apache-2.0 (incl. "Apache Software License") | 39 |
| BSD (3-Clause, 2-Clause and variants) | 35 |
| PSF / Python Software Foundation License | 4 |
| MPL-2.0 (weak copyleft, file-level) | 3 |
| GPL — **build-time tool only** (PyInstaller, bootloader exception) | 2 |

The three MPL-2.0 packages are `orjson`, `tqdm` and `certifi`. The two GPL-2.0
packages are `pyinstaller` and `pyinstaller-hooks-contrib`, used only to produce
the bundled backend binary. Counts above are derived from the regenerated full
package list below; MPL is matched before MIT because several packages carry
dual `MPL-2.0 AND MIT` declarations.

No GPL or AGPL code is linked into the running application. The two GPL-2.0
entries are PyInstaller and pyinstaller-hooks-contrib, used only to *build* the
bundled backend binary — they are build-time tools, not runtime dependencies, and
neither ships inside the application. PyInstaller is distributed with an explicit
bootloader exception stating that the bundled application does not inherit the
GPL. Neither package has been modified.

The three MPL-2.0 packages (`certifi`, `orjson`, `tqdm`) are shipped
unmodified. MPL-2.0 is a file-level weak copyleft license: using an unmodified MPL
library as a dependency does not require disclosing the application's own source.
Any future modification to those files would need to be published under the MPL.

The GPL-2.0 entries are `pyinstaller` and `pyinstaller-hooks-contrib`, build-time tools used with the
bootloader exception. The bundled application does not inherit the GPL, and
PyInstaller itself is unmodified.

### JavaScript frontend — 681 packages

| License | Count |
|---|---|
| MIT | 540 |
| ISC | 62 |
| BSD-3-Clause | 22 |
| Apache-2.0 | 21 |
| BSD-2-Clause | 12 |
| 0BSD / Unlicense / CC0 / WTFPL / MIT-0 | 10 |
| BlueOak-1.0.0 | 8 |
| **MPL-2.0** | **4** |
| Python-2.0 / PSF | 1 |
| BSD (other) | 1 |

Every package declares a license — none are unidentified. The earlier count of
502 was an undercount from a hand-built script that did not descend into scoped
packages (`@scope/pkg`); `tools/js-licenses.cjs` exists now so this figure comes
from a maintained tool rather than a one-off.

`@sentry/electron` and its eleven transitive MIT packages are included again.
Crash reporting is restored, but it is consent-gated and the SDK is not even
loaded unless the user accepts telemetry in the licence dialog. The gate lives in
`src/main.tsx` (renderer), `electron/telemetry-consent.js` (main process) and
`backend/utils/crash_reporting.py` (backend).

**Note on the four MPL-2.0 entries:** `lightningcss` and `lightningcss-darwin-x64`
each appear at two versions — 1.32.0 and 1.33.0 — simultaneously in the tree.
That is a duplicate transitive dependency, not two separate projects. It is worth
resolving so exactly one version ships.

Six packages are Unlicense (public domain): `fast-shallow-equal`,
`react-universal-interface`, `nano-css`, `react-use`, `set-harmonic-interval`,
`ts-easing`. The first two ship no `license` field in package.json and were
recovered from their `LICENSE` files by the tool's fallback.

The MPL-2.0 packages are `lightningcss` and `lightningcss-darwin-x64`, pulled in
transitively by Tailwind CSS and shipped unmodified.

Attribution note for `react-icons`: the wrapper package is MIT-licensed, but the
icon sets it bundles carry their own licenses. Font Awesome Free icons are
licensed **CC BY 4.0**, which requires the credit:
*"Icons by Font Awesome Free — licensed under CC BY 4.0."*
Circum Icons are MPL-2.0. See https://react-icons.github.io/react-icons for the
full bundled license table.

## MIT License — permission notice

The packages marked **MIT** in the lists below are distributed under the MIT
License. The permission notice below is identical for every one of them, so it is
reproduced once here and applies to each package whose name and version appear in
the full package lists with an MIT licence. The copyright holder for any given
package is its respective author, as identified by the package itself.

This notice is provided because the MIT License requires that "the above
copyright notice and this permission notice shall be included in all copies or
substantial portions of the Software."

```
MIT License

Copyright (c) the respective authors of each MIT-licensed package listed below

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

Full licence text is also reproduced individually for MIT-licensed packages whose
`package.json` embeds it — for example `tiktoken` in the Python list — where the
upstream states it verbatim.

---

## How these notices are distributed, and why

Each obligation below is satisfied by **redistributing the notice with the
application**. None of the licenses we are bound by requires that a user be able
to read the text from inside the UI — that would be a usability choice, not a
licensing requirement. The texts ship in the app bundle under
`Mace.app/Contents/Resources/` and are reachable via
Show Package Contents → Contents → Resources.

| License | What it requires | How it is satisfied |
|---|---|---|
| MIT | The copyright notice and permission notice must be included in all copies or substantial portions | Notice + license text in this file; per-file MIT headers on the modified shadcn/ui copies |
| Apache-2.0 | Give recipients a copy of the license; retain attribution, copyright, patent, trademark and change notices; state changes to modified files | `APACHE-2.0.txt` full text; `editor-LICENSE-NOTICE.md` scope + change list; two-line change headers on all 40 modified files |
| BSD-2-Clause / BSD-3-Clause | Reproduce the copyright notice, list of conditions and disclaimer in the documentation and/or other materials provided with the distribution | Notices in this file, redistributed with the app |
| Chromium / Electron (3-clause BSD + extra notices) | `LICENSES.chromium.html` must accompany the app | Redistributed in the bundle |
| MPL-2.0 (unmodified) | Distribute the license and inform recipients how they can obtain the source for *modified* files | Dependencies are unmodified, so no copyleft obligation is triggered; the license is listed here |
| GPL-2.0 (build-time only) | PyInstaller carries an explicit bootloader exception: bundling does not make the application a derivative work | Neither package ships inside the application as runtime code; the exception is recorded |
| CC BY 4.0 (Font Awesome Free icons) | Retain creator identification, copyright notice, license notice, disclaimer and URI; credit "in any reasonable manner requested by the Licensor" | Credit string reproduced below and in the app's Legal screen |
| Unlicense (public domain, 6 packages) | No obligation | Notices listed for completeness |

The two documents that ARE presented inside the application are the End-User
License Agreement and the Privacy Policy. Neither is a third-party obligation:
they are the agreement the user must accept and the policy consent is given
against, which is what makes the acceptance enforceable.

## Electron / Chromium

Electron redistributes Chromium, which contains components under the 3-Clause
BSD License and other permissive licenses. The complete Chromium attribution
list is distributed with this application as `LICENSES.chromium.html`
(path: `Electron.app/Contents/Frameworks/Electron Framework.framework/`).

## Bundled assets

| Asset | License | Author / Source |
|---|---|---|
| Orbitron (display typeface, `frontend/src/assets/fonts/Orbitron.ttf`) | SIL Open Font License 1.1 | Matt McInerney — https://github.com/google/fonts/tree/main/ofl/orbitron |

The SIL Open Font License 1.1 permits commercial use and embedding of the font
in applications. It does not permit selling the font on its own.

Orbitron replaced an earlier bundled typeface that was covered only by the
Typodermic free Desktop EULA, which explicitly excludes embedding in software.

### SIL Open Font License 1.1 — required notice

The following is the full text of the license governing Orbitron. Under OFL 1.1
clauses 1 and 4, this license and the copyright notice must accompany any
distribution of the font, including distributions embedded in software.

```
Copyright (c) 2011, Matt McInerney (matt@pixelspread.com),
with Reserved Font Name Orbitron.

SIL OPEN FONT LICENSE Version 1.1 - 26 February 2007

PREAMBLE
The goals of the Open Font License (OFL) are to stimulate worldwide
development of collaborative font projects, to support the font creation
efforts of academic and linguistic communities, and to provide a free and
open framework in which fonts may be shared and improved in partnership
with others.

The OFL allows the licensed fonts to be used, studied, modified and
redistributed freely as long as they are not sold by themselves. The
fonts, including any derivative works, can be bundled, embedded,
redistributed and/or sold with any software provided that any reserved
names are not used by derivative works. The fonts and derivatives,
however, cannot be released under any other type of license. The
requirement for fonts to remain under this license does not apply
to any document created using the fonts or their derivatives.

DEFINITIONS
"Font Software" refers to the set of files released by the Copyright
Holder(s) under this license and clearly marked as such. This may
include source files, build scripts and documentation.

"Reserved Font Name" refers to any names specified as such after the
copyright statement(s).

"Original Version" refers to the collection of Font Software components as
distributed by the Copyright Holder(s).

"Modified Version" refers to any derivative made by adding to, deleting,
or substituting -- in part or in whole -- any of the components of the
Original Version, by changing formats or by porting the Font Software to a
new environment.

"Author" refers to any designer, engineer, programmer, technical
writer or other person who contributed to the Font Software.

PERMISSION & CONDITIONS
Permission is hereby granted, free of charge, to any person obtaining
a copy of the Font Software, to use, study, copy, merge, embed, modify,
redistribute, and sell modified and unmodified copies of the Font
Software, subject to the following conditions:

1) Neither the Font Software nor any of its individual components,
in Original or Modified Versions, may be sold by itself.

2) Original or Modified Versions of the Font Software may be bundled,
redistributed and/or sold with any software, provided that each copy
contains the above copyright notice and this license. These can be
included either as stand-alone text files, human-readable headers or
in the appropriate machine-readable metadata fields within text or
binary files as long as those fields can be easily viewed by the user.

3) No Modified Version of the Font Software may use the Reserved Font
Name(s) unless explicit written permission is granted by the corresponding
Copyright Holder. This restriction only applies to the primary font name as
presented to the users.

4) The name(s) of the Copyright Holder(s) or the Author(s) of the Font
Software shall not be used to promote, endorse or advertise any
Modified Version, except to acknowledge the contribution(s) of the
Copyright Holder(s) and the Author(s) or with their explicit written
permission.

5) The Font Software, modified or unmodified, in part or in whole,
must be distributed entirely under this license, and must not be
distributed under any other license. The requirement for fonts to
remain under this license does not apply to any document created
using the Font Software.

TERMINATION
This license becomes null and void if any of the above conditions are
not met.

DISCLAIMER
THE FONT SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO ANY WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT
OF COPYRIGHT, PATENT, TRADEMARK, OR OTHER RIGHT. IN NO EVENT SHALL THE
COPYRIGHT HOLDER BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
INCLUDING ANY GENERAL, SPECIAL, INDIRECT, INCIDENTAL, OR CONSEQUENTIAL
DAMAGES, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE FONT SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE FONT SOFTWARE.
```

### Obligations carried by Mace for Orbitron

| Clause | Obligation | How it is met |
|---|---|---|
| 1 | Font not sold by itself | Orbitron is bundled inside the application, never offered as a standalone product |
| 2 | Copyright notice + this licence must accompany every distribution | This file ships with the application (see `frontend/package.json` → `electron-builder` `files`) and is shown in-app under Settings → Legal |
| 3 | Reserved Font Name "Orbitron" not reused by modified versions | The font is bundled **unmodified**. Subsetting or renaming is not required and is not performed |
| 5 | Font itself stays under OFL | Satisfied — unmodified redistribution |

The font is **not** modified, subset, or renamed. No OFL obligations are
transferable to Mace's own proprietary code: OFL clause 5 makes the
font-licensing requirement apply only to the Font Software, not to documents or
applications that use it.

The replacement font is embedded locally so the application remains fully
offline.


## ISC License — permission notice

The packages marked **ISC** in the lists below are distributed under the ISC
License, a permissive licence functionally equivalent to MIT. The permission
notice below is identical for every one of them and applies to each package whose
name and version appear in the lists with an ISC licence. The copyright holder for
any given package is its respective author, as identified by the package itself.

The ISC License requires that "the above copyright notice and this permission
notice shall be included in all copies or substantial portions of the Software."

```
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```

---

## BSD licences — permission notices

Packages marked **BSD-2-Clause** or **BSD-3-Clause** in the lists below are
distributed under those licences. Both require the copyright notice, the list of
conditions and the disclaimer to be reproduced in the documentation and/or other
materials provided with the distribution. BSD-3-Clause adds a third condition
prohibiting use of the copyright holder's name for endorsement without written
permission.

Both texts below are reproduced once and apply to every BSD package in the lists;
the copyright holder for any given package is its respective author.

### BSD 2-Clause "Simplified" License

```
Copyright (c) the respective authors of each BSD-licensed package listed below
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this
   list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice,
   this list of conditions and the following disclaimer in the documentation
   and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND
ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR
ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON
ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```

### BSD 3-Clause License

```
Copyright (c) the respective authors of each BSD-licensed package listed below
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this
   list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice,
   this list of conditions and the following disclaimer in the documentation
   and/or other materials provided with the distribution.

3. Neither the name of the copyright holder nor the names of its
   contributors may be used to endorse or promote products derived from
   this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND
ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR
ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON
ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```

---

## Mozilla Public License 2.0 — notice and source availability

MPL-2.0 is a weak, file-level copyleft licence: its obligations attach only to
*modified* files. An unmodified MPL-2.0 dependency creates no obligation to
publish anything. What it does require is that this notice accompany the
distribution, that the licence text be available, and that recipients can obtain
the source. The full text is reproduced below; this section records how that is
satisfied.

**Packages governed by MPL-2.0 alone** — these are the ones that need the notice
and the source route:

| Package | Version as bundled |
|---|---|
| `lightningcss` | 1.32.0 and 1.33.0 |
| `lightningcss-darwin-x64` | 1.32.0 and 1.33.0 |
| `certifi` | 2026.7.22 |

**Packages under MPL-2.0 *in addition to* a permissive alternative** — `orjson`
(MPL-2.0 **AND** Apache-2.0 or MIT) and `tqdm` (MPL-2.0 **AND** MIT). These are
dual-licensed, so the MPL terms are elective rather than binding; they are listed
here for completeness and no MPL obligation is asserted against them.

**Source availability.** None of the above is modified. Each is distributed
unmodified from its package registry at the exact version listed in the package
lists below, and can be obtained with your package manager:

```
pip download certifi==2026.7.22 --no-binary :all:
npm pack lightningcss@1.33.0
npm pack lightningcss-darwin-x64@1.33.0
```

The bundled copies are the registry originals, unmodified.

---

## Mozilla Public License 2.0 — full text

```
 Mozilla Public License Version 2.0
==================================

1. Definitions
--------------

1.1. "Contributor"
means each individual or legal entity that creates, contributes to
the creation of, or owns Covered Software.

1.2. "Contributor Version"
means the combination of the Contributions of others (if any) used
by a Contributor and that particular Contributor's Contribution.

1.3. "Contribution"
means Covered Software of a particular Contributor.

1.4. "Covered Software"
means Source Code Form to which the initial Contributor has attached
the notice in Exhibit A, the Executable Form of such Source Code
Form, and Modifications of such Source Code Form, in each case
including portions thereof.

1.5. "Incompatible With Secondary Licenses"
means

(a) that the initial Contributor has attached the notice described
in Exhibit B to the Covered Software; or

(b) that the Covered Software was made available under the terms of
version 1.1 or earlier of the License, but not also under the
terms of a Secondary License.

1.6. "Executable Form"
means any form of the work other than Source Code Form.

1.7. "Larger Work"
means a work that combines Covered Software with other material, in
a separate file or files, that is not Covered Software.

1.8. "License"
means this document.

1.9. "Licensable"
means having the right to grant, to the maximum extent possible,
whether at the time of the initial grant or subsequently, any and
all of the rights conveyed by this License.

1.10. "Modifications"
means any of the following:

(a) any file in Source Code Form that results from an addition to,
deletion from, or modification of the contents of Covered
Software; or

(b) any new file in Source Code Form that contains any Covered
Software.

1.11. "Patent Claims" of a Contributor
means any patent claim(s), including without limitation, method,
process, and apparatus claims, in any patent Licensable by such
Contributor that would be infringed, but for the grant of the
License, by the making, using, selling, offering for sale, having
made, import, or transfer of either its Contributions or its
Contributor Version.

1.12. "Secondary License"
means either the GNU General Public License, Version 2.0, the GNU
Lesser General Public License, Version 2.1, the GNU Affero General
Public License, Version 3.0, or any later versions of those
licenses.

1.13. "Source Code Form"
means the form of the work preferred for making modifications.

1.14. "You" (or "Your")
means an individual or a legal entity exercising rights under this
License. For legal entities, "You" includes any entity that
controls, is controlled by, or is under common control with You. For
purposes of this definition, "control" means (a) the power, direct
or indirect, to cause the direction or management of such entity,
whether by contract or otherwise, or (b) ownership of more than
fifty percent (50%) of the outstanding shares or beneficial
ownership of such entity.

2. License Grants and Conditions
--------------------------------

2.1. Grants

Each Contributor hereby grants You a world-wide, royalty-free,
non-exclusive license:

(a) under intellectual property rights (other than patent or trademark)
Licensable by such Contributor to use, reproduce, make available,
modify, display, perform, distribute, and otherwise exploit its
Contributions, either on an unmodified basis, with Modifications, or
as part of a Larger Work; and

(b) under Patent Claims of such Contributor to make, use, sell, offer
for sale, have made, import, and otherwise transfer either its
Contributions or its Contributor Version.

2.2. Effective Date

The licenses granted in Section 2.1 with respect to any Contribution
become effective for each Contribution on the date the Contributor first
distributes such Contribution.

2.3. Limitations on Grant Scope

The licenses granted in this Section 2 are the only rights granted under
this License. No additional rights or licenses will be implied from the
distribution or licensing of Covered Software under this License.
Notwithstanding Section 2.1(b) above, no patent license is granted by a
Contributor:

(a) for any code that a Contributor has removed from Covered Software;
or

(b) for infringements caused by: (i) Your and any other third party's
modifications of Covered Software, or (ii) the combination of its
Contributions with other software (except as part of its Contributor
Version); or

(c) under Patent Claims infringed by Covered Software in the absence of
its Contributions.

This License does not grant any rights in the trademarks, service marks,
or logos of any Contributor (except as may be necessary to comply with
the notice requirements in Section 3.4).

2.4. Subsequent Licenses

No Contributor makes additional grants as a result of Your choice to
distribute the Covered Software under a subsequent version of this
License (see Section 10.2) or under the terms of a Secondary License (if
permitted under the terms of Section 3.3).

2.5. Representation

Each Contributor represents that the Contributor believes its
Contributions are its original creation(s) or it has sufficient rights
to grant the rights to its Contributions conveyed by this License.

2.6. Fair Use

This License is not intended to limit any rights You have under
applicable copyright doctrines of fair use, fair dealing, or other
equivalents.

2.7. Conditions

Sections 3.1, 3.2, 3.3, and 3.4 are conditions of the licenses granted
in Section 2.1.

3. Responsibilities
-------------------

3.1. Distribution of Source Form

All distribution of Covered Software in Source Code Form, including any
Modifications that You create or to which You contribute, must be under
the terms of this License. You must inform recipients that the Source
Code Form of the Covered Software is governed by the terms of this
License, and how they can obtain a copy of this License. You may not
attempt to alter or restrict the recipients' rights in the Source Code
Form.

3.2. Distribution of Executable Form

If You distribute Covered Software in Executable Form then:

(a) such Covered Software must also be made available in Source Code
Form, as described in Section 3.1, and You must inform recipients of
the Executable Form how they can obtain a copy of such Source Code
Form by reasonable means in a timely manner, at a charge no more
than the cost of distribution to the recipient; and

(b) You may distribute such Executable Form under the terms of this
License, or sublicense it under different terms, provided that the
license for the Executable Form does not attempt to limit or alter
the recipients' rights in the Source Code Form under this License.

3.3. Distribution of a Larger Work

You may create and distribute a Larger Work under terms of Your choice,
provided that You also comply with the requirements of this License for
the Covered Software. If the Larger Work is a combination of Covered
Software with a work governed by one or more Secondary Licenses, and the
Covered Software is not Incompatible With Secondary Licenses, this
License permits You to additionally distribute such Covered Software
under the terms of such Secondary License(s), so that the recipient of
the Larger Work may, at their option, further distribute the Covered
Software under the terms of either this License or such Secondary
License(s).

3.4. Notices

You may not remove or alter the substance of any license notices
(including copyright notices, patent notices, disclaimers of warranty,
or limitations of liability) contained within the Source Code Form of
the Covered Software, except that You may alter any license notices to
the extent required to remedy known factual inaccuracies.

3.5. Application of Additional Terms

You may choose to offer, and to charge a fee for, warranty, support,
indemnity or liability obligations to one or more recipients of Covered
Software. However, You may do so only on Your own behalf, and not on
behalf of any Contributor. You must make it absolutely clear that any
such warranty, support, indemnity, or liability obligation is offered by
You alone, and You hereby agree to indemnify every Contributor for any
liability incurred by such Contributor as a result of warranty, support,
indemnity or liability terms You offer. You may include additional
disclaimers of warranty and limitations of liability specific to any
jurisdiction.

4. Inability to Comply Due to Statute or Regulation
---------------------------------------------------

If it is impossible for You to comply with any of the terms of this
License with respect to some or all of the Covered Software due to
statute, judicial order, or regulation then You must: (a) comply with
the terms of this License to the maximum extent possible; and (b)
describe the limitations and the code they affect. Such description must
be placed in a text file included with all distributions of the Covered
Software under this License. Except to the extent prohibited by statute
or regulation, such description must be sufficiently detailed for a
recipient of ordinary skill to be able to understand it.

5. Termination
--------------

5.1. The rights granted under this License will terminate automatically
if You fail to comply with any of its terms. However, if You become
compliant, then the rights granted under this License from a particular
Contributor are reinstated (a) provisionally, unless and until such
Contributor explicitly and finally terminates Your grants, and (b) on an
ongoing basis, if such Contributor fails to notify You of the
non-compliance by some reasonable means prior to 60 days after You have
come back into compliance. Moreover, Your grants from a particular
Contributor are reinstated on an ongoing basis if such Contributor
notifies You of the non-compliance by some reasonable means, this is the
first time You have received notice of non-compliance with this License
from such Contributor, and You become compliant prior to 30 days after
Your receipt of the notice.

5.2. If You initiate litigation against any entity by asserting a patent
infringement claim (excluding declaratory judgment actions,
counter-claims, and cross-claims) alleging that a Contributor Version
directly or indirectly infringes any patent, then the rights granted to
You by any and all Contributors for the Covered Software under Section
2.1 of this License shall terminate.

5.3. In the event of termination under Sections 5.1 or 5.2 above, all
end user license agreements (excluding distributors and resellers) which
have been validly granted by You or Your distributors under this License
prior to termination shall survive termination.

************************************************************************
* *
* 6. Disclaimer of Warranty *
* ------------------------- *
* *
* Covered Software is provided under this License on an "as is" *
* basis, without warranty of any kind, either expressed, implied, or *
* statutory, including, without limitation, warranties that the *
* Covered Software is free of defects, merchantable, fit for a *
* particular purpose or non-infringing. The entire risk as to the *
* quality and performance of the Covered Software is with You. *
* Should any Covered Software prove defective in any respect, You *
* (not any Contributor) assume the cost of any necessary servicing, *
* repair, or correction. This disclaimer of warranty constitutes an *
* essential part of this License. No use of any Covered Software is *
* authorized under this License except under this disclaimer. *
* *
************************************************************************

************************************************************************
* *
* 7. Limitation of Liability *
* -------------------------- *
* *
* Under no circumstances and under no legal theory, whether tort *
* (including negligence), contract, or otherwise, shall any *
* Contributor, or anyone who distributes Covered Software as *
* permitted above, be liable to You for any direct, indirect, *
* special, incidental, or consequential damages of any character *
* including, without limitation, damages for lost profits, loss of *
* goodwill, work stoppage, computer failure or malfunction, or any *
* and all other commercial damages or losses, even if such party *
* shall have been informed of the possibility of such damages. This *
* limitation of liability shall not apply to liability for death or *
* personal injury resulting from such party's negligence to the *
* extent applicable law prohibits such limitation. Some *
* jurisdictions do not allow the exclusion or limitation of *
* incidental or consequential damages, so this exclusion and *
* limitation may not apply to You. *
* *
************************************************************************

8. Litigation
-------------

Any litigation relating to this License may be brought only in the
courts of a jurisdiction where the defendant maintains its principal
place of business and such litigation shall be governed by laws of that
jurisdiction, without reference to its conflict-of-law provisions.
Nothing in this Section shall prevent a party's ability to bring
cross-claims or counter-claims.

9. Miscellaneous
----------------

This License represents the complete agreement concerning the subject
matter hereof. If any provision of this License is held to be
unenforceable, such provision shall be reformed only to the extent
necessary to make it enforceable. Any law or regulation which provides
that the language of a contract shall be construed against the drafter
shall not be used to construe this License against a Contributor.

10. Versions of the License
---------------------------

10.1. New Versions

Mozilla Foundation is the license steward. Except as provided in Section
10.3, no one other than the license steward has the right to modify or
publish new versions of this License. Each version will be given a
distinguishing version number.

10.2. Effect of New Versions

You may distribute the Covered Software under the terms of the version
of the License under which You originally received the Covered Software,
or under the terms of any subsequent version published by the license
steward.

10.3. Modified Versions

If you create software not governed by this License, and you want to
create a new license for such software, you may create and use a
modified version of this License if you rename the license and remove
any references to the name of the license steward (except to note that
such modified license differs from this License).

10.4. Distributing Source Code Form that is Incompatible With Secondary
Licenses

If You choose to distribute Source Code Form that is Incompatible With
Secondary Licenses under the terms of this version of the License, the
notice described in Exhibit B of this License must be attached.

Exhibit A - Source Code Form License Notice
-------------------------------------------

This Source Code Form is subject to the terms of the Mozilla Public
License, v. 2.0. If a copy of the MPL was not distributed with this
file, You can obtain one at https://mozilla.org/MPL/2.0/.

If it is not possible or desirable to put the notice in a particular
file, then You may include the notice in a location (such as a LICENSE
file in a relevant directory) where a recipient would be likely to look
for such a notice.

You may add additional accurate notices of copyright ownership.

Exhibit B - "Incompatible With Secondary Licenses" Notice
---------------------------------------------------------

This Source Code Form is "Incompatible With Secondary Licenses", as
defined by the Mozilla Public License, v. 2.0.
```

---
## Proprietary modules

The individual author. **Operates under Teralidarium Works with contact email
`legal@lidarium.com`** (`lidarium.com`). Created the following from
scratch. They are **not** open source and are **not** covered by any licence in
this file:

| Component | Location |
|---|---|
| FastAPI backend application and all API routes | `backend/` |
| Prompt interceptor and rate limiter services | `backend/services/` |
| Scraping adapters | `backend/adapters/scraping/` |
| Secure keychain storage with biometric auth | `frontend/electron/keys.js` |
| Electron main process, IPC bridge and update logic | `frontend/electron/main.js` |
| Application metrics module | `frontend/electron/metrics.js` |
| React application, hooks and state management | `frontend/src/` |
| Structured logging module | `frontend/src/lib/logger.ts` |
| Third-Party Notices data and schema | `frontend/src/lib/thirdPartyNotices.ts` |
| Offline font loader | `frontend/src/lib/fonts.ts` |
| Shadcn-based UI component set | `frontend/src/components/ui/` |
| Cloudflare deployment worker (Google + Meta adapters) | `cloudflare-worker/src/index.js` |

> Note: `backend/adapters/ads/` contained the original Phase 6 Python ad
> platform adapters. These were ported to `cloudflare-worker/src/index.js` and
> are no longer part of the shipped application.

---


## Python backend — full package list

Regenerated with: `backend/venv/bin/pip-licenses --format=markdown --order=license`

| Name                      | Version     | License                                                                        |
|---------------------------|-------------|--------------------------------------------------------------------------------|
| protobuf                  | 6.33.6      | 3-Clause BSD License                                                           |
| multidict                 | 6.9.0       | Apache License 2.0                                                             |
| aiofiles                  | 25.1.0      | Apache Software License                                                        |
| aiosignal                 | 1.4.0       | Apache Software License                                                        |
| cyclonedx-python-lib      | 11.12.0     | Apache Software License                                                        |
| distro                    | 1.9.0       | Apache Software License                                                        |
| google-api-core           | 2.29.0      | Apache Software License                                                        |
| google-api-python-client  | 2.188.0     | Apache Software License                                                        |
| google-auth               | 2.48.0      | Apache Software License                                                        |
| google-auth-httplib2      | 0.4.2       | Apache Software License                                                        |
| google-auth-oauthlib      | 1.2.4       | Apache Software License                                                        |
| groq                      | 1.0.0       | Apache Software License                                                        |
| openai                    | 2.26.0      | Apache Software License                                                        |
| pip_api                   | 0.0.35      | Apache Software License                                                        |
| pip_audit                 | 2.10.1      | Apache Software License                                                        |
| proto-plus                | 1.28.4      | Apache Software License                                                        |
| py-serializable           | 2.1.0       | Apache Software License                                                        |
| requests                  | 2.33.0      | Apache Software License                                                        |
| requests-toolbelt         | 1.0.0       | Apache Software License                                                        |
| rsa                       | 4.9.1       | Apache Software License                                                        |
| sortedcontainers          | 2.4.0       | Apache Software License                                                        |
| tenacity                  | 9.1.4       | Apache Software License                                                        |
| python-dateutil           | 2.9.0.post0 | Apache Software License; BSD License                                           |
| pyinstaller-hooks-contrib | 2026.7      | Apache Software License; GNU General Public License v2 (GPLv2)                 |
| sniffio                   | 1.3.1       | Apache Software License; MIT License                                           |
| CacheControl              | 0.14.4      | Apache-2.0                                                                     |
| Cython                    | 3.3.0       | Apache-2.0                                                                     |
| frozenlist                | 1.8.0       | Apache-2.0                                                                     |
| google-genai              | 1.65.0      | Apache-2.0                                                                     |
| googleapis-common-protos  | 1.75.3      | Apache-2.0                                                                     |
| license-expression        | 30.4.4      | Apache-2.0                                                                     |
| msgpack                   | 1.2.3       | Apache-2.0                                                                     |
| opentelemetry-api         | 1.44.0      | Apache-2.0                                                                     |
| playwright                | 1.63.0      | Apache-2.0                                                                     |
| propcache                 | 0.5.4       | Apache-2.0                                                                     |
| pytest-asyncio            | 1.4.0       | Apache-2.0                                                                     |
| python-multipart          | 0.0.32      | Apache-2.0                                                                     |
| yarl                      | 1.25.1      | Apache-2.0                                                                     |
| regex                     | 2026.9.29   | Apache-2.0 AND CNRI-Python                                                     |
| aiohttp                   | 3.14.3      | Apache-2.0 AND MIT                                                             |
| packaging                 | 26.3        | Apache-2.0 OR BSD-2-Clause                                                     |
| cryptography              | 50.0.1      | Apache-2.0 OR BSD-3-Clause                                                     |
| ormsgpack                 | 1.12.2      | Apache-2.0 OR MIT                                                              |
| uritemplate               | 4.2.0       | BSD 3-Clause OR Apache-2.0                                                     |
| cloudpickle               | 3.1.2       | BSD License                                                                    |
| httpx                     | 0.28.1      | BSD License                                                                    |
| jsonpatch                 | 1.33        | BSD License                                                                    |
| jsonpointer               | 3.1.1       | BSD License                                                                    |
| prompt_toolkit            | 3.0.53      | BSD License                                                                    |
| pyasn1_modules            | 0.4.2       | BSD License                                                                    |
| reportlab                 | 4.4.9       | BSD License                                                                    |
| requests-oauthlib         | 2.0.0       | BSD License                                                                    |
| websockets                | 15.0.1      | BSD License                                                                    |
| Pygments                  | 2.21.0      | BSD-2-Clause                                                                   |
| boolean.py                | 5.0         | BSD-2-Clause                                                                   |
| pyasn1                    | 0.6.4       | BSD-2-Clause                                                                   |
| xxhash                    | 4.0.1       | BSD-2-Clause                                                                   |
| click                     | 8.3.3       | BSD-3-Clause                                                                   |
| httpcore                  | 1.0.9       | BSD-3-Clause                                                                   |
| httpcore2                 | 2.13.0      | BSD-3-Clause                                                                   |
| httpx2                    | 2.13.0      | BSD-3-Clause                                                                   |
| idna                      | 3.20        | BSD-3-Clause                                                                   |
| lxml                      | 6.1.3       | BSD-3-Clause                                                                   |
| oauthlib                  | 3.3.1       | BSD-3-Clause                                                                   |
| portalocker               | 4.4.0       | BSD-3-Clause                                                                   |
| psutil                    | 7.2.2       | BSD-3-Clause                                                                   |
| pycparser                 | 3.0         | BSD-3-Clause                                                                   |
| pypdf                     | 6.16.2      | BSD-3-Clause                                                                   |
| python-dotenv             | 1.2.2       | BSD-3-Clause                                                                   |
| sse-starlette             | 3.4.11      | BSD-3-Clause                                                                   |
| starlette                 | 1.6.0       | BSD-3-Clause                                                                   |
| uuid_utils                | 0.17.1      | BSD-3-Clause                                                                   |
| uvicorn                   | 0.53.0      | BSD-3-Clause                                                                   |
| zstandard                 | 0.25.0      | BSD-3-Clause                                                                   |
| pyinstaller               | 6.22.3      | GNU General Public License v2 (GPLv2)                                          |
| PyJWT                     | 2.14.0      | MIT                                                                            |
| annotated-doc             | 0.0.5       | MIT                                                                            |
| annotated-types           | 0.8.0       | MIT                                                                            |
| anyio                     | 4.12.1      | MIT                                                                            |
| attrs                     | 26.1.0      | MIT                                                                            |
| browser-harness           | 0.1.13      | MIT                                                                            |
| browser-use-sdk           | 3.4.2       | MIT                                                                            |
| charset-normalizer        | 3.5.1       | MIT                                                                            |
| fastapi                   | 0.141.1     | MIT                                                                            |
| filelock                  | 4.1.1       | MIT                                                                            |
| iniconfig                 | 2.3.0       | MIT                                                                            |
| jiter                     | 0.17.0      | MIT                                                                            |
| jsonschema                | 4.26.0      | MIT                                                                            |
| jsonschema-specifications | 2025.9.1    | MIT                                                                            |
| langchain-google-genai    | 4.4.0       | MIT                                                                            |
| langgraph                 | 1.2.12      | MIT                                                                            |
| langgraph-checkpoint      | 4.2.0       | MIT                                                                            |
| langgraph-prebuilt        | 1.1.0       | MIT                                                                            |
| langgraph-sdk             | 0.4.5       | MIT                                                                            |
| langsmith                 | 0.14.2      | MIT                                                                            |
| ollama                    | 0.6.1       | MIT                                                                            |
| pip-requirements-parser   | 32.0.1      | MIT                                                                            |
| platformdirs              | 4.13.0      | MIT                                                                            |
| pydantic                  | 2.13.5      | MIT                                                                            |
| pydantic-settings         | 2.15.0      | MIT                                                                            |
| pydantic_core             | 2.46.5      | MIT                                                                            |
| pyobjc-core               | 12.2.2      | MIT                                                                            |
| pyobjc-framework-Cocoa    | 12.2.2      | MIT                                                                            |
| pyparsing                 | 3.3.2       | MIT                                                                            |
| pytest                    | 9.1.1       | MIT                                                                            |
| referencing               | 0.37.0      | MIT                                                                            |
| rpds-py                   | 2026.6.3    | MIT                                                                            |
| sentry-sdk                | 2.71.0      | MIT                                                                            |
| soupsieve                 | 2.9.2       | MIT                                                                            |
| tomli                     | 2.5.0       | MIT                                                                            |
| truststore                | 0.10.4      | MIT                                                                            |
| typing-inspection         | 0.4.4       | MIT                                                                            |
| urllib3                   | 2.8.0       | MIT                                                                            |
| greenlet                  | 3.5.6       | MIT AND PSF-2.0                                                                |
| PyYAML                    | 6.0.3       | MIT License                                                                    |
| altgraph                  | 0.17.5      | MIT License                                                                    |
| anthropic                 | 0.76.0      | MIT License                                                                    |
| backoff                   | 2.2.1       | MIT License                                                                    |
| beautifulsoup4            | 4.15.0      | MIT License                                                                    |
| browser-use               | 0.13.10     | MIT License                                                                    |
| bubus                     | 1.5.6       | MIT License                                                                    |
| cdp-use                   | 1.4.5       | MIT License                                                                    |
| docstring_parser          | 0.18.0      | MIT License                                                                    |
| fetch-use                 | 0.4.0       | MIT License                                                                    |
| filetype                  | 1.2.0       | MIT License                                                                    |
| h11                       | 0.16.0      | MIT License                                                                    |
| httplib2                  | 0.32.0      | MIT License                                                                    |
| inquirerpy                | 0.3.4       | MIT License                                                                    |
| langchain                 | 1.4.3       | MIT License                                                                    |
| langchain-core            | 1.6.6       | MIT License                                                                    |
| langchain-openai          | 1.3.4       | MIT License                                                                    |
| langchain-protocol        | 0.0.19      | MIT License                                                                    |
| macholib                  | 1.16.4      | MIT License                                                                    |
| markdown-it-py            | 4.2.0       | MIT License                                                                    |
| markdownify               | 1.2.2       | MIT License                                                                    |
| mcp                       | 2.1.1       | MIT License                                                                    |
| mcp-types                 | 2.1.1       | MIT License                                                                    |
| mdurl                     | 0.1.2       | MIT License                                                                    |
| packageurl-python         | 0.17.6      | MIT License                                                                    |
| pfzy                      | 0.3.4       | MIT License                                                                    |
| pluggy                    | 1.6.0       | MIT License                                                                    |
| posthog                   | 7.7.0       | MIT License                                                                    |
| pyee                      | 13.0.1      | MIT License                                                                    |
| pyotp                     | 2.9.0       | MIT License                                                                    |
| python-docx               | 1.2.0       | MIT License                                                                    |
| rich                      | 14.3.3      | MIT License                                                                    |
| screeninfo                | 0.8.1       | MIT License                                                                    |
| six                       | 1.17.0      | MIT License                                                                    |
| tomli_w                   | 1.2.0       | MIT License                                                                    |
| uuid7                     | 0.1.0       | MIT License                                                                    |
| tiktoken                  | 0.14.0      | MIT License                                                                    |
|                           |             |                                                                                |
|                           |             | Copyright (c) 2022 OpenAI, Shantanu Jain                                       |
|                           |             |                                                                                |
|                           |             | Permission is hereby granted, free of charge, to any person obtaining a copy   |
|                           |             | of this software and associated documentation files (the "Software"), to deal  |
|                           |             | in the Software without restriction, including without limitation the rights   |
|                           |             | to use, copy, modify, merge, publish, distribute, sublicense, and/or sell      |
|                           |             | copies of the Software, and to permit persons to whom the Software is          |
|                           |             | furnished to do so, subject to the following conditions:                       |
|                           |             |                                                                                |
|                           |             | The above copyright notice and this permission notice shall be included in all |
|                           |             | copies or substantial portions of the Software.                                |
|                           |             |                                                                                |
|                           |             | THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR     |
|                           |             | IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,       |
|                           |             | FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE    |
|                           |             | AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER         |
|                           |             | LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,  |
|                           |             | OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE  |
|                           |             | SOFTWARE.                                                                      |
|                           |             |                                                                                |
| structlog                 | 26.1.0      | MIT OR Apache-2.0                                                              |
| cffi                      | 2.1.1       | MIT-0                                                                          |
| pillow                    | 12.3.0      | MIT-CMU                                                                        |
| orjson                    | 3.12.0      | MPL-2.0 AND (Apache-2.0 OR MIT)                                                |
| tqdm                      | 4.70.1      | MPL-2.0 AND MIT                                                                |
| certifi                   | 2026.7.22   | Mozilla Public License 2.0 (MPL 2.0)                                           |
| typing_extensions         | 4.15.0      | PSF-2.0                                                                        |
| aiohappyeyeballs          | 2.7.1       | Python Software Foundation License                                             |
| defusedxml                | 0.7.1       | Python Software Foundation License                                             |


## JavaScript frontend — full package list

Produced by `tools/js-licenses.cjs`, which reads each installed package's
own `license` field and falls back to its `LICENSE` file when package.json
omits one. Transitive dependencies are included.

## JavaScript frontend — full package list

Generated by `tools/js-licenses.cjs` from each installed package's own `license` field. Transitive dependencies are included.

| Name | Version | License |
|---|---|---|
| @babel/runtime | 7.29.7 | MIT |
| @electron-internal/extract-zip | 1.0.5 | BSD-2-Clause |
| @electron/asar | 3.4.1 | MIT |
| @electron/fuses | 1.8.0 | MIT |
| @electron/get | 5.1.0 | MIT |
| @electron/get | 3.1.0 | MIT |
| @electron/notarize | 2.5.0 | MIT |
| @electron/osx-sign | 1.3.3 | BSD-2-Clause |
| @electron/rebuild | 4.2.0 | MIT |
| @electron/universal | 2.0.3 | MIT |
| @emnapi/core | 1.11.1 | MIT |
| @emnapi/runtime | 1.11.1 | MIT |
| @emnapi/wasi-threads | 1.2.2 | MIT |
| @epic-web/invariant | 1.0.0 | MIT |
| @floating-ui/core | 1.8.0 | MIT |
| @floating-ui/dom | 1.8.0 | MIT |
| @floating-ui/react-dom | 2.1.9 | MIT |
| @floating-ui/utils | 0.2.12 | MIT |
| @hapi/address | 5.1.1 | BSD-3-Clause |
| @hapi/formula | 3.0.2 | BSD-3-Clause |
| @hapi/hoek | 11.0.7 | BSD-3-Clause |
| @hapi/pinpoint | 2.0.1 | BSD-3-Clause |
| @hapi/tlds | 1.1.7 | BSD-3-Clause |
| @hapi/topo | 6.0.2 | BSD-3-Clause |
| @icons/material | 0.2.4 | MIT |
| @isaacs/fs-minipass | 4.0.1 | ISC |
| @jridgewell/gen-mapping | 0.3.13 | MIT |
| @jridgewell/remapping | 2.3.5 | MIT |
| @jridgewell/resolve-uri | 3.1.2 | MIT |
| @jridgewell/sourcemap-codec | 1.5.5 | MIT |
| @jridgewell/trace-mapping | 0.3.31 | MIT |
| @malept/cross-spawn-promise | 2.0.0 | Apache-2.0 |
| @malept/flatpak-bundler | 0.4.0 | MIT |
| @mapbox/node-pre-gyp | 1.0.11 | BSD-3-Clause |
| @napi-rs/wasm-runtime | 1.2.1 | MIT |
| @noble/hashes | 2.2.0 | MIT |
| @noble/hashes | 1.4.0 | MIT |
| @opentelemetry/api | 1.9.1 | Apache-2.0 |
| @opentelemetry/api-logs | 0.220.0 | Apache-2.0 |
| @opentelemetry/core | 2.11.0 | Apache-2.0 |
| @opentelemetry/instrumentation | 0.220.0 | Apache-2.0 |
| @opentelemetry/resources | 2.11.0 | Apache-2.0 |
| @opentelemetry/sdk-trace | 2.11.0 | Apache-2.0 |
| @opentelemetry/sdk-trace-base | 2.11.0 | Apache-2.0 |
| @opentelemetry/semantic-conventions | 1.43.0 | Apache-2.0 |
| @oxc-project/types | 0.139.0 | MIT |
| @oxlint/binding-darwin-x64 | 1.76.0 | MIT |
| @peculiar/asn1-schema | 2.8.0 | MIT |
| @peculiar/json-schema | 1.1.12 | MIT |
| @peculiar/utils | 2.0.3 | MIT |
| @peculiar/webcrypto | 1.7.1 | MIT |
| @pinojs/redact | 0.4.0 | MIT |
| @radix-ui/number | 1.0.1 | MIT |
| @radix-ui/number | 1.1.3 | MIT |
| @radix-ui/number | 1.1.3 | MIT |
| @radix-ui/primitive | 1.1.7 | MIT |
| @radix-ui/primitive | 1.0.1 | MIT |
| @radix-ui/react-arrow | 1.0.3 | MIT |
| @radix-ui/react-arrow | 1.1.16 | MIT |
| @radix-ui/react-arrow | 1.1.16 | MIT |
| @radix-ui/react-collection | 1.0.3 | MIT |
| @radix-ui/react-collection | 1.1.16 | MIT |
| @radix-ui/react-collection | 1.1.16 | MIT |
| @radix-ui/react-collection | 1.1.16 | MIT |
| @radix-ui/react-collection | 1.1.15 | MIT |
| @radix-ui/react-compose-refs | 1.0.1 | MIT |
| @radix-ui/react-compose-refs | 1.0.1 | MIT |
| @radix-ui/react-compose-refs | 1.1.5 | MIT |
| @radix-ui/react-compose-refs | 1.0.1 | MIT |
| @radix-ui/react-compose-refs | 1.0.1 | MIT |
| @radix-ui/react-compose-refs | 1.0.1 | MIT |
| @radix-ui/react-context | 1.0.1 | MIT |
| @radix-ui/react-context | 1.2.2 | MIT |
| @radix-ui/react-context | 1.0.1 | MIT |
| @radix-ui/react-context | 1.0.1 | MIT |
| @radix-ui/react-dialog | 1.1.23 | MIT |
| @radix-ui/react-direction | 1.0.1 | MIT |
| @radix-ui/react-direction | 1.1.5 | MIT |
| @radix-ui/react-direction | 1.1.5 | MIT |
| @radix-ui/react-direction | 1.1.5 | MIT |
| @radix-ui/react-direction | 1.1.5 | MIT |
| @radix-ui/react-dismissable-layer | 1.1.19 | MIT |
| @radix-ui/react-dismissable-layer | 1.1.20 | MIT |
| @radix-ui/react-dismissable-layer | 1.0.4 | MIT |
| @radix-ui/react-dismissable-layer | 1.1.20 | MIT |
| @radix-ui/react-dropdown-menu | 2.1.25 | MIT |
| @radix-ui/react-focus-guards | 1.1.6 | MIT |
| @radix-ui/react-focus-guards | 1.0.1 | MIT |
| @radix-ui/react-focus-scope | 1.1.16 | MIT |
| @radix-ui/react-focus-scope | 1.2.0 | MIT |
| @radix-ui/react-focus-scope | 1.0.3 | MIT |
| @radix-ui/react-id | 1.1.4 | MIT |
| @radix-ui/react-id | 1.0.1 | MIT |
| @radix-ui/react-label | 2.1.16 | MIT |
| @radix-ui/react-menu | 2.1.25 | MIT |
| @radix-ui/react-popper | 1.3.8 | MIT |
| @radix-ui/react-popper | 1.1.2 | MIT |
| @radix-ui/react-popper | 1.3.8 | MIT |
| @radix-ui/react-portal | 1.1.18 | MIT |
| @radix-ui/react-portal | 1.1.17 | MIT |
| @radix-ui/react-portal | 1.0.3 | MIT |
| @radix-ui/react-portal | 1.1.18 | MIT |
| @radix-ui/react-presence | 1.1.11 | MIT |
| @radix-ui/react-presence | 1.1.10 | MIT |
| @radix-ui/react-presence | 1.1.11 | MIT |
| @radix-ui/react-presence | 1.1.11 | MIT |
| @radix-ui/react-primitive | 1.0.3 | MIT |
| @radix-ui/react-primitive | 1.0.3 | MIT |
| @radix-ui/react-primitive | 2.1.11 | MIT |
| @radix-ui/react-primitive | 2.1.11 | MIT |
| @radix-ui/react-primitive | 2.1.11 | MIT |
| @radix-ui/react-primitive | 1.0.3 | MIT |
| @radix-ui/react-primitive | 2.1.10 | MIT |
| @radix-ui/react-primitive | 2.1.11 | MIT |
| @radix-ui/react-primitive | 2.1.11 | MIT |
| @radix-ui/react-primitive | 1.0.3 | MIT |
| @radix-ui/react-primitive | 2.1.11 | MIT |
| @radix-ui/react-primitive | 2.1.11 | MIT |
| @radix-ui/react-primitive | 2.1.11 | MIT |
| @radix-ui/react-primitive | 1.0.3 | MIT |
| @radix-ui/react-roving-focus | 1.1.20 | MIT |
| @radix-ui/react-scroll-area | 1.3.0 | MIT |
| @radix-ui/react-select | 1.2.2 | MIT |
| @radix-ui/react-separator | 1.1.16 | MIT |
| @radix-ui/react-slider | 1.5.0 | MIT |
| @radix-ui/react-slot | 1.0.2 | MIT |
| @radix-ui/react-slot | 1.0.2 | MIT |
| @radix-ui/react-slot | 1.4.0 | MIT |
| @radix-ui/react-slot | 1.4.0 | MIT |
| @radix-ui/react-slot | 1.4.0 | MIT |
| @radix-ui/react-slot | 1.0.2 | MIT |
| @radix-ui/react-slot | 1.4.0 | MIT |
| @radix-ui/react-slot | 1.4.0 | MIT |
| @radix-ui/react-slot | 1.0.2 | MIT |
| @radix-ui/react-slot | 1.4.0 | MIT |
| @radix-ui/react-slot | 1.4.0 | MIT |
| @radix-ui/react-slot | 1.3.3 | MIT |
| @radix-ui/react-slot | 1.4.0 | MIT |
| @radix-ui/react-slot | 1.0.2 | MIT |
| @radix-ui/react-toast | 1.2.23 | MIT |
| @radix-ui/react-tooltip | 1.3.0 | MIT |
| @radix-ui/react-use-callback-ref | 1.0.1 | MIT |
| @radix-ui/react-use-callback-ref | 1.0.1 | MIT |
| @radix-ui/react-use-callback-ref | 1.1.4 | MIT |
| @radix-ui/react-use-callback-ref | 1.0.1 | MIT |
| @radix-ui/react-use-controllable-state | 1.0.1 | MIT |
| @radix-ui/react-use-controllable-state | 1.2.6 | MIT |
| @radix-ui/react-use-effect-event | 0.0.5 | MIT |
| @radix-ui/react-use-escape-keydown | 1.0.3 | MIT |
| @radix-ui/react-use-is-hydrated | 0.1.3 | MIT |
| @radix-ui/react-use-layout-effect | 1.0.1 | MIT |
| @radix-ui/react-use-layout-effect | 1.0.1 | MIT |
| @radix-ui/react-use-layout-effect | 1.1.4 | MIT |
| @radix-ui/react-use-layout-effect | 1.0.1 | MIT |
| @radix-ui/react-use-previous | 1.1.4 | MIT |
| @radix-ui/react-use-previous | 1.0.1 | MIT |
| @radix-ui/react-use-rect | 1.1.4 | MIT |
| @radix-ui/react-use-rect | 1.1.4 | MIT |
| @radix-ui/react-use-rect | 1.0.1 | MIT |
| @radix-ui/react-use-size | 1.1.5 | MIT |
| @radix-ui/react-use-size | 1.1.5 | MIT |
| @radix-ui/react-use-size | 1.1.5 | MIT |
| @radix-ui/react-use-size | 1.0.1 | MIT |
| @radix-ui/react-visually-hidden | 1.2.11 | MIT |
| @radix-ui/react-visually-hidden | 1.2.12 | MIT |
| @radix-ui/react-visually-hidden | 1.0.3 | MIT |
| @radix-ui/rect | 1.1.3 | MIT |
| @radix-ui/rect | 1.1.3 | MIT |
| @radix-ui/rect | 1.0.1 | MIT |
| @rolldown/binding-darwin-x64 | 1.1.5 | MIT |
| @rolldown/pluginutils | 1.0.1 | MIT |
| @sentry/browser | 10.75.0 | MIT |
| @sentry/browser-utils | 10.75.0 | MIT |
| @sentry/conventions | 0.16.0 | MIT |
| @sentry/core | 10.75.0 | MIT |
| @sentry/electron | 7.20.0 | MIT |
| @sentry/feedback | 10.75.0 | MIT |
| @sentry/node | 10.75.0 | MIT |
| @sentry/node-core | 10.75.0 | MIT |
| @sentry/opentelemetry | 10.75.0 | MIT |
| @sentry/replay | 10.75.0 | MIT |
| @sentry/replay-canvas | 10.75.0 | MIT |
| @sentry/server-utils | 10.75.0 | MIT |
| @sindresorhus/is | 4.6.0 | MIT |
| @standard-schema/spec | 1.1.0 | MIT |
| @szmarczak/http-timer | 4.0.6 | MIT |
| @tailwindcss/node | 4.3.3 | MIT |
| @tailwindcss/oxide | 4.3.3 | MIT |
| @tailwindcss/oxide-darwin-x64 | 4.3.3 | MIT |
| @tailwindcss/vite | 4.3.3 | MIT |
| @tootallnate/once | 2.0.1 | MIT |
| @tybys/wasm-util | 0.10.3 | MIT |
| @types/cacheable-request | 6.0.3 | MIT |
| @types/debug | 4.1.13 | MIT |
| @types/fs-extra | 9.0.13 | MIT |
| @types/http-cache-semantics | 4.2.0 | MIT |
| @types/js-cookie | 3.0.6 | MIT |
| @types/keyv | 3.1.4 | MIT |
| @types/lodash | 4.17.25 | MIT |
| @types/lodash.debounce | 4.0.9 | MIT |
| @types/material-colors | 1.2.3 | MIT |
| @types/ms | 2.1.0 | MIT |
| @types/node | 24.13.3 | MIT |
| @types/react | 19.2.17 | MIT |
| @types/react-color | 3.0.13 | MIT |
| @types/react-dom | 19.2.3 | MIT |
| @types/reactcss | 1.2.13 | MIT |
| @types/responselike | 1.0.3 | MIT |
| @types/uuid | 8.3.4 | MIT |
| @vitejs/plugin-react | 6.0.5 | MIT |
| @xmldom/xmldom | 0.8.13 | MIT |
| @xobotyi/scrollbar-width | 1.9.5 | MIT |
| abab | 2.0.6 | BSD-3-Clause |
| abbrev | 1.1.1 | ISC |
| abbrev | 4.0.0 | ISC |
| acorn | 8.18.0 | MIT |
| acorn | 7.4.1 | MIT |
| acorn-globals | 6.0.0 | MIT |
| acorn-walk | 7.2.0 | MIT |
| adm-zip | 0.6.1 | MIT |
| agent-base | 6.0.2 | MIT |
| agent-base | 7.1.4 | MIT |
| agent-base | 6.0.2 | MIT |
| agent-base | 6.0.2 | MIT |
| ajv | 8.20.0 | MIT |
| ansi-regex | 6.2.2 | MIT |
| ansi-regex | 5.0.1 | MIT |
| ansi-regex | 5.0.1 | MIT |
| ansi-regex | 5.0.1 | MIT |
| ansi-styles | 4.3.0 | MIT |
| ansi-styles | 6.2.3 | MIT |
| ansi-styles | 4.3.0 | MIT |
| ansi-styles | 4.3.0 | MIT |
| ansi-styles | 4.3.0 | MIT |
| app-builder-lib | 26.15.3 | MIT |
| aproba | 2.1.0 | ISC |
| are-we-there-yet | 2.0.0 | ISC |
| argparse | 2.0.1 | Python-2.0 |
| aria-hidden | 1.2.6 | MIT |
| asn1js | 3.0.10 | BSD-3-Clause |
| async | 3.2.6 | MIT |
| async-exit-hook | 2.0.1 | MIT |
| asynckit | 0.4.0 | MIT |
| at-least-node | 1.0.0 | ISC |
| atomic-sleep | 1.0.0 | MIT |
| aws4 | 1.13.2 | MIT |
| axios | 1.19.0 | MIT |
| balanced-match | 1.0.2 | MIT |
| balanced-match | 1.0.2 | MIT |
| balanced-match | 4.0.4 | MIT |
| balanced-match | 1.0.2 | MIT |
| balanced-match | 1.0.2 | MIT |
| balanced-match | 1.0.2 | MIT |
| base64-js | 1.5.1 | MIT |
| bluebird | 3.7.2 | MIT |
| boolean | 3.2.0 | MIT |
| brace-expansion | 1.1.18 | MIT |
| brace-expansion | 2.1.4 | MIT |
| brace-expansion | 5.0.9 | MIT |
| brace-expansion | 1.1.18 | MIT |
| brace-expansion | 2.1.4 | MIT |
| brace-expansion | 1.1.18 | MIT |
| browser-process-hrtime | 1.0.0 | BSD-2-Clause |
| buffer-from | 1.1.2 | MIT |
| builder-util | 26.15.3 | MIT |
| builder-util-runtime | 9.7.0 | MIT |
| bytestreamjs | 2.0.1 | BSD-3-Clause |
| cacheable-lookup | 5.0.4 | MIT |
| cacheable-request | 7.0.4 | MIT |
| call-bind-apply-helpers | 1.0.2 | MIT |
| canvas | 2.11.2 | MIT |
| chalk | 4.1.2 | MIT |
| chalk | 4.1.2 | MIT |
| chalk | 5.6.2 | MIT |
| chalk | 4.1.2 | MIT |
| chalk | 4.1.2 | MIT |
| chownr | 2.0.0 | ISC |
| chownr | 3.0.0 | BlueOak-1.0.0 |
| chromium-pickle-js | 0.2.0 | MIT |
| ci-info | 4.3.1 | MIT |
| ci-info | 4.4.0 | MIT |
| cjs-module-lexer | 2.2.1 | MIT |
| class-variance-authority | 0.7.1 | Apache-2.0 |
| cliui | 9.0.1 | ISC |
| cliui | 8.0.1 | ISC |
| clone-response | 1.0.3 | MIT |
| clsx | 2.1.1 | MIT |
| color-convert | 2.0.1 | MIT |
| color-name | 1.1.4 | MIT |
| color-support | 1.1.3 | ISC |
| combined-stream | 1.0.8 | MIT |
| commander | 5.1.0 | MIT |
| compare-version | 0.1.2 | MIT |
| concat-map | 0.0.1 | MIT |
| concurrently | 10.0.4 | MIT |
| console-control-strings | 1.1.0 | ISC |
| copy-to-clipboard | 3.3.3 | MIT |
| core-util-is | 1.0.3 | MIT |
| cross-env | 10.1.0 | MIT |
| cross-spawn | 7.0.6 | MIT |
| css-in-js-utils | 3.1.0 | MIT |
| css-tree | 1.1.3 | MIT |
| cssom | 0.5.0 | MIT |
| cssom | 0.3.8 | MIT |
| cssstyle | 2.3.0 | MIT |
| csstype | 3.2.3 | MIT |
| data-urls | 3.0.2 | MIT |
| debug | 4.4.3 | MIT |
| decimal.js | 10.6.0 | MIT |
| decompress-response | 6.0.0 | MIT |
| decompress-response | 4.2.1 | MIT |
| defer-to-connect | 2.0.1 | MIT |
| define-data-property | 1.1.4 | MIT |
| define-properties | 1.2.1 | MIT |
| delayed-stream | 1.0.0 | MIT |
| delegates | 1.0.0 | MIT |
| detect-libc | 2.1.2 | Apache-2.0 |
| detect-node | 2.1.0 | MIT |
| detect-node-es | 1.1.0 | MIT |
| dir-compare | 4.2.0 | MIT |
| dmg-builder | 26.15.3 | MIT |
| domexception | 4.0.0 | MIT |
| dotenv | 16.6.1 | BSD-2-Clause |
| dotenv-expand | 11.0.7 | BSD-2-Clause |
| dunder-proto | 1.0.1 | MIT |
| duplexer2 | 0.1.4 | BSD-3-Clause |
| ejs | 3.1.10 | Apache-2.0 |
| electron | 43.2.0 | MIT |
| electron-builder | 26.15.3 | MIT |
| electron-notarize | 1.2.2 | MIT |
| electron-publish | 26.15.3 | MIT |
| electron-updater | 6.8.9 | MIT |
| emoji-regex | 8.0.0 | MIT |
| emoji-regex | 10.6.0 | MIT |
| emoji-regex | 8.0.0 | MIT |
| emoji-regex | 8.0.0 | MIT |
| end-of-stream | 1.4.5 | MIT |
| enhanced-resolve | 5.24.5 | MIT |
| env-paths | 2.2.1 | MIT |
| env-paths | 3.0.0 | MIT |
| env-paths | 2.2.1 | MIT |
| err-code | 2.0.3 | MIT |
| error-stack-parser | 2.1.4 | MIT |
| es-define-property | 1.0.1 | MIT |
| es-errors | 1.3.0 | MIT |
| es-module-lexer | 3.0.2 | MIT |
| es-object-atoms | 1.1.2 | MIT |
| es-set-tostringtag | 2.1.0 | MIT |
| es6-error | 4.1.1 | MIT |
| escalade | 3.2.0 | MIT |
| escape-string-regexp | 4.0.0 | MIT |
| escodegen | 2.1.0 | BSD-2-Clause |
| esprima | 4.0.1 | BSD-2-Clause |
| estraverse | 5.3.0 | BSD-2-Clause |
| esutils | 2.0.3 | BSD-2-Clause |
| exponential-backoff | 3.1.3 | Apache-2.0 |
| fabric | 5.5.2 | MIT |
| fast-deep-equal | 3.1.3 | MIT |
| fast-shallow-equal | 1.0.0 | Unlicense (public domain) |
| fast-uri | 3.1.4 | BSD-3-Clause |
| fastest-stable-stringify | 2.0.2 | MIT |
| fdir | 6.5.0 | MIT |
| file-selector | 2.1.2 | MIT |
| filelist | 1.0.6 | Apache-2.0 |
| follow-redirects | 1.16.0 | MIT |
| form-data | 4.0.6 | MIT |
| fs-extra | 9.1.0 | MIT |
| fs-extra | 9.1.0 | MIT |
| fs-extra | 11.4.0 | MIT |
| fs-extra | 9.1.0 | MIT |
| fs-extra | 8.1.0 | MIT |
| fs-extra | 9.1.0 | MIT |
| fs-extra | 10.1.0 | MIT |
| fs-extra | 11.3.1 | MIT |
| fs-minipass | 2.1.0 | ISC |
| fs.realpath | 1.0.0 | ISC |
| fsevents | 2.3.3 | MIT |
| function-bind | 1.1.2 | MIT |
| gauge | 3.0.2 | ISC |
| get-caller-file | 2.0.5 | ISC |
| get-east-asian-width | 1.6.0 | MIT |
| get-intrinsic | 1.3.0 | MIT |
| get-nonce | 1.0.1 | MIT |
| get-proto | 1.0.1 | MIT |
| get-stream | 5.2.0 | MIT |
| glob | 7.2.3 | ISC |
| global-agent | 3.0.0 | BSD-3-Clause |
| globalthis | 1.0.4 | MIT |
| gopd | 1.2.0 | MIT |
| got | 11.8.6 | MIT |
| graceful-fs | 4.2.11 | ISC |
| has-flag | 4.0.0 | MIT |
| has-property-descriptors | 1.0.2 | MIT |
| has-symbols | 1.1.0 | MIT |
| has-tostringtag | 1.0.2 | MIT |
| has-unicode | 2.0.1 | ISC |
| hasown | 2.0.4 | MIT |
| hosted-git-info | 4.1.0 | ISC |
| html-encoding-sniffer | 3.0.0 | MIT |
| http-cache-semantics | 4.2.0 | BSD-2-Clause |
| http-proxy-agent | 7.0.2 | MIT |
| http-proxy-agent | 5.0.0 | MIT |
| http2-wrapper | 1.0.3 | MIT |
| https-proxy-agent | 5.0.1 | MIT |
| https-proxy-agent | 5.0.1 | MIT |
| https-proxy-agent | 7.0.6 | MIT |
| https-proxy-agent | 5.0.1 | MIT |
| hyphenate-style-name | 1.1.0 | BSD-3-Clause |
| iconv-lite | 0.6.3 | MIT |
| import-in-the-middle | 3.5.1 | Apache-2.0 |
| inflight | 1.0.6 | ISC |
| inherits | 2.0.4 | ISC |
| inline-style-prefixer | 7.0.1 | MIT |
| is-fullwidth-code-point | 3.0.0 | MIT |
| is-potential-custom-element-name | 1.0.1 | MIT |
| isarray | 1.0.0 | MIT |
| isbinaryfile | 4.0.10 | MIT |
| isbinaryfile | 5.0.7 | MIT |
| isexe | 3.1.5 | BlueOak-1.0.0 |
| isexe | 2.0.0 | ISC |
| isexe | 4.0.0 | BlueOak-1.0.0 |
| jake | 10.9.4 | Apache-2.0 |
| jiti | 2.7.0 | MIT |
| joi | 18.2.3 | BSD-3-Clause |
| js-cookie | 3.0.8 | MIT |
| js-tokens | 4.0.0 | MIT |
| js-yaml | 4.3.0 | MIT |
| jsdom | 19.0.0 | MIT |
| json-buffer | 3.0.1 | MIT |
| json-schema-traverse | 1.0.0 | MIT |
| json-stringify-safe | 5.0.1 | ISC |
| json5 | 2.2.3 | MIT |
| jsonfile | 4.0.0 | MIT |
| jsonfile | 6.2.1 | MIT |
| keyv | 4.5.4 | MIT |
| lazy-val | 1.0.5 | MIT |
| lightningcss | 1.32.0 | MPL-2.0 |
| lightningcss | 1.33.0 | MPL-2.0 |
| lightningcss-darwin-x64 | 1.32.0 | MPL-2.0 |
| lightningcss-darwin-x64 | 1.33.0 | MPL-2.0 |
| lodash | 4.18.1 | MIT |
| lodash-es | 4.18.1 | MIT |
| lodash.debounce | 4.0.8 | MIT |
| lodash.escaperegexp | 4.1.2 | MIT |
| lodash.isequal | 4.5.0 | MIT |
| loose-envify | 1.4.0 | MIT |
| lowercase-keys | 2.0.0 | MIT |
| lru-cache | 6.0.0 | ISC |
| lucide-react | 0.263.1 | ISC |
| magic-string | 0.30.21 | MIT |
| make-dir | 3.1.0 | MIT |
| matcher | 3.0.0 | MIT |
| material-colors | 1.2.6 | ISC |
| math-intrinsics | 1.1.0 | MIT |
| mdn-data | 2.0.14 | CC0-1.0 |
| mime | 2.6.0 | MIT |
| mime-db | 1.52.0 | MIT |
| mime-types | 2.1.35 | MIT |
| mimic-response | 3.1.0 | MIT |
| mimic-response | 1.0.1 | MIT |
| mimic-response | 2.1.0 | MIT |
| minimatch | 3.1.5 | ISC |
| minimatch | 9.0.9 | ISC |
| minimatch | 3.1.5 | ISC |
| minimatch | 5.1.9 | ISC |
| minimatch | 3.1.5 | ISC |
| minimatch | 10.2.6 | BlueOak-1.0.0 |
| minimist | 1.2.8 | MIT |
| minipass | 5.0.0 | ISC |
| minipass | 3.3.6 | ISC |
| minipass | 3.3.6 | ISC |
| minipass | 7.1.3 | BlueOak-1.0.0 |
| minizlib | 2.1.2 | MIT |
| minizlib | 3.1.0 | MIT |
| mkdirp | 1.0.4 | MIT |
| module-details-from-path | 1.0.4 | MIT |
| ms | 2.1.3 | MIT |
| nan | 2.29.0 | MIT |
| nano-css | 5.6.2 | Unlicense |
| nanoid | 3.3.16 | MIT |
| node-abi | 4.33.0 | MIT |
| node-api-version | 0.2.1 | MIT |
| node-fetch | 2.7.0 | MIT |
| node-gyp | 12.4.0 | MIT |
| node-int64 | 0.4.0 | MIT |
| nopt | 5.0.0 | ISC |
| nopt | 9.0.0 | ISC |
| normalize-url | 6.1.0 | MIT |
| npmlog | 5.0.1 | ISC |
| nwsapi | 2.2.28 | MIT |
| object-assign | 4.1.1 | MIT |
| object-keys | 1.1.1 | MIT |
| on-exit-leak-free | 2.1.2 | MIT |
| once | 1.4.0 | ISC |
| oxlint | 1.76.0 | MIT |
| p-cancelable | 2.1.1 | MIT |
| p-limit | 3.1.0 | MIT |
| parse5 | 6.0.1 | MIT |
| path-is-absolute | 1.0.1 | MIT |
| path-key | 3.1.1 | MIT |
| pe-library | 0.4.1 | MIT |
| picocolors | 1.1.1 | ISC |
| picomatch | 4.0.5 | MIT |
| pino | 10.3.1 | MIT |
| pino-abstract-transport | 3.0.0 | MIT |
| pino-std-serializers | 7.1.0 | MIT |
| pkijs | 3.4.0 | BSD-3-Clause |
| plist | 3.1.0 | MIT |
| postcss | 8.5.25 | MIT |
| proc-log | 6.1.0 | ISC |
| process-nextick-args | 2.0.1 | MIT |
| process-warning | 5.1.0 | MIT |
| progress | 2.0.3 | MIT |
| promise-retry | 2.0.1 | MIT |
| prop-types | 15.8.1 | MIT |
| proper-lockfile | 4.1.2 | MIT |
| proxy-from-env | 2.1.0 | MIT |
| psl | 1.15.0 | MIT |
| pump | 3.0.4 | MIT |
| punycode | 2.3.1 | MIT |
| pvtsutils | 1.3.6 | MIT |
| pvutils | 1.1.5 | MIT |
| querystringify | 2.2.0 | MIT |
| quick-format-unescaped | 4.0.4 | MIT |
| quick-lru | 5.1.1 | MIT |
| react | 19.2.8 | MIT |
| react-color | 2.19.3 | MIT |
| react-dom | 19.2.8 | MIT |
| react-icons | 5.7.0 | MIT |
| react-is | 16.13.1 | MIT |
| react-remove-scroll | 2.5.5 | MIT |
| react-remove-scroll | 2.7.2 | MIT |
| react-remove-scroll-bar | 2.3.8 | MIT |
| react-style-singleton | 2.2.3 | MIT |
| react-universal-interface | 0.6.2 | Unlicense (public domain) |
| react-use | 17.6.1 | Unlicense |
| reactcss | 1.2.3 | MIT |
| read-binary-file-arch | 1.0.6 | MIT |
| readable-stream | 3.6.2 | MIT |
| readable-stream | 2.3.8 | MIT |
| real-require | 0.2.0 | MIT |
| real-require | 1.0.0 | MIT |
| require-directory | 2.1.1 | MIT |
| require-from-string | 2.0.2 | MIT |
| require-in-the-middle | 8.0.1 | MIT |
| requires-port | 1.0.0 | MIT |
| resedit | 1.7.2 | MIT |
| resize-observer-polyfill | 1.5.1 | MIT |
| resolve-alpn | 1.2.1 | MIT |
| responselike | 2.0.1 | MIT |
| retry | 0.12.0 | MIT |
| rimraf | 3.0.2 | ISC |
| roarr | 2.15.4 | BSD-3-Clause |
| rolldown | 1.1.5 | MIT |
| rtl-css-js | 1.16.1 | MIT |
| rxjs | 7.8.2 | Apache-2.0 |
| safe-buffer | 5.1.2 | MIT |
| safe-stable-stringify | 2.5.0 | MIT |
| safer-buffer | 2.1.2 | MIT |
| sanitize-filename | 1.6.4 | WTFPL OR ISC |
| sax | 1.6.1 | BlueOak-1.0.0 |
| saxes | 5.0.1 | ISC |
| scheduler | 0.27.0 | MIT |
| screenfull | 5.2.0 | MIT |
| semver | 6.3.1 | ISC |
| semver | 7.7.4 | ISC |
| semver | 7.7.4 | ISC |
| semver | 6.3.1 | ISC |
| semver | 7.8.5 | ISC |
| semver | 5.7.2 | ISC |
| semver-compare | 1.0.0 | MIT |
| serialize-error | 7.0.1 | MIT |
| set-blocking | 2.0.0 | ISC |
| set-harmonic-interval | 1.0.1 | Unlicense |
| shebang-command | 2.0.0 | MIT |
| shebang-regex | 3.0.0 | MIT |
| shell-quote | 1.9.0 | MIT |
| signal-exit | 3.0.7 | ISC |
| simple-concat | 1.0.1 | MIT |
| simple-get | 3.1.1 | MIT |
| simple-update-notifier | 2.0.0 | MIT |
| sonic-boom | 4.2.1 | MIT |
| source-map | 0.6.1 | BSD-3-Clause |
| source-map | 0.5.6 | BSD-3-Clause |
| source-map-js | 1.2.1 | BSD-3-Clause |
| source-map-support | 0.5.21 | MIT |
| split2 | 4.2.0 | ISC |
| sprintf-js | 1.1.3 | BSD-3-Clause |
| stack-generator | 2.0.10 | MIT |
| stackframe | 1.3.4 | MIT |
| stacktrace-gps | 3.1.2 | MIT |
| stacktrace-js | 2.0.2 | MIT |
| stat-mode | 1.0.0 | MIT |
| string_decoder | 1.1.1 | MIT |
| string-width | 4.2.3 | MIT |
| string-width | 4.2.3 | MIT |
| string-width | 7.2.0 | MIT |
| string-width | 4.2.3 | MIT |
| strip-ansi | 6.0.1 | MIT |
| strip-ansi | 6.0.1 | MIT |
| strip-ansi | 7.2.0 | MIT |
| strip-ansi | 6.0.1 | MIT |
| stylis | 4.4.0 | MIT |
| sumchecker | 3.0.1 | Apache-2.0 |
| supports-color | 7.2.0 | MIT |
| supports-color | 7.2.0 | MIT |
| supports-color | 7.2.0 | MIT |
| supports-color | 7.2.0 | MIT |
| supports-color | 10.2.2 | MIT |
| symbol-tree | 3.2.4 | MIT |
| tailwind-merge | 1.14.0 | MIT |
| tailwindcss | 4.3.3 | MIT |
| tapable | 2.3.3 | MIT |
| tar | 6.2.1 | ISC |
| tar | 7.5.22 | BlueOak-1.0.0 |
| temp-file | 3.4.0 | MIT |
| thread-stream | 4.2.0 | MIT |
| throttle-debounce | 3.0.1 | MIT |
| tiny-async-pool | 1.3.0 | MIT |
| tiny-typed-emitter | 2.1.0 | MIT |
| tinycolor2 | 1.6.0 | MIT |
| tinyglobby | 0.2.17 | MIT |
| tmp | 0.2.7 | MIT |
| tmp-promise | 3.0.3 | MIT |
| toggle-selection | 1.0.6 | MIT |
| tough-cookie | 4.1.4 | BSD-3-Clause |
| tr46 | 0.0.3 | MIT |
| tr46 | 3.0.0 | MIT |
| tree-kill | 1.2.2 | MIT |
| truncate-utf8-bytes | 1.0.2 | WTFPL |
| ts-easing | 0.2.0 | Unlicense |
| tslib | 2.8.1 | 0BSD |
| type-fest | 0.13.1 | (MIT OR CC0-1.0) |
| typescript | 6.0.3 | Apache-2.0 |
| undici | 6.28.0 | MIT |
| undici | 7.29.0 | MIT |
| undici-types | 7.18.2 | MIT |
| universalify | 0.1.2 | MIT |
| universalify | 0.2.0 | MIT |
| universalify | 2.0.1 | MIT |
| unzipper | 0.12.5 | MIT |
| url-parse | 1.5.10 | MIT |
| use-callback-ref | 1.3.3 | MIT |
| use-file-picker | 2.1.4 | MIT |
| use-sidecar | 1.1.3 | MIT |
| utf8-byte-length | 1.0.5 | (WTFPL OR MIT) |
| util-deprecate | 1.0.2 | MIT |
| uuid | 8.3.2 | MIT |
| uuidv4 | 6.2.13 | MIT |
| vite | 8.1.5 | MIT |
| w3c-hr-time | 1.0.2 | MIT |
| w3c-xmlserializer | 3.0.0 | MIT |
| wait-on | 9.1.0 | MIT |
| webcrypto-core | 1.9.2 | MIT |
| webfontloader | 1.6.28 | Apache-2.0 |
| webidl-conversions | 3.0.1 | BSD-2-Clause |
| webidl-conversions | 7.0.0 | BSD-2-Clause |
| whatwg-encoding | 2.0.0 | MIT |
| whatwg-mimetype | 3.0.0 | MIT |
| whatwg-url | 11.0.0 | MIT |
| whatwg-url | 5.0.0 | MIT |
| whatwg-url | 10.0.0 | MIT |
| which | 5.0.0 | ISC |
| which | 6.0.1 | ISC |
| which | 2.0.2 | ISC |
| wide-align | 1.1.5 | ISC |
| wrap-ansi | 7.0.0 | MIT |
| wrap-ansi | 9.0.2 | MIT |
| wrappy | 1.0.2 | ISC |
| ws | 8.21.3 | MIT |
| xml-name-validator | 4.0.0 | Apache-2.0 |
| xmlbuilder | 15.1.1 | MIT |
| xmlchars | 2.2.0 | MIT |
| y18n | 5.0.8 | ISC |
| yallist | 5.0.0 | BlueOak-1.0.0 |
| yallist | 4.0.0 | ISC |
| yargs | 17.7.3 | MIT |
| yargs | 18.0.0 | MIT |
| yargs-parser | 21.1.1 | ISC |
| yargs-parser | 22.0.0 | ISC |
| yocto-queue | 0.1.0 | MIT |

## Bundled derived components

The following is **not** a package dependency. It is source code derived from an
upstream project and included in this distribution as a Derivative Work.

| Component | Upstream | Upstream license | Copyright holder |
|---|---|---|---|
| Canvas editor — `frontend/src/features/editor/` | [Davronov-Alimardon/canva-clone](https://github.com/Davronov-Alimardon/canva-clone) | **Apache License 2.0** | Copyright (c) 2025 Alimardon Davronov |

This component has been **modified** from its upstream source. Per Apache-2.0
section 4(b), every modified file carries a notice stating that it was changed,
and per 4(c) the upstream attribution notices are retained. The full statement of
what was extracted, stripped and added is in `editor-LICENSE-NOTICE.md`, which
ships inside the application. The complete Apache License 2.0 text ships as
`APACHE-2.0.txt`.

All other code in this application was written from scratch by Mace and
is proprietary under `LICENSE` and `EULA.md`. It is **not** covered by the
Apache License above.

The Apache-2.0 license applies to `frontend/src/features/editor/` only. Nothing
else in this repository is licensed under Apache-2.0.
