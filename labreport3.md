# `reversed(int[] arr)`

The bug that I plan to be writing about and fixing is the bug with the `reversed` method within ArrayExamples.java from the lab3 repository of week 4.

The initial code looks something like this

```
public class ArrayExamples {

  // Returns a *new* array with all the elements of the input array in reversed order
  
  static int[] reversed(int[] arr) {
  
    int[] newArray = new int[arr.length];
   
    for(int i = 0; i < arr.length; i += 1) {
   
      arr[i] = newArray[arr.length - i - 1];
     
  }
   
 return arr;
   
 }
 
}
```
---

For a failure inducing input, we would write a test with JUnit such as this one

```
public class ArrayTests {
  @Test
   public void testReversed() {
     int[] input1 = { 3, 4, 5 };
     assertArrayEquals(new int[]{ 5, 4, 3 }, ArrayExamples.reversed(input1));
   }
}
```

Here, our failure-inducing input would be any array which in this case is an int array of `{ 3, 4, 5 }`. If this test were to run it would evaluate as false because the expected new array of `{ 5, 4, 3 }` would not match given actual value of `ArrayExamples.reversed(input1)`

---

For an input that doesn't induce a failure, we would write a test with JUnit such as this one 

```
public class ArrayTests {
  @Test
   public void testReversed2() {
     int[] input1 = { };
     assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
   }
}
```
---

We can run both JUnit tests and see that 2 tests will be run with 1 ending in failure

![image](https://github.com/nathantruong0205/cse15l-lab-reports/assets/108157832/33c0ec4e-951c-4919-b738-21ef1ddeb610)

![image](https://github.com/nathantruong0205/cse15l-lab-reports/assets/108157832/97563c1f-21ed-4caf-ad17-5e15aca25af6)

Based off this result and the fact that we know which one is the failure inducing input, we can deduce that there is something wrong with the `reversed(arr)` method when it comes to actually reversing the numbers into a new array.

---

Before code (with bug)

```
public class ArrayExamples {

  // Returns a *new* array with all the elements of the input array in reversed order
  
  static int[] reversed(int[] arr) {
  
    int[] newArray = new int[arr.length];
   
    for(int i = 0; i < arr.length; i += 1) {
   
      arr[i] = newArray[arr.length - i - 1];
     
  }
   
 return arr;
   
 }
 
}
```

After code (without bug) 

```
public class ArrayExamples {

  // Returns a *new* array with all the elements of the input array in reversed order
  
  static int[] reversed(int[] arr) {
  
    int[] newArray = new int[arr.length];
   
    for(int i = 0; i < arr.length; i += 1) {
   
      newArray[i] = arr[arr.length - i - 1];
     
  }
   
 return newArray;
   
 }
 
}
```

If we run the two tests again, we will now see that they both pass

![image](https://github.com/nathantruong0205/cse15l-lab-reports/assets/108157832/a4e446bd-db82-4caf-ba3c-f01ae6ef2a87)

The before code's mistake was that it was attempting to reverse the array with the array parameter it was already given while also trying to get numbers from the `newArray` which was empty. So for the fix I simply changed the 5th line of code so that in the for statement, `newArray` would be the one being assigned numbers from the input array `arr` as its index is incremented downwards. This way the last index of `arr` would be the first index of `newArray` and it would copy it all the way through until we are left with a new array that is the reversed of the initial array. 



# Researching Commands

`grep -r <text>`

```
Nathans-MBP:docsearch nathantruong$ grep -r "freedom"
./technical/government/About_LSC/commission_report.txt:providing legal assistance must have full freedom to protect the
./technical/government/About_LSC/LegalServCorp_v_VelazquezDissent.txt:enjoy the full range of constitutionally protected freedom of
./technical/government/About_LSC/LegalServCorp_v_VelazquezDissent.txt:freedom to protect the best interests of their clients"). And it is
./technical/government/Post_Rate_Comm/Mitchell_RMVancouver.txt:would make if it had the freedom to position itself to withstand
./technical/government/Post_Rate_Comm/Mitchell_RMVancouver.txt:With the freedoms and goals described above, there are a number
./technical/government/Post_Rate_Comm/Mitchell_RMVancouver.txt:discount closer to the figure of 1.5 cents. So, with freedom to
./technical/government/Post_Rate_Comm/Mitchell_RMVancouver.txt:freedom and be able to engage in negotiations with selected
./technical/government/Post_Rate_Comm/Mitchell_RMVancouver.txt:mailers, one way to provide such freedom, even without further
./technical/government/Post_Rate_Comm/Mitchell_RMVancouver.txt:certain inverse price caps. This would provide substantial freedom
./technical/government/Post_Rate_Comm/Mitchell_6-17-Mit.txt:arrangement, but the Postal Service were given the freedom to
./technical/government/Media/Legal_Aid_in_Clay_County.txt:helping indigent victims of domestic violence achieve the freedom
./technical/government/Media/Volunteers_Step_Up.txt:Web site -- www.dialogueonfreedom.org -- is giving lawyers the
./technical/government/Media/Volunteers_Step_Up.txt:freedoms that are rooted in our nation's very soul while ensuring
./technical/government/Media/Volunteers_Step_Up.txt:that defines our democracy and protects our freedoms.
./technical/government/Media/Legal_Aid_Society.txt:Kaye as saying, "The promise of freedom and equal justice is an
./technical/government/Media/Legal_Aid_Society.txt:be denied the protection of the laws and freedoms we cherish and
./technical/plos/pmed.0010039.txt:        promotes physicians' freedom to maximize their personal financial reward, even though those
./technical/plos/pmed.0020099.txt:        describes education as the “practice of freedom,” as learners continuously work to
./technical/plos/journal.pbio.0030056.txt:        But allowing authors the freedom to use the criteria as they see fit could come at a
./technical/plos/pmed.0020246.txt:        scientific advancements [32], the right to privacy [33], and the right to freedom of
./technical/plos/journal.pbio.0020228.txt:        freedoms—to permit a work's reproduction for any noncommercial purpose (the Noncommercial
./technical/plos/pmed.0020047.txt:        which promotes the public's freedom to redistribute scientific and scholarly articles. In
./technical/plos/journal.pbio.0020172.txt:        This success in exploiting the visual system, and the intellectual freedom intrinsic to
./technical/biomed/1471-2202-2-9.txt:          freedom. The correspondence between the orientation of
./technical/biomed/gb-2001-2-4-research0010.txt:          freedom is n1 + n2 - 4: the data are constrained by a sum
./technical/biomed/gb-2001-2-4-research0010.txt:          The model actually has only 18 degrees of freedom (rather
./technical/biomed/gb-2001-2-4-research0010.txt:          freedom.
./technical/biomed/gb-2003-4-4-r24.txt:            with one degree of freedom [ 34 ] , where 
./technical/biomed/1471-2202-2-8.txt:          in the available degrees of freedom. In fact, the
./technical/biomed/1472-6807-2-1.txt:          conformational freedom of functional groups buried upon
./technical/biomed/1472-6807-2-1.txt:          degrees of freedom, was omitted, and only differences in
./technical/biomed/1477-7525-1-9.txt:          restores to the patient some of the freedom and autonomy
./technical/biomed/1472-6831-2-2.txt:          2.42, degrees of freedom, d.f. = 35; p < 0.03) was due
./technical/biomed/gb-2002-3-7-research0037.txt:            freedom and is described in detail in [ 11]. Their
./technical/biomed/gb-2002-3-7-research0037.txt:            of freedom provides a smooth estimate of the local
./technical/biomed/gb-2001-2-11-research0046.txt:          combinations of RI sets provides new degrees of freedom
./technical/biomed/gb-2001-2-8-research0032.txt:          degree of freedom irrespective of the values of θ 
./technical/biomed/1471-2105-4-26.txt:          "pooled" data with degrees of freedom being reduced to 10
./technical/biomed/1471-2105-4-26.txt:          of freedom for the test. Next, we consider the effects of
./technical/biomed/1471-2105-4-26.txt:          decreased because the degrees of freedom are reduced to 
./technical/biomed/1471-2105-4-26.txt:          to reduction of degrees of freedom will be partially
./technical/biomed/1471-2164-3-28.txt:            unequal variances, the associated degrees of freedom
./technical/biomed/1471-2164-3-28.txt:          because of the variation in degrees of freedom. So, we
./technical/biomed/1471-2164-3-28.txt:            statistics and the appropriate degrees of freedom. An
./technical/biomed/1478-7954-1-3.txt:          Chi-square variable with 4 degrees of freedom. The
./technical/biomed/1478-7954-1-3.txt:          degree of freedom.
./technical/biomed/1475-925X-2-6.txt:        neural tissue is related to our greater freedom in
./technical/biomed/1472-684X-2-2.txt:        death" include, besides freedom of pain, death at home with
./technical/biomed/1471-2288-1-9.txt:          with degrees of freedom equal to the number of hospitals
./technical/biomed/1471-2288-1-9.txt:          11 hospitals, there are 10 degrees of freedom and the
./technical/biomed/1471-2288-2-10.txt:          freedom when appropriate. Details of statistical models
./technical/biomed/gb-2002-3-5-research0022.txt:          of freedom, as predicted from the 
./technical/biomed/1471-2202-3-11.txt:          t-distribution with N-m degrees of freedom, N is the
./technical/biomed/1472-6807-2-9.txt:        freedom fixes the entire side chain. A fixed tripeptide
./technical/biomed/1471-2148-3-7.txt:          - G (p < 0.01 [three degrees of freedom]), with the Gs
./technical/biomed/1471-2474-3-23.txt:          moment, with six degrees of freedom, allowing coupled
./technical/biomed/bcr570.txt:          χ 2test with one degree of freedom. To evaluate the role
./technical/biomed/1472-6947-3-5.txt:        participants wanted the freedom to add [proprietary] data
./technical/biomed/1472-6947-3-5.txt:        freedom comes responsibility. It is quite possible to
./technical/biomed/1471-2202-3-17.txt:          degrees of freedom. This strongly favors the cooperative
./technical/911report/chapter-2.txt:                Sudanese, clearly thought that he had new freedom to publish his appeals for jihad.
./technical/911report/chapter-2.txt:                in Afghanistan a freedom of movement that he had lacked in Sudan. Al Qaeda members
./technical/911report/chapter-12.txt:                greater freedom, women and girls are emerging from subjugation, and 3 million
./technical/911report/chapter-12.txt:                Muslims that we must encourage reform, freedom, democracy, and opportunity, even
./technical/911report/chapter-12.txt:                The United Nations has rightly equated "literacy as freedom."
./technical/911report/chapter-12.txt:                manifestation of our belief in freedom, democracy, global economic growth, and the
```

```
Nathans-MBP:docsearch nathantruong$ grep -r "Taliban"
./technical/911report/chapter-13.4.txt:            121. Frank G. and Mary S. briefing (July 15, 2003). The Taliban's support was limited
./technical/911report/chapter-13.4.txt:                providing substantial financial support to the Taliban.
./technical/911report/chapter-13.4.txt:                theTaliban, see Frank G.and Mary S. briefing (July 15, 2003); CIA analytic
./technical/911report/chapter-13.4.txt:                Laden; Penttbomb; Taliban," May 25, 2002.
./technical/911report/chapter-13.4.txt:                Taliban. The diplomat said the United States was delivering "a strong and
./technical/911report/chapter-13.4.txt:                unmistakable message to the Taliban that should such attacks occur, they and Bin
./technical/911report/chapter-13.4.txt:                003900,"Saudis on USG Warning to Taliban Concerning UBLThreats,"Dec. 14,1999. Berger
./technical/911report/chapter-13.4.txt:                register with the Taliban. See NSC memo, Berger to President Clinton, terrorist
./technical/911report/chapter-13.4.txt:                Taliban's Military Campaign in Afghanistan," Sept. 26, 2000.
./technical/911report/chapter-13.4.txt:                called for countries to withdraw their officials and agents from the Taliban-held
./technical/911report/chapter-13.4.txt:                Taliban's primary supporters: Pakistan, Saudi Arabia, and the United Arab Emirates.
./technical/911report/chapter-13.4.txt:                Taliban-Controlled Assets," undated (probably Oct. 18, 1999).
./technical/911report/chapter-13.4.txt:                taken against Bin Ladin. Given diplomatic failures to directly pressure the Taliban
./technical/911report/chapter-13.4.txt:                wrote, but "it may also serve as a healthy reminder to al Qida and the Taliban that
./technical/911report/chapter-13.4.txt:            136. For Berger's authorization, see NSC memo, TNT to Berger, responding to Taliban's
./technical/911report/chapter-13.4.txt:                Strategy with the Taliban," Nov. 25, 2000.
./technical/911report/chapter-13.4.txt:                already talked with Rice and Hadley about Bin Ladin and al Qaeda, the Taliban, and
./technical/911report/chapter-13.4.txt:                possible impact of Taliban actions against al Qaeda and on the likely regional
./technical/911report/chapter-13.4.txt:                impact of increased aid to anti-Taliban groups in Afghanistan). Both Secretary
./technical/911report/chapter-13.4.txt:                on Bin Ladin, the Taliban and Afghanistan for DCI meetings with Powell, Feb. 13,
./technical/911report/chapter-13.4.txt:                Taliban. Marc Grossman interview (Jan. 20, 2004).
./technical/911report/chapter-13.4.txt:                with Taliban Deputy Foreign Minister Jalil in Islamabad. Milam tried to dispel any
./technical/911report/chapter-13.4.txt:                confusion about where Bin Ladin fit into U.S.-Taliban relations-the Saudi terrorist
./technical/911report/chapter-13.4.txt:                was the issue, and he had to be expelled. DOS cable, Islamabad 3628, "Taliban's
./technical/911report/chapter-13.4.txt:                theTaliban. It opposed a policy to overthrow theTaliban and was cautious about
./technical/911report/chapter-13.4.txt:                the goal was not to overthrow the Taliban, see Jonathan F. interview (Jan. 19,
./technical/911report/chapter-13.4.txt:                memo,"U.S. Engagement with the Taliban on Usama Bin Laden," undated (attached to NSC
./technical/911report/chapter-13.4.txt:                Sattar urging the United States to engage the Taliban, see DOS cable, State 109130,
./technical/911report/chapter-13.5.txt:                recruits fought on the front lines alongside the Taliban and participated in the
./technical/911report/chapter-13.5.txt:                to Bin Ladin, al Qaeda, the Taliban, and key countries such as Afghanistan,
./technical/911report/chapter-13.5.txt:                workers in Afghanistan who had been imprisoned by the Taliban in August 2001. Two
./technical/911report/chapter-13.5.txt:                Christianity. The Taliban and other Islamists found their activities an affront to
./technical/911report/chapter-13.5.txt:                that he considered having Powell deliver the ultimatum to the Taliban, but
./technical/911report/chapter-13.5.txt:                several places. See, e.g., CIA analytic report, "Likely Impact of Taliban Actions
./technical/911report/chapter-13.3.txt:            63. Ahmed Rashid, Taliban: Militant Islam, Oil and Fundamentalism in Central Asia
./technical/911report/chapter-13.3.txt:            64. Rashid, Taliban, pp. 88-90.
./technical/911report/chapter-13.3.txt:                Raffat Pasha interview (Oct. 25, 2003); Rashid, Taliban; Waleed Ziad, "How the Holy
./technical/911report/chapter-13.3.txt:                Rashid, Taliban, p. 139; Intelligence report, Terrorism: Activities of Bin Ladin's
./technical/911report/chapter-13.3.txt:                Qaeda, p. 41; Rashid, Taliban, pp. 19-21, 133.
./technical/911report/chapter-13.3.txt:            73. On Bin Ladin's promise to Taliban leaders, see government exhibit no. 1559-T,
./technical/911report/chapter-13.3.txt:                the Taliban's invitation to UBL, see Mike briefing (Dec. 12, 2003); Rashid, Taliban,
./technical/911report/chapter-13.3.txt:                his relationship with, and eventually gain control over, the Taliban. Ahmed Rashid
./technical/911report/chapter-13.3.txt:                On relations between the Arabs in Afghanistan and the Taliban, see ibid. On
./technical/911report/chapter-13.3.txt:                Marty Miller, denied working exclusively with the Taliban and told us that his
./technical/911report/chapter-13.3.txt:                and Oakley, Oct.1996. On giving the Taliban a chance, see Marvin Weinbaum interview
./technical/911report/chapter-13.3.txt:                interview (Feb. 5, 2004). For speculation on tipping off the Taliban, see, e.g.,
./technical/911report/chapter-13.3.txt:            62. DOS cable, Islamabad 06863, "Afghanistan: Demarche toTaliban on New Bin
./technical/911report/chapter-13.3.txt:            64. DOS cable, Islamabad 007665, "High-Level Taliban Official Gives the Standard Line
./technical/911report/chapter-13.3.txt:                for the Taliban,"Apr. 9, 1999.
./technical/911report/chapter-13.3.txt:                calling for increased high-level pressure on the Taliban and the three countries
./technical/911report/chapter-13.3.txt:                to assemble an anti-Taliban ruling coalition inside and outside Afghanistan. Peter
./technical/911report/chapter-13.3.txt:                "Designating the Taliban a FTO," Apr. 22, 1999; Executive Order 13129, July 4, 1999.
./technical/911report/chapter-13.3.txt:                theTaliban, the sanctions under this executive order mimicked the sanctions that
./technical/911report/chapter-13.3.txt:                that the Taliban render Bin Ladin to justice within 30 days; upon noncompliance, UN
./technical/911report/chapter-13.3.txt:                member states were called on to restrict takeoff and landing rights of Taliban-owned
./technical/911report/chapter-13.3.txt:                aircraft. The sanctions also required member states to freeze Taliban funds and
./technical/911report/chapter-13.3.txt:                financial resources. But Taliban "charter flights" continued to fly between
./technical/911report/chapter-13.3.txt:            91. See Intelligence report, relations between al Qaeda and the Taliban, Feb. 20,
./technical/911report/chapter-13.3.txt:                arms flow from Pakistan to the Taliban, it had enormous symbolic importance. He also
./technical/911report/chapter-13.3.txt:                noted that UNSCR 1333 must have stigmatized the Taliban because they "went ballistic
./technical/911report/chapter-13.3.txt:                "very nervous" about their relationships with the Taliban. Michael Sheehan interview
./technical/911report/chapter-13.3.txt:                Bin Ladin's Taliban security detail) was dispatched to the north, further
./technical/911report/chapter-13.3.txt:            166. DOS memo, Indyk and Sheehan to Albright, "UAE Gives Ultimatum to Taliban on Bin
./technical/911report/chapter-13.3.txt:                cable, Abu Dhabi 04644,"Taliban Refuse to Expel Bin Ladin Despite UAEG Ultimatum:
./technical/911report/chapter-13.3.txt:            167. DOS memo, Indyk and Sheehan to Albright, "UAE Gives Ultimatum to Taliban on Bin
./technical/911report/chapter-13.3.txt:            169. For discussion of the Taliban generally, see Ahmed Rashid, Taliban: Militant
./technical/911report/chapter-3.txt:                seemed, and ultimately proved, to be a hopeless effort to persuade the Taliban
./technical/911report/chapter-3.txt:                Taliban. The chief of the Counterterrorist Center, whom we will call "Jeff," told
./technical/911report/chapter-3.txt:                table.U.S. diplomats did not favor the Taliban over the rival factions. Despite
./technical/911report/chapter-3.txt:                "give the Taliban a chance."
./technical/911report/chapter-3.txt:            Though Secretary Albright made no secret of thinking the Taliban "despicable," the
./technical/911report/chapter-3.txt:                Americans, Richardson asked the Taliban to expel Bin Ladin. They answered that they
./technical/911report/chapter-3.txt:                did not know his whereabouts. In any case, the Taliban said, Bin Ladin was not a
./technical/911report/chapter-3.txt:                Taliban's human rights abuses than on driving out Bin Ladin. Another key actor,
./technical/911report/chapter-3.txt:                Kandahar, the Taliban capital where he sometimes stayed the night, and his primary
./technical/911report/chapter-3.txt:                Tenet an all-out secret effort to persuade the Taliban to expel Bin Ladin so that he
./technical/911report/chapter-3.txt:                Taliban leaders. Apparently employing a mixture of possible incentives and threats,
./technical/911report/chapter-3.txt:                might have sent a warning to the Taliban or Bin Ladin.
./technical/911report/chapter-3.txt:                he argued that rolling attacks might persuade the Taliban to hand over Bin Ladin
./technical/911report/chapter-3.txt:            After the August missile strikes, diplomatic options to press the Taliban seemed no
./technical/911report/chapter-3.txt:                to the Taliban, and also to Sudan, that they would be held directly responsible for
./technical/911report/chapter-3.txt:                Taliban into thinking of giving up Bin Ladin. On August 22, the reclusive Mullah
./technical/911report/chapter-3.txt:            Meeting in Islamabad with William Milam, the U.S. ambassador to Pakistan, Taliban
./technical/911report/chapter-3.txt:                whether he would keep his earlier promise to expel Bin Ladin, the Taliban leader
./technical/911report/chapter-3.txt:                government. Riyadh then suspended its diplomatic relations with the Taliban regime.
./technical/911report/chapter-3.txt:                recognized the Taliban as the legitimate government of Afghanistan.) Crown Prince
./technical/911report/chapter-3.txt:            In October, an NSC counterterrorism official noted that Pakistan's pro-Taliban
./technical/911report/chapter-3.txt:                spending 45 to 50 percent of his time working the Taliban- Bin Ladin portfolio.
./technical/911report/chapter-3.txt:                Intelligence Directorate), was the Taliban's primary patron, which made progress
./technical/911report/chapter-3.txt:            Additional pressure on the Pakistanis-beyond demands to press theTaliban on Bin
./technical/911report/chapter-3.txt:                Taliban and Bin Ladin. A senior State Department official concluded that Saudi Crown
./technical/911report/chapter-3.txt:                a promise to talk with the Taliban.
./technical/911report/chapter-3.txt:                channel, he repeated the earlier warning to the Taliban of the possible dire
./technical/911report/chapter-3.txt:                Taliban regime a state sponsor of terrorism. This was technically difficult to do,
./technical/911report/chapter-3.txt:                weapon against the Taliban. He told us that he thought he was regarded in the
./technical/911report/chapter-3.txt:                was "behaving as a rogue state in two areas-backing Taliban/UBL terror and provoking
./technical/911report/chapter-3.txt:                and the CIA, called for labeling the Taliban a terrorist group and ultimately
./technical/911report/chapter-3.txt:                possible moderate governing alternative to theTaliban. In late 1999, Washington
./technical/911report/chapter-3.txt:                anti-Taliban forces inside Afghanistan and linking the RESPONSES TO AL QAEDA'S
./technical/911report/chapter-3.txt:            Frustrated by the Taliban's resistance, two senior State Department officials
./technical/911report/chapter-3.txt:                suggested asking the Saudis to offer the Taliban $250 million for Bin Ladin. Clarke
./technical/911report/chapter-3.txt:                the Taliban" and suggested that the idea might not seem attractive to either
./technical/911report/chapter-3.txt:                Taliban's record on women's rights.
./technical/911report/chapter-3.txt:                to designateTaliban-controlled Afghanistan as a state sponsor of terrorism or to
./technical/911report/chapter-3.txt:                of whether to recognize the Taliban as Afghanistan's government). Sheehan and Clarke
./technical/911report/chapter-3.txt:                declaring the Taliban regime a state sponsor of terrorism.
./technical/911report/chapter-3.txt:                Taliban appear to be up to something." Mullah Omar had
./technical/911report/chapter-3.txt:                Taliban, who seemed "to be looking for a face-saving way out of the Bin Ladin
./technical/911report/chapter-3.txt:                learned that at the end of 1999, theTaliban Council of Ministers unanimously
./technical/911report/chapter-3.txt:                and theTaliban leadership were sometimes tense, but the foundation was deep and
./technical/911report/chapter-3.txt:                Taliban, in December 2000.
./technical/911report/chapter-3.txt:            The aim of the resolution was to hit the Taliban where it was most sensitive- on the
./technical/911report/chapter-3.txt:                flow of Pakistani military assistance to the Taliban.
./technical/911report/chapter-3.txt:                the Taliban to stop sheltering Bin Ladin. President Clinton contacted Sharif again
./technical/911report/chapter-3.txt:                the strongest way I can," to persuade the Taliban to expel Bin Ladin.
./technical/911report/chapter-3.txt:                Taliban and over Afghan imports through Karachi. Sharif suggested instead that
./technical/911report/chapter-3.txt:                failure to take effective action with respect to the Taliban and Bin Ladin. Sharif
./technical/911report/chapter-3.txt:                intelligence service, which supported the Taliban. Berger speculated that the new
./technical/911report/chapter-3.txt:                like the efforts with the Taliban, had, according to Under Secretary of State Thomas
./technical/911report/chapter-3.txt:                some Taliban leaders, though not Mullah Omar, had urged Bin Ladin to go to Iraq. If
./technical/911report/chapter-3.txt:                the region, but all the options were unappealing. Pro-Taliban elements of Pakistan's
./technical/911report/chapter-3.txt:                the Taliban's only travel and financial outlets to the outside world, to break off
./technical/911report/chapter-3.txt:                Foreign Affairs Hamdan bin Zayid threatened to break relations with the Taliban over
./technical/911report/chapter-3.txt:            The Taliban did not take him seriously, however. Bin Zayid later told an American
./technical/911report/chapter-3.txt:                relations with the Taliban because the Afghan radicals offered a counterbalance to
./technical/911report/chapter-3.txt:                northern and eastern parts of Afghanistan. In contrast, Taliban members came
./technical/911report/chapter-3.txt:            Because of the Taliban's behavior and its association with Pakistan, the Northern
./technical/911report/chapter-3.txt:                Kandahar, far from the front lines ofTaliban operations against the Northern
./technical/911report/chapter-3.txt:                Bin Ladin's network and to hit Taliban government sites as well. General Shelton
./technical/911report/chapter-3.txt:                told us that the Taliban targets were "easier" to hit and more substantial.
./technical/911report/chapter-3.txt:                retaliating, including possible strikes on the Taliban. But Clarke observed that Bin
./technical/911report/chapter-3.txt:                Alliance rebels fighting the Taliban.
./technical/911report/chapter-2.txt:                Taliban movement, espousing a ruthless version of Islamic law, perhaps could bring
./technical/911report/chapter-2.txt:                reportedly introduced Bin Ladin to Taliban leaders in Kandahar, their main base of
./technical/911report/chapter-2.txt:            For a time, it may not have been clear to Bin Ladin that the Taliban would be his
./technical/911report/chapter-2.txt:                Gulbuddin Hekmatyar, who, though an Islamic extremist, was also one of the Taliban's
./technical/911report/chapter-2.txt:                Kabul fell to the Taliban, Bin Ladin cemented his ties with them.
./technical/911report/chapter-2.txt:                At about the time when the Taliban were making their final drive toward Jalalabad
./technical/911report/chapter-2.txt:                Khurasan." But theTaliban, like the Sudanese, would eventually hear warnings,
./technical/911report/chapter-2.txt:            Though Bin Ladin had promised Taliban leaders that he would be circumspect, he broke
./technical/911report/chapter-2.txt:                1997. The Taliban leader Mullah Omar promptly "invited" Bin Ladin to move to
./technical/911report/chapter-2.txt:                Iraqi delegation traveled to Afghanistan to meet first with the Taliban and then
./technical/911report/chapter-2.txt:                in 1999 during a period of some reported strains with the Taliban. According to the
./technical/911report/chapter-2.txt:                the Taliban-Bin Ladin was able to circumvent restrictions; Mullah Omar would stand
./technical/911report/chapter-2.txt:                by him even when otherTaliban leaders raised objections. Bin Ladin appeared to have
./technical/911report/chapter-2.txt:            The Taliban seemed to open the doors to all who wanted to come to Afghanistan to
./technical/911report/chapter-2.txt:                train in the camps. The alliance with theTaliban provided al Qaeda a sanctuary in
./technical/911report/chapter-2.txt:                in 1996, and the months spent establishing ties with the Taliban may also have
./technical/911report/chapter-5.txt:                Ladin was building ties to the rival Taliban.
./technical/911report/chapter-5.txt:                fighting there and also to learn about the Taliban. He again encountered Bin Ladin,
./technical/911report/chapter-5.txt:                more conventional military jihad, joining the Taliban forces in their fight against
./technical/911report/chapter-5.txt:                camp near Khowst with cruise missiles in August 1998, and before theTaliban granted
./technical/911report/chapter-5.txt:                someone named Umar al Masri at the Taliban office.
./technical/911report/chapter-5.txt:                Taliban office in Quetta, there was no one named Umar al Masri. The name,
./technical/911report/chapter-5.txt:                Bin Ladin arrived in Afghanistan, he relied on the Taliban until he was able to
./technical/911report/chapter-5.txt:            It does not appear that any government other than the Taliban financially supported
./technical/911report/chapter-5.txt:                Africa embassy bombings, including UN resolutions against it and the Taliban.
./technical/911report/chapter-5.txt:                provided approximately $10-$20 million per year to the Taliban in return for safe
./technical/911report/chapter-5.txt:                a source of income for the Taliban, it did not serve the same purpose for al Qaeda,
./technical/911report/chapter-6.txt:                Taliban in Afghanistan in the event of any attacks on U.S. interests, anywhere, by
./technical/911report/chapter-6.txt:                Taliban that they would be held responsible for future al Qaeda attacks." Mike was
./technical/911report/chapter-6.txt:                not diplomatic," Clarke reported to Berger. With virtually no evidence of a Taliban
./technical/911report/chapter-6.txt:                the Taliban had proved unsuccessful. As one NSC staff note put it,
./technical/911report/chapter-6.txt:            "Under the Taliban, Afghanistan is not so much a state sponsor of terrorism as it is
./technical/911report/chapter-6.txt:                over the Taliban. In January 2000, Assistant Secretary of State Karl Inderfurth and
./technical/911report/chapter-6.txt:                anything," given what it sees as the benefits of Taliban control of
./technical/911report/chapter-6.txt:                supporting a Taliban military offensive aimed at completing the conquest of
./technical/911report/chapter-6.txt:                country to provide the Taliban with arms or military assistance.
./technical/911report/chapter-6.txt:            This, too, had little if any effect. The Taliban did not expel Bin Ladin. Pakistani
./technical/911report/chapter-6.txt:            In July 1999, the President applied the same designation to the Taliban for harboring
./technical/911report/chapter-6.txt:                Bin Ladin. Here, OFAC had more success. It blocked more than $34 million in Taliban
./technical/911report/chapter-6.txt:            Attacking the funds of an institution, even the Taliban, was easier than finding and
./technical/911report/chapter-6.txt:                overthrow theTaliban and to recognize that they were fighting common enemies. Clarke
./technical/911report/chapter-6.txt:            During at least one trial mission, the Taliban spotted the Predator and scrambled MiG
./technical/911report/chapter-6.txt:                Ladin and the Taliban.
./technical/911report/chapter-6.txt:                Department make another approach toTaliban Deputy Foreign Minister Abdul Jalil about
./technical/911report/chapter-6.txt:                Afghanistan, or deliver an ultimatum to theTaliban threatening strikes if they did
./technical/911report/chapter-6.txt:                Taliban. For the first time, these strikes envisioned an air campaign against
./technical/911report/chapter-6.txt:                idea: a last-chance ultimatum for the Taliban. Clarke was developing the idea with
./technical/911report/chapter-6.txt:                Noncompliance would mean U.S. "force directed at the Taliban itself " and U.S.
./technical/911report/chapter-6.txt:                efforts to ensure that the Taliban would never defeat the Northern Alliance. No such
./technical/911report/chapter-6.txt:                order to go to war or deliver an ultimatum to the Taliban threatening war. The
./technical/911report/chapter-6.txt:                have sought a UN Security Council ultimatum and given the Taliban one, two, or three
./technical/911report/chapter-6.txt:                days before taking further action against both al Qaeda and the Taliban. But he did
./technical/911report/chapter-6.txt:                might inflame the Islamic world and increase support for the Taliban. Defense
./technical/911report/chapter-6.txt:                    and increased funding so that it could stave off the Taliban army and tie down
./technical/911report/chapter-6.txt:                    al Qaeda fighters. This effort was not intended to remove theTaliban from power,
./technical/911report/chapter-6.txt:                Assistance to anti-Taliban groups and proxies who might be encouraged to
./technical/911report/chapter-6.txt:                    passively resist the Taliban.
./technical/911report/chapter-6.txt:                targets and infrastructure andTaliban military and command assets. The paper also
./technical/911report/chapter-6.txt:                that decisions should be made soon on messages to theTaliban and Pakistan over the
./technical/911report/chapter-6.txt:                told about Clinton administration warnings to the Taliban. The President told us
./technical/911report/chapter-6.txt:                Washington would first consider options for aiding other anti- Taliban groups.
./technical/911report/chapter-6.txt:                influence Bin Ladin or the Taliban. Clarke and Black replied that the CIA's ongoing
./technical/911report/chapter-6.txt:                anti-Taliban groups. The draft also tasked OMB with ensuring that sufficient funds
./technical/911report/chapter-6.txt:                the Taliban to turn Bin Ladin "over to a country where he could face justice" and
./technical/911report/chapter-6.txt:                repeated, yet again, the warning that the Taliban would be held responsible for any
./technical/911report/chapter-6.txt:            The Taliban's representatives repeated their old arguments. Deputy Secretary of State
./technical/911report/chapter-6.txt:                forTaliban cooperation with the United States on al Qaeda. The NSC staff was tasked
./technical/911report/chapter-6.txt:                to flesh out options for dealing with the Taliban. Revisiting these issues tried the
./technical/911report/chapter-6.txt:                told us. Clarke kept arguing that moves against the Taliban and al Qaeda should not
./technical/911report/chapter-6.txt:            As all hope in moving the Taliban faded, debate revived about giving covert
./technical/911report/chapter-6.txt:                without aiming to overthrow the Taliban.
./technical/911report/chapter-6.txt:                needed to have a big part for Pashtun opponents of theTaliban. They also thought the
./technical/911report/chapter-6.txt:                Northern Alliance's final defeat at the hands of the Taliban.
./technical/911report/chapter-6.txt:                assistance to the Taliban's foes. The draft authorities expressly stated that the
./technical/911report/chapter-6.txt:                goal of the assistance was not to overthrow the Taliban. But even this program would
./technical/911report/chapter-6.txt:                made to convince theTaliban to shift position and then, if that failed, the
./technical/911report/chapter-6.txt:                the deputies a lengthy historical review of U.S. efforts to engage the Taliban about
./technical/911report/chapter-6.txt:                strategy. First an envoy would give the Taliban a last chance. If this failed,
./technical/911report/chapter-6.txt:                program encouraging anti-Taliban Afghans of all major ethnic groups to stalemate the
./technical/911report/chapter-6.txt:                Taliban in the civil war and attack al Qaeda bases, while the United States
./technical/911report/chapter-6.txt:                theTaliban's policy still did not change, the deputies agreed that the United States
./technical/911report/chapter-6.txt:                would try covert action to topple the Taliban's leadership from within.
./technical/911report/chapter-6.txt:                the Taliban. From his point of view, once the United States made the commitment to
./technical/911report/chapter-6.txt:                his influence with the Taliban on Bin Ladin and al Qaeda.
./technical/911report/chapter-6.txt:                Sattar urged senior U.S. policymakers to engage the Taliban, arguing that such a
./technical/911report/chapter-6.txt:                contingency plans" to attack both al Qaeda and Taliban targets in Afghanistan. The
./technical/911report/chapter-6.txt:                al Qaeda or the Taliban before 9/11.
./technical/911report/chapter-6.txt:                finding that did concern aid to opponents of the Taliban regime; the other was a
./technical/911report/chapter-6.txt:                purposes. He recalled that theTaliban had spotted a Predator in the fall of 2000 and
./technical/911report/chapter-6.txt:                program termination when the stakes are raised by the Taliban parading a charred
./technical/911report/chapter-6.txt:                "Many in al Qida and the Taliban may have drawn the wrong lesson from the Cole: that
./technical/911report/chapter-6.txt:                plan to pressure and perhaps ultimately topple theTaliban leadership.
./technical/911report/chapter-6.txt:                the Taliban, and Pakistan.
./technical/911report/chapter-7.txt:                Qaeda and the Taliban argued over strategy for 2001. Our focus has naturally been on
./technical/911report/chapter-7.txt:                for the year. Living in Afghanistan, interacting constantly with the Taliban, the al
./technical/911report/chapter-7.txt:                had a different view. The Taliban leaders put their main emphasis on the year's
./technical/911report/chapter-7.txt:                Taliban's perspective, an attack against the United States might be
./technical/911report/chapter-7.txt:                argued that al Qaeda should defer to theTaliban's wishes. Another source says that
./technical/911report/chapter-7.txt:                were not privy to the full scope of al Qaeda andTaliban planning. Bin Ladin and
./technical/911report/chapter-7.txt:                The general Taliban offensive against the Northern Alliance would rely on al
./technical/911report/chapter-7.txt:            But on September 9, the Massoud assassination took place. The delayedTaliban
./technical/911report/chapter-7.txt:                for vital support in the Taliban military operations. KSM remembers Atef telling him
./technical/911report/chapter-7.txt:                that al Qaeda had an agreement with the Taliban to eliminate Massoud, after which
./technical/911report/chapter-7.txt:                the Taliban would begin an offensive to take over Afghanistan. Atef hoped Massoud's
./technical/911report/chapter-7.txt:                death would also appease the Taliban when the 9/11 attacks happened. There are also
./technical/911report/chapter-12.txt:                the Taliban and pursue al Qaeda. This work continues. But long-term success demands
./technical/911report/chapter-12.txt:                insufficient attention to Afghanistan, the rule of the Taliban or warlords and
./technical/911report/chapter-12.txt:                terrorists, many Taliban fighters, and-perhaps-Usama Bin Ladin. Pakistan possesses
./technical/911report/chapter-12.txt:                On terrorism, Pakistan helped nurture theTaliban. The Pakistani army and
./technical/911report/chapter-12.txt:                    bad. But before 9/11, preserving good relations with the Taliban took
./technical/911report/chapter-12.txt:                coalition to destroy theTaliban regime. In other ways, Pakistan actively assisted:
./technical/911report/chapter-12.txt:                its authorities arrested more than 500 al Qaeda operatives and Taliban members, and
./technical/911report/chapter-12.txt:                against al Qaeda while seeking to avoid a larger confrontation withTaliban remnants
./technical/911report/chapter-12.txt:                2001, the U.S.-led international coalition and its Afghan allies toppled the Taliban
./technical/911report/chapter-12.txt:            But grave challenges remain. Taliban and al Qaeda fighters have regrouped in the
./technical/911report/chapter-12.txt:                in June 2004, Taliban fighters resorted to slaughtering 16 Afghans on a bus,
./technical/911report/chapter-12.txt:                    the military mission is narrowly focused on al Qaeda andTaliban remnants in the
./technical/911report/chapter-12.txt:                initiatives aimed at theTaliban or Pakistan before 9/11. At the same time, Saudi
./technical/911report/chapter-10.txt:                Pakistan and what it could do to turn the Taliban against al Qaeda. They concluded
./technical/911report/chapter-10.txt:                to cut off all shipments of fuel to the Taliban and stop recruits from going
./technical/911report/chapter-10.txt:                if the evidence implicated bin Ladin and al Qaeda and the Taliban continued to
./technical/911report/chapter-10.txt:                    harbor them, to break relations with the Taliban government.
./technical/911report/chapter-10.txt:                President Bush led a discussion of an appropriate ultimatum to the Taliban. He also
./technical/911report/chapter-10.txt:                ordered Secretary Rumsfeld to develop a military plan against the Taliban. The
./technical/911report/chapter-10.txt:                President wanted the United States to strike the Taliban, step back, wait to see if
./technical/911report/chapter-10.txt:                military should focus on targets that would influence the Taliban's behavior.
./technical/911report/chapter-10.txt:                continue to act against the United States even while under Taliban control. It
./technical/911report/chapter-10.txt:                therefore detailed specific U.S. demands for the Taliban: surrender Bin Ladin and
./technical/911report/chapter-10.txt:                Taliban knew about al Qaeda and its operations; close all terrorist camps; free all
./technical/911report/chapter-10.txt:            The State Department proposed delivering an ultimatum to the Taliban: produce Bin
./technical/911report/chapter-10.txt:                The State Department did not expect the Taliban to comply. Therefore, State and
./technical/911report/chapter-10.txt:                to the Taliban along the lines that his department had originally proposed. The
./technical/911report/chapter-10.txt:                military plan to attack the Taliban and al Qaeda if the Taliban rejected the
./technical/911report/chapter-10.txt:                administration knew that theTaliban was unlikely to turn over Bin Ladin.
./technical/911report/chapter-10.txt:                Qaeda, theTaliban, and Iraq. It argued that of the three, al Qaeda and Iraq posed a
./technical/911report/chapter-10.txt:                conflict, the references to specific enemies or regions named only the Taliban, al
./technical/911report/chapter-10.txt:                meant for his area of responsibility. He knew he would soon be striking the Taliban
./technical/911report/chapter-10.txt:                that had already been conveyed privately." The Taliban must act, and act
./technical/911report/chapter-10.txt:                    Qaeda and Taliban targets. In an innovative joint effort, CIA and Special
./technical/911report/chapter-10.txt:                    faction opposed to the Taliban. The Phase Two strikes and raids began on October
./technical/911report/chapter-10.txt:                    all elements of national power, including ground troops, to topple the Taliban
./technical/911report/chapter-10.txt:                    November 9. Four days later the Taliban had fled from Kabul. By early December,
./technical/911report/chapter-10.txt:                    Taliban.
./technical/911report/chapter-10.txt:                destroy theTaliban regime and disrupt al Qaeda. They had killed or captured about a
./technical/911report/chapter-11.txt:                Between Taliban and Bin Ladin" (January 1999), "Terrorist Threat to US Interests in
./technical/911report/chapter-11.txt:                Interest in Biological, Radiological Weapons" (February 2001), "Taliban Holding Firm
./technical/911report/chapter-11.txt:                blunt ultimatum to the Taliban, backed by a readiness to at least launch an
./technical/911report/chapter-11.txt:                Taliban that they would be held accountable for further attacks by Bin Ladin against
./technical/911report/chapter-11.txt:                Taliban. Clarke developed a paper laying out a formal, specific ultimatum. But
```

This `grep -r <text>` command is a simple grep command that returns the line that matches whatever is in the text, however putting the -r option next to it allows it to recursively search through all directories and subdirectories in order to find the desired match. This is useful in cases such as this one in which there are so many .txt files that it would be impossible to search for all instances of a specific phrase manually. It would also be troublesome to have to run grep on each directory and subdirectory. 

---

`grep -v <text> <file>`

```
Nathans-MBP:911report nathantruong$ grep -v "of" chapter-2.txt

    
        
            THE FOUNDATION OF THE NEW TERRORISM
            A DECLARATION OF WAR
            In February 1998, the 40-year-old Saudi exile Usama Bin Ladin and a fugitive Egyptian
                physician, Ayman al Zawahiri, arranged from their Afghan headquarters for an Arabic
                respected Islamic authority, but neither Bin Ladin, Zawahiri, nor the three others
                American, anywhere on earth, as the "individual duty for every Muslim who can do it
                in any country in which it is possible to do it."
            
            Three months later, when interviewed in Afghanistan by ABC-TV, Bin Ladin enlarged on
                these themes.
            
            He claimed it was more important for Muslims to kill Americans than to kill other
                infidels." It is far better for anyone to kill a single American soldier than to
                in the world today and the worst terrorists are the Americans. Nothing could stop
                you except perhaps retaliation in kind. We do not have to differentiate between
                military or civilian. As far as we are concerned, they are all targets." Note:
                the last word in the names by which they are known: Nawaf al Hazmi as Hazmi, for
                accepted way to transliterate Arabic words and names into English. We have relied on
                materials, the press, or government documents. When we quote from a source document,
                since 1992 that singled out the United States for attack. In August 1996, Bin Ladin
                had issued his own self-styled fatwa calling on Muslims to drive American soldiers
                Kingdom. It praised the 1983 suicide bombing in Beirut that killed 241 U.S. Marines,
                the 1992 bombing in Aden, and especially the 1993 firefight in Somalia after which
                the United States "left the area carrying disappointment, humiliation, defeat and
                your dead with you."
            
            Bin Ladin said in his ABC interview that he and his followers had been preparing in
                Somalia for another long struggle, like that against the Soviets in Afghanistan, but
                could overcome a superpower, he told the interviewer: "We are certain that we
                "If the present injustice continues . . . , it will inevitably move the battle to
                American soil."
            
            Plans to attack the United States were developed with unwavering singlemindedness
                destroy America and bring the world to Islam.
            BIN LADIN'S APPEAL IN THE ISLAMIC WORLD 
                past greatness, he promises to restore pride to people who consider themselves the
                cyclonic change as they confront modernity and globalization. His rhetoric
                selectively draws from multiple sources-Islam, history, and the region's political
                and economic malaise. He also stresses grievances against the United States widely
                conveyed by the angel Gabriel, are recorded in the Qur'an. Muslims believe that
                from Abraham through Jesus, complete God's message to humanity. The Hadith, which
                recount Mohammed's sayings and deeds as recorded by his contemporaries, are another
                the Qur'an and the Hadith. Islam is divided into two main branches, Sunni and Shia.
                for the Muslim community, or Ummah, arose. Initially, his successors could be drawn
                from the Prophet's contemporaries, but with time, this was no longer possible. Those
                the Prophet; those who became the Sunni argued that lineal descent was not required
                the Sunni became (and remain) the majority sect. (The Shia are dominant in Iran.)
                institution that continued until 1924, first under Arab and eventually under Ottoman
                Turkish control. Many Muslims look back at the century after the revelations to the
                Prophet Mohammed as a golden age. Its memory is strongest among the Arabs. What
                East, North Africa, and even into Europe within less than a century- seemed, and
                seems, miraculous.
            
            Nostalgia for Islam's past glory remains a powerful force.
                faith. This does not necessarily translate into a desire for clerical rule and the
                uncomfortable with distinctions between religion and state, though Muslim rulers
                throughout history have readily separated the two.
                legislation, only prove these rulers to be false Muslims usurping God's authority
            
            Denouncing waywardness among the faithful, some clerics have appealed for a return to
                fourteenth century from whom Bin Ladin selectively quotes, Ibn Taimiyyah, condemned
                both corrupt rulers and the clerics who failed to criticize them. He urged Muslims
                to read the Qur'an and the Hadith for themselves, not to depend solely on learned
                their observance.
            
                leaving Islam vulnerable to encroaching foreign powers eager to steal their land,
                wealth, and even their souls.
            
                attempting to overthrow the government, Qutb mixed Islamic scholarship with a very
                superficial acquaintance with Western history and thought. Sent by the Egyptian
                government to study in the United States in the late 1940s, Qutb returned with an
                as entirely material, arguing that Western society possesses "nothing that will
                satisfy its own conscience and justify its existence."
            
            Three basic themes emerge from Qutb's writings. First, he claimed that the world was
                beset with barbarism, licentiousness, and unbelief (a condition he called jahiliyya,
                Prophet Mohammed). Qutb argued that humans can choose only between Islam and
                jahiliyya. Second, he warned that more people, including Muslims, were attracted to
                therefore triumph over Islam. Third, no middle ground exists in what Qutb conceived
                as a struggle between God and Satan. All Muslims-as he defined them-therefore must
                take up arms in this fight. Any Muslim who rejects his ideas is just one more
            
            Bin Ladin shares Qutb's stark view, permitting him and his followers to rationalize
                Americans have wondered, "Why do 'they' hate us?" Some also ask, "What can we do to
                stop these attacks?"
            Bin Ladin and al Qaeda have given answers to both these questions. To the first, they
                say that America had attacked Islam; America is responsible for all conflicts
                involving Muslims. Thus Americans are blamed when Israelis fight with Palestinians,
                when Russians fight with Chechens, when Indians fight with Kashmiri Muslims, and
                when the Philippine government fights ethnic Muslims in its southern islands.
                al Qaeda as "your agents." Bin Ladin has stated flatly,"Our fight against these
                governments is not separate from our fight against you."
                support for their countries' repressive rulers.
            Bin Ladin's grievance with the United States may have started in reaction to specific
                U.S. policies but it quickly became far deeper. To the second question, what America
                could do, al Qaeda's answer was that America should abandon the Middle East, convert
                saddening to tell you that you are the worst civilization witnessed by the history
                Islamic nation, a nation that al Qaeda's leaders said "desires death more than you
                desire life."
            
            History and Political Context Few fundamentalist movements in the Islamic world
                gained lasting political power. In the nineteenth and twentieth centuries,
                fundamentalists helped articulate anticolonial grievances but played little role in
                the overwhelmingly secular struggles for independence after World War I.
                and clerical influence and traditional culture were seen as obstacles to national
                progress. After gaining independence from Western powers following World War II, the
                indifference, cynicism, and despair. In several countries, a dynastic state already
                existed or was quickly established under a paramount tribal family. Monarchies in
                countries such as Saudi Arabia, Morocco, and Jordan still survive today. Those in
                Egypt, Libya, Iraq, and Yemen were eventually overthrown by secular nationalist
                revolutionaries.
                (such as those promoted by Egyptian President Gamal Abdel Nasser's Arab Socialism or
                However, what emerged were almost invariably autocratic regimes that were usually
                unwilling to tolerate any opposition-even in countries, such as Egypt, that had a
                parliamentary tradition. Over time, their policies- repression, rewards, emigration,
                shaped by the desire to cling to power.
                for peaceful opposition, forcing their critics to choose silence, exile, or violent
                opposition. Iran's 1979 revolution swept a Shia theocracy into power. Its success
                encouraged Sunni fundamentalists elsewhere. In the 1980s, awash in sudden oil
                wealth, Saudi Arabia competed with Shia Iran to promote its Sunni fundamentalist
                the Kingdom and other states bordering the Persian Gulf in donating money to build
                Islamic doctrine. In this competition for legitimacy, secular regimes had no
                Emboldened rather than satisfied, the Islamists continued to push for power-a trend
                especially clear in Egypt. Confronted with a violent Islamist movement that killed
                education and society.
            These experiments in political Islam faltered during the 1990s: the Iranian
                revolution lost momentum, prestige, and public support, and Pakistan's rulers found
                revival movements gained followers across the Muslim world, but failed to secure
                political power except in Iran and Sudan. In Algeria, where in 1991 Islamists seemed
                almost certain to win power through the ballot box, the military preempted their
                rulers have few, if any, ways to participate in the existing political system. They
                are thus a ready audience for calls to Muslims to purify their society, reject
                unwelcome modernization, and adhere strictly to the Sharia. Social and Economic
                funded huge infrastructure projects, vastly expanded education, and created
                subsidized social welfare programs. These programs established a widespread feeling
                development projects, and population growth made these entitlement programs
                unsustainable. The resulting cutbacks created enormous resentment among recipients
                who had come to see government largesse as their right. This resentment was further
            Unlike the oil states (or Afghanistan, where real economic development has barely
                begun), the other Arab nations and Pakistan once had seemed headed toward balanced
                modernization. The established commercial, financial, and industrial sectors in
                and opaque bureaucracies slowly stifled growth. More importantly, these
                state-centered regimes placed their highest priority on preserving the elite's grip
                on national wealth. Unwilling to foster dynamic economies that could create jobs
                attractive to educated young men, the countries became economically stagnant and
                countries have not only seriously limited individual opportunity but also crippled
                overall economic productivity.
            
                common problem throughout the Muslim world: a large, steadily increasing population
                enormous number trained only in religious schools, lacked the skills needed by their
                societies. Far more acquired valuable skills but lived in stagnant economies that
                could not generate satisfying jobs. Millions, pursuing secular as well as religious
                education reflected a strong cultural preference for technical fields over the
                abroad, lacked the perspective and skills needed to understand a different culture.
            Frustrated in their search for a decent living, unable to benefit from an education
            Bin Ladin's Historical Opportunity Most Muslims prefer a peaceful and inclusive
                Ladin's followers are commonly nicknamed takfiri, or "those who define other Muslims
                they disagree. Beyond the theology lies the simple human fact that most Muslims,
                like most other human beings, are repelled by mass murder and barbarism whatever
                their justification.
                President Bush observed." Islam is a faith that brings comfort to a billion people
                It's a faith based upon love, not hate." Yet as
                political, social, and economic problems created flammable societies, Bin Ladin used
                Islam's most extreme, fundamentalist traditions as his match. All these
                elements-including religion-combined in an explosive compound.
                West and to America. He could present himself and his allies as victorious warriors
                in the one great successful experience for Islamic militancy in the 1980s: the
                Afghan jihad against the Soviet occupation.
            By 1998, Bin Ladin had a distinctive appeal, as he focused on attacking America. He
                argued that other extremists, who aimed at local rulers or Israel, did not go far
            
            Finally, Bin Ladin had another advantage: a substantial, worldwide organization. By
                organization for nearly ten years. He could attract, train, and use recruits for
                ever more ambitious attacks, rallying new adherents with each demonstration that his
            THE RISE OF BIN LADIN AND AL QAEDA (1988-1992)
                rallying point and training field. A Communist government in Afghanistan gained
                Soviet government sent in military units to ensure that the country would remain
                securely under Moscow's influence. The response was an Afghan national resistance
                movement that defeated Soviet forces.
            
            Young Muslims from around the world flocked to Afghanistan to join as volunteers in
                what was seen as a "holy war"-jihad-against an invader. The largest numbers came
                from the Middle East. Some were Saudis, and among them was Usama Bin Ladin.
                appeared to be ungainly but was in fact quite athletic, skilled as a horseman,
                runner, climber, and soccer player. He had attended Abdul Aziz University in Saudi
                Arabia. By some accounts, he had been interested there in religious studies,
                family's huge fortune. Though he took part in at least one actual battle, he became
                known chiefly as a person who generously helped fund the anti-Soviet jihad.
            
                increasingly complex, almost worldwide organization. This organization included a
                financial support network that came to be known as the "Golden Chain," put together
                mainly by financiers in Saudi Arabia and the Persian Gulf states. Donations flowed
                through charities or other nongovernmental organizations (NGOs). Bin Ladin and the
                "Afghan Arabs" drew largely on funds raised by this network, whose agents roamed
                world markets to buy arms and supplies for the mujahideen, or "holy warriors."
            
                the world, including the United States. Some were set up by Islamic extremists or
                their financial backers. Bin Ladin had an important part in this activity. He and
                or MAK), which channeled recruits into Afghanistan.
            
            The international environment for Bin Ladin's efforts was ideal. Saudi Arabia and the
                groups in Afghanistan fighting the Soviet occupation. This assistance was funneled
                through Pakistan: the Pakistani military intelligence service (Inter- Services
                Intelligence Directorate, or ISID), helped train the rebels and distribute the arms.
                they received little or no assistance from the United States.
            
            April 1988 brought victory for the Afghan jihad. Moscow declared it would pull its
                their withdrawal, the jihad's leaders debated what to do next. Bin Ladin and Azzam
                agreed that the organization successfully created for Afghanistan should not be
                allowed to dissolve. They established what they called a base or foundation (al
                Qaeda) as a potential general headquarters for future jihad.
            
            Though Azzam had been considered number one in the MAK, by August 1988 Bin Ladin was
                operating arms an intelligence component, a military committee, a financial
                    circle.
            
                self-confidence and ambition. He soon made clear his desire for unchallenged control
                and for preparing the mujahideen to fight anywhere in the world. Azzam, by contrast,
                favored continuing to fight in Afghanistan until it had a true Islamist government.
                And, as a Palestinian, he saw Israel as the top priority for the next stage.
            
            Whether the dispute was about power, personal differences, or strategy, it ended on
                sons. The killers were assumed to be rival Egyptians. The outcome left Bin Ladin
            
                Saudi educational system, Islamists already had a strong intellectual influence on
                Bin Ladin and his al Qaeda colleagues. By the late 1980s, the Egyptian Islamist
                movement-badly battered in the government crackdown following President Sadat's
                assassination-was centered in two major organizations: the Islamic Group and the
                Egyptian Islamic Jihad. A spiritual guide for both, but especially the Islamic
                Group, was the so-called Blind Sheikh, Omar Abdel Rahman. His preaching had inspired
                1980s, Abdel Rahman found refuge in the United States. From his headquarters in
            
            The most important Egyptian in Bin Ladin's circle was a surgeon, Ayman al Zawahiri,
                important members in the new organization, and his own close ties with Bin Ladin led
                Ladin's deputy some years later, when they merged their organizations.
            
                Islamic extremists that a Sudanese political leader, Hassan al Turabi, urged him to
                transplant his whole organization to Sudan. Turabi headed the National Islamic Front
                in a coalition that had recently seized power in Khartoum.
            
            Bin Ladin agreed to help Turabi in an ongoing war against African Christian
                separatists in southern Sudan and also to do some road building. Turabi in return
                would let Bin Ladin use Sudan as a base for worldwide business operations and for
                preparations for jihad.
            
                August 1990, Iraq invaded Kuwait. Bin Ladin, whose efforts in Afghanistan had earned
                him celebrity and respect, proposed to the Saudi monarchy that he summon mujahideen
                for a jihad to retake Kuwait. He was rebuffed, and the Saudis joined the U.S.-led
                coalition. After the Saudis agreed to allow U.S. armed forces to be based in the
                arrangement. The Saudi government exiled the clerics and undertook to silence Bin
                Ladin by, among other things, taking away his passport. With help from a dissident
                government would freeze his financial assets and revoke his citizenship.
            
            He no longer had a country he could call his own.
                business and terrorist enterprises. In time, the former would encompass numerous
                Fulfilling his bargain with Turabi, Bin Ladin used his construction company to build
                a new highway from Khartoum to Port Sudan on the Red Sea coast. Meanwhile, al Qaeda
                to acquire weapons, explosives, and technical equipment for terrorist purposes. One
                investment company to carry out procurement trips from western Europe to the Far
                East. Two others, Wadi al Hage and Mubarak Douri, who had become acquainted in
                Tucson, Arizona, in the late 1980s, went as far afield as China, Malaysia, the
            
                for terrorist activities. The network included a major business enterprise in
                Foundation in Sarajevo, which supported the Bosnian Muslims in their conflict with
                Serbia and Croatia; and an NGO in Baku, Azerbaijan, that was employed as well by
                Egyptian Islamic Jihad both as a source and conduit for finances and as a support
                already-established Third World Relief Agency (TWRA) headquartered in Vienna, whose
                in Nairobi as a cover for operatives there.)
            
                confederation. In Sudan, he established an "Islamic Army Shura" that was to serve as
                building this Islamic army, he enlisted groups from Saudi Arabia, Egypt, Jordan,
                Lebanon, Iraq, Oman, Algeria, Libya, Tunisia, Morocco, Somalia, and Eritrea. Al
                Qaeda also established cooperative but less formal relationships with other
                Malaysia, and Indonesia. Bin Ladin maintained connections in the Bosnian conflict as
                    well.
            
            The groundwork for a true global terrorist network was being laid.
            Bin Ladin also provided equipment and training assistance to the Moro Islamic
                Liberation Front in the Philippines and also to a newly forming Philippine group
                    commanders.
            
            Al Qaeda helped Jemaah Islamiya (JI), a nascent organization headed by Indonesian
                Islamists with cells scattered across Malaysia, Singapore, Indonesia, and the
                Philippines. It also aided a Pakistani group engaged in insurrectionist attacks in
                Afghanistan border to assist the Tajikistan Islamists in the ethnic conflicts that
                became independent states.
            
                which was in the Farouq mosque in Brooklyn. In the mid- 1980s, it had been set up as
            
                and Tucson.
            
                participate in terrorist actions in the United States in the early 1990s and in al
                Qaeda operations elsewhere, including the 1998 attacks on U.S. embassies in East
                Africa.
            BUILDING AN ORGANIZATION, DECLARING WAR ON THE UNITED STATES
                (1992-1996)
            Bin Ladin began delivering diatribes against the United States before he left Saudi
                Arabia. He continued to do so after he arrived in Sudan. In early 1992, the al Qaeda
                Islamic lands. Specifically singling out U.S. forces for attack, the language
                resembled that which would appear in Bin Ladin's public fatwa in August 1996. In
            
            By this time, Bin Ladin was well-known and a senior figure among Islamist extremists,
                especially those in Egypt, the Arabian Peninsula, and the Afghanistan-Pakistan
                Bin Ladin's close comrades were more peers than subordinates. For example, Usama
                Asmurai, also known as Wali Khan, worked with Bin Ladin in the early 1980s and
                helped him in the Philippines and in Tajikistan. The Egyptian spiritual guide based
                in New Jersey, the Blind Sheikh, whom Bin Ladin admired, was also in the network.
                power and Abu Zubaydah, who helped operate a popular terrorist training camp near
                the border with Pakistan. There were also rootless but experienced operatives, such
                as Ramzi Yousef and Khalid Sheikh Mohammed, who-though not necessarily formal
                in projects that were supported by or linked to Bin Ladin, the Blind Sheikh, or
                their associates.
            
                connections. And in this network, Bin Ladin's agenda stood out. While his allied
                Islamist groups were focused on local battles, such as those in Egypt, Algeria,
                Bosnia, or Chechnya, Bin Ladin concentrated on attacking the "far enemy"-the United
                States.
            Attacks Known and Suspected
            After U.S. troops deployed to Somalia in late 1992, al Qaeda leaders formulated a
                fatwa demanding their eviction. In December, bombs exploded at two hotels in Aden
                where U.S. troops routinely stopped en route to Somalia, killing two, but no
                Americans. The perpetrators are reported to have belonged to a group from southern
                had trained at an al Qaeda camp in Sudan.
            
            Al Qaeda leaders set up a Nairobi cell and used it to send weapons and trainers to
                the Somali warlords battling U.S. forces, an operation directly supervised by al
                Qaeda's military leader.
            
                trainers were later heard boasting that their assistance led to the October 1993
            
            In November 1995, a car bomb exploded outside a Saudi-U.S. joint facility in Riyadh
                were killed. The Saudi government arrested four perpetrators, who admitted being
                inspired by Bin Ladin. They were promptly executed. Though nothing proves that Bin
                Ladin ordered this attack, U.S. intelligence subsequently learned that al Qaeda
                leaders had decided a year earlier to attack a U.S. target in Saudi Arabia, and had
                later took credit.
            
            In June 1996, an enormous truck bomb detonated in the Khobar Towers residential
                complex in Dhahran, Saudi Arabia, that housed U.S. Air Force personnel. Nineteen
                Americans were killed, and 372 were wounded. The operation was carried out
                principally, perhaps exclusively, by Saudi Hezbollah, an organization that had
                involvement is strong, there are also signs that al Qaeda played some role, as yet
                    unknown.
            
            In this period, other prominent attacks in which Bin Ladin's involvement is at best
                destroy landmarks in New York, and the 1995 Manila air plot to blow up a dozen U.S.
                airliners over the Pacific. Details on these plots appear in chapter 3.
            Another scheme revealed that Bin Ladin sought the capability to kill on a mass scale.
                set the price at $1.5 million, which did not deter Bin Ladin. Al Qaeda
                representatives asked to inspect the uranium and were shown a cylinder about 3 feet
                long, and one thought he could pronounce it genuine. Al Qaeda apparently purchased
                the cylinder, then discovered it to be bogus.
            
            But while the effort failed, it shows what Bin Ladin and his associates hoped to do.
                people with uranium."
            
            Bin Ladin seemed willing to include in the confederation terrorists from almost every
                violent Islamist extremists came from all the groups represented in Bin Ladin's
                Islamic Army Shura. Representatives also came from organizations such as the
                Palestine Liberation Organization, Hamas, and Hezbollah.
            
            Turabi sought to persuade Shiites and Sunnis to put aside their divisions and join
                against the common enemy. In late 1991 or 1992, discussions in Sudan between al
                Qaeda and Iranian operatives led to an informal agreement to cooperate in providing
                support-even if only training-for actions carried out primarily against Israel and
                the United States. Not long afterward, senior al Qaeda operatives and trainers
                such delegation went to the Bekaa Valley in Lebanon for further training in
                explosives as well as in intelligence and security. Bin Ladin reportedly showed
                particular interest in learning how to use truck bombs such as the one that had
                killed 241 U.S. Marines in Lebanon in 1983. The relationship between al Qaeda and
                Iran demonstrated that Sunni-Shia divisions did not necessarily pose an
                insurmountable barrier to cooperation in terrorist operations. As will be described
                in chapter 7, al Qaeda contacts with Iran continued in ensuing years.
            
            Bin Ladin was also willing to explore possibilities for cooperation with Iraq, even
                though Iraq's dictator, Saddam Hussein, had never had an Islamist agenda-save for
                Islamists in Iraqi Kurdistan, and sought to attract them into his Islamic army.
            
            To protect his own ties with Iraq, Turabi reportedly brokered an agreement that Bin
                Ladin would stop supporting activities against Saddam. Bin Ladin apparently honored
                the late 1990s, these extremist groups suffered major defeats by Kurdish forces. In
                2001, with Bin Ladin's help they re-formed into an organization called Ansar al
                Islam. There are indications that by then the Iraqi regime tolerated and may even
                have helped Ansar al Islam against the common Kurdish enemy.
            
            With the Sudanese regime acting as intermediary, Bin Ladin himself met with a senior
                to have asked for space to establish training camps, as well as assistance in
                procuring weapons, but there is no evidence that Iraq responded to this
                    request.
            
            As described below, the ensuing years saw additional efforts to establish
                connections.
            Sudan Becomes a Doubtful Haven
                large part because Bin Ladin lost his base in Sudan. Ever since the Islamist regime
                came to power in Khartoum, the United States and other Western governments had
                pressed it to stop providing a haven for terrorist organizations. Other governments
                Sudanese regime began to change. Though Turabi had been its inspirational leader,
                General Omar al Bashir, president since 1989, had never been entirely under his
                thumb. Thus as outside pressures mounted, Bashir's supporters began to displace
                1995 appears to have been a tipping point. The would-be killers, who came from the
                Egyptian Islamic Group, had been sheltered in Sudan and helped by Bin Ladin.
            
            When the Sudanese refused to hand over three individuals identified as involved in
                the assassination plot, the UN Security Council passed a resolution criticizing
                their inaction and eventually sanctioned Khartoum in April 1996.
            
            A clear signal to Bin Ladin that his days in Sudan were numbered came when the
                government advised him that it intended to yield to Libya's demands to stop giving
                Islamic army that he could no longer protect them and that they had to leave the
                renounced all connections with him.
            
            Bin Ladin also began to have serious money problems. International pressure on Sudan,
                also probably took some toll. In any case, Bin Ladin found it necessary both to cut
                back his spending and to control his outlays more closely. He appointed a new
                financial manager, whom his followers saw as miserly.
            
            Money problems proved costly to Bin Ladin in other ways. Jamal Ahmed al Fadl, a
                Sudanese-born Arab, had spent time in the United States and had been recruited for
                the Afghan war through the Farouq mosque in Brooklyn. He had joined al Qaeda and
                Bin Ladin discovered that Fadl had skimmed about $110,000, and he asked for
                Egyptians in al Qaeda were given $1,200 a month. He defected and became a star
                informant for the United States. Also testifying about al Qaeda in a U.S. court was
                    section.
            
                Ladin expelled from Sudan. They had already revoked his citizenship, however, and
                would not tolerate his presence in their country. And Bin Ladin may have no longer
                felt safe in Sudan, where he had already escaped at least one assassination attempt
                any case, on May 19, 1996, Bin Ladin left Sudan-significantly weakened, despite his
                ambitions and organizational skills. He returned to Afghanistan.
            
            AL QAEDA'S RENEWAL IN AFGHANISTAN (1996-1998)
            Bin Ladin flew on a leased aircraft from Khartoum to Jalalabad, with a refueling
                stopover in the United Arab Emirates.
            
            He was accompanied by family members and bodyguards, as well as by al Qaeda members
                who had been close associates since his organization's 1988 founding in Afghanistan.
            
            Though Bin Ladin's destination was Afghanistan, Pakistan was the nation that held the
                key to his ability to use Afghanistan as a base from which to revive his ambitious
                enterprise for war against the United States.
                derived from Islam, but its politics had been decidedly secular. The army was-and
                remains-the country's strongest and most respected institution, and the army had
                been and continues to be preoccupied with its rivalry with India, especially over
            From the 1970s onward, religion had become an increasingly powerful force in
                Pakistani politics. After a coup in 1977, military leaders turned to Islamist groups
                for support, and fundamentalists became more prominent. South Asia had an indigenous
            
                institutions. Moreover, the fighting in Afghanistan made Pakistan home to an
                strained Pakistani education system could not accommodate the refugees, the
                government increasingly let privately funded religious schools serve as a cost-free
                men with no marketable skills but with deeply held Islamic views.
            
                potential trouble at home but potentially useful abroad. Those who joined the
                order in chaotic Afghanistan and make it a cooperative ally. They thus might give
            
            It is unlikely that Bin Ladin could have returned to Afghanistan had Pakistan
                disapproved. The Pakistani military intelligence service probably had advance
                his entire time in Sudan, he had maintained guesthouses and training camps in
                organizations for recruiting and training fighters for Islamic insurgencies in such
                available for training Kashmiri militants.
            
            Yet Bin Ladin was in his weakest position since his early days in the war against the
                everything Bin Ladin had possessed there.
            
                had accompanied Bin Ladin to Afghanistan, Banshiri had remained in Kenya to oversee
                died in a ferryboat accident on Lake Victoria just a few days after Bin Ladin
                arrived in Jalalabad, leaving Bin Ladin with a need to replace him not only in the
                    Africa.
            
            He had to make other adjustments as well, for some al Qaeda members viewed Bin
                maintained collaborative relationships with al Qaeda, but many disengaged
                    entirely.
            
            For a time, it may not have been clear to Bin Ladin that the Taliban would be his
                country, but key centers, including Kabul, were still held by rival warlords. Bin
                Ladin went initially to Jalalabad, probably because it was in an area controlled by
                factions. Bin Ladin apparently kept his options open, maintaining contacts with
                most militant opponents. But after September 1996, when first Jalalabad and then
                Kabul fell to the Taliban, Bin Ladin cemented his ties with them.
            
            That process did not always go smoothly. Bin Ladin, no longer constrained by the
                Sudanese, clearly thought that he had new freedom to publish his appeals for jihad.
                At about the time when the Taliban were making their final drive toward Jalalabad
                and Kabul, Bin Ladin issued his August 1996 fatwa, saying that "We . . . have been
                Allah, a safe base here is now available in the high Hindu Kush mountains in
                Khurasan." But theTaliban, like the Sudanese, would eventually hear warnings,
                including from the Saudi monarchy.
            
            Though Bin Ladin had promised Taliban leaders that he would be circumspect, he broke
                this promise almost immediately, giving an inflammatory interview to CNN in March
                1997. The Taliban leader Mullah Omar promptly "invited" Bin Ladin to move to
                situate him where he might be easier to control.
            
                significant response. According to one report, Saddam Hussein's efforts at this time
                to rebuild relations with the Saudis and other Middle Eastern regimes led him to
            
            In mid-1998, the situation reversed; it was Iraq that reportedly took the initiative.
                In March 1998, after Bin Ladin's public fatwa against the United States, two al
                Qaeda members reportedly went to Iraq to meet with Iraqi intelligence. In July, an
                Iraqi delegation traveled to Afghanistan to meet first with the Taliban and then
                his own to the Iraqis. In 1998, Iraq was under intensifying U.S. pressure, which
            
                declined, apparently judging that his circumstances in Afghanistan remained more
                favorable than the Iraqi alternative. The reports describe friendly contacts and
                we have seen no evidence that these or the earlier contacts ever developed into a
                collaborative operational relationship. Nor have we seen evidence indicating that
                Iraq cooperated with al Qaeda in developing or carrying out any attacks against the
                United States.
            
            Bin Ladin eventually enjoyed a strong financial position in Afghanistan, thanks to
                Saudi and other financiers associated with the Golden Chain. Through his
                relationship with Mullah Omar-and the monetary and other benefits that it brought
                the Taliban-Bin Ladin was able to circumvent restrictions; Mullah Omar would stand
                by him even when otherTaliban leaders raised objections. Bin Ladin appeared to have
                could travel freely within the country, enter and exit it without visas or any
                immigration procedures, purchase and import vehicles and weapons, and enjoy the use
                state-owned Ariana Airlines to courier money into the country.
            
            The Taliban seemed to open the doors to all who wanted to come to Afghanistan to
                train in the camps. The alliance with theTaliban provided al Qaeda a sanctuary in
                which to train and indoctrinate fighters and terrorists, import weapons, forge ties
                with other jihad groups and leaders, and plot and staff terrorist schemes. While Bin
                Ladin maintained his own al Qaeda guesthouses and camps for vetting and training
                underwent instruction in Bin Ladin-supported camps in Afghanistan from 1996 through
                9/11 at 10,000 to 20,000.
            
                guesthouses and camps provided a mechanism by which al Qaeda could screen and vet
                candidates for induction into its own organization. Thousands flowed through the
                camps, but no more than a few hundred seem to have become al Qaeda members. From the
                "worthy" candidates.
            
            Al Qaeda continued meanwhile to collaborate closely with the many Middle Eastern
                groups-in Egypt, Algeria, Yemen, Lebanon, Morocco, Tunisia, Somalia, and
                elsewhere-with which it had been linked when Bin Ladin was in Sudan. It also
                Caucasus. Bin Ladin bolstered his links to extremists in South and Southeast Asia,
                including the Malaysian-Indonesian JI and several Pakistani groups engaged in the
                Kashmir conflict.
            
                world. And he had strengthened the internal ties in his own organization.
                positions, tasks, and salaries. Most but not all in this core swore fealty (or
                bayat) to Bin Ladin. Other operatives were committed to Bin Ladin or to his goals
                and would take assignments for him, but they did not swear bayat and maintained, or
                al Qaeda or train in its camps but remained essentially independent. Nevertheless,
                they constituted a potential resource for al Qaeda.
            
            Now effectively merged with Zawahiri's Egyptian Islamic Jihad, al Qaeda promised to become the general headquarters for international
                terrorism, without the need for the Islamic Army Shura. Bin Ladin was prepared to
                snake." Al Qaeda's role in organizing terrorist operations had also changed. Before
                the move to Afghanistan, it had concentrated on providing funds, training, and
                his chief aides.
                begun casing targets in Nairobi for future attacks. It was led by Ali Mohamed, a
                enlisted in the U.S. Army, and became an instructor at Fort Bragg. He had provided
                guidance and training to extremists at the Farouq mosque in Brooklyn, including some
                who were subsequently convicted in the February 1993 attack on the World Trade
                Center. The casing team also included a computer expert whose write-ups were
                reviewed by al Qaeda leaders.
            
            The team set up a makeshift laboratory for developing their surveillance photographs
                in an apartment in Nairobi where the various al Qaeda operatives and leaders based
                in or traveling to the Kenya cell sometimes met. Banshiri, al Qaeda's military
                he was constantly on the move, Bin Ladin had dispatched another operative, Khaled al
                Fawwaz, to serve as the on-site manager. The technical surveillance and
                communications equipment employed for these casing missions included
                casing team also reconnoitered targets in Djibouti.
            
            As early as January 1994, Bin Ladin received the surveillance reports, complete with
                diagrams prepared by the team's computer specialist. He, his top military committee
                members-Banshiri and his deputy, Abu Hafs al Masri (also known as Mohammed Atef)-and
                embassy in Nairobi was an easy target because a car bomb could be parked close by,
                they began to form a plan. Al Qaeda had begun developing the tactical expertise for
                members and several operatives who were involved with the Kenya cell among them-were
                sent to Hezbollah training camps in Lebanon.
            
                the relatively long delay before the attack was actually carried out. The
                difficulties Bin Ladin began to encounter in Sudan in 1995, his move to Afghanistan
                in 1996, and the months spent establishing ties with the Taliban may also have
                played a role, as did Banshiri's accidental drowning. In August 1997, the Kenya cell
                panicked. The London Daily Telegraph reported that Madani al Tayyib, formerly head
                The article said (incorrectly) that the Saudis were sharing Tayyib's information
                with the U.S. and British authorities.
            
            At almost the same time, cell members learned that U.S. and Kenyan agents had
                in Nairobi, and that Hage's telephone was being tapped. Hage was a U.S.citizen who
                had worked with Bin Ladin in Afghanistan in the 1980s, and in 1992 he went to Sudan
                manager was taken over by Harun Fazul, a Kenyan citizen who had been in Bin Ladin's
                advance team to Sudan back in 1990. Harun faxed a report on the "security situation"
                to several sites, warning that "the crew members in East Africa is [sic] in grave
                carried out the operations to hit Americans in Somalia." The report provided
                instructions for avoiding further exposure.
            
            On February 23, 1998, Bin Ladin issued his public fatwa. The language had been in
                organization and Zawahiri's Egyptian Islamic Jihad. Less than a month after the
                instructions indicate that the decision to launch the attacks had been made by the
                time the fatwa was issued.
            
            The next four months were spent setting up the teams in Nairobi and Dar es Salaam.
                transport vehicles. At least one additional explosives expert was brought in to
                assist in putting the weapons together. In Nairobi, a hotel room was rented to put
                attack date.
            
            While this was taking place, Bin Ladin continued to push his public message. On May
                Afghanistan. A week later, it appeared in Al Quds al Arabi, the same Arabic-language
                newspaper in London that had first published Bin Ladin's February fatwa, and it
                that, Bin Ladin gave a videotaped interview to ABC News with the same slogans,
                adding that "we do not differentiate between those dressed in military uniforms and
                civilians; they are all targets in this fatwa."
            
                departed from East Africa. The remaining operatives prepared and assembled the
                bombs, and acquired the delivery vehicles. On August 4, they made one last casing
                teams and one or two persons assigned to remove the evidence trail had left East
                Africa. Back in Afghanistan, Bin Ladin and the al Qaeda leadership had left Kandahar
                for the countryside, expecting U.S. retaliation. Declarations taking credit for the
                in Baku, with instructions to stand by for orders to "instantly" transmit them to Al
            
                five minutes apart-about 10:35 A.M. in Nairobi and 10:39 A.M. in Dar es Salaam.
                Shortly afterward, a phone call was placed from Baku to London. The previously
                prepared messages were then faxed to London.
            
            The attack on the U.S. embassy in Nairobi destroyed the embassy and killed 12
                Americans and 201 others, almost all Kenyans. About 5,000 people were injured. The
                that "when it becomes apparent that it would be impossible to repel these Americans
                permissible under Islam." Asked if he had indeed masterminded these bombings, Bin
                Ladin said that the World Islamic Front for jihad against "Jews and Crusaders" had
                issued a "crystal clear" fatwa. If the instigation for jihad against the Jews and
                the Americans to liberate the holy places "is considered a crime,"he said,"let
                history be a witness that I am a criminal."
```

```
Nathans-MBP:911report nathantruong$ grep -v "the" chapter-5.txt

    
        
            AL QAEDA AIMS AT THE AMERICAN HOMELAND
            TERRORIST ENTREPRENEURS
                Ladin and his chief of operations, Abu Hafs al Masri, also known as Mohammed Atef,
                occupied undisputed leadership positions atop al Qaeda's organizational structure.
                Within this structure, al Qaeda's worldwide terrorist operations relied heavily on
                subordinate commanders: Khalid Sheikh Mohammed (KSM), Riduan Isamuddin (better known
            
            Highly educated and equally comfortable in a government office or a terrorist
                safehouse, KSM applied his imagination, technical aptitude, and managerial skills to
                hatching and planning an extraordinary array of terrorist schemes. These ideas
                included conventional car bombing, political assassination, aircraft bombing,
                guided by suicide operatives.
            Like his nephew Ramzi Yousef (three years KSM's junior), KSM grew up in Kuwait but
                1983, following his graduation from secondary school, KSM left Kuwait to enroll at
                Chowan College, a small Baptist school in Murfreesboro, North Carolina. After a
                semester at Chowan, KSM transferred to North Carolina Agricultural and Technical
                future al Qaeda member. KSM earned a degree in mechanical engineering in December
                    1986.
            
            Although he apparently did not attract attention for extreme Islamist beliefs or
                Union Party). Sayyaf became KSM's mentor and provided KSM with military training at
                for three months before being summoned to perform administrative duties for Abdullah
                communications needs of Afghan groups, where he learned about drills used to
                excavate caves in Afghanistan.
            
            Between 1988 and 1992, KSM helped run a nongovernmental organization (NGO) in
                Peshawar and Jalalabad; sponsored by Sayyaf, it was designed to aid young Afghan
                and supporting that effort with financial donations. After returning briefly to
                Islamic affairs of Qatar, Sheikh Abdallah bin Khalid bin Hamad al Thani. KSM took a
                Water. Although he engaged in extensive international travel during his tenure at
                    authorities.
            
                had numerous telephone conversations during which Yousef discussed his progress and
                bank account of Yousef 's co-conspirator, Mohammed Salameh. KSM does not appear to
                have contributed any more substantially to this operation.
            
                and timers. They also cased target flights to Hong Kong and Seoul that would have
                developed plans to assassinate President Clinton during his November 1994 trip to
                Manila, and to bomb U.S.-bound cargo carriers by smuggling jackets containing
                nitrocellulose on board.
            
                Manila; but by that time, KSM was safely back at his government job in Qatar. Yousef
                Islamabad by Pakistani authorities on February 7, 1995, after an accomplice turned
                him in.
            
                connects him to terrorist activities in those locations. While in Sudan, he
                reportedly failed in his attempt to meet with Bin Ladin. But KSM did see Atef, who
                gave him a contact in Brazil. In January 1996, well aware that U.S. authorities were
                chasing him, he left Qatar for good and fled to Afghanistan, where he renewed his
                relationship with Rasul Sayyaf.
            
            Just as KSM was reestablishing himself in Afghanistan in mid-1996, Bin Ladin and his
                did not yet enjoy an especially close working relationship. Indeed, KSM has
                his nephew, Yousef.
            
                operation that would involve training pilots who would crash planes into buildings
            
                money, and logistical support that only an extensive and well-funded organization
            
                KSM's ideas without much comment, but did ask KSM formally to join al Qaeda and move
                his family to Afghanistan.
            
            After meeting with Bin Ladin, KSM says he journeyed onward to India, Indonesia, and
                Malaysia, where he met with Jemaah Islamiah's Hambali. Hambali was an Indonesian
                relocated by January 1997.
            
                Khattab in Chechnya. Unable to travel through Azerbaijan, KSM returned to Karachi
                KSM may not have been a member of al Qaeda at this time, he admits traveling
                visiting Bin Ladin and cultivating relationships with his lieutenants, Atef and Sayf
            
                States. He continued to make himself useful, collecting news articles and helping
                operation sometime in late 1998 or early 1999.
            
                retaining a last vestige of his cherished autonomy.
            
                sent al Qaeda operative Issa al Britani to Kuala Lumpur, Malaysia, to learn about
                9/11 operation first. Similarly, KSM's proposals to Atef around this same time for
                although Hambali's Jemaah Islamiah operatives did some casing of possible
                    targets.
            
                describe him as an intelligent, efficient, and even-tempered manager who approached
                his projects with a single-minded dedication that he expected his colleagues to
                share. Al Qaeda associate Abu Zubaydah has expressed more qualified admiration for
                that although KSM floated many general ideas for attacks, he rarely conceived a
                in any case, KSM was plainly a capable coordinator, having had years to hone his
                skills and build relationships.
            Hambali
                close relationship with Jemaah Islamiah (JI). In that relationship, Hambali became
                Islamist extremist teachings of various clerics, including one named Abdullah
                jihad by sending him to Afghanistan in 1986. After undergoing training at Rasul
                Soviets; he eventually returned to Malaysia after 18 months in Afghanistan. By 1998,
            
            Also by 1998, Sungkar and JI spiritual leader Abu Bakar Bashir had accepted Bin
                Ladin's offer to ally JI with al Qaeda in waging war against Christians and
                    Jews.
            
            Hambali met with KSM in Karachi to arrange for JI members to receive training in
                Afghanistan at al Qaeda's camps. In addition to his close working relationship with
                KSM, Hambali soon began dealing with Atef as well. Al Qaeda began funding JI's
                increasingly ambitious terrorist plans, which Atef and KSM sought to expand. Under
                provide bomb-making expertise, and deliver suicide operatives.
            
            The al Qaeda-JI partnership yielded a number of proposals that would marry al Qaeda's
                financial and technical strengths with JI's access to materials and local
                example, Atef turned to Hambali when al Qaeda needed a scientist to take over its
                biological weapons program. Hambali obliged by introducing a U.S.- educated JI
                member, Yazid Sufaat, to Ayman al Zawahiri in Kandahar. In 2001, Sufaat would spend
                several months attempting to cultivate anthrax for al Qaeda in a laboratory he
            
                but his involvement with al Qaeda appears to have inspired him to pursue American
                targets. KSM, in his post-capture interrogations, has taken credit for this shift,
            
                in a spate of terrorist plans. Fortunately, none came to fruition.
            In addition to staging actual terrorist attacks in partnership with al Qaeda, Hambali
                and JI assisted al Qaeda operatives passing through Kuala Lumpur. One important
                occasion was in December 1999-January 2000. Hambali accommodated KSM's requests to
                help several veterans whom KSM had just finished training in Karachi. They included
                and future 9/11 hijackers Nawaf al Hazmi and Khalid al Mihdhar. Hambali arranged
                assistance (including information on flight schools and help in acquiring ammonium
                nitrate) for Zacarias Moussaoui, an al Qaeda operative sent to Malaysia by Atef and
                    KSM.
            
            Hambali used Bin Ladin's Afghan facilities as a training ground for JI recruits.
                Though he had a close relationship with Atef and KSM, he maintained JI's
                institutional independence from al Qaeda. Hambali insists that he did not discuss
                operations with Bin Ladin or swear allegiance to him, having already given such a
                pledge of loyalty to Bashir, Sungkar's successor as JI leader. Thus, like any
                powerful bureaucrat defending his domain, Hambali objected when al Qaeda leadership
                tried to assign JI members to terrorist projects without notifying him.
            
            Abd al Rahim al Nashiri KSM and Hambali both decided to join forces with al Qaeda
                career as a terrorist by Bin Ladin himself.
                30 mujahideen in pursuit of jihad in Tajikistan in 1996. When serious fighting
                and refused. After several days of indoctrination that included a barrage of news
                clippings and television documentaries, Nashiri left Afghanistan, first returning to
            
            Nashiri returned to Afghanistan, probably in 1997, primarily to check on relatives
                period, Nashiri also led a plot to smuggle four Russian-made antitank missiles into
                Saudi Arabia from Yemen in early 1998 and helped an embassy bombing operative obtain
                a Yemeni passport.
            
            At some point, Nashiri joined al Qaeda. His cousin, Jihad Mohammad Ali al Makki, also
                between Yemen and Afghanistan. In late 1998, Nashiri proposed mounting an attack
                and send operatives to Yemen, and he later provided money.
            
            
            Nashiri's success brought him instant status within al Qaeda. He later was recognized
                projects, he retained discretion in selecting operatives and devising attacks. In
                because of security concerns.31Those concerns, it seems, were well placed, as
                as a terrorist.
            THE "PLANES OPERATION"
                    KSM.
            
                and explosives could be problematic, and that he needed to graduate to a more novel
                form of attack. He maintains that he and Yousef began thinking about using aircraft
            
            Certainly KSM was not alone in contemplating new kinds of terrorist operations. A
                study reportedly conducted by Atef, while he and Bin Ladin were still in Sudan,
                Bojinka concept. Such a study, if it actually existed, yields significant insight
                over Lockerbie, Scotland- a promising means to inflict massive casualties; and (3)
                    targets.
            
            KSM has insisted to his interrogators that he always contemplated hijacking and
                crashing large commercial aircraft. Indeed, KSM describes a grandiose original plan:
                a total of ten aircraft to be hijacked, nine of which would crash into targets on
                U.S. economy, this vision gives a better glimpse of his true ambitions. This is
                    superterrorist.
            
            KSM concedes that this proposal received a lukewarm response from al Qaeda leaders
                skeptical of its scale and complexity. Although Bin Ladin listened to KSM's
                proposal, he was not convinced that it was practical. As mentioned earlier, Bin
                Ladin was receiving numerous ideas for potential operations- KSM's proposal to
                attack U.S. targets with commercial airplanes was only one of many.
            
            KSM presents himself as an entrepreneur seeking venture capital and people. He simply
                retaining his independence. It is easy to question such a statement. Money is one
                thing; supplying a cadre of trained operatives willing to die is much more. Thus,
                although KSM contends he would have been just as likely to consider working with any
                thought could supply such exceptional commodities.
            
            KSM acknowledges formally joining al Qaeda, in late 1998 or 1999, and states that
                how Bin Ladin came to share his preoccupation with attacking America, Bin Ladin in
                in part because Atef himself is not available to describe it. He was killed in
                November 2001 by an American air strike in Afghanistan.
            
            Bin Ladin summoned KSM to Kandahar in March or April 1999 to tell him that al Qaeda
                "planes operation."
            
            The Plan Evolves
                selection of targets.
            
            Bin Ladin also soon selected four individuals to serve as suicide operatives: Khalid
                meetings, Bin Ladin told KSM that Mihdhar and Hazmi were so eager to participate in
                States for pilot training.
            
            
                expelled from Yemen because of his extremist views. Khallad had grown up in Saudi
                allegiance to Bin Ladin-whom he had first met as a child in Jeddah-and volunteered
                to become a suicide operative.
            
            When Khallad applied for a U.S. visa, however, his application was denied. Earlier in
                application. Khallad contacted this individual to help him get an appointment at a
                appointment, however, he was arrested by Yemeni authorities. The arrest resulted
            
                apparently concerned that Khallad might reveal Nashiri's operation while under
                interrogation, had contacted a Yemeni official to demand Khallad's release,
                Khallad returned to Afghanistan.
            
                both of whom were Yemenis, would not be able to obtain U.S. visas as easily as Saudi
                operatives like Mihdhar and Hazmi. Although Khallad had been unable to acquire a
                because individuals with Saudi passports could travel much more easily than Yemeni,
                two components.
            
                targets-would remain as planned, with Mihdhar and Hazmi playing key roles. The
                up planes, a refinement of KSM's old Manila air plot. The operatives would hijack
                U.S.-flagged commercial planes flying Pacific routes across East Asia and destroy
                alternate scenario apparently involved flying planes into U.S. targets in Japan,
                Thailand, South Korea, Hong Kong, or Malaysia, and using Yemenis who would not need
            
                training course at al Qaeda's Mes Aynak camp in Afghanistan. Bin Ladin personally
                destined for important operations. One example is Ibrahim al Thawar, or Nibras, who
            
            The Mes Aynak training camp was located in an abandoned Russian copper mine near
                full range of instruction, including an advanced commando course taught by senior al
                of trainees and said that no more than 20 could be handled at once, Bin Ladin
            
            The special training session at Mes Aynak was rigorous and spared no expense. The
                course focused on physical fitness, firearms, close quarters combat, shooting from a
            
                he collected Western aviation magazines; telephone directories for American cities
                such as San Diego and Long Beach, California; brochures for schools; and airline
                timetables, and he conducted Internet searches on U.S. flight schools. He also
                purchased flight simulator software and a few movies depicting hijackings. To house
                his students, KSM rented a safehouse in Karachi with money provided by Bin
                    Ladin.
            
                safehouse where, according to KSM, an Egyptian named Mohamed Atta simultaneously
                stayed on his way to Afghanistan for jihad training.
            
                never met with Mihdhar in 1999 but assumed that Bin Ladin and Atef had briefed
            
            The course in Karachi apparently lasted about one or two weeks. According to KSM, he
                communications, make travel reservations, and rent an apartment. Khallad adds that
                featured hijackings, and reading flight schedules to determine which flights would
                    countries.
            
            The four trainees traveled to Kuala Lumpur: Khallad, Abu Bara, and Hazmi came from
                Karachi; Mihdhar traveled from Yemen. As discussed in chapter 6, U.S. intelligence
            
                doctored Hazmi's Saudi passport so it would appear as if Hazmi had traveled to Kuala
                Lumpur from Saudi Arabia via Dubai. Khallad and Abu Bara went to Kuala Lumpur to
                study airport security and conduct casing flights. According to Khallad, he and Abu
                later after briefly returning to Afghanistan to attend to some passport issues.
            
                opportunity to case flights as well. According to Khallad, Malaysia was an ideal
                Gulf states to have a visa. Malaysian security was reputed to be lax when it came to
            
            
                Hong Kong aboard a U.S. airliner. He flew in first class, which he realized was a
                mistake because this seating assignment on that flight did not afford him a view of
            
            After completing his casing mission, Khallad returned to Kuala Lumpur. Hazmi arrived
                Abu Bara at Endolite. Mihdhar arrived on January 5, probably one day after Hazmi.
                who made his home available at Hambali's request. According to Khallad, he and Hazmi
            
            While in Kuala Lumpur, Khallad wanted to go to Singapore to meet Nibras and Fahd al
                earlier. Nibras and Quso were bringing Khallad money from Yemen, but were stopped in
                tourists to have passport stamps from a popular tourist destination such as
                return to Pakistan, so he traveled to Yemen instead.
            
                Bin Ladin.
            
                few days before Khallad and arrived in Los Angeles on January 15, 2000.
            
                had just surfaced in Afghanistan. As Hazmi and Mihdhar were deploying from Asia to
                had formed a close-knit group as students in Hamburg, Germany. The new recruits had
                come to Afghanistan aspiring to wage jihad in Chechnya. But al Qaeda quickly
            THE HAMBURG CONTINGENT
            Although Bin Ladin, Atef, and KSM initially contemplated using established al Qaeda
                aspiring jihadists from Germany suddenly presented a more attractive alternative.
                in Germany. Not surprisingly, Mohamed Atta, Ramzi Binalshibh, Marwan al Shehhi, and
            Mohamed Atta
            Mohamed Atta was born on September 1, 1968, in Kafr el Sheikh, Egypt, to a
                University with a degree in architectural engineering in 1990, Atta worked as an
                family he had met in Cairo to help him continue his education in Germany. They
                himself fairly seriously to his studies (at least in comparison to his jihadist
                friends) and actually received his degree shortly before traveling to Afghanistan.
                In school, Atta came across as very intelligent and reasonably pleasant, with an
            
            When Atta arrived in Germany, he appeared religious, but not fanatically so. This
                would change, especially as his tendency to assert leadership became increasingly
                pronounced. According to Binalshibh, as early as 1995 Atta sought to organize a
                Muslims and Christians. Atta proved a poor bridge, however, because of his abrasive
                and increasingly dogmatic personality. But among those who shared his beliefs, Atta
                stood out as a decisionmaker. Atta's friends during this period remember him as
                charismatic, intelligent, and persuasive, albeit intolerant of dissent.
            
                anti-American opinions, ranging from condemnations of what he described as a global
                Saddam Hussein was an American stooge set up to give Washington an excuse to
                visit home to Egypt in 1998, Atta met one of his college friends. According to this
                friend, Atta had changed a great deal, had grown a beard, and had "obviously adopted
                fundamentalism" by that time.
            
            Ramzi Binalshibh
            Ramzi Binalshibh was born on May 1,1972, in Ghayl Bawazir, Yemen. There does not seem
                to be anything remarkable about his family or early background. A friend who knew
                Binalshibh in Yemen remembers him as "religious, but not too religious." From 1987
                attempted to leave Yemen in 1995, when he applied for a U.S. visa. After his
                Ramzi Omar, claiming to be a Sudanese citizen seeking asylum. While his asylum
                petition was pending, Binalshibh lived in Hamburg and associated with individuals
                true name, this time registering as a student in Hamburg. Binalshibh continually had
                academic problems, failing tests and cutting classes; he was expelled from one
                school in September 1998.
            
            According to Binalshibh, he and Atta first met at a mosque in Hamburg in 1995. The
                    adventuresome.
            
                    Shehhi.
            
            Marwan al Shehhi
                received half a year of basic training before gaining admission to a military
                scholarship program that would fund his continued study in Germany.
            
            Shehhi first entered Germany in April 1996. After sharing an apartment in Bonn for
                family, with whom he resided for several months before moving into his own
                apartment. During this period, he came across as very religious, praying five times
                a day. Friends also remember him as convivial and "a regular guy,"wearing Western
            
            As a student, Shehhi was less than a success. Upon completing a course in German, he
                university denied his request, Shehhi left anyway, and consequently was compelled to
                his faith; for example, he specifically avoided restaurants that cooked with or
                served alcohol. In late 1997, he applied for permission to complete his course work
                in Hamburg, a request apparently motivated by his desire to join Atta and
                1998. Atta and Binalshibh moved into his apartment in April.
            
            The transfer to Hamburg did not help Shehhi's academic progress; he was directed by
                semester starting in August 1998, but back in Bonn. Shehhi initially flouted this
                more significantly, residing once again with Atta and Binalshibh, in an apartment at
                54 Marienstrasse.
            
            After Shehhi moved in with Atta and Binalshibh, his evolution toward Islamic
                fundamentalism became more pronounced. A fellow Emirati student who came to Hamburg
                to visit Shehhi noticed he no longer lived as comfortably as before. Shehhi now
                occupied an old apartment with a roommate, had no television, and wore inexpensive
            
            Similarly, when someone asked why he and Atta never laughed, Shehhi retorted, "How
                can you laugh when people are dying in Palestine?"
            
            Ziad Jarrah
            Born on May 11, 1975, in Mazraa, Lebanon, Ziad Jarrah came from an affluent family
                and attended private, Christian schools. Like Atta, Binalshibh, and Shehhi, Jarrah
                aspired to pursue higher education in Germany. In April 1996, he and a cousin
                was preparing to study dentistry.
            
                becoming an Islamic extremist. Far from displaying radical beliefs when he first
                discos and beaches in Beirut, and in Greifswald was known to enjoy student parties
                and drinking beer. Although he continued to share an apartment in Greifswald with
                his cousin, Jarrah was mostly at Senguen's apartment. Witnesses interviewed by
                German authorities after 9/11, however, recall that Jarrah started showing signs of
                world "in a natural way."
            
            In September 1997, Jarrah abruptly switched his intended course of study from
                His motivation for this decision remains unclear. The rationale he expressed to
                Senguen-that he had been interested in aviation since playing with toy airplanes as
                a child-rings somewhat hollow. In any event, Jarrah appears already to have had
                Hamburg contacts by this time, some of whom may have played a role in steering him
                toward Islamic extremism.
            
            Following his move to Hamburg that fall, he began visiting Senguen in Greifswald on
                and his visits to Senguen became less and less frequent. He began criticizing her
                for not being religious enough and for dressing too provocatively. He grew a full
                beard and started praying regularly. He refused to introduce her to his Hamburg
                more observant embarrassed him. At some point in 1999, Jarrah told Senguen that he
                invariably were followed by reconciliation.
            
            Forming a Cell
            In Hamburg, Jarrah had a succession of living accommodations, but he apparently never
                resided with his future co-conspirators. It is not clear how and when he became part
                of Atta's circle. He became particularly friendly with Binalshibh after meeting him
                The worshippers at this mosque featured an outspoken, flamboyant Islamist named
                witness has reported hearing Zammar press Binalshibh to fulfill his duty to wage
                jihad. Moreover, after 9/11, Zammar reportedly took credit for influencing not just
            
            
            
                extremists, some of whom also would attend al Qaeda training camps and, in some
            
                    group. Educated in Morocco, Bahaji returned to Germany to study electrical
                    Binalshibh at 54 Marienstrasse for eight months between November 1998 and July
                    1999. Described as an insecure follower with no personality and with limited
                    violence. Atta and Binalshibh used Bahaji's computer for Internet research, as
                    evidenced by documents and diskettes seized by German authorities after
                        9/11.
                
                Zakariya Essabar, a Moroccan citizen, moved to Germany in February 1997 and to
                    Hamburg in 1998, where he studied medical technology. Soon after moving to
                    turned extremist fairly suddenly, probably in 1999, and reportedly pressured one
                    acquaintance with physical force to become more religious, grow a beard, and
                    compel his wife to convert to Islam. Essabar's parents were said to have made
                    repeated but unsuccessful efforts to sway him from this lifestyle. Shortly
                
                    University. A witness has recalled Motassadeq saying that he would kill his
                    entire family if his religious beliefs demanded it. One of Motassadeq's
                    roommates recalls him referring to Hitler as a "good man" and organizing film
                    Hamburg group's trip to Afghanistan in late 1999.
                
                    after completing university courses in physics and chemistry. Mzoudi studied in
                    Dortmund, Bochum, and Muenster before moving to Hamburg in 1995. Mzoudi
                    described himself as a weak Muslim when he was home in Morocco, but much more
                    devout when he was back in Hamburg. In April 1996, Mzoudi and Motassadeq
                
            
            
            Going to Afghanistan The available evidence indicates that in 1999, Atta, Binalshibh,
                Afghanistan instead. An individual named Khalid al Masri approached Binalshibh and
                Germany. Abu Musab turned out to be Mohamedou Ould Slahi, a significant al Qaeda
                recruits to come see him in Duisburg.
            
                it was difficult to get to Chechnya at that time because many travelers were being
            
                pledge to those of his Hamburg colleagues. By this time, Binalshibh claims, he
                assumed he was volunteering for a martyrdom operation.
            
                to return to Germany and enroll in flight training. Atta- whom Bin Ladin chose to
            
            The new recruits also learned that an individual named Rabia al Makki (Nawaf al
            
                planned by al Qaeda.
                evidence of his presence in Germany and when he conceivably could have been in
                    Afghanistan.
            
                attorney to pay bills from Shehhi's bank account.
            
            Motassadeq also assisted Jarrah, offering to look after Aysel Senguen in Jarrah's
                absence. Said Bahaji attended to similar routine matters for Atta and Binalshibh,
            
            In early 2000, Atta, Jarrah, and Binalshibh returned to Hamburg. Jarrah arrived
                first, on January 31, 2000.97 According to Binalshibh, he and Atta left Kandahar
                (where he acquired a new passport and a U.S. visa), Saudi Arabia, Bahrain, and one
                    March.
            
            
                his beard, and no longer attended extremist mosques. Jarrah also no longer wore a
                wedding celebration (he actually had been married in 1999), a friend of his was
                surprised to see that he had shaved off his beard and was acting like his old self
                    again.
            
            But Jarrah's apparent efforts to appear less radical did not completely conceal his
                transformation from his Lebanese family, which grew increasingly concerned about his
                cousin-a close companion from boyhood-to intercede. The cousin's ensuing effort to
                contact with his family and continued his intimate relationship with Senguen. These
                to order a Boeing 747-400 flight simulator program and a Boeing 767 flight deck
                were less expensive and required shorter training periods.
            
            In March 2000, Atta emailed 31 different U.S. flight schools on behalf of a small
                group of men from various Arab countries studying in Germany who, while lacking
                    accommodations.
            
                suspicions about possible travel to Afghanistan. Shehhi obtained his visa on January
                18, 2000; Atta, on May 18; and Jarrah, on May 25.
            
            Binalshibh's visa request was rejected, however, as were his three subsequent
                generalized suspicion that visa applicants from Yemen-especially young men applying
                provide critical assistance from abroad to his co-conspirators.
            Travel
                references to dozens of international trips. Operations required travel, as did
                regarded as insecure, al Qaeda relied even more heavily on couriers.
            KSM and Abu Zubaydah each played key roles in facilitating travel for al Qaeda
                operatives. In addition, al Qaeda had an office of passports and host country issues
                managed by Atef. The committee altered papers, including passports, visas, and
                identification cards.
            
            Moreover, certain al Qaeda members were charged with organizing passport collection
            
            The operational mission training course taught operatives how to forge documents.
                Certain passport alteration methods, which included substituting photos and erasing
                "cleaning" visas were reportedly circulated among operatives. Mohamed Atta and
                Zakariya Essabar were reported to have been trained in passport alteration.
            
            The purpose of all this training was twofold: to develop an institutional capacity
                field. It was well-known, for example, that if a Saudi traveled to Afghanistan via
                    passports.
            
            A MONEY TRAIL?
                on America. The 9/11 plotters eventually spent somewhere between $400,000 and
                tradecraft was not especially sophisticated, but it was good enough. They moved,
            
            General Financing
            As we explained in chapter 2, Bin Ladin did not fund al Qaeda through a personal
                fortune and a network of businesses in Sudan. Instead, al Qaeda relied primarily on
                a fund-raising network developed over time. The CIA now estimates that it cost al
                Qaeda about $30 million per year to sustain its activities before 9/11 and that this
                money was raised almost entirely through donations.
            
                through a vast personal inheritance. Bin Ladin purportedly inherited approximately
                to wage jihad while in Sudan and Afghanistan and to secure his leadership position
                roughly from 1970 through 1994, Bin Ladin received about $1 million per year-a
                significant sum, to be sure, but not a $300 million fortune that could be used to
                fund jihad.
            
                    fortune.
            
            Nor were Bin Ladin's assets in Sudan a source of money for al Qaeda. When Bin Ladin
                These could not have provided significant income, as most were small or not
                government expropriated all his assets: he left Sudan with practically nothing. When
                reinvigorate his fund-raising efforts by drawing on ties to wealthy Saudi
            
            Al Qaeda appears to have relied on a core group of financial facilitators who raised
                countries and particularly in Saudi Arabia.
            
                charitable giving, zakat. These financial facilitators also appeared to rely heavily
                on certain imams at mosques who were willing to divert zakat donations to al Qaeda's
                    cause.
            
            Al Qaeda also collected money from employees of corrupt charities.
            
            It took two approaches to using charities for fund-raising. One was to rely on al
                Qaeda sympathizers in specific foreign branch offices of large, international
                charities-particularly those with lax external oversight and ineffective internal
            
            
                participated in funneling money to al Qaeda. In those cases, al Qaeda operatives
            
            Charities were a source of money and also provided significant cover, which enabled
                organization.
                al Qaeda before 9/11, although some governments may have contained al Qaeda
                sympathizers who turned a blind eye to al Qaeda's fundraising activities.
            
                funds to al Qaeda.)122 Still, al Qaeda found fertile fund-raising ground in Saudi
                Arabia, where extreme religious views are common and charitable giving was both
            
                trust-based system for transferring funds.
            
            In some ways, al Qaeda had no choice after its move to Afghanistan in 1996: first,
            
                with al Qaeda may have used banks to move and store money, as did various al Qaeda
                that Bin Ladin or core al Qaeda members used banks while in Afghanistan.
            
                operations represented a relatively small part of al Qaeda's estimated $30 million
                annual operating budget. Al Qaeda funded salaries for jihadists, training camps,
                organizations, although it is unlikely that al Qaeda was funding an overall jihad
                for specific terrorist operations.
            
            Al Qaeda has been alleged to have used a variety of illegitimate means, particularly
                through drug trafficking.
            
            Similarly, we have seen no persuasive evidence that al Qaeda funded itself by trading
                in African conflict diamonds. 129 There also have been claims that al Qaeda financed
            
                significance. Al Qaeda had many avenues of funding. If a particular funding source
                had dried up, al Qaeda could have easily tapped a different source or diverted funds
                two years.
                and accessed from this country. Our investigation has uncovered no credible evidence
                assistance. Similarly, we have seen no evidence that any foreign government-or
                foreign government official-supplied any funding.
            
            
                discussed in more detail in chapter 7.
            Requirements for a Successful Attack
                organize and conduct a complex international terrorist operation to inflict
                catastrophic harm. We believe such a list of requirements would have included 
            
                    enemy strengths and weaknesses;
```

This `grep -v <text> <file>` command is one that filters out <text> instead of searching for the specified text. So instead of printing every line that contains the <text>, it will instead print every line that does NOT contain the <text> from the specific <file>. Essentially it is the opposite of normal grep. This is useful for finding and filtering out lines with undesirable <text>. It can also be used in combination with -r such as -rv in order to apply this recursively to all directories, subdirectories, and files. 

---

`grep -o <text> <file>` 

```
Nathans-MBP:technical nathantruong$ grep -ro "defense"
./government/About_LSC/LegalServCorp_v_VelazquezDissent.txt:defense
./government/About_LSC/LegalServCorp_v_VelazquezDissent.txt:defense
./government/Env_Prot_Agen/tech_adden.txt:defense
./government/Gen_Account_Office/d0269g.txt:defense
./government/Gen_Account_Office/Testimony_cg00010t.txt:defense
./government/Gen_Account_Office/Testimony_cg00010t.txt:defense
./government/Gen_Account_Office/Testimony_cg00010t.txt:defense
./government/Gen_Account_Office/Testimony_cg00010t.txt:defense
./government/Gen_Account_Office/Testimony_cg00010t.txt:defense
./government/Gen_Account_Office/Testimony_cg00010t.txt:defense
./government/Gen_Account_Office/Testimony_cg00010t.txt:defense
./government/Gen_Account_Office/Testimony_cg00010t.txt:defense
./government/Gen_Account_Office/Testimony_cg00010t.txt:defense
./government/Gen_Account_Office/Testimony_cg00010t.txt:defense
./government/Gen_Account_Office/Testimony_cg00010t.txt:defense
./government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt:defense
./government/Gen_Account_Office/Statements_Feb28-1997_volume.txt:defense
./government/Gen_Account_Office/Statements_Feb28-1997_volume.txt:defense
./government/Gen_Account_Office/Statements_Feb28-1997_volume.txt:defense
./government/Gen_Account_Office/Statements_Feb28-1997_volume.txt:defense
./government/Gen_Account_Office/Statements_Feb28-1997_volume.txt:defense
./government/Gen_Account_Office/Statements_Feb28-1997_volume.txt:defense
./government/Gen_Account_Office/Statements_Feb28-1997_volume.txt:defense
./government/Gen_Account_Office/Statements_Feb28-1997_volume.txt:defense
./government/Gen_Account_Office/Statements_Feb28-1997_volume.txt:defense
./government/Gen_Account_Office/d01591sp.txt:defense
./government/Gen_Account_Office/d01591sp.txt:defense
./government/Gen_Account_Office/d01591sp.txt:defense
./government/Gen_Account_Office/d01591sp.txt:defense
./government/Gen_Account_Office/Oct15-2001_d0224.txt:defense
./government/Gen_Account_Office/Oct15-2001_d0224.txt:defense
./government/Gen_Account_Office/Oct15-2001_d0224.txt:defense
./government/Gen_Account_Office/Oct15-2001_d0224.txt:defense
./government/Gen_Account_Office/InternalControl_ai00021p.txt:defense
./government/Gen_Account_Office/Testimony_Jul17-2002_d02957t.txt:defense
./government/Gen_Account_Office/Testimony_Jul17-2002_d02957t.txt:defense
./government/Gen_Account_Office/ai9868.txt:defense
./government/Gen_Account_Office/May1998_ai98068.txt:defense
./government/Gen_Account_Office/d02701.txt:defense
./government/Gen_Account_Office/d02701.txt:defense
./government/Gen_Account_Office/d02701.txt:defense
./government/Gen_Account_Office/d02701.txt:defense
./government/Media/Kiosks_for_court_forms.txt:defense
./government/Media/Poverty_Lawyers.txt:defense
./government/Media/Local_Attorneys.txt:defense
./government/Media/Local_Attorneys.txt:defense
./government/Media/Local_Attorneys.txt:defense
./government/Media/defend_yourself.txt:defense
./plos/journal.pbio.0030032.txt:defense
./plos/journal.pbio.0020068.txt:defense
./plos/journal.pbio.0020068.txt:defense
./plos/journal.pbio.0020068.txt:defense
./plos/journal.pbio.0020068.txt:defense
./plos/journal.pbio.0020133.txt:defense
./plos/journal.pbio.0020133.txt:defense
./plos/pmed.0020015.txt:defense
./plos/journal.pbio.0020276.txt:defense
./plos/journal.pbio.0020276.txt:defense
./plos/journal.pbio.0020276.txt:defense
./plos/journal.pbio.0020276.txt:defense
./plos/journal.pbio.0020276.txt:defense
./plos/journal.pbio.0020276.txt:defense
./plos/journal.pbio.0020276.txt:defense
./plos/pmed.0010050.txt:defense
./plos/journal.pbio.0020067.txt:defense
./plos/journal.pbio.0020311.txt:defense
./plos/journal.pbio.0020311.txt:defense
./plos/pmed.0020140.txt:defense
./plos/journal.pbio.0020028.txt:defense
./plos/journal.pbio.0020400.txt:defense
./plos/journal.pbio.0020400.txt:defense
./plos/journal.pbio.0020400.txt:defense
./plos/journal.pbio.0020213.txt:defense
./biomed/ar319.txt:defense
./biomed/1471-2415-3-5.txt:defense
./biomed/1471-2180-2-35.txt:defense
./biomed/1471-2180-2-35.txt:defense
./biomed/1471-230X-2-23.txt:defense
./biomed/1471-230X-2-23.txt:defense
./biomed/gb-2002-3-11-research0059.txt:defense
./biomed/1471-2180-1-8.txt:defense
./biomed/1471-2431-3-4.txt:defense
./biomed/1472-6785-2-7.txt:defense
./biomed/1472-6785-2-7.txt:defense
./biomed/1472-6785-2-7.txt:defense
./biomed/1471-2180-1-16.txt:defense
./biomed/1471-2180-1-16.txt:defense
./biomed/1472-6823-2-2.txt:defense
./biomed/1477-7827-1-6.txt:defense
./biomed/1471-2148-2-2.txt:defense
./biomed/1471-2091-2-5.txt:defense
./biomed/1471-2091-2-5.txt:defense
./biomed/1476-511X-1-2.txt:defense
./biomed/1476-511X-1-2.txt:defense
./biomed/gb-2000-1-1-research002.txt:defense
./biomed/gb-2001-3-1-research0004.txt:defense
./biomed/1471-2180-1-26.txt:defense
./biomed/gb-2003-4-3-r20.txt:defense
./biomed/gb-2003-4-3-r20.txt:defense
./biomed/gb-2003-4-3-r20.txt:defense
./biomed/gb-2003-4-3-r20.txt:defense
./biomed/gb-2003-4-3-r20.txt:defense
./biomed/gb-2003-4-3-r20.txt:defense
./biomed/gb-2003-4-3-r20.txt:defense
./biomed/gb-2003-4-3-r20.txt:defense
./biomed/gb-2003-4-3-r20.txt:defense
./biomed/gb-2003-4-3-r20.txt:defense
./biomed/gb-2003-4-3-r20.txt:defense
./biomed/gb-2003-4-3-r20.txt:defense
./biomed/gb-2003-4-3-r20.txt:defense
./biomed/gb-2003-4-3-r20.txt:defense
./biomed/gb-2003-4-3-r20.txt:defense
./biomed/gb-2003-4-3-r20.txt:defense
./biomed/gb-2003-4-3-r20.txt:defense
./biomed/gb-2003-4-3-r20.txt:defense
./biomed/gb-2003-4-3-r20.txt:defense
./biomed/gb-2003-4-3-r20.txt:defense
./biomed/gb-2003-4-3-r20.txt:defense
./biomed/1471-2180-3-5.txt:defense
./biomed/1471-2334-2-5.txt:defense
./biomed/1471-2229-2-9.txt:defense
./biomed/gb-2003-4-2-r9.txt:defense
./biomed/gb-2003-4-2-r8.txt:defense
./biomed/gb-2002-3-10-research0056.txt:defense
./biomed/gb-2002-3-10-research0056.txt:defense
./biomed/rr191.txt:defense
./biomed/gb-2001-2-12-research0053.txt:defense
./biomed/gb-2001-2-12-research0053.txt:defense
./biomed/gb-2001-2-12-research0053.txt:defense
./biomed/1477-5956-1-1.txt:defense
./biomed/1471-2172-3-9.txt:defense
./biomed/gb-2001-2-3-research0007.txt:defense
./911report/chapter-13.4.txt:defense
./911report/chapter-13.4.txt:defense
./911report/chapter-13.5.txt:defense
./911report/chapter-13.5.txt:defense
./911report/chapter-13.5.txt:defense
./911report/chapter-13.5.txt:defense
./911report/chapter-13.5.txt:defense
./911report/chapter-13.5.txt:defense
./911report/chapter-13.5.txt:defense
./911report/chapter-13.5.txt:defense
./911report/chapter-13.5.txt:defense
./911report/chapter-13.1.txt:defense
./911report/chapter-13.1.txt:defense
./911report/chapter-13.1.txt:defense
./911report/chapter-13.1.txt:defense
./911report/chapter-13.1.txt:defense
./911report/chapter-13.1.txt:defense
./911report/chapter-13.1.txt:defense
./911report/chapter-13.1.txt:defense
./911report/chapter-13.1.txt:defense
./911report/chapter-13.1.txt:defense
./911report/chapter-13.1.txt:defense
./911report/chapter-13.1.txt:defense
./911report/chapter-13.1.txt:defense
./911report/chapter-13.1.txt:defense
./911report/chapter-13.1.txt:defense
./911report/chapter-13.3.txt:defense
./911report/chapter-13.3.txt:defense
./911report/chapter-13.3.txt:defense
./911report/chapter-3.txt:defense
./911report/chapter-3.txt:defense
./911report/chapter-3.txt:defense
./911report/chapter-3.txt:defense
./911report/chapter-3.txt:defense
./911report/chapter-3.txt:defense
./911report/chapter-3.txt:defense
./911report/chapter-3.txt:defense
./911report/chapter-3.txt:defense
./911report/chapter-3.txt:defense
./911report/chapter-3.txt:defense
./911report/chapter-3.txt:defense
./911report/chapter-3.txt:defense
./911report/chapter-3.txt:defense
./911report/chapter-3.txt:defense
./911report/chapter-3.txt:defense
./911report/chapter-3.txt:defense
./911report/chapter-3.txt:defense
./911report/chapter-3.txt:defense
./911report/chapter-3.txt:defense
./911report/chapter-3.txt:defense
./911report/chapter-2.txt:defense
./911report/chapter-1.txt:defense
./911report/chapter-1.txt:defense
./911report/chapter-1.txt:defense
./911report/chapter-1.txt:defense
./911report/chapter-1.txt:defense
./911report/chapter-1.txt:defense
./911report/chapter-1.txt:defense
./911report/chapter-1.txt:defense
./911report/chapter-6.txt:defense
./911report/chapter-6.txt:defense
./911report/chapter-6.txt:defense
./911report/chapter-6.txt:defense
./911report/chapter-6.txt:defense
./911report/chapter-6.txt:defense
./911report/chapter-6.txt:defense
./911report/chapter-6.txt:defense
./911report/chapter-6.txt:defense
./911report/chapter-6.txt:defense
./911report/chapter-6.txt:defense
./911report/chapter-6.txt:defense
./911report/chapter-9.txt:defense
./911report/chapter-9.txt:defense
./911report/chapter-8.txt:defense
./911report/chapter-8.txt:defense
./911report/chapter-8.txt:defense
./911report/chapter-12.txt:defense
./911report/chapter-12.txt:defense
./911report/chapter-12.txt:defense
./911report/chapter-12.txt:defense
./911report/chapter-12.txt:defense
./911report/chapter-12.txt:defense
./911report/chapter-12.txt:defense
./911report/chapter-10.txt:defense
./911report/chapter-10.txt:defense
./911report/chapter-10.txt:defense
./911report/chapter-11.txt:defense
./911report/chapter-11.txt:defense
./911report/chapter-11.txt:defense
./911report/chapter-11.txt:defense
./911report/chapter-11.txt:defense
./911report/chapter-11.txt:defense
```

```
Nathans-MBP:technical nathantruong$ grep -o "protection" 911report/chapter-13.3.txt
protection
```

The `grep -o <text> <file>` command is one that is used to print only the matching parts of the matched line. So it will search the <file> for the <text> and return it exactly, without the accompanying sentence. As seen here, `-o` can also be used recursively with `-r` to form `-ro` in order to search all files under all directories and subdirectories for the specific <text>. This command can be useful for finding all files that may contain a certain phrase or word. 

---

`grep -l <text> <file>`

```
Nathans-MBP:technical nathantruong$ grep -rl "law"
./government/About_LSC/LegalServCorp_v_VelazquezSyllabus.txt
./government/About_LSC/Progress_report.txt
./government/About_LSC/Strategic_report.txt
./government/About_LSC/Comments_on_semiannual.txt
./government/About_LSC/Special_report_to_congress.txt
./government/About_LSC/CONFIG_STANDARDS.txt
./government/About_LSC/commission_report.txt
./government/About_LSC/LegalServCorp_v_VelazquezDissent.txt
./government/About_LSC/ONTARIO_LEGAL_AID_SERIES.txt
./government/About_LSC/LegalServCorp_v_VelazquezOpinion.txt
./government/About_LSC/diversity_priorities.txt
./government/About_LSC/reporting_system.txt
./government/About_LSC/State_Planning_Report.txt
./government/About_LSC/Protocol_Regarding_Access.txt
./government/About_LSC/ODonnell_et_al_v_LSCdecision.txt
./government/About_LSC/conference_highlights.txt
./government/About_LSC/State_Planning_Special_Report.txt
./government/Env_Prot_Agen/multi102902.txt
./government/Env_Prot_Agen/final.txt
./government/Env_Prot_Agen/ro_clear_skies_book.txt
./government/Env_Prot_Agen/bill.txt
./government/Env_Prot_Agen/nov1.txt
./government/Env_Prot_Agen/tech_adden.txt
./government/Alcohol_Problems/Session3-PDF.txt
./government/Alcohol_Problems/Session4-PDF.txt
./government/Gen_Account_Office/d0269g.txt
./government/Gen_Account_Office/Testimony_cg00010t.txt
./government/Gen_Account_Office/og97032.txt
./government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt
./government/Gen_Account_Office/Sept27-2002_d02966.txt
./government/Gen_Account_Office/d01376g.txt
./government/Gen_Account_Office/Statements_Feb28-1997_volume.txt
./government/Gen_Account_Office/pe1019.txt
./government/Gen_Account_Office/Testimony_Jul15-2002_d02940t.txt
./government/Gen_Account_Office/gg96118.txt
./government/Gen_Account_Office/ffm.txt
./government/Gen_Account_Office/og97023.txt
./government/Gen_Account_Office/d01121g.txt
./government/Gen_Account_Office/d03419sp.txt
./government/Gen_Account_Office/Letter_Walkeraug17let.txt
./government/Gen_Account_Office/og97045.txt
./government/Gen_Account_Office/Testimony_d01609t.txt
./government/Gen_Account_Office/og97050.txt
./government/Gen_Account_Office/og96038.txt
./government/Gen_Account_Office/Sept14-2002_d011070.txt
./government/Gen_Account_Office/Oct15-1999_gg00026t.txt
./government/Gen_Account_Office/og97052.txt
./government/Gen_Account_Office/d03232sp.txt
./government/Gen_Account_Office/og97043.txt
./government/Gen_Account_Office/June30-2000_gg00135r.txt
./government/Gen_Account_Office/d01591sp.txt
./government/Gen_Account_Office/Oct15-2001_d0224.txt
./government/Gen_Account_Office/og96028.txt
./government/Gen_Account_Office/d01145g.txt
./government/Gen_Account_Office/InternalControl_ai00021p.txt
./government/Gen_Account_Office/d01186g.txt
./government/Gen_Account_Office/og98032.txt
./government/Gen_Account_Office/ai00134.txt
./government/Gen_Account_Office/og96020.txt
./government/Gen_Account_Office/Testimony_Jul17-2002_d02957t.txt
./government/Gen_Account_Office/og96047.txt
./government/Gen_Account_Office/ai9868.txt
./government/Gen_Account_Office/og97038.txt
./government/Gen_Account_Office/Paper_Walker11-2002_acpro122.txt
./government/Gen_Account_Office/May1998_ai98068.txt
./government/Gen_Account_Office/og96041.txt
./government/Gen_Account_Office/d02701.txt
./government/Gen_Account_Office/ai2132.txt
./government/Post_Rate_Comm/Gleiman_EMASpeech.txt
./government/Post_Rate_Comm/Cohenetal_CreamSkimming.txt
./government/Post_Rate_Comm/Cohenetal_DeliveryCost.txt
./government/Post_Rate_Comm/Mitchell_RMVancouver.txt
./government/Post_Rate_Comm/Gleiman_gca2000.txt
./government/Post_Rate_Comm/Redacted_Study.txt
./government/Post_Rate_Comm/Cohenetal_comparison.txt
./government/Post_Rate_Comm/Cohenetal_Scale.txt
./government/Post_Rate_Comm/ReportToCongress2002WEB.txt
./government/Media/Federal_agency.txt
./government/Media/water_fees.txt
./government/Media/Helping_Out.txt
./government/Media/balance_scales_of_justice.txt
./government/Media/Legal-aid_chief.txt
./government/Media/Unusual_Woodburn.txt
./government/Media/Funding_cuts_force.txt
./government/Media/Good_guys_reward.txt
./government/Media/Anthem_Payout.txt
./government/Media/Donald_Hilliker.txt
./government/Media/Free_legal_service.txt
./government/Media/Owning_a_Piece.txt
./government/Media/Targeting_Domestic_Violence.txt
./government/Media/highlight_Senior_Day.txt
./government/Media/Few_who_need.txt
./government/Media/City_Council_Budget.txt
./government/Media/Legal_system_fails_poor.txt
./government/Media/Supporting_Legal_Center.txt
./government/Media/Lindsays_legacy.txt
./government/Media/New_funding_sources.txt
./government/Media/Barnes_new_job.txt
./government/Media/Providing_Legal_Aid.txt
./government/Media/Nonprofit_Buys.txt
./government/Media/Legal_Aid_in_Clay_County.txt
./government/Media/Domestic_Violence_Ruling.txt
./government/Media/Abuse_penalties.txt
./government/Media/Law_Award_from_College.txt
./government/Media/Law_Schools.txt
./government/Media/Raising_the_Bar.txt
./government/Media/Justice_for_all.txt
./government/Media/agency_expands.txt
./government/Media/Helping_Hands.txt
./government/Media/not_accessible_to_disabled.txt
./government/Media/Campaign_Pays.txt
./government/Media/New_Online_Resources.txt
./government/Media/Annual_Fee.txt
./government/Media/Oregon_Poor.txt
./government/Media/Barnes_pro_bono.txt
./government/Media/Poor_Lacking_Legal_Aid.txt
./government/Media/Workers_aid_center.txt
./government/Media/Philly_Lawyers.txt
./government/Media/Too_Crucial_to_Take_Cut.txt
./government/Media/Pro_Bono_Services.txt
./government/Media/Rumble_in_the_Bronx.txt
./government/Media/FortWorthStarTelegram.txt
./government/Media/predatory_loans.txt
./government/Media/Survey.txt
./government/Media/AP_LawSchoolDebts.txt
./government/Media/Working_for_Free.txt
./government/Media/Eviction_law.txt
./government/Media/Law-school_grads.txt
./government/Media/FY_04_Budget_Outlook.txt
./government/Media/Texas_Lawyer.txt
./government/Media/Disaster_center.txt
./government/Media/Kiosks_for_court_forms.txt
./government/Media/Higher_Registration_Fees.txt
./government/Media/Fire_Victims_Sue.txt
./government/Media/Funds_Shortage.txt
./government/Media/Terrorist_Attack.txt
./government/Media/Butler_Co_attorneys.txt
./government/Media/BergenCountyRecord.txt
./government/Media/Volunteers_Step_Up.txt
./government/Media/Coup_Reshapes_Legal_Aid.txt
./government/Media/IOLTA_INTEREST_RATE.txt
./government/Media/Ginny_Kilgore.txt
./government/Media/Legal_Aid_looks_to_legislators.txt
./government/Media/Poverty_Lawyers.txt
./government/Media/Avoids_Budget_Cut.txt
./government/Media/grants_fail_to_come.txt
./government/Media/Lockyer_Warns.txt
./government/Media/Rental_rules.txt
./government/Media/Using_Tech_Tools.txt
./government/Media/Assuring_Underprivileged.txt
./government/Media/Boone_legal_service.txt
./government/Media/Firm_to_the_Poor_Needs_Help.txt
./government/Media/Making_a_case.txt
./government/Media/Barnes_Volunteers.txt
./government/Media/Commercial_Appeal.txt
./government/Media/Justice_requests.txt
./government/Media/Free_Legal_Assistance.txt
./government/Media/Local_Attorneys.txt
./government/Media/Texas_Supreme_Court.txt
./government/Media/Civil_Matters.txt
./government/Media/Low-income_children.txt
./government/Media/BusinessWire.txt
./government/Media/The_Columbian.txt
./government/Media/Higher_court.txt
./government/Media/Service_Agency.txt
./government/Media/Marylands_Legal_Aid.txt
./government/Media/Attorney_gives_his_time.txt
./government/Media/Library_Lawyers.txt
./government/Media/Crains_New_York_Business.txt
./government/Media/Hard_to_Get.txt
./government/Media/The_State_of_Pro_Bono.txt
./government/Media/residents_sue_city.txt
./government/Media/Legal_Aid_Society.txt
./government/Media/GreensburgDailyNews.txt
./government/Media/Major_Changes.txt
./government/Media/Program_Lodges.txt
./government/Media/Wilmington_lawyer.txt
./government/Media/All_May_Have_Justice.txt
./government/Media/Domestic_violence_aid.txt
./government/Media/CommercialAppealMemphis2.txt
./government/Media/Weak_economy.txt
./government/Media/Lawyer_Web_Survey.txt
./government/Media/Valley_Needing_Legal_Services.txt
./government/Media/Barr_sharpening_ax.txt
./government/Media/Legal_Aid_attorney.txt
./government/Media/The_Bend_Bulletin.txt
./government/Media/Legal_services_for_poor.txt
./government/Media/Farm_workers.txt
./government/Media/Entities_Merge.txt
./government/Media/less_legal_aid.txt
./government/Media/Do-it-yourself_divorce.txt
./government/Media/Politician_Practices.txt
./government/Media/defend_yourself.txt
./government/Media/Towson_Attorney.txt
./government/Media/Pro-bono_road_show.txt
./government/Media/A_Perk_of_Age.txt
./government/Media/A_helping_hand.txt
./government/Media/pro_bono_efforts.txt
./government/Media/5_Legal_Groups.txt
./government/Media/Greedy_Generous.txt
./government/Media/Retirement_Has_Its_Appeal.txt
./government/Media/RoanokeTimes.txt
./government/Media/NJ_Legal_Services.txt
./government/Media/Bridging_legal_aid_gap.txt
./government/Media/Legal_Aid_campaign.txt
./government/Media/Aid_Gets_7_Million.txt
./plos/journal.pbio.0030032.txt
./plos/pmed.0020071.txt
./plos/pmed.0010039.txt
./plos/journal.pbio.0020419.txt
./plos/pmed.0020098.txt
./plos/journal.pbio.0020223.txt
./plos/pmed.0020088.txt
./plos/journal.pbio.0020150.txt
./plos/journal.pbio.0020232.txt
./plos/pmed.0020048.txt
./plos/pmed.0020060.txt
./plos/journal.pbio.0020147.txt
./plos/journal.pbio.0020054.txt
./plos/journal.pbio.0020337.txt
./plos/journal.pbio.0020440.txt
./plos/journal.pbio.0020101.txt
./plos/journal.pbio.0020262.txt
./plos/journal.pbio.0030065.txt
./plos/pmed.0020009.txt
./plos/journal.pbio.0020113.txt
./plos/journal.pbio.0020112.txt
./plos/pmed.0020208.txt
./plos/journal.pbio.0020307.txt
./plos/pmed.0020209.txt
./plos/pmed.0020246.txt
./plos/journal.pbio.0020214.txt
./plos/pmed.0020050.txt
./plos/pmed.0020247.txt
./plos/pmed.0020047.txt
./plos/journal.pbio.0020439.txt
./plos/journal.pbio.0020164.txt
./plos/pmed.0020055.txt
./biomed/1476-069X-2-4.txt
./biomed/gb-2003-4-4-r24.txt
./biomed/1471-2180-2-35.txt
./biomed/gb-2001-2-3-research0008.txt
./biomed/1472-6823-3-1.txt
./biomed/1471-2148-3-18.txt
./biomed/gb-2002-3-8-research0040.txt
./biomed/cc105.txt
./biomed/1476-072X-2-4.txt
./biomed/1472-6831-3-1.txt
./biomed/1471-2407-2-17.txt
./biomed/cc1852.txt
./biomed/1471-2296-3-19.txt
./biomed/1476-072X-2-3.txt
./biomed/1471-213X-1-9.txt
./biomed/1471-2202-2-18.txt
./biomed/1471-2121-3-4.txt
./biomed/1477-7525-1-12.txt
./biomed/1472-6963-3-12.txt
./biomed/1471-2202-3-1.txt
./biomed/1472-6947-2-7.txt
./biomed/1472-6963-3-1.txt
./biomed/1472-6963-3-14.txt
./biomed/1471-2288-3-9.txt
./biomed/1472-6793-2-18.txt
./biomed/1471-2202-3-7.txt
./biomed/1471-2148-3-1.txt
./biomed/1468-6708-3-4.txt
./biomed/1472-6882-1-10.txt
./biomed/1471-2121-3-19.txt
./biomed/1471-2180-2-1.txt
./biomed/1472-6882-1-11.txt
./biomed/1471-2105-1-1.txt
./biomed/gb-2002-3-10-research0052.txt
./biomed/gb-2001-2-12-research0055.txt
./biomed/1472-6882-1-12.txt
./biomed/1472-6955-2-1.txt
./biomed/1472-6947-1-6.txt
./biomed/cc343.txt
./biomed/gb-2002-3-3-research0011.txt
./biomed/bcr605.txt
./biomed/1476-069X-2-9.txt
./911report/chapter-13.4.txt
./911report/chapter-13.5.txt
./911report/chapter-13.1.txt
./911report/chapter-13.3.txt
./911report/chapter-3.txt
./911report/chapter-2.txt
./911report/chapter-1.txt
./911report/chapter-5.txt
./911report/chapter-6.txt
./911report/chapter-7.txt
./911report/chapter-9.txt
./911report/chapter-8.txt
./911report/preface.txt
./911report/chapter-12.txt
./911report/chapter-10.txt
./911report/chapter-11.txt
```

```
Nathans-MBP:technical nathantruong$ grep -rl "safety"
./government/About_LSC/Special_report_to_congress.txt
./government/About_LSC/commission_report.txt
./government/About_LSC/reporting_system.txt
./government/Env_Prot_Agen/multi102902.txt
./government/Env_Prot_Agen/ctf1-6.txt
./government/Env_Prot_Agen/ctm4-10.txt
./government/Env_Prot_Agen/1-3_meth_901.txt
./government/Env_Prot_Agen/atx1-6.txt
./government/Env_Prot_Agen/bill.txt
./government/Env_Prot_Agen/tech_adden.txt
./government/Alcohol_Problems/Session4-PDF.txt
./government/Gen_Account_Office/Testimony_cg00010t.txt
./government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt
./government/Gen_Account_Office/Sept27-2002_d02966.txt
./government/Gen_Account_Office/pe1019.txt
./government/Gen_Account_Office/gg96118.txt
./government/Gen_Account_Office/July11-2001_gg00172r.txt
./government/Gen_Account_Office/Testimony_d01609t.txt
./government/Gen_Account_Office/og97050.txt
./government/Gen_Account_Office/Oct15-1999_gg00026t.txt
./government/Gen_Account_Office/d01591sp.txt
./government/Gen_Account_Office/Oct15-2001_d0224.txt
./government/Gen_Account_Office/og96014.txt
./government/Gen_Account_Office/og96034.txt
./government/Gen_Account_Office/Testimony_Jul17-2002_d02957t.txt
./government/Gen_Account_Office/Letter_WalkerJan30-2001.txt
./government/Media/Survey.txt
./government/Media/Volunteers_Step_Up.txt
./government/Media/Firm_to_the_Poor_Needs_Help.txt
./government/Media/Farm_workers.txt
./government/Media/Bridging_legal_aid_gap.txt
./plos/pmed.0020258.txt
./plos/pmed.0020115.txt
./plos/pmed.0020061.txt
./plos/pmed.0020210.txt
./plos/pmed.0010058.txt
./plos/pmed.0010070.txt
./plos/pmed.0010064.txt
./plos/pmed.0010060.txt
./plos/pmed.0020161.txt
./plos/pmed.0020203.txt
./plos/pmed.0020002.txt
./plos/pmed.0020231.txt
./plos/pmed.0010047.txt
./plos/pmed.0010052.txt
./plos/pmed.0020187.txt
./plos/pmed.0020009.txt
./plos/pmed.0020196.txt
./plos/journal.pbio.0020112.txt
./plos/pmed.0020208.txt
./plos/pmed.0020157.txt
./plos/pmed.0020209.txt
./plos/pmed.0020247.txt
./plos/journal.pbio.0020404.txt
./plos/pmed.0010026.txt
./biomed/1471-2369-3-9.txt
./biomed/1471-2180-2-20.txt
./biomed/1471-2458-3-5.txt
./biomed/1471-2172-3-2.txt
./biomed/1471-2091-2-16.txt
./biomed/1471-2458-3-2.txt
./biomed/ar309.txt
./biomed/gb-2003-4-9-r58.txt
./biomed/1475-925X-2-11.txt
./biomed/cc1538.txt
./biomed/1471-2458-2-6.txt
./biomed/1471-2253-1-1.txt
./biomed/cc1529.txt
./biomed/1472-6882-2-5.txt
./biomed/1471-2377-3-4.txt
./biomed/cc2358.txt
./biomed/1471-2105-3-26.txt
./biomed/1472-6963-3-7.txt
./biomed/cc2167.txt
./biomed/bcr273.txt
./biomed/1471-2334-2-27.txt
./biomed/1472-6947-2-7.txt
./biomed/1472-6963-3-1.txt
./biomed/1472-6963-3-14.txt
./biomed/1471-2288-3-9.txt
./biomed/1472-6793-1-2.txt
./biomed/cc350.txt
./biomed/1471-2334-1-17.txt
./biomed/cvm-2-6-278.txt
./biomed/cvm-2-4-180.txt
./biomed/1471-2407-2-9.txt
./biomed/cvm-2-6-286.txt
./biomed/1471-2334-3-10.txt
./biomed/1472-6955-2-1.txt
./biomed/1468-6708-3-3.txt
./biomed/1476-069X-2-9.txt
./911report/chapter-13.5.txt
./911report/chapter-13.2.txt
./911report/chapter-3.txt
./911report/chapter-2.txt
./911report/chapter-1.txt
./911report/chapter-9.txt
./911report/chapter-12.txt
```

This `grep -l <text> <file>` command is used in order to print the name of all files in which the <text> reside. In these examples I use `-rl` to recursively search through all files of directories and subdirectories because just using `-l` and the file location would just return <file> if `grep -l` were to evaluate as true. This command is useful for finding every file that a certain word or phrase resides in. 

---

# Works Cited

[Grep Wikibooks](https://en.wikibooks.org/wiki/Grep)

[Grep Linux Man](https://man7.org/linux/man-pages/man1/grep.1.html )
