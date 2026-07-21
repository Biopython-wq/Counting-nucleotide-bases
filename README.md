# Counting-nucleotide-bases
# Counting bases and finding GC content
# from Bio import SeqIO
# def basecount(file,name):
#     for sequence in SeqIO.parse(file,"fasta"):
#         dna = sequence.seq
#     compleseq =dna.complement()
#     totalcount = dna.count("A")+compleseq.count("A")
#     totalcount2 = dna.count("T")+compleseq.count("T")
#     totalcount3 = dna.count("G")+compleseq.count("G")
#     totalcount4 = dna.count("C")+compleseq.count("C")
#     GCcount = ((totalcount3+totalcount4)/len(dna))*100
#     #print(" Adenine count is ",totalcount,"Thymine count is",totalcount2,"Guanine count is",totalcount3,"Cytosine count is",totalcount4)
#     print(f"total gc content for {name}is {GCcount:.2f}%")
# basecount("sequence.fasta","cannabis sativa")
# basecount("sequence2.fasta","thermus thermophilus")
# Transcritption
# from Bio import SeqIO
# def rna (file,name):
#   for sequence in SeqIO.parse(file,"fasta") :
#     dna = sequence.seq
#     rna = dna.replace("T","U")
#     print(f" Rna sequence for {name} is ",rna)
# rna("sequence.fasta","cannabis sativa")
# rna("sequence2.fasta","thermus thermophilus")

#Translation
from Bio import SeqIO
from Bio.Data import IUPACData
def trans (file,name):
 for sequence in SeqIO.parse(file,"fasta"):
    dna = sequence.seq
    rna = dna.replace("T","U")
    trimseq = len(rna)-(len(rna)%3)
    trimlen = rna[:trimseq]
    for i in range(0,len(trimlen),3):
        codon =trimlen[i:i+3]
        protein = codon.translate()
        aa =IUPACData.protein_letters_1to3_extended
        for x in protein:
            print(codon,protein,aa.get(x,x))
trans("sequence.fasta","cannabis sativa") 
