# Data Hosting Update
Due to significant dataset expansion to enhance experimental reproducibility and accessibility, the full data resources have been migrated to Zenodo for stable long-term archival. The dataset remains permanently available at:
Liu, Y. (2025). Urban street network morphology classification through street-block based graph neural networks and multi-model fusion (Version 1.0) [Data set]. Zenodo. https://doi.org/10.5281/zenodo.15315222

# 1.1 Dataset Overview

The **Urban Street Network Morphology Subtypes (USNMS)** dataset is designed for the analysis of urban street network structures, focusing on major U.S. cities. The dataset contains over 6,700 samples, each representing a 1 km × 1 km grid patch. The data was constructed using OpenStreetMap (OSM) data extracted from 12 major U.S. cities using the OSMnx tool.

The dataset is categorized into six distinct urban street network morphology types, reflecting various street patterns observed in urban areas:  
- **Regular Grid**  
- **Irregular Grid**  
- **Broken Grid**  
- **Warped Parallel**  
- **Loops & Lollipops**  
- **Sparse**

These categories were defined based on both prior research and expert visual inspection of street patterns within the study areas.

# 1.2 Dataset Construction

The USNMS dataset was constructed with the goal of supporting urban planning and network analysis research. It leverages data extracted from OpenStreetMap (OSM) through the OSMnx tool. The dataset is divided into 1 km × 1 km grid patches, each representing a sample of street network morphology from urban areas of 12 U.S. cities.

The six morphology categories were selected based on a combination of factors, including recognition of street network patterns in existing studies and the characteristics of street layouts observed in the study areas. The categories represent a diverse set of urban street network forms, from highly structured grid patterns to more irregular and disconnected layouts.

# 1.3 Sample Labeling

Sample labeling for the dataset was performed manually by a team of urban planning experts, ensuring high accuracy in the classification of urban street network morphology. The labeling process followed a rigorous, expert-driven approach:

- **Expert Evaluation:** Three experts independently reviewed the street network samples and assigned labels based on predefined categories.  
- **Majority Voting:** In cases where there was disagreement (e.g., 1:1:1), the sample was discarded. Where there was a clear majority (e.g., 2:1), the majority label was assigned.  
- **Ambiguous Samples:** Some samples may have ambiguous labels due to the majority voting process. Users are encouraged to adjust these labels as necessary based on their needs.

# 1.4 Dataset Format and Data Loading

The USNMS dataset is stored in the **h5py** format, which is a versatile and efficient file format for storing complex data. The following fields represent the key data types within the dataset:

- **images:** Contains the image data for each 1 km × 1 km grid, represented as 3D arrays (Height × Width × Channels), with pixel values normalized to the range [0, 1].

- **nx_list (Street-Block Graph):** Contains the street-block graph data. This includes:
  - **Node Features:** Characteristics of each street block, such as area, perimeter, degree, and other geometric attributes.
  - **Edge Features:** Represents spatial relationships between street blocks.
  - **Adjacency Information (edge_index):** Defines the structure of the graph, representing the connection between street blocks.

- **dual_graph_nx_list (Dual Graph):** Contains the dual graph, representing streets and their relationships.

- **primal_graph_nx_list (Primal Graph):** Contains the primal graph, representing intersections and streets used for calculating node-level attributes, distinct from the dual graph.

- **global_handcrafted_features:** Stores global descriptors that represent overarching characteristics of the street network. These descriptors capture network-wide features, such as node count, edge count, total edge length, and other high-level network properties.

- **label0:** Represents the label for each sample, indicating the type of street network morphology (e.g., "Regular Grid", "Irregular Grid").

- **edges_precise_matches:** Contains precise matching information for street edges correponding to 1km*1km grid. This data is stored in GeoDataFrame format and provides spatial attributes for street network analysis.
.
- **nodes_precise_matches:** Contains precise matching information for nodes correponding to 1km*1km grid. This data is stored in GeoDataFrame format and provides spatial attributes for street network analysis.

- **polygons_df:** Contains polygonal data corresponding to 1 km × 1 km grid sections. This data is stored in GeoDataFrame format and provides spatial attributes for street network analysis.

- **splits:** Defines the dataset splits for training, validation, and testing, facilitating cross-validation during model training and evaluation.

- **splits_train_ratio_0.6, splits_train_ratio_0.8:** Store dataset partitioning information for training, validation, and test splits, with training ratios of 60% and 80%, respectively.

The data loading and processing follow a structured approach, where different types of data (images, graphs, global features) are loaded based on their type, and each graph is processed to extract node features, edge attributes, and adjacency information, allowing for seamless integration into graph-based learning tasks.
 

# 1.5 Dataset Partitioning

The USNMS dataset is split into training, validation, and test sets in a 6:2:2 ratio for 10-fold cross-validation. This partitioning enables the dataset to be used for model training, evaluation, and generalization tests.

# 1.6 Citation

For more details on the methodology and application of the USNMS dataset, please refer to the related paper:

**Title:** Urban street network morphology classification through street-block based graph neural networks and multi-model fusion  
**Authors:** Yang Liu, Qingsheng Guo, Chuanbang Zheng  
**Journal:** *International Journal of Digital Earth*  
**DOI:** [https://doi.org/10.1080/17538947.2025.2497490](https://doi.org/10.1080/17538947.2025.2497490)


The dataset supports various machine learning and network analysis tasks, such as urban morphology classification and graph-based analysis of street networks.

