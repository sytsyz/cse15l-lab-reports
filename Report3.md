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
   r stands for recursive. grep -r search all things containg keword (in this case "Darwin") of the working directory and its sub directories.
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

- Directory
  ```
  linda@Yutongs-MacBook-Pro technical % grep -n "Darwin"  biomed
  grep: biomed: Is a directory
  ```
  n can only be applied on files.

4. -v
- Files
  ```
  linda@Yutongs-MacBook-Pro biomed % grep -v  "a"  1471-2105-3-2.txt  

  
    
      
        tree.
        13 ] .
        determined for 
        E. coli in 1978 [ 14 ] , the first
        more 16S rRNA sequences were determined [ 15 16 17 ] . The
        E. coli in 1980 [ 18 ] ; the first
        e.g., U:U <-> C:C; A:A
        <-> G:G; G:U <-> A:C; 
        been studied with this perspective. These include the group
        RNA molecules ( 
      
      
        
          
            1A. Current structure models for reference
            Methods Section
            two RNAs.
            E. coli is the preferred choice
            
            from the "Current Structure Models for Reference
            PDF
            
            The 
            E. coli positions 9-13/21-25, is
            below). The 
            The 
            In th*/e 
            Helices" plot
            the 
            E. coli 16S rRNA, with 1542
            For the 
            E. coli 23S rRNA (2904 nt), there
            (see CRW Methods
            of structure models.
          
          
            structure models
            structure models were determined independently of ours,
            (H-1B.2).
            the structure models.
          
          
            1C. RNA structure definitions
            A:U, or G:U; 
            within three or more helices).
          
        
        
          
            the rows. The nucleotide frequencies were determined
            the reference sequence, for every RNA in this
            e.g., A:U <-> G:C) is
            etc. ). The collective score for
            C1+C3 scores >= 1.5.
          
          
            phylogenetic tree
            the NCBI phylogenetic tree
            tree, with the frequencies for the selected single
            phylogenetic tree from the point of origin, which is
            ("*").
          
          
            study ( 
            conserved in 98-100% of the sequences in the group
            90-98% of the sequences in the group (shown with red
            open circles).
            the group.
            ( 
            introns.
            given sequence should consult the CRW RDBMS (see
          
        
        
          
            elements ( 
            positioning of the sequence positions in our
            them.
          
          
            Aligning new sequences
            phylogenetic tree ( 
            regions ( 
            semi-conserved regions ( 
            sub-second ( 
            phylogenetic tree. However, regions of the sequences
            regions ( 
            sequences in 1988 (see Figures 35-43 in [ 48 ] ).
          
          
            of these two sequences, the sequence for the new
            priority over other rRNA sequences.
            CRW RDBMS.
            4A-4B.
          
          
            structures
          
          
            then the links in the structure field.
          
          
            queries.)
          
          
            June 2002.
          
          
            3E. rRNA Introns
            position in the rRNA, 2) intron type, 3) phylogenetic
            gene.
          
          
            E. coli rRNA reference sequence
            e.g., the introns between
            rRNA introns, sorted by the numeric order of the intron
            the intron position; 3) the number of documented
            distributed into four distinct phylogenetic groups,
            etc.
            comment.
            number of introns per rRNA position; 2) number of
            introns per rRNA site.
            distributed over 152 different positions, 84 in the 16S
            positions is not evenly distributed (1184/152 = 7.79
            distribution of rRNA introns with the Poisson
            distribution for the observed number of introns. The
            Poisson distribution, 
            P(x) = 
            e -μμ 
            x 
          
          
            three subgroups: I (276 introns), IC1 (415 introns),
            rRNA group I introns (753 vs. 227). 4) Among the three
            from 49 to 292 nucleotides. A future version of this
            group.
          
          
            Distribution
            The distribution of introns on the phylogenetic tree
            the number of rRNA introns per rRNA gene for the
            the 90% completeness criterion for inclusion in this
            phylogeny, followed by fields for the genus of the
          
          
            Exon
            expected.
            two introns), grouped by their exons. As with the other
          
          
            3F. Group 1/11 Intron distributions
          
        
        
          
            Step 1. At the onset, the user selects the fields to
            ( 
            "Qintron" (query intron), or "All" options will
            H-4A.1).
            in the scroll box.
            field.
            word.
            tree.
            sequence entry to be identified with this method. In
            etc.; H-4A.3). Accordingly, the
            Selecting "Mosses" brings up the phylogeny for the
            by simply clicking the "S" buttons in the order the
            low number) by checking the box in the "R" (or reverse)
            entries, only those entries 
            entries 
            the sort order for this query.
            sequence.
            clicking the "m" button in the Phylogeny column. This
          
          
            4B. RDBMS (PhyloBrowser)
            group is shown in red preceding the phylogenetic group
            ( 
            (H-4B.3).
            NCBI phylogeny from the root to the level of the
            selections. After clicking the white "Submit" button,
            (rRNA: 5S, green; 16S, red; 23S, blue; introns: group
            in our CRW RDBMS for RNA types ( 
            e.g., Chl, Mit, Nuc).
          
          
            4C. RNA Structure Query System
            positions (42.64%), followed by G (23.6%), U (21.27%),
            by GA (13.35%), UA (9.821%), AU (6.703%), 
            (24.99%; H-4C.4), followed by AC (13.28%), GG (8.28%), 
            H-4C.
            online.
          
        
      
      
        "23S rRNA Folding" [ 66 ] ). In the "Phylogenetic Structure
      
      
        Conclusions
        positions in the reference structure;
        structure;
        of this writing.
        ( 
        supported.
      
      
        
          Sequence collection
          e.g., the 

          CRW RDBMS.
        
        
          exons ( 
          number of nucleotides.
        
        
          sequences
          
          
          
            34 ] or the more recently determined subgroup IE [ 82 ]
            e.g., group I or group II) but
            not the specific intron type ( 
            subgroups.
          
          
          
          
          
        
        
          
            intron-specific)
            utilizes the MySQL engine http://www.mysql.com/. The
            e.g., rRNA or intron); 5) RNA
            exon), intron position (for rRNA introns only: the 
          
          
            by XRNA were converted into PDF using ghostscript
            (version 7.00;
            http://www.cs.wisc.edu/~ghost/index.htm).
          
        
        
          
            (version 3.23.29; http://www.mysql.com/) provides the
          
          
          
          
            URL rewriting
            specific URLs.
          
        
      
      
        nt = nucleotide
      
    ```
  v is invert match. When applied to files, the result of lines that does not contains the key word will be displayed. This is usefule when you want to view the file without undisred distracting informations.

  - Directories
```
linda@Yutongs-MacBook-Pro biomed % grep -v "and" biomed             
grep: biomed: No such file or directory
```
Unfortunatley this does not apply on directoreis.   


## Work Cited
1. Chat GPT
   
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


   

     


