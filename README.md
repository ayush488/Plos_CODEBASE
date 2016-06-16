# Plos_CODEBASE
#Contains code for extraction disease-gene-mutation triplets from PubMed literature.

#Author: Ayush Singhal
#Folder_name: "PloS_CODEBASE"

	A. Pre-compiled dictionaries:
	
		1. BingApi_Dict.p: Contain fetched data from Bing server for mutation search; may not be useful for this version of code since Bing function is de-activated.
		2. CDT_MeSh_2_DiseaseName.p: Contains CDT mapping between MeSH IDs and corresponding disease names.
		3. Entrez2uniprotID.p: Mapping for converting NCBI's Entrez ID to Uniport Accession numbers.
		4. gene_new_list.p: Mapping of gene name to NCBI's Entrez ID.
		5. Gene_Sym2ID.p: Maps HUGO gene names to NCBI's Entrez ID for genes. 
		6. GeneDB_latest.p: This is same as (4); it is not used but I recommend to keep it in the folder.
		7. GeneidMap.p:This is same as (4); it is not used but I recommend to keep it in the folder. Sorry for so many duplications.
		8. GenSeq_FASTA.p: Contains NCBI's gene sequence for checking mutation position in neocleotide sequences. 
		9. HUGO_dict.p: Contains the HUGO Gene names for dictonary based look up. 
		10. human_gene_check.p: A dictionary to check its presence in this human only gene dictionary. Used to filter non-human genes.
		11. NCBI_gene_protein_map_full2.p: A mapping from NCBI gene Entrez ID to corresponding Proteins (and isoforms).
		12. NCBI_protein_FASTA.p: Contains the FASTA sequences for the protein IDs. 
		
	B. Non-used text and .csv files:
	
		1. PCa_Merged_unq_mut_dis_weka_features.csv: training data for Machine Learning algorithm.
		2. CDT_disease_map.txt: contains diseases and Mesh IDs.
		3. HUGOGeneNames.txt: HUGO gene names.
		4. gene_result_latest.txt: NCBI's lastest dump of genes.
		
	C. Python codes:
	
		a. External libraries required to be installed:
		
			1.TextBlob : https://textblob.readthedocs.io/en/dev/ : very simple to install.
			2.	Sklearn, numpy : Bsaic libraries which can be easily installedtalled.
			
		b. Other Codes:
		
			final_triplet_extraction.py: The main file which the user should run. Please provide your email address to use Entrez facilities. Provide a disease MeSH_ID for the disease you want the triplets. Rest it wil create all folders and files based on the disease name. Note: No Need to mention the disease name.
			fetchAll.py: Fetches PMIDs for the disease from PubMed.
			get_from_web_Pub.py: Fetches PubTator output for the PMIDs.
			get_Testful_api_results_into_text.py: Seprates disease,gene, mutation and abstract text information from the PubTator outputs.
			remove_non_SUB_mutations.py: Filters inconsistent mutations from PubTator output.
			filter_disease.py: Filters inconsistent disease from PubTator output.
			Match_disese_with_tmVar_mutation.py: Builds match between mutation and disease mention in abstract using PubTator output.
			Large_dataset_count_disease.py: get frequency of disease terms in the abstract for ML features.
			convert_Dnorm_file_to_EMU_input.py: Convet PubTator abstract text output to single line (EMU style) format.
			check_inbetween_text_for_sentiment.py: Checks sentiments of text between mutation mention and disease mention.
			get_all_features_merged.py: Merges several features for ML classification input.
			csv_input_for_weka_prep.py: Cleaning up of ML classification input.
			predict_using_DT_for_large.py: Classification of mutation-disease relationship using Decision tree classifier. 
			print_most_frequent_mutations.py: Ranks mutations based on PMID support count.
			find_genes_using_GeneDb.py: Prepares Gene database for finding genes.
			new_code_gene_prediction_includes_protein_isoform_check_nearest_gene_mention.py: Code for assigning genes to the mutation (includes sequence validation, protein isoform check)
			prepare_output_file.py: tp get the final output file.

	D. Commands to run the code:
	
		1. Install the extration libraries as mentioned in C.a
		2. Do not change the location of the codes. Keep all of them in one place.
		3. Open the final_triplet_extraction_code.py
		4. This file requires 3 input from the users [See lines 45-48]
			i. disease_meshID: provide the MeSH ID for the disease you want to extract triplet. Please use the format: 'MESH:D010190' (Sample). Please do not write a disease name here; program will not run.
			ii. path: Enter the path where you want the folder for this disease to be created. You need not make a folder for diseaes name. This path on tells where to keep everything. E.g.: 'E:\\ANIH\\Precision_medicine_project\\general_codes\\'. Please include the last two backslashes as well.
			iii. email: please enter a valid email because it is required to use Entrex facilities. 
		5. Once you have provided all the inputs, press the run button and wait... it will take sometime to get the output.... It will alarm you with a beep once the output is ready!

		
