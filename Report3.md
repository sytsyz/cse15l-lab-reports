## Part 1 Bugs
Chosen bug: ReversedInPlace
1. A failure-inducing input 
```
@Test 
	public void testReverseInPlace2()
  {
    int[] input1 = { 1,2,7 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 7,2,1 }, input1);
	}
```
2. An input that doesn’t induce a failure
```
@Test 
	public void testReverseInPlace3()
  {
    int[] input1 = { };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ }, input1);
	}
```
3. Symptoms
   - failure input
     <img width="993" alt="image" src="https://github.com/sytsyz/cse15l-lab-reports/assets/146896888/39fc2b73-b6f2-4644-85cd-37316b4a2f7a">
   - no failure input
     <img width="943" alt="image" src="https://github.com/sytsyz/cse15l-lab-reports/assets/146896888/06bf5d96-8ab3-4373-a191-acf9eb15ada7">
4. The Bug
   - Before
     
   ```
   // Changes the input array to be in reversed order
    static void reverseInPlace(int[] arr) 
    {
      for(int i = 0; i < arr.length; i += 1) 
      {
        arr[i] = arr[arr.length - i - 1];
      }
    }
   ```
   - After
   ```
   // Changes the input array to be in reversed order
   static void reverseInPlace(int[] arr) 
    {
      for(int i = 0; i < arr.length/2; i += 1) 
      {
        int temp = arr[i];
        arr[i] = arr[arr.length - i - 1];
        arr[arr.length-i-1] = temp;
      }
    }
   ```
  - Explanation
    The original code did not fulfill the fuction of reserve the input, it simply rewrite the array in the beginning by the number at the end of the array.
    As a result, the original code will have an output which an array that contains only the last number in the array. The fix address this issue. By adding a temperory
    number holder "temp", the code is now able to store the original number before it get rewrite by the last number of the array, then able to put this temp number towards
    the last places of the array.

## Part 2 Researching Commands: Gerp
1. -r
- directory
```
	linda@Yutongs-MacBook-Pro technical % grep -r "Darwin" biomed
	biomed/1471-2105-3-2.txt:        In the 1830's, Charles Darwin's investigation of the
	biomed/1471-2105-3-2.txt:        In the 1970's, Woese and Fox revisited Darwinian
```
r stands for recursive. Shen applied to directory, it searches all the files that contains the keyword "Darwin" biomed and its subdirectory, displaying the pathway to the files and the lines in which the keywords is contained. It is usefule to find the desired file with the content in the files. 

- files
```
	linda@Yutongs-MacBook-Pro biomed % grep -r "Darwin" 1471-2105-3-2.txt 
	1471-2105-3-2.txt:        In the 1830's, Charles Darwin's investigation of the
	1471-2105-3-2.txt:        In the 1970's, Woese and Fox revisited Darwinian
```
r stands for recursive. Shen applied to file, it searches all the files that contains the keyword "Darwin" in working directory, displaying the name of the files and the lines in which the keywords is contained. It is usefule to find the desired file with the content in the files. 

2. -w
- Files
  
 ```
   linda@Yutongs-MacBook-Pro biomed % grep -w "Darwin" 1471-2105-3-2.txt
        In the 1830's, Charles Darwin's investigation of the
   linda@Yutongs-MacBook-Pro biomed % grep  "Darwin" 1471-2105-3-2.txt 
        In the 1830's, Charles Darwin's investigation of the
        In the 1970's, Woese and Fox revisited Darwinian
 ```

w meant wholeword. The result will exclued the lines where the keword is only a phrase of a word. This is usefule for precise search. 

*previously I thought the 2 examples must be one for file one for directoris, a new working example of files will be added*

-Files

```
	linda@Yutongs-MacBook-Pro biomed % grep "can" 1471-2105-3-2.txt       
	        those that can only be observed with a microscope, using a
	        that the number of possible structure models can be larger
	        significant findings was the discovery of the third kingdom
	        28 ] . Today, with a significantly larger number of
	        can require very large, phylogenetically and structurally
	        large subunit [ 58 59 ] ) groups). With significant
	            When implemented properly, covariation analysis can
	            lower, although significant, extent of covariation.
	            of possible secondary structure models is significantly
	            significant covariation was identified with our newer
	            nucleotides in a comparative structure model can be
	            can be part of either a secondary structure helix (two
	            These include any non-canonical base pair (not a G:C,
	            are base paired, nucleotides can also be unpaired in
	            they can be within a hairpin loop (nucleotides capping
	            due to a significant number of covariations within the
	            has a significant covariation score (H-2A); thus, only
	            Here, six of the seven alignments have significant
	            sequences can be eliminated from the screen by changing
	            displayed on the screen can also be modulated with the
	            phylogenetic tree that contain a significant number of
	            and variation present in RNA sequence alignments can
	            juxtapositioning or alignment of sequences can be
	            there is a significant amount of variation between the
	            information alone. For these situations, we can
	            associated with the second hand; these can change many
	            sequences contain subsequences that cannot be aligned
	            For these sequences, the majority of the sequence can
	            more sequences with significant similarity in these
	            albicans, and 
	            sequences has increased significantly within the past
	            Entries not shown on the first page can be viewed by
	            PDF, and BPSEQ files can be viewed by clicking the
	            Multiple secondary structure diagrams can be
	            tar file, which can be uncompressed with appropriate
	            limitation can be avoided by subdividing large
	            significant. Newer alignments might also contain
	            Eucarya that have significant numbers of rRNA
	            nucleus, 1.20 for the mitochondria). A significant
	            button. While the user can select the individual fields
	            fields, can be determined with the "V" (values) button
	            (nuclear), and Vir (viral); each can be selected by
	            the main frame, and can be selected by clicking the
	            Sequence Length, and Exon can be determined by
	            The values for these attributes can also be found by
	            can be selected from the main frame), "Common Name"
	            "Intron Position," and "Comment" can only be observed
	            • The number of possible values for an attribute can
	            For mode one, you can systematically navigate
	            the desired goal point; otherwise, mode two can help
	            The "Common Name" attribute can also help identify
	            can make answering questions easier. Take, for example,
	            significantly different orders and overall arrangements
	            you can type numbers into these boxes to set the sort
	            attribute can be reversed (z -> a, high number ->
	            sortings can be reset to the default values by clicking
	            page can be modulated. While the system defaults to 50
	            output page can be set to 20, 100, 200, and 400. The
	            user can scroll to those entries that do not appear on
	            can be retrieved from the results window. The system
	            link is clicked; PDF or BPSEQ files can be obtained
	            listing that can be retrieved in a new window by
	            background), where the user can select the phylogenetic
	            can be navigated with this system. The base
	            can be modulated from one (the default) to five levels
	            tree. The user can enter a partial or complete
	            text can be viewed in the Results Frame by checking the
	            RNA information can be mapped onto the phylogenetic
	            panel in the Selection Frame, the user can choose to
	            phylogenetic/cell location groups can be selected,
	            and four nucleotides. Each category can be searched
	        the search. In parallel, with the significant advancements
	            we do have sequence information but cannot fully
	            cannot be subclassified as IB1, IB2, IB3, or IB4. Those
	linda@Yutongs-MacBook-Pro biomed % grep -w "can" 1471-2105-3-2.txt 
	        those that can only be observed with a microscope, using a
	        that the number of possible structure models can be larger
	        can require very large, phylogenetically and structurally
	            When implemented properly, covariation analysis can
	            nucleotides in a comparative structure model can be
	            can be part of either a secondary structure helix (two
	            are base paired, nucleotides can also be unpaired in
	            they can be within a hairpin loop (nucleotides capping
	            sequences can be eliminated from the screen by changing
	            displayed on the screen can also be modulated with the
	            and variation present in RNA sequence alignments can
	            juxtapositioning or alignment of sequences can be
	            information alone. For these situations, we can
	            associated with the second hand; these can change many
	            For these sequences, the majority of the sequence can
	            Entries not shown on the first page can be viewed by
	            PDF, and BPSEQ files can be viewed by clicking the
	            Multiple secondary structure diagrams can be
	            tar file, which can be uncompressed with appropriate
	            limitation can be avoided by subdividing large
	            button. While the user can select the individual fields
	            fields, can be determined with the "V" (values) button
	            (nuclear), and Vir (viral); each can be selected by
	            the main frame, and can be selected by clicking the
	            Sequence Length, and Exon can be determined by
	            The values for these attributes can also be found by
	            can be selected from the main frame), "Common Name"
	            "Intron Position," and "Comment" can only be observed
	            • The number of possible values for an attribute can
	            For mode one, you can systematically navigate
	            the desired goal point; otherwise, mode two can help
	            The "Common Name" attribute can also help identify
	            can make answering questions easier. Take, for example,
	            you can type numbers into these boxes to set the sort
	            attribute can be reversed (z -> a, high number ->
	            sortings can be reset to the default values by clicking
	            page can be modulated. While the system defaults to 50
	            output page can be set to 20, 100, 200, and 400. The
	            user can scroll to those entries that do not appear on
	            can be retrieved from the results window. The system
	            link is clicked; PDF or BPSEQ files can be obtained
	            listing that can be retrieved in a new window by
	            background), where the user can select the phylogenetic
	            can be navigated with this system. The base
	            can be modulated from one (the default) to five levels
	            tree. The user can enter a partial or complete
	            text can be viewed in the Results Frame by checking the
	            RNA information can be mapped onto the phylogenetic
	            panel in the Selection Frame, the user can choose to
	            phylogenetic/cell location groups can be selected,
	            and four nucleotides. Each category can be searched
```
in this case, when one looks for can without -w,the result of cannot will also shows up, whcih messed with the intention. 


- Directory
  ```
	  linda@Yutongs-MacBook-Pro biomed % grep -w "Darwin" biomed
	  grep: biomed: No such file or directory
	  
  ```
  unforfunately this command does not apply to directories, which makes it less useful in this case. 
  

3. -n
- Files
  ```
	  linda@Yutongs-MacBook-Pro biomed % grep -n "Darwin"  1471-2105-3-2.txt 
	  6:        In the 1830's, Charles Darwin's investigation of the
	  20:        In the 1970's, Woese and Fox revisited Darwinian
  ```
  n display the number line of the matched resulte. It is useful when you try to describe a certain part of the artile to others but you only remember the content but do now remember the location.

  *previously I thought the 2 examples must be one for file one for directoris, a new working example of files will be added*

  - files
    ```
	    linda@Yutongs-MacBook-Pro biomed % grep -n "Data" 1471-2105-3-2.txt 
		575:            ("Data Frame;" H-2A.1). The collective scoring data
		986:            Our goals for the "Sequence and Structure Data"
		1005:            (see Section 4: Data Access Systems for more
		1453:            ribosomal RNA. The "Intron Distribution Data" page
		1496:          4. Data access systems
		2249:          Database System
		2355:        RDBMS = Relational Database Management System.
    ```


by using -n and grep title-like keyworkds, one can easily locate where the disire content is




  
4. -v
- Files
  
  ```
  	linda@Yutongs-MacBook-Pro biomed % grep -v "t" 1471-2105-3-2.txt   


        Background
        for any one RNA sequence, such as for 
        13 ] .
        models have undergone numerous revisions [ 23 24 25 26 27
        e.g., U:U <-> C:C; A:A
        <-> G:G; G:U <-> A:C; 
        RNA molecules ( 
        e.g., 16S and 23S rRNAs) have been
        [ 46 47 ] and 23S (and 23S-like) ribosomal RNAs [ 48 49 50
      
      
        
          
            organisms
            Noller & Woese models (16S [ 15 22 ] and 23S [ 19 ]
            Reference Organisms" page, our primary focus has been
            example, 
            
            (Figures 2A, 2B, and 2C) reveals our confidence for
            base pairs, small closed circles for G:U, large open
            E. coli 16S and 23S rRNA
            16S and 23S rRNA have a red base pair symbol, our
            8500 16S and 16S-like rRNA sequences and 1050 23S and
            and in Table 2. These sequences have been aligned and
            PDF
            
            The 
            unambiguously numbering each helix in a RNA molecule.
            16S rRNA helix, which spans 
            below). The 
            The 
          
          
            and 23S [ 19 ] rRNA models. Every base pair in each of
            models; 2) changes since 1983 (16S rRNA) or 1984 (23S
            (H-1B.2).
          
          
            A:U, or G:U; 
            e.g., U:U), lone or single base
          
        
        
          
            organelles (Table 2).
            Michel (group I [ 32 ] and group II [ 34 ] ) and Suh
            subgroups, IIA and IIB (Table 2).
            e.g., A:U <-> G:C) is
            red base pair. Black base pairs have a lower
            e.g., Three Domain/Two Organelle,
            Three Domain, Archaea, 
            C1+C3 scores >= 1.5.
          
          
            ("*").
          
          
            diagrams
            hidden from view, and replaced by arcs. These regions
            open circles).
            ( 
          
        
        
          
          
          
            Aligning new sequences
            on a clock [ 4 ] . The highly variable regions are
            regions ( 
            i.e., hour hand regions) and
            semi-conserved regions ( 
            sub-second ( 
            regions ( 
            sequences in 1988 (see Figures 35-43 in [ 48 ] ).
            Schizosaccharomyces pombe,
            albicans, and 
            even more animal 23S-like rRNA sequences from organisms
          
          
            diagrams
            unpaired.
            GenBank;
            CRW RDBMS.
            4A-4B.
          
          
            3A. Index of available sequences and
          
          
          
          
            from organism names, phylogeny (general: Archaea,
            queries.)
          
          
            June 2002.
          
          
            gene.
          
          
            E. coli rRNA reference sequence
            and accession number.
            phylogeny; 7) organism name; 8) accession number; 9)
            P(x) = 
            e -μμ 
            x 
            and 
          
          
            of 16S and 23S rRNA exons, non-rRNA exons, number of
            remaining 183 (15%) are unclassified (see below). While
            Dibaeis baeomyces nuclear 23S
            (group I, group II, Archaeal, or spliceosomal),
            group.
          
          
            Calliphora vicina nuclear-encoded
            23S-like rRNA (GenBank accession number K02309).
          
          
            Exon
          
          
            from a specific series of RDBMS queries on a daily
          
        
        
          
            ( 
            e.g., "Organism" or "Phylogeny"),
            H-4A.1).
            values are possible.
            field.
            word.
            "Phylogeny" and "Common Name" fields is downloaded from
            genera Gorilla, Pan (chimpanzees), Pongo, and Homo (see
            (Figure 3and H-4A.1).
            Mammals, 
            i.e., "mammals" or "mosses") do
            page.
            diagram.
            sequence.
          
          
            4B. RDBMS (PhyloBrowser)
            background).
            ( 
            e.g., "human;" see H-4B.2). Once
            (H-4B.3).
          
          
            or 5' and 3' ends of helices and loops.
            and C (12.49%) (Figure 5and H-4C.1). These values are
            i.e., paired, unpaired, 
            by GA (13.35%), UA (9.821%), AU (6.703%), 
            (24.99%; H-4C.4), followed by AC (13.28%), GG (8.28%), 
            sequences, nearly 75% occur in loops, while
            H-4C.
            online.
          
        
      
      
      
      
        Conclusions
        molecule are:
        ( 
      
      
        

          CRW RDBMS.
        
        
          exons ( 
        
        
          sequences
          
            boundaries
          
          
            subgroups.
          
          
            Aureoumbra lagunensis (U40258;
            Chara sp. Qiu 96222 (AF191800;
          
          
            available.
          
        
        
          
            (Table 4). The primary fields are: 1) organism name; 2)
            e.g., 16S or IC1); 6) GenBank
            E. coli (GenBank Accession Number
          
          
            Diagrams
            (version 7.00;
          
        
        
          
            using webalizer (version 2.01;
          
          
          
          
            specific URLs.
          
  ```


v is invert match. When applied to files, the result of lines that does not contains the key word will be displayed. This is useful when you want to view the file without undisred distracting informations. or words that do not contain a certian alphabet




*previously I thought the 2 examples must be one for file one for directoris, a new working example of files will be added*

- files

  
  
  ```
	  grep -v "e" 1471-2105-3-2.txt   

  
    
      
        Background
        13 ] .
        <-> G:G; G:U <-> A:C; 
      
      
        
          
            organisms
            two RNAs.
            
            E. coli 16S and 23S rRNA
            PDF
            
            E. coli positions 9-13/21-25, is
            "Histogram" and 
            "Circular" diagram formats
            E. coli 16S rRNA, with 1542
          
          
            (H-1B.2).
          
          
            A:U, or G:U; 
          
        
        
          information
          
            covariation analysis.
          
          
            ("*").
          
          
            diagrams
            study ( 
            ( 
            introns.
          
        
        
          
          
          
            albicans, and 
          
          
            diagrams
            CRW RDBMS.
            4A-4B.
          
          
            11,464 rRNA (5S, 16S, and 23S) and intron (group I, II,
          
          
          
          
          
          
          
          
            3E. rRNA Introns
          
          
            rRNA and 68 in 23S rRNA. 2) Although 16S rRNA is
            Poisson distribution, 
            P(x) = 
            x 
            and 
            (16S rRNA positions 516 and 1199, and 23S rRNA position
          
          
            IA, IB, IC2, ID, and II subgroups occur almost
            occurs in mitochondrial 
            including all four mitochondrial introns in this
            group.
          
          
            Distribution
          
          
            Exon
            has 9 introns.
            particular class ( 
          
          
            3F. Group 1/11 Intron distributions
          
        
        
          
            4A. RDBMS (Standard)
            ( 
            H-4A.1).
            word.
            group that contains 
            platypus ( 
            Mammals, 
            that group of organisms.
            is an option to output 
            diagram.
          
          
            background).
            ( 
            (H-4B.3).
          
          
            by GA (13.35%), UA (9.821%), AU (6.703%), 
            H-4C.
          
        
      
      
        "Algal Introns" [ 69 ] .
      
      
        Conclusions
        variation;
        of this writing.
        ( 
      
      
        

          CRW RDBMS.
        
        
        
        
          
          
          
            Classification of introns
            intron classification ( 
            subgroups.
          
          
            Chara sp. Qiu 96222 (AF191800;
          
          
            About TBD and NSEQ
          
        
        
          
          
          
            Diagrams
          
        
        
          
          
          
          
          
          
        
      
      
        Information.
      
    ```
one can easily see the words that does not contains letter "e", which could be useful for some tasks. 

  - Directories
```
linda@Yutongs-MacBook-Pro biomed % grep -v "and" biomed             
grep: biomed: No such file or directory
```
Unfortunatley this does not apply on directoreis.   


## Work Cited
Chat GPT
   
   **Prompt: give me 8 grep command-line options that works on files and directories**
   Answer: Certainly! Here are eight `grep` command-line options that can be used for searching text patterns in both files and directories:

1. `-r` (Recursive Search):
   - Use `-r` to perform a recursive search, searching for text patterns in files within directories and their subdirectories.

2. `-l` (List Matching Files):
   - Use `-l` to list only the names of files that contain the pattern, rather than displaying the matching lines.

3. `-v` (Invert Match):
   - Use `-v` to invert the match, displaying lines that do not contain the pattern.

4. `-n` (Display Line Numbers):
   - Use `-n` to display line numbers along with matching lines.

5. `-c` (Count Matches):
   - Use `-c` to count the number of matching lines in files without displaying the lines themselves.

6. `-w` (Match Whole Words):
   - Use `-w` to match whole words, ensuring that the pattern is not part of a larger word.

7. `-E` (Extended Regular Expressions):
   - Use `-E` to enable extended regular expressions for more complex pattern matching.

8. `-o` (Display Only Matching Part):
   - Use `-o` to display only the matching part of the line, rather than the entire line.

These options provide you with flexibility when searching for text patterns in both files and directories using `grep`.

   **Prompt: is -r the only grep command-line that works on both directory and files?** 
   Answer: Yes, the `-r` (recursive) option in `grep` is the primary option that is used to search for text patterns within both directories and files. It allows you to perform a recursive search in directories and their subdirectories, searching for patterns within files contained in those directories.

While some other `grep` options may also apply to directories (such as `-l` for listing matching files), they are typically used to modify the behavior of `grep` when working with individual files rather than directories.

*I did not use or change any of the output, since I just used it as a seaching engine/tutor*


   

     


