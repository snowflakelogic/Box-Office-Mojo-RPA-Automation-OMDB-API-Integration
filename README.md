# Box Office Mojo RPA Automation & OMDB API Integration

A comprehensive UiPath RPA workflow with intelligent API integration for automated data extraction from Box Office Mojo and real-time movie metadata enrichment via OMDB API, featuring advanced data preprocessing and cleaning pipeline.

## 📋 Project Overview

This RPA solution automates the complete data pipeline for movie analytics:
1. **RPA Data Extraction**: Intelligent web scraping from Box Office Mojo's website
2. **API Integration**: Seamless OMDB API integration for enriched movie metadata
3. **Data Processing**: Comprehensive preprocessing and cleaning for analysis-ready datasets
4. **Automated Export**: Clean, structured data output for downstream applications

## 🖼️ Workflow Screenshot

![UiPath Workflow](RPA_UIPATH_DATA_EXTRACTION.PNG)

*Box Office Mojo RPA Data Extraction Workflow*

## 🎯 Features

### Core RPA Automation Features
- **Intelligent Web Navigation**: Automated browser control and navigation to Box Office Mojo pages
- **Dynamic Data Extraction**: Advanced table scraping with adaptive selectors
- **Multi-Country Support**: Scalable extraction across different geographical regions
- **Error Handling**: Robust exception handling and retry mechanisms

### Advanced API Integration
- **OMDB API Integration**: Real-time movie metadata enrichment
- **Rate Limiting Management**: Intelligent request throttling and optimization
- **Data Validation**: API response validation and error handling
- **Batch Processing**: Efficient handling of multiple API requests

### Automated Data Processing
- **Date Standardization**: Automated date format conversion (YYYY-MM-DD)
- **Data Type Optimization**: Smart conversion of percentages and currency values
- **Missing Value Handling**: Intelligent imputation and data quality management
- **Export Automation**: Seamless CSV generation and file management

## 🛠️ Technical Requirements

### Software Dependencies
- **UiPath Studio** (Latest version recommended)
- **UiPath Robot** for execution
- **Modern web browser** (Chrome/Edge recommended)
- **Python** (for OMDB API integration and data preprocessing)

### UiPath Packages Required
- `UiPath.WebAPI.Activities`
- `UiPath.Excel.Activities`
- `UiPath.System.Activities`
- `UiPath.UIAutomation.Activities`

### Python Dependencies
```python
pip install pandas numpy requests tqdm
```

### API Requirements
- **OMDB API Key**: Register at [OMDB API](http://www.omdbapi.com/) for movie metadata access

## 📁 Project Structure

```
BoxOfficeMojo_RPA_API/
├── Main.xaml                 # Main UiPath RPA workflow
├── Data/
│   ├── MOJO_ALL.csv         # Raw extracted data
│   ├── processed_data.csv   # API-enriched and cleaned data
├── Scripts/
│   ├── data_preprocessing.py # Data cleaning and OMDB integration
│   ├── omdb_api.py          # OMDB API handler and utilities
├── Config/
│   ├── config.json          # API keys and automation settings
├── Screenshots/             # Workflow documentation
└── README.md               # This file
```

## 🔧 Complete Workflow Process

### Phase 1: RPA Automation
1. **Initialize** - Set up browser automation environment
2. **Navigate** - Intelligent navigation to Box Office Mojo pages
3. **Extract** - Dynamic table extraction with error handling
4. **Store** - Raw data storage in structured format

### Phase 2: Data Preprocessing
1. **Format Standardization** - Date formatting (YYYY-MM-DD)
2. **Data Cleaning** - Remove inconsistencies and format data
3. **Validation** - Quality checks and data integrity verification

### Phase 3: OMDB API Integration
1. **API Configuration** - Set up OMDB API credentials and rate limiting
2. **Metadata Extraction** - Automated movie data enrichment:
   ```python
   df[['OMDB_Runtime', 'OMDB_Genre', 'OMDB_imdbID', 'OMDB_Budget']] = df['#1 Release'].progress_apply(fetch_omdb_data)
   ```
3. **Data Merging** - Intelligent integration of API responses with scraped data

### Phase 4: Advanced Processing & Export
1. **Data Optimization** - Column management and unnecessary data removal
2. **Type Conversion** - Automated percentage and currency formatting
3. **Missing Value Handling** - Smart imputation strategies
4. **Export** - Clean, analysis-ready data output

## 🚀 Setup Instructions

### 1. Environment Setup
```bash
# Install UiPath Studio
# Install Python and required packages
pip install pandas numpy requests tqdm

# Set up browser automation
# Verify internet connectivity
```

### 2. API Configuration
1. Register for OMDB API key at http://www.omdbapi.com/
2. Create `Config/config.json`:
```json
{
    "omdb_api_key": "your_api_key_here",
    "output_path": "Data/",
    "delay_between_requests": 1
}
```

### 3. Project Configuration
1. Clone or download the project files
2. Open `Main.xaml` in UiPath Studio
3. Update the target URL if needed
4. Configure output file paths
5. Set up Python script paths in UiPath workflow

## ▶️ Execution Steps

### Complete Pipeline Execution
1. **Run RPA Extraction**:
   - Open UiPath Studio
   - Load `Main.xaml` workflow
   - Execute data extraction process

2. **Run Data Processing**:
   ```bash
   python Scripts/data_preprocessing.py
   ```

3. **Verify Output**:
   - Check `processed_data.csv` for enriched dataset
   - Validate data quality and completeness

### Automated Execution
1. Create batch script combining RPA and Python processing
2. Schedule via UiPath Orchestrator or system scheduler
3. Set up monitoring and error notifications

## 📊 Data Output

### Enhanced Dataset Structure
The processed dataset includes:

#### Original Box Office Data
- Movie titles, rankings, revenue figures
- Weekend performance metrics
- Country-specific data

#### OMDB Enriched Data
- **OMDB_Runtime**: Movie duration in minutes
- **OMDB_Genre**: Movie genres (comma-separated)
- **OMDB_imdbID**: IMDb identifier for cross-referencing
- **OMDB_Budget**: Production budget information

#### Processed Fields
- **Standardized Dates**: YYYY-MM-DD format
- **Numeric Values**: Clean float representations of percentages and currency
- **Quality Indicators**: Data completeness and validation flags

### File Outputs
- **Raw Data**: `Data/MOJO_ALL.csv`
- **Processed Data**: `Data/processed_data.csv`
- **Processing Log**: `Data/processing_log.txt`

## 🔍 Troubleshooting

### RPA Issues
**Browser Not Opening**
- Verify browser installation and UiPath extensions
- Update browser drivers

**Data Not Extracting**
- Check website structure changes
- Update CSS selectors

### API Issues
**OMDB API Errors**
- Verify API key validity
- Check rate limiting (1000 requests/day for free tier)
- Implement retry mechanisms for failed requests

**Data Processing Errors**
- Check Python dependencies
- Verify data format consistency
- Review error logs for specific issues

### Performance Optimization
- Implement caching for OMDB requests
- Use batch processing for large datasets
- Add progress tracking for long-running operations

## 📈 Applications & Use Cases

### Data Science & Analytics
The processed dataset enables:
- **Movie Performance Analysis**: Revenue trends and market insights
- **Genre Analysis**: Performance patterns across different movie categories
- **Budget ROI Studies**: Cost vs. revenue analysis using OMDB budget data
- **Market Research**: Geographic and temporal box office patterns
- **Predictive Modeling**: Features for machine learning applications

### Business Intelligence
- **Market Intelligence**: Competitive analysis and industry insights
- **Investment Decisions**: Data-driven movie financing decisions
- **Distribution Strategy**: Geographic performance optimization
- **Content Strategy**: Genre and runtime impact analysis

## 🔄 Maintenance & Updates

### Regular Maintenance
- **API Key Management**: Monitor OMDB API usage limits
- **Selector Updates**: Maintain web scraping reliability
- **Data Quality Monitoring**: Regular validation checks
- **Performance Optimization**: Monitor processing times

### Data Quality Assurance
- Automated data validation rules
- Missing value monitoring
- Outlier detection and handling
- Cross-reference validation with external sources

## 📝 Future Enhancements

### Planned Enhancements
1. **Multi-API Integration**: TMDb, Rotten Tomatoes, and other movie databases
2. **Advanced RPA Features**: Parallel processing and dynamic country selection
3. **Real-time Monitoring**: Live data extraction and processing capabilities
4. **Cloud Deployment**: AWS/Azure automation and API management
5. **Machine Learning Pipeline**: Automated feature engineering and model training
6. **Advanced Error Recovery**: Sophisticated retry mechanisms and fallback strategies

### RPA & API Optimization
- **Intelligent Scheduling**: Dynamic extraction timing based on data freshness
- **API Caching**: Redis/database caching for repeated requests
- **Distributed Processing**: Multi-bot RPA execution
- **Performance Monitoring**: Real-time automation metrics and alerting

## 🤝 Contributing

### Development Guidelines
1. Fork the repository
2. Create feature branch for new functionality
3. Test with sample datasets
4. Document API changes and new features
5. Submit pull request with comprehensive testing

### Code Standards
- Follow PEP 8 for Python code
- Include error handling and logging
- Add unit tests for new functions
- Update documentation for changes

## 📄 License & Compliance

This project is for educational and research purposes. Ensure compliance with:
- Box Office Mojo's terms of service
- OMDB API usage policies
- Data privacy regulations
- Fair use guidelines for commercial applications

---

**Maintained by**: snowflakelogic  
**Last Updated**: June 2025  
**Version**: 2.0 - RPA & API Integration Focused  
**Focus**: Automated Data Extraction & API Integration Pipeline
