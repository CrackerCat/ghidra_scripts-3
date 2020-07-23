# ghidra_scripts
Scripts for the Ghidra software reverse engineering suite.
For developing python scripts in context of Ghidra SRE please visit WIKI.

## Installation
Insert script to Ghidra script directory. Example:$USER_HOME/ghidra_scripts.

## tiny_tracer_tag_annotate.py
The tags generated by the Tiny Tracer are helpful in deobfuscating obfuscated API calls. This script will annotate and bookmark the code with tags produced by tool Tiny Tracer.
Tiny Tracer repo: https://github.com/hasherezade/tiny_tracer. Tested on Tiny_tracer version 1.3.2

Run script via Ghidra Script Manager, import relevant .tag file for analyzed sample, produced by Tiny Tracer.

Ghidra annotated Graph_View:

![Ghidra annotated Graph view](/Images/GHIDRA_GRAPHVIEW_annotated.PNG)


Ghidra annotated Listing_View and Bookmarks:

![Ghidra annotated_Listing_bookmark_view](/Images/GHIDRA_listing%20view_bookmarks_annotated.PNG)



## CAPA_Importer.py
This script works with exported results of CAPA tool.
It will annotate (PRE_COMMENT) code with Capability, bookmark the code with Capability, Matched RVA location and Scope.
If more than one Capability for relevant RVA is presented, script will add annotation for the capability to RVA in code and also edit bookmark so the bookmark with location (RVA) will contains all Capabilities.
If matched capability in CAPA result has scope 'file', no annotation (PRE_COMMENT) will be presented in code, bookmark will be created with RVA = ImageBase

Capa detects capabilities in executable files. You run it against a PE file or shellcode and it tells you what it thinks the program can do.
For example, it might suggest that the file is a backdoor, is capable of installing services, or relies on HTTP to communicate.
CAPA repo: https://github.com/fireeye/capa
CAPA blog post: https://www.fireeye.com/blog/threat-research/2020/07/capa-automatically-identify-malware-capabilities.html

How to use:
Analyze sample with CAPA.
Example: CAPA -v malware.exe > exported.txt
Parameter '-v' must be presented in cmdline argument.
Run script via Ghidra Script Manager, import exported.txt and it will annotate (with PRE_COMMENT) and bookmark the code with Capability, Matched RVA location and Scope.

If no PRE_COMMENT presented in Decompile window or Graph window --> Check if you have in relevant windows option "Display PRE comments" enabled.

Ghidra annotated Listing view, Decompile view and Bookmarks (1):

![Ghidra annotated Graph view](/Images/CAPA_Importer_All_in_one_view.PNG)


Ghidra annotated Listing view, Decompile view and Bookmarks (2):

![Ghidra annotated Graph view](/Images/CAPA_Importer_All_in_one_view2.PNG)



Ghidra annotated Function Graph view and Bookmarks:

![Ghidra annotated Graph view](/Images/CAPA_Importer_Graph_Bookmarks_view.PNG)


