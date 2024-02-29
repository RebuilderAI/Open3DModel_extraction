# Open3DModel_extraction

This is the repository for extraction of 3D model data contained within "Open3DModel",
a website from which any user can access and extract 3D models of various categories, including
character, plant, animal, etc.

File crawling code is: "data_extraction_v2.ipynb"

Starting URL is ##https://open3dmodel.com/3d-models/

We are using BeautifulSoup4 to extract .zip files within each successsive link within the
URL.

Request parser and BeautifulSoup are used as the following:
  - response = requests.get((url))
  - soup = BeautifulSoup(response, "html.parser")

Python request is used as a parser to parse .html info.

The first one parses the URLs for each category. Second one parses .html links, each containing
the objects of each category. For each of these links, another BeautifulSoup parser is used to get php
that leads to "Download" button that allows the user to download the .zip files.

Final response parser and Beautifulsoup are used, and by attaching the main url: "https://open3dmodel.com/"
and token of each object. 
  -Sample token: "?token_id=UTVxMTRpcnNkRWMwWXAxQW9YbVlkUT09&key=Nm1uL0dJeGJTMFlwZWdlTnJaVlFOUT09"

zipfile package is used to read the contents of the token urls, and .extractall is used to extract .zip files
in order to make it more comfortable for users to directly obtain datasets extracted. 
