---
title: "perl one-liner to change table layout with Hash-of-Hash-of-Array"
date: 2010-03-25T01:42:53+00:00
tags:
  - one-liner
  - perl
---
I really like one-liners which can do a lot in a single line.. I wanted to share one I just used to arrange a big table.

In the list of proteins below, only two proteins are shown, one protein has multiple attributes for 4 categories (InterPro, Cellular Component, Biological Process and Molecular Function). The other thing to notice is that, not all proteins have to have all the attributes, for instance, one protein might miss BiologicalProcess attribute.

<table style="border-collapse: collapse;" border="1" cellpadding="2" cellspacing="2">
  <tr>
    <td>
      protein1
    </td>
    
    <td>
      Interpro
    </td>
    
    <td>
      kinase
    </td>
  </tr>

  <tr>
    <td>
      protein1
    </td>
    
    <td>
      BiologicalProcess
    </td>
    
    <td>
      protein folding
    </td>
  </tr>

  <tr>
    <td>
      protein1
    </td>
    
    <td>
      BiologicalProcess
    </td>
    
    <td>
      metabolic process
    </td>
  </tr>

  <tr>
    <td>
      protein1
    </td>
    
    <td>
      MolecularFunction
    </td>
    
    <td>
      DNA binding
    </td>
  </tr>

  <tr>
    <td>
      protein1
    </td>
    
    <td>
      CellularComponent
    </td>
    
    <td>
      membrane
    </td>
  </tr>

  <tr>
    <td>
      protein2
    </td>
    
    <td>
      Interpro
    </td>
    
    <td>
      transferase
    </td>
  </tr>

  <tr>
    <td>
      protein2
    </td>
    
    <td>
      Interpro
    </td>
    
    <td>
      Methyltransferase
    </td>
  </tr>

  <tr>
    <td>
      protein2
    </td>
    
    <td>
      CellularComponent
    </td>
    
    <td>
      membrane
    </td>
  </tr>

  <tr>
    <td>
      protein2
    </td>
    
    <td>
      CellularComponent
    </td>
    
    <td>
      integral to membrane
    </td>
  </tr>
</table>

Out of this table, I'm trying to get the following table:

<table style="border-collapse: collapse;" border="1" cellpadding="2" cellspacing="2">
  <tr>
    <td >
      ProteinID
    </td>
    
    <td >
      InterPro
    </td>
    
    <td >
      Cellular Component
    </td>
    
    <td >
      Biological Process
    </td>
    
    <td >
      Molecular Function
    </td>
  </tr>

  <tr>
    <td >
      protein1
    </td>
    
    <td >
      kinase
    </td>
    
    <td >
      membrane
    </td>
    
    <td >
      protein folding; metabolic process
    </td>
    
    <td >
      DNA binding
    </td>
  </tr>

  <tr>
    <td >
      protein2
    </td>
    
    <td >
      transferase; Methyltransferase
    </td>
    
    <td >
      membrane; integral to membrane
    </td>
    
    <td >
    </td>
    
    <td >
    </td>
  </tr>
</table>


Do you think this is possible with perl one-liner? Yes, it is.. 

Below is the code (suppose that Table 1 is in file called `GeneCategories.txt`

```bash
perl -F"\t" -ane 'chomp($F[2]); push @{$hash->{$F[0]}->{$F[1]}},$F[2]; END {foreach $id (sort keys %$hash){print $id,"\t"; foreach $field qw(Interpro CellularComponent BiologicalProcess MolecularFunction){print join ";",@{$hash->{$id}->{$field}}; print "\t";}; print "\n"; } }' GeneCategories.txt
```

Let's breakdown the code now. As we know, you can run perl code within terminal in this format:

```bash
perl -e 'code'
```

If you want to run your code in a loop, then -n option should be used. In that case, either a filename should be provided or data should be piped to perl. Auto split can be turned on by -a option which will assign split elements to an array named @F.

If I don't indicate that TAB is the separator, then SPACE or TAB is considered as separator. Since my data contains SPACE, I should specifically indicate that TAB is the separator by `-F` option.

One more thing about running perl in commandline with `-n` option. Suppose you wish to run additional code before and/or after the loop, then you should use the following format:

```bash
perl -ne 'BEGIN {code1}; code2; END {code3}' filename
```

In this particular example, code1 will run before looping thru lines of filename and code3 will run after loop ended.

Okay, now the meaning of the actual code:

```perl
chomp($F[2])
```

Last column contains newline character at the end, I am removing it so that final output is not bad.

```perl
push @{$hash->{$F[0]}->{$F[1]}},$F[2]
```

This is the core part where one protein can have multiple categories (Hash of hash) and one category can hold multiple values in an array (Hash of hash of array). Whatever is in third column is pushed into an array referred by hash of hash `$hash->{ProteinNo}->{Category}`

After loop ended, hash structure is printed and mission accomplished..
