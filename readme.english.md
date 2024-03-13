# Exercise material for SFMI's openEHR course (January 2021)
Below you find a slightly edited auto-translation of the Swedish original at https://github.com/modellbibliotek/kurs-openEHR-jan-2021/blob/main/README.md 

See https://discourse.openehr.org/t/digital-utbildningsserie-om-openehr-nov-2020-jan-2021/1105 and https://www.sfmi.se/ for details about the course. Feel free to check out https://discourse.openehr.org/t/openehr-se-borja-lasa-har/391 for more info on Swedish archetype work.

We recommend using Google Chrome for Archetype Designer and EHR Studio, but some other modern browsers may also work. Be prepared that it takes time (up to half a minute) to open a repository and several seconds to then open or save an individual archetype in the tool.

Remember that you can scout, translate and download archetypes also via https://ckm.openehr.org/ckm/

If you find errors and opportunities for improvement in the labs below, please report them as under the "Issues" tab above (Direct link: https://github.com/modellbibliotek/kurs-openEHR-jan-2021/issues)

## Preparations to be made before the teaching session 3
1. Create users on Github and in Archetype Designer according to instructions in the first two instructions at https://openehr.atlassian.net/wiki/spaces/healthmod/pages/966295553/Snabbstartsguide+f+r+modelleringsverketig
1. If you are not already logged in to Archetype Designer (https://tools.openehr.org/designer/) follow instruction 3 (about logging in)
1. In order to be able to experiment and save withour risking destroying any body elses work, create your own repository by:
    1. Click the green "+ New repository" button
    1. Select: Repository type = Local Folder
    1. Pick a name of your own choice and fill out under "Repository name"
1. Download the example files for the course from this GitHub project (in any library on your computer):
   1. Click on https://github.com/modellbibliotek/kurs-openEHR-jan-2021/archive/main.zip and download the file
   1. Unzip the zip file on your computer. (Update 2022: Nowadays it is possible to upload entire ZIP files so they don't necessarily need to be unzipped locally, so in the next step below you can choose to upload the entire zip file instead)
1. In Archetype Designer:
   1. Click on the repository you created. Note that it may take a while (up to a minute) to open it.
   1. Click "Import" at the top of the window.
   1. Select the files from the "local" sub-library among the files you unpacked in the previous step and drag-and-drop them into the box with the text "Drop here" in the dialog window.    
   1. Click on the green "Upload all" button, wait until everything is uploaded and then click on "Close".
1. Now you can open the template "akutmall_undervisningsexempel_2a" or the included archetypes by clicking on them.

### Info about emergency template_undervisingsexempel_2a (will be used in exercise 3b)
Template/template akutumall_undervisingsexempel_2a that was used at the second teaching session (13 Jan) is a simplified (not entirely realistic) subset of things that may be interesting in the emergency care of certain injuries. It is designed to demonstrate various useful properties of models based on a combination of openEHR and Snomed CT.

## Exercises during teaching 3

### 3a. Archetypes - Create and terminology bind archetype for exercise race
We are now pretending that we are going to help a research project to capture more detailed data about accidents at the Vätternrundan https://vatternrundan.se/en/ that require medical interventions, those of Region Östergötland's clinics that usually deal with the most injuries from the Vätternrundan are in the study and have agreed to expand their accident form. We do not find a suitable ready-made archetype, but decide to write our own. But making a special vätternrunde archetype seems a bit too specific so we decide to make a more general one about events during recreational races.

1. Start Archetype Designer in Google Chrome (https://tools.openehr.org/designer) and log in with your personal account (which you created yourself earlier, see above)
1. Inspect the existing `Problem/Diagnosis` archetype (it will then open as another tab at the top, to the right of the tab for your created repository). Use the drop-down menu in the top right corner to check different available languages (just so you know how to do it), we will use English though. Find and read the description/metadata ("Details" tab in the right-hand column) for the field `Extension' which is of the type "SLOT" - there we are considering inserting our new exercise/recreational race event archetype later in the template.
1. Go back to the tab of your created repository and create a new archetype by clicking the big green "New" button and selecting "Archetype" (there are also shortcuts available to specific kinds of archetypes, but now we take the long more detailed road...)
   * In Rm Type, select CLUSTER
   * In Concept enter "Recreational_race_event_NN" where NN is your initials (NOTE: no YYYY or hyphens) or other unique text (so we don't later clash with names in our common lab environment for forms).
   * In the Version field, nothing should be filled in/changed.
   * In the Original Language field, select English (en) (In the original exercise we used Swedish as the original language since we didn't think it would spread internationally, but in this translated exercise we use english.)
   * Click on the Create button. (If nothing happens, an illegal character may have slipped into the name. Then try changing the name and click again.)
1. Create a tree (roughly) like the one in the image [English: recreational_race_event.png](https://raw.githubusercontent.com/modellbibliotek/kurs-openEHR-jan-2021/main/images/recreational_race_event.png) or [Swedish: motionslopp.png](https://raw.githubusercontent.com/modellbibliotek/kurs-openEHR-jan-2021/main/images/motionslopp.png)  by clicking on the corresponding symbol in the left edge for each field/row and entering a name.
Keep the following tips in mind to test different features of the tool.
   * It is possible to duplicate fields so that all settings are included, do it e.g. to copy between the `Latitude` and `Longitude` fields.
   * For values ​​in `Type of exercise` select "Internal Coded", then press the blue button "Edit" and create a list with e.g. the four lines:
        * Cycling
        * Running
        * Skiing
        * Swimming
   * For values ​​in `Training experience level` select "Internal Coded", then press the blue button "Edit" and create a list with e.g. the lines below. To save time, you can select and copy the entire list below and when you are on the first empty field in the "Text" column, paste the entire clipboard and all three lines will be created, then press "Save". (From some out-of-the-box sources, you may need to copy first via, for example, a text editor such as "Notes", clear the list of the special characters, and then copy again and paste into Archetype Designer)
        * Beginner
        * Intermediate
        * Elite
   * For the settings in the field `Number of previous participations in this race` remove the tick in front of "unbound" under the heading "Range". Then new choices appear, set/keep 0 as minimum limit (to prohibit negative values) and remove the tick in front of "Max" so there is no upper limit.
   * For the field `Time after start` we would like to use the data type "Duration". Instead of using the button on the left side, you can select another data type (e.g. "Any") and by clicking in the box next to "Available types" bring up a scrolling list where, among other things, "Duration" exists.
   * In fields of the type "Quantity" you can choose to allow (several) different units by pressing the ´+´ button at the label "Units". Then a box will appear with search fields for "Category" and "Units" by clicking in the field a scrolling list will appear, but you can also start typing what you are looking for. In Category, you can search for size/type, e.g. "length", and when you have selected size/type, you can click in the search field "unit" and only get units that fit the size.
       * For `Distance from start` choose to allow both meters and kilometers
       * For `Longitude` and for `Latitude` select "degree (deg)" as unit (which is of category "Angle, plane")
1. Save your work often, and at least now.
1. Terminology bind at least "skiing" in the `Type of exercise' field to Snomed CT (Appropriate snomed term: 45033006). *See description of how on e.g. https://youtu.be/BqUWVpnFXiw if you haven't already seen another demo.* Those who have time to spare can start looking into the concepts under [415577004 | sport |](https://browser.ihtsdotools.org/?perspective=full&conceptId1=415577004&edition=MAIN/SNOMEDCT-SE/2020-11-30&release=&languages=sv,en) in Snomed CT and try to terminologically bind more things.
1. Save your work often, and at least now.
1. Bonus task 1: Create and select a "Cluster" named "Protective equipment used on:". Then explore the button "Paste from clipboard" by pasting into the gray field "Paste here" a list such as below and then select the data types and any value sets you think might be suitable/fun (can be modeled in many ways, there is no conclusion. Remember that you need to balance the work situation for the staff who will enter the data against the researchers who want to use the data on the get any data at all in practice...)
    * Head
    * Hands
    * Joints (Knee, elbows etc)
 1. Bonus task 2: In an archetype, you can allow a choice between several data types on the same node and leave the choice to the template author to choose what suits the use case. Try e.g. that by clicking "Hands" in the field "Available types" and adding the type "Boolean"
       
### 3b. Templates - Create and adjust NN_akutmall_undervisningsexempel_3b
1. Copy the example template from the last teaching session, "akutmall_undervisningsexempel_2a" by placing the pointer over the template in the list of templates and archetypes so that three dots appear on the line in the list, press them and the `Duplicate` option will appear, see [copy_template.png](https://raw.githubusercontent.com/modellbibliotek/kurs-openEHR-jan-2021/main/images/copy_template.png). Then give the copy a new name like NN_akutmall_undervisingsexempel_3b (where NN is your initials or other unique text so that we don't later clash with names in our common lab environment for forms. Avoid åäö and other special characters in file names.)
1. If you look in the list of templates, you will see that the name in small text at the bottom of one of the templates has been changed to the one you selected in the previous step, but the name in large bold text on that row is unchanged from the original. Open the template and change the name of the top node in the template to the name you gave the copy, if you think it's nicer you can replace the underscores `_` here with real spaces (but keep your initials to avoid confusion later). Save the template. Go back to the (green) tab with the list of archetypes and templates and check if the change took effect.
1. Switch back to the template tab. Check that, depending on preference and tha language(s) you used in your recently created CLUSTER archetype from exercise 3a, either English (En) or e.g. Swedish (Sv) is selected (top right)
1. Plug in our newly produced archetype about exercise race in the `Extension` field of the template (found under `Problem/Diagnosis') by clicking on the `Extension` field and in the list of cluster archetypes that then appears in the panel on the right, select your archetype. Note that it is now not possible to view the template in English and German anymore, if your added archetype is only available in Swedish.
1. In the `Name of race` field of the template, we want to list the different variants of the Vätternrundan so that it will be smooth for the staff. Select "Free text" then "Edit values" copy the entire list below, and when you are in the top blank field then  paste the previously copied list and press "Save".

   * Vätternrundan 300 km
   * Halvvättern 150 km
   * Tjejvättern 100 km
   * Vätternrundan 100 km
   * MTB-Vättern
   * Minivättern

1. Then make sure that "Limit to list" is *not* checked, otherwise you cannot enter names of other exercise runs when using the template. As "Default Value" select Vätternrundan. Save the template.
1. In the settings for the `Time after start` field, remove the tick in front of "Allow all time units" and then deselect "Years", "Months" and "Weeks".
1. Terminology bind the 'Clinical interpretation' field, under `Respiration`, to the list of all children of the snomed concept 85617008 (abnormal breathing rhythm). Details:
   * In https://browser.ihtsdotools.org/ make sure the language version you want, eg the international or "Release: Swedish Edition..." is selected. Then select the tab `Expression Constraint search` and enter `<< 85617008 | abnormal breathing rhythm |` see image [snomed_andningsrytm.png](https://github.com/modellbibliotek/kurs-openEHR-jan-2021/blob/main/images/snomed_andningsrytm.png?raw=true).
   * Copy the list of results from the search tool and paste into a spreadsheet, if you want to use some other language than english, remove the column with terms in English, change the position of the remaining columns so that numerical codes are to the left of the descriptions you want. (We usually use Google Sheets, e.g. Excel also works, but you may then need to change the number format to get back whole numbers when Excel automatically converts large numbers into a different form: Select the column with codes, right-click and select "Format cells", in the "Numbers" tab enter Numbers as category and set decimals to 0, click "OK".)
   * In the settings for the template field 'Clinical interpretation' select "External Coded",
       * under `terminology` write `SNOMED-CT`
       * under `Uri` type `[http://snomed.info/id/](http://snomed.info/id/)` (TODO: double check thread at https://discourse.openehr.org/t/snomed-ct-uris-in-openehr/2430)
   * Check "Add value set"
   * Press "Edit value set"
   * Copy from your spreadsheet the two columns of code and text, paste them into the empty "Edit valueset" list (when the cursor is in the top empty field in the code column) and then press "Save"
1. Save your work often, and at least now.
1. Let's pretend it's 31-Aug-2020 and we need to download and include the updated Swedish translation of the blood pressure archetype in Sofia Janstad's "Branch" Rev 8.3 in the Clinical Knowledge Manager. It had not then been returned to the main version ("trunk").
   * Open shortcut to the blood pressure archetype revision history: https://ckm.openehr.org/ckm/archetypes/1013.1.3574/revisionhistory (it takes some time before the history is loaded)
   * Click on Sofia Janstad's "Branch", the line with Rev 8.3...
   * ...then a box opens with a description and directly below it a "Details" button, press that button.
   * In the menu that then appears select "Export Archetype"
   * Now a new tab will open for this particular version and three buttons for export will appear, select "Export ADL"
   * Save the file locally on your computer (remember where)
   * Switch back to the Archetype Designer where we were previously editing our template
   * Press "Import" at the top and import the Blood Pressure archetype you just downloaded (the same way you previously imported archetypes in preparation for the practice session)
   * In the template select the node "Pulse/Heart rate" then click on Blood pressure in the list of archetypes on the left, it will then be imported below the "Pulse/Heart rate" archetype
1. Deselect/exclude parts of the blood pressure archetype
    1. Select `24 hour blood pressure measurement` and press the yellow `0..0`
    1. Under "Unspecified Event", select the "Mean Arterial Pressure" field, hold down the shift key on your keyboard while highlighting "comment" four lines down. Now all four lines should be marked and the "Prohibit all" button appears on the right. Tap it to extinguish the four rows in one swipe.
    1. Similarly, turn off everything except "position" under "state"
    1. Similarly, turn off everything under "protocol"
1. The emergency department says they want the registration template in the form ABCDE (Airway, Breathing, Circulation...) as the paper emergency record, [see example (pretend patients)](https://drive.google.com/file/d/0BwdHmPbK5e3SWjRsQzUyR243OEk /view?usp=sharing). They also need a way to report airway problems. The target image is a template that looks roughly like the image [ABCDE.png](https://github.com/modellbibliotek/kurs-openEHR-jan-2021/blob/main/images/ABCDE.png?raw=true)
   1. Get a better overview by pressing `-` to collapse the archetypes under the Vital Parameters heading
   1. Rename the heading "Vital parameters" to "ABCDE"
   1. Insert a new instance of the SECTION archetype "Heading" (eng. Ad Hoc Heading) at the top of the template, directly below "content" and name it "Damage". Then drag the existing Problem/Diagnosis branch under the new "Damage" heading "items"
   1. Add three new instances of the SECTION archetype "Heading" under ABCDE and name them
       * A. Airway
       * B. Breathing
       * C. Circulation
   
   1. Under "items" under "A. Airway" add an instance of the "Problem/Diagnosis" archetype and adjust it like this:
      * Rename this copy of "Problem/Diagnosis" to "Airway"
      * Change the "Occurrences" field (under the "Constraints" tab) from `0..1` to `0..*` (to allow more instances of the node).
1. Delete everything except `Problem/Diagnosis name' and `Clinical Description' in the archetype we renamed "Airway".
1. Terminology bind the `Problem/Diagnosis name' field in the archetype we renamed "Airway"
   1. select "External Coded",
       * under `terminology` write `SNOMED-CT`
       * under `Uri` type `http://snomed.info/sct/`
   * Check "Add value set"
   * Press "Edit value set"
   * Copy all codes and terms (simultaneously) from the table below, and paste them into the empty "Edit valueset" list, then press "Save"

    |SCTID|Term|
    |---|---|
    |70407001|Stridor|
    |79688008|Respiratory obstruction|
    |217808004|Respiratory obstruction due to foreign body in esophagus|
    |427286007|Obstruction of lower respiratory tract|
    |68372009|Upper respiratory tract obstruction|
    |427562009|Blood in upper airway|
1. Save your work often, and at least now.
1. Export your template as an "Operational template" (OPT). Details:
   * Click on Export, a box will appear
   * Click on the blue-white "Export" button and select "Export to OPT"
   * Remember where you save the exported file on your computer, you will need it in the next exercise

### 3c. Create and adjust forms
1. Now we change tools. Log in to https://tools.better.care/studio/ with the username `sfmi' and the password you received via email in the calendar invitation (can also be requested in the meeting chat), select the ehrscape.com domain at the bottom.
1. Select Form Builder
1. At the bottom left are gray icons. Click the import icon, the one with the up arrow inside a box.
1. An import window will now appear, drag-and-drop your Operational Template (OPT), which you exported in the previous exercise, there. (The import may take some time.)
1. You should now have a list where your template is included somewhere, click on it.
1. Now the form "editor" opens, the content from your template should be visible in the left column, drag the top node (the entire tree is included) from your template to the large white editing area in the middle of the screen. The form will be quite large with many frames within frames.
1. Remove the outermost/top frame by going up to the top (grey) border (where your template name is likely to be), new icons will appear. Click on the red icon that looks like a cross surrounded by four corners = "Remove frame".
1. Now select the frame "Damage" (if you have one) and in the right column under the heading "Presentation" change from "Container" to "Collapsible title".
1. Select the "Problem/Diagnosis" frame and click on the red "Remove frame"
1. Swap "Clinical Description" and "Anatomic Location"
1. Select "Clinical Description", change in the right column "Display in" to 5 lines.
1. Now we decide that in this form we will not include the detailed way of specifying location, so select the frame "Anatomical location" and press the red bin. Note in the left column that the data fields we removed are now marked in black and are there to be able to drag into other parts of the form if you wish.
1. In the exercise race frame, look at the "Race name" in the vätternrundan is already selected because we had set it as the default in our template. If you want, you can say that today is the time for Tjejvättern instead and change it so that it becomes the default today instead of the Vätternrundan.
1. In the drop-down menu for "Type of exercise" select "Cycling" so that it also becomes the default in the form.
1. Now it's time to test drive for the first time, select "preview" above the form.
    * Try switching between the display modes, "Desktop", "Tablet" and "Mobile"
    * Note that for "anatomical location" you can select several options at the same time
    * Note that you now have to select meters or kilometers during the distance from the start, the default is missing (you can fix that later in the editor mode if you want)
    * If the left column is not open, open it with `>>` near the upper left corner- Inspect how the data changes when you make selections in the form.
    * Select "Combats" under airway. Then press "+ Add another Airway" and in the new box that appears below select any additional airway concerns (this is the desired functionality).
    * Note that it is also possible to add more instances of "Unspecified Event" inside the "Breathing", "Pulse/Heart Rate" and "Blood Pressure" observations. The template we made allows that, but for our entry form we only want to allow one of each kind, so…
1. ...exit "Preview" by switching to "Editor".
1. Under "Breathing" select the "Unspecified Event" frame and in the settings (right column) change the "max" field under "MULTIPLICITY" from 100 to 1. Do the same for "Unspecified Event" under "Pulse/Heart Rate" and "Blood Pressure" . Also click the red "remove frame" on all "Unspecified event"
1. Test run again with "preview" and then go back to Editor mode.
1. Publish a first version of your form by clicking "Publish" at the top of the screen (so it can be used in the records system)
1. Now we want exercise run hidden until you choose to open it with a small switch.
    * in the left edge, select "Generics" (similar to lego piece)
    * Then drag "Boolean" to just above "exercise run" and drop it there and rename the label to "Exercise run?".
    * Under the "Design" tab on the right change presentation to "toggle switch"
    * Under the "Interactions" tab on the right, under "When" first click on "Select field" and then on the Motion run switch you just edited. in the menu that then appears select "is" and then "true".
    * Under the "Interactions" tab on the right again, under "Then" click first on "Select field" and then on the Motion race frame. In the menu that then appears, select "is shown"
    * Click on "Otherwise" and click on "Select field" and then on the Motion run frame again. In the menu that then appears, select "is hidden"
    * It could look something like this now: [motionslopp-switch.png](https://github.com/modellbibliotek/kurs-openEHR-jan-2021/blob/main/images/motionslopp-switch.png)
1. Test run, via Preview, the logic/conditional control you just built
1. Tidy up under the heading "B. Breathing"
    * Click red "Remove frame" for "Pulse oximetry"
    * Click red "Remove frame" for the top "Inhaled oxygen" (ie the one for pulse oximetry, not the one for breathing further down)
    * Within the inner frame "Breathing" do the following:
        * Select "Instance". We can clarify things at the form level in case we don't have the opportunity to change the archetype/template:
            * In the "Design" tab in the right column, change "Presentation" to "button group", then turn on the "hide label" and Show in columns switches. Set Number of columns to 2.
            * In the "Content" tab in the right column, under "Selection values" change "Occurs" to "Breathe"
            * In the "Content" tab in the right column, under "Selection values" change "Undetectable" to "Breathing not detected"
        * Select "Regularity"
            * In the "Design" tab in the right column, change "Presentation" to "button group", then turn on the "hide label" and Show in columns switches. Set Number of columns to 2.
1. Optional extra exercise:
    * Connect with when+then+otherwise rules:
        * the pulse oximeter's "On air" checkbox to the equivalent of breathing and to "Air or oxygen?" in NEWS2.
        * the pulse oximeter's "Oxygen flow" (both value and unit) to the corresponding field for breathing
    * Mark the entire frame of breathing around "inhaled oxygen" as the "hidden"
    * Clue to the oxygen part of this over-course assignment: [syrgas-koppling.png](https://github.com/modellbibliotek/kurs-openEHR-jan-2021/blob/main/images/syrgas-koppling.png?raw= true) (spoiler alert!) It is of course ok if your form looks different graphically.
    
--- End of exercises for lesson 3 (January 18) ---

## Sample patients (for AQL examples, etc. at a later date)
|Field|Patient One|Patient Two|Patient Three|Patient Four|
|---|---|---|---|---|
|**Problem/Diagnosis**|||||
|Damage|127347009 working damage + 125665001 crushing damage (or 50793006 crushing damage to hand?) | 125667009 contusion (or 44801007 contusion of hip?)|443786003 injury during sports activity + 281599007 distortion of ligaments of leg (or 54888009 distortion of knee) |397996002 injury caused by explosion|
|Clinical description|The patient held his hand in a door opening at work when a colleague accidentally slammed it.|The patient fell down the stairs at home and landed on his right hip.|The patient sprained her knee while playing badminton.|The patient was experimenting with a friend when things went out of control and there was an explosion.|
|Anatomical location (rough to simplify example)|80768000 left arm, structure|62175007 right leg, structure|32153003 left leg, structure|6921000 right arm, structure|
|Anatomical location (option without laterality)|53120007 upper extremity, structure|61685007 lower extremity, structure |61685007 lower extremity, structure|53120007 upper extremity, structure|
|Date and time of injury|2020-01-23 11:34|2020-01-23 12:34|2020-01-23 13:34|2020-01-23 14:34|
|**Pulse Oximetry**|||||
|SpO₂|98%|96%||97%|
|Oxygen flow||||5 l/min|
|On air|True|True||False|
|**Breathing**|||||
|Frequency|19|21|14|18|
|Oxygen flow||||5 l/min|
|On air|True|True||False|
|**Pulse/Heart Rate**||||
|Frequency|72|92|50|112|
|Regular|Regular|Regular|Regular|Irregular|
|Irregular type||||Regularly Irregular|
|Body Position|Reclining|Lying|Reclining|Lying|
|Method|Automatic, non-invasive|Automatic, non-invasive|Palpation|Automatic, non-invasive|
|Location|Finger|Finger|Radial Artery - Left|Toe|

It is not obvious which Snomed terms would be suitable "parent terms" for a field "Damage" above. 417163006 | traumatic and/or non-traumatic injury | is a proposal that still does not cover all the above examples. You can go higher in the hierarchies.
Probably one would have to use/make terminology selection for emergency care. (Perhaps linked to the emergency departments' RETTS codes, etc.?)

## Optional extra steps later:
1. [Follow tip 4 `Connect Archetype Designer to workspace on GitHub` (Swedish)](https://openehr.atlassian.net/wiki/spaces/healthmod/pages/966295553/Verktyg+-+quickstart+f+r+modelingswerktig)
1. If you want to connect more repositories, repeat step 4 with different contents in "Repository". CKM mirror can e.g. be fun to plug in and explore, but takes some time to load with its 500+ archetypes.
