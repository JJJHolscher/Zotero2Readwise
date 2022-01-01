# Zotero ➡️ Readwise

`zotero2readwise` is a Python library that retrieves all [Zotero](https://www.zotero.org/) annotations† and notes. 
Then, It automatically uploads them to your [Readwise](https://readwise.io/)§§. 

This is particularly useful for the new [Zotero PDF Reader](https://www.zotero.org/support/pdf_reader_preview) 
that stores all highlights in the Zotero database. 
The new Zotero, also available for [iOS app](https://www.zotero.org/iosbeta) (currently in beta). 
In the new Zotero, the annotations are NOT saved in the PDF file unless you export the highlights in order to save them.

If you annotate your files outside the new Zotero PDF reader, this library may not work with your PDF annotations as those are not retrievable from Zotero API.

**_This library is for you if you annotate (highlight + note) using the Zotero's PDF reader (including the Zotero iOS)_**

👉***Updating an existing Zotero annotation or note and re-running this library will update the corresponding Readwise highlight without creating a duplicate!***

† Annotations made in the new Zotero PDF reader and note editor.

§ Readwise is a _paid_ service/software that integrates your highlights from almost everywhere (Pocket, Instapaper, Twitter, Medium, Apple Books, and many more). 
It even has an amazing OCR for directly importing your highlights on a physical book/article into Readwise and allowing 
you to export all your highlights to Obsidian, Notion, Roam, Markdown, etc. 
Moreover, It has an automated [Spaced Repition](https://en.wikipedia.org/wiki/Spaced_repetition) and [Active Recall](https://en.wikipedia.org/wiki/Testing_effect). You can use the the link [here](https://readwise.io/i/essi) to get an extra free month (*Disclaimer: I will get a free month too!*)

---


# Installation 
You can install the library by running 
```shell
pip install zotero2readwise
```

Note: If you do not have pip installed on your system, you can follow the instructions [here](https://pip.pypa.io/en/stable/installation/).


# Usage
Since we have to retrieve the notes from Zotero API and then upload them to the Readwise, the minimum requirements are:
* **Readwise access token** [Required]: You can get your access token from https://readwise.io/access_token
* **Zotero API key** [Required]: Create a new Zotero Key from [your Zotero settings](https://www.zotero.org/settings/key)
* **Zotero personal or group ID** [Required]: 
    * Your **personal library ID** (aka **userID**) can be found [here](https://www.zotero.org/settings/key) next to `Your userID for use in API calls is XXXXXX`.
    * If you're using a **group library**, you can find the library ID by 
        1. Go to `https://www.zotero.org/groups/`
        2. Click on the interested group.
        3. You can find the library ID from the URL link that has format like *https://www.zotero.org/groups/<group_id>/group_name*. The number between `/groups/` and `/group_name` is the libarry ID. 
* **Zotero library type** [Optional]: *"user"* (default) if using personal library and *"group"* if using group library.

Note that if you want to retrieve annotations and notes from a group, you should provide the group ID (`zotero_library_id=<group_id>`) and set the library type to group (`zotero_library_type="group"`).

## Approach 1 (Recommended)
```python 
from zotero2readwise.zt2rw import Zotero2Readwise

zt_rw = Zotero2Readwise(
    readwise_token="your_readwise_access_token",  # Visit https://readwise.io/access_token)
    zotero_key="your_zotero_key",  # Visit https://www.zotero.org/settings/keys
    zotero_library_id="your_zotero_id", # Visit https://www.zotero.org/settings/keys
    zotero_library_type="user", # "user" or "group"
    include_annotations=True, # Include Zotero annotations -> Default: True
    include_notes=False, # Include Zotero notes -> Default: False
)
zt_rw.run_all()
```

## Approach 2:
You can use the `run.py` script. Run `python run.py -h` to get more information about all options. 
You can simply run the script as the following:
```shell
python run.py <readwise_token> <zotero_key> <zotero_id> 
```

# Request a new feature or report a bug
Feel free to request a new feature or report a bug in GitHub issue [here](https://github.com/e-alizadeh/Zotero2MD/issues).


# 📫 How to reach me:
<a href="https://ealizadeh.com" target="_blank"><img alt="Personal Website" src="https://img.shields.io/badge/Personal%20Website-%2312100E.svg?&style=for-the-badge&logoColor=white" /></a>
<a href="https://www.linkedin.com/in/alizadehesmaeil/" target="_blank"><img alt="LinkedIn" src="https://img.shields.io/badge/linkedin-%230077B5.svg?&style=for-the-badge&logo=linkedin&logoColor=white" /></a>
<a href="https://medium.ealizadeh.com/" target="_blank"><img alt="Medium" src="https://img.shields.io/badge/medium-%2312100E.svg?&style=for-the-badge&logo=medium&logoColor=white" /></a>
<a href="https://twitter.com/intent/follow?screen_name=es_alizadeh&tw_p=followbutton" target="_blank"><img alt="Twitter" src="https://img.shields.io/badge/twitter-%231DA1F2.svg?&style=for-the-badge&logo=twitter&logoColor=white" /></a>

<a href="https://www.buymeacoffee.com/ealizadeh" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-blue.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>
