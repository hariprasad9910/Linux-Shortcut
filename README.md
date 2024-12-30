# Write a scripy in CLI without using text editor
cat <<'EOF'> hh.sh
echo " Hello, World!"
EOF
-------------------------------------------------------------
# Count the files in the folder of particular pattern(ex: .mol, .pdb, .sdf, .fasta)
ls *.mol 2>/dev/null | wc-l
---------------------------------------------------------------------------------------------------------------------------------------------------------------
# Download the as many as files from the URL present in the .txt file separatly
for file in .txt; do
wget -i "$file"
done
----------------------------------------------------------------------------------------------------------------------------------------------------------------
# Select and extract the particular column data in .csv file & save the output 
cut -d ',' -f1,7 data.csv > output.csv
----------------------------------------------------------------------------------------------------------------------------------------------------------------
# Splits single files in to seaprate files whihc contain string ">" from the first line of accession ID and rename accession name it their seaprate file 
awk '/^>/ {if (out) close(out); out=substr($0, 2)".fasta"} {print > out}' your.fasta
Example Input:
>accession1
ATCGGCTA
>accession2
GCTAGCTA
Output: accession1.fasta(>accession1 ATCGGCTA) accession2.fasta(>accession2 GCTAGCTA)
----------------------------------------------------------------------------------------------------------------------------------------------------------------
# Add double quotes(") around each accession number present in   the folder and arrnge them in vertically
ls *.fasta | awk '{print "\" $0 "\"}' > quoted_accession.txt
