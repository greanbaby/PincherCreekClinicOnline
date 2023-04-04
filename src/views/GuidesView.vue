<script>
/** GuidesView.vue
 * 
 * This page contains the TAB looking button interface for choosing a Guide
 * 
 * @author Scott Gingras March 30, 2023
 */
import { ref } from 'vue';


/*
const currentTab = ref('Prevention');

const tabs = {
  Prevention,
  NoShows
}
*/


</script>

<template>
  <div class="guides">
    <div class=WordSection1>
      <img alt="EMR Guide" src="@/assets/hospital-files.svg" width="44" height="44" />
			<p class=MsoTitle><span lang=EN-US>Prevention and Screening Instructions</span></p>

			<p class=MsoSubtitle><span lang=EN-US>RBT (Report by Template) details for The
			Associate Clinic, Pincher Creek Dec. 23 2022</span></p>

			<h1><span lang=EN-US>Panel – By Age 18-118</span></h1>

			<p class=MsoNormal><span lang=EN-US>Use <b>Panel – By Age</b> and specify
			18-118.</span></p>

			<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

			<h1><span lang=EN-US>Juno Report by Templates Used to Generate Numerator and Denominator
			Lists</span></h1>

			<p class=MsoListParagraphCxSpFirst style='text-indent:-.25in'><span lang=EN-US
			style='font-family:Symbol'>·<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
			</span></span><span lang=EN-US>CRC Screening Due</span></p>

			<p class=MsoListParagraphCxSpMiddle style='text-indent:-.25in'><span
			lang=EN-US style='font-family:Symbol'>·<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
			</span></span><span lang=EN-US>Mammo Due</span></p>

			<p class=MsoListParagraphCxSpMiddle style='text-indent:-.25in'><span
			lang=EN-US style='font-family:Symbol'>·<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
			</span></span><span lang=EN-US>Pap Screening Due</span></p>

			<p class=MsoListParagraphCxSpLast style='text-indent:-.25in'><span lang=EN-US
			style='font-family:Symbol'>·<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
			</span></span><span lang=EN-US>Measurements Done (BP, EXE, SMK, WT–3yrs, HT)
			and HT added to previous HT to look for it EVER being done</span></p>

			<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

			<h1><span lang=EN-US>Query By Example for NEVER_REMIND Patients to be Removed
			from CRC, Pap, Mammo Denominators</span></h1>

			<p class=MsoListParagraph style='text-indent:-.25in'><span lang=EN-US
			style='font-family:Symbol'>·<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
			</span></span>select demographic_no, prevention_type from preventions where
			never &gt; 0</p>

			<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

			<h1><span lang=EN-US>Denominators File List</span></h1>

			<p class=MsoListParagraphCxSpFirst><span lang=EN-US>Pts_Age_18_to_118.xlsx</span></p>

			<p class=MsoListParagraphCxSpMiddle><span lang=EN-US>CRC-Age_50-74_Not_In_Never_Remind_Preventions_List.xlsx</span></p>

			<p class=MsoListParagraphCxSpMiddle><span lang=EN-US>MAM-Females_50-74_Not_In_Never_Remind_Preventions_List.xlsx</span></p>

			<p class=MsoListParagraphCxSpMiddle><span lang=EN-US>PAP-Females_25-69_Not_In_Never_Remind_Preventions_List.xlsx</span></p>

			<p class=MsoListParagraphCxSpLast><span lang=EN-US>&nbsp;</span></p>

			<h1><span lang=EN-US>Numerators File List</span></h1>

			<p class=MsoListParagraphCxSpFirst><span lang=EN-US>CRC-COMPLETED-pts_not_in_emr_due_list.xlsx</span></p>

			<p class=MsoListParagraphCxSpMiddle><span lang=EN-US>MAM-COMPLETED-pts_not_in_emr_due_list.xlsx</span></p>

			<p class=MsoListParagraphCxSpMiddle><span lang=EN-US>PAP-COMPLETED-pts_not_in_emr_due_list.xlsx</span></p>

			<p class=MsoListParagraphCxSpMiddle><span lang=EN-US>Pts_Age_18_to_118 - With
			BP Done Past Year.xlsx</span></p>

			<p class=MsoListParagraphCxSpMiddle><span lang=EN-US>Pts_Age_18_to_118 - With
			EXE Done Past Year.xlsx</span></p>

			<p class=MsoListParagraphCxSpMiddle><span lang=EN-US>Pts_Age_18_to_118 - With
			HT Done.xlsx</span></p>

			<p class=MsoListParagraphCxSpMiddle><span lang=EN-US>Pts_Age_18_to_118 - With
			SMK Done Past Year.xlsx</span></p>

			<p class=MsoListParagraphCxSpMiddle><span lang=EN-US>Pts_Age_18_to_118 - With
			WT Done Past 3 Years.xlsx</span></p>

			<p class=MsoListParagraphCxSpLast><span lang=EN-US>&nbsp;</span></p>

		</div>
  </div>
</template>
<style>
@media (min-width: 1024px) {
  .guides {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}

 /* Style Definitions */
 p.MsoNormal, li.MsoNormal, div.MsoNormal
	{margin-top:0in;
	margin-right:0in;
	margin-bottom:8.0pt;
	margin-left:0in;
	line-height:107%;
	font-size:11.0pt;
	font-family:"Verdana Pro",sans-serif;}
h1
	{mso-style-link:"Heading 1 Char";
	margin-top:12.0pt;
	margin-right:0in;
	margin-bottom:0in;
	margin-left:0in;
	line-height:107%;
	page-break-after:avoid;
	font-size:16.0pt;
	font-family:"Verdana Pro",sans-serif;
	color: hsla(160, 100%, 37%, 1);
	font-weight:normal;}
p.MsoTitle, li.MsoTitle, div.MsoTitle
	{mso-style-link:"Title Char";
	margin:0in;
	font-size:28.0pt;
	font-family:"Verdana Pro",sans-serif;
	letter-spacing:-.5pt;}
p.MsoTitleCxSpFirst, li.MsoTitleCxSpFirst, div.MsoTitleCxSpFirst
	{mso-style-link:"Title Char";
	margin:0in;
	font-size:28.0pt;
	font-family:"Verdana Pro",sans-serif;
	letter-spacing:-.5pt;}
p.MsoTitleCxSpMiddle, li.MsoTitleCxSpMiddle, div.MsoTitleCxSpMiddle
	{mso-style-link:"Title Char";
	margin:0in;
	font-size:28.0pt;
	font-family:"Verdana Pro",sans-serif;
	letter-spacing:-.5pt;}
p.MsoTitleCxSpLast, li.MsoTitleCxSpLast, div.MsoTitleCxSpLast
	{mso-style-link:"Title Char";
	margin:0in;
	font-size:28.0pt;
	font-family:"Verdana Pro",sans-serif;
	letter-spacing:-.5pt;}
p.MsoSubtitle, li.MsoSubtitle, div.MsoSubtitle
	{mso-style-link:"Subtitle Char";
	margin-top:0in;
	margin-right:0in;
	margin-bottom:8.0pt;
	margin-left:0in;
	line-height:107%;
	font-size:11.0pt;
	font-family:"Verdana Pro",sans-serif;
	color:#5A5A5A;
	letter-spacing:.75pt;}
p.MsoListParagraph, li.MsoListParagraph, div.MsoListParagraph
	{margin-top:0in;
	margin-right:0in;
	margin-bottom:8.0pt;
	margin-left:.5in;
	line-height:107%;
	font-size:12.0pt;
	font-family:"Lucida Console";}
p.MsoListParagraphCxSpFirst, li.MsoListParagraphCxSpFirst, div.MsoListParagraphCxSpFirst
	{margin-top:0in;
	margin-right:0in;
	margin-bottom:0in;
	margin-left:.5in;
	line-height:107%;
	font-size:12.0pt;
	font-family:"Lucida Console";}
p.MsoListParagraphCxSpMiddle, li.MsoListParagraphCxSpMiddle, div.MsoListParagraphCxSpMiddle
	{margin-top:0in;
	margin-right:0in;
	margin-bottom:0in;
	margin-left:.5in;
	line-height:107%;
	font-size:12.0pt;
	font-family:"Lucida Console";}
p.MsoListParagraphCxSpLast, li.MsoListParagraphCxSpLast, div.MsoListParagraphCxSpLast
	{margin-top:0in;
	margin-right:0in;
	margin-bottom:8.0pt;
	margin-left:.5in;
	line-height:107%;
	font-size:12.0pt;
	font-family:"Lucida Console";}
span.Heading1Char
	{mso-style-name:"Heading 1 Char";
	mso-style-link:"Heading 1";
	font-family:"Verdana Pro",sans-serif;
	color:#2F5496;}
span.TitleChar
	{mso-style-name:"Title Char";
	mso-style-link:Title;
	font-family:"Verdana Pro",sans-serif;
	letter-spacing:-.5pt;}
span.SubtitleChar
	{mso-style-name:"Subtitle Char";
	mso-style-link:Subtitle;
	font-family:"Times New Roman",serif;
	color:#5A5A5A;
	letter-spacing:.75pt;}
.MsoChpDefault
	{font-family:"Calibri",sans-serif;}
.MsoPapDefault
	{margin-bottom:8.0pt;
	line-height:107%;}
@page WordSection1
	{size:8.5in 11.0in;
	margin:.5in .5in .5in .5in;}
div.WordSection1
	{page:WordSection1;}
 /* List Definitions */
 ol
	{margin-bottom:0in;}
ul
	{margin-bottom:0in;}

</style>
