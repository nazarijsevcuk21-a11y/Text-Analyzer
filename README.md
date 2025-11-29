# Text-Analyzer
A project to demonstrate skills
# Text Analyzer

A comprehensive tool for statistical text analysis with data visualization capabilities. Supports word counting, frequency analysis, stop-word filtering, and generates professional charts.

## Features

### Statistical Analysis
- Word, sentence, and character counting
- Unique words and vocabulary richness calculation
- Word frequency analysis
- Word length distribution
- Average sentence length
- Longest words identification

### Text Processing
- Tokenization (word splitting)
- Stop-word removal (Ukrainian/English)
- Punctuation cleaning
- Sentence segmentation
- Text normalization

### Data Visualization
- Word frequency charts (horizontal bar charts)
- Word length distribution plots
- Summary dashboard (4-panel overview)
- Word visualization (bubble chart)
- File comparison charts

### Export Capabilities
- CSV - word frequency data
- TXT - detailed text reports
- PNG - high-quality charts (300 DPI)

## Technologies

- Python 3.8 or higher
- pandas - data processing
- matplotlib - chart generation
- seaborn - enhanced visualizations
- numpy - numerical operations

## Installation

```bash
git clone https://github.com/yourusername/text-analyzer.git
cd text-analyzer
pip install -r requirements.txt
```

## Quick Start

### Basic Usage

```bash
python text_analyzer.py
```

The script will:
- Analyze sample text
- Generate 4 types of charts
- Create a text report
- Export data to CSV

Check the `output/` folder for results.

### Run Examples

```bash
python examples.py
```

This demonstrates 7 different usage scenarios.

## Usage as Library

### Basic Analysis

```python
from text_analyzer import TextAnalyzer

# Create analyzer
analyzer = TextAnalyzer(language='en')

# Set text
analyzer.set_text("Your text here...")
analyzer.tokenize()

# Get statistics
stats = analyzer.get_basic_stats()
print(stats)

# Generate charts
analyzer.plot_word_frequency()
analyzer.plot_statistics_summary()
```

### Analyze File

```python
analyzer = TextAnalyzer()
analyzer.load_text('article.txt')
analyzer.tokenize()
analyzer.save_report()
```

### Word Frequency

```python
analyzer.tokenize()
freq = analyzer.word_frequency(top_n=20, remove_stop_words=True)

for word, count in freq.most_common(10):
    print(f"{word}: {count}")
```

## API Reference

### TextAnalyzer Class

#### __init__(language='en')
Initialize analyzer. Language options: 'en' or 'uk'.

**Parameters:**
- language (str) - text language for stop-words

#### load_text(filepath)
Load text from file.

**Parameters:**
- filepath (str) - path to text file

**Returns:** str

#### set_text(text)
Set text for analysis.

**Parameters:**
- text (str) - text content

#### tokenize(clean=True)
Split text into words.

**Parameters:**
- clean (bool) - remove punctuation if True

**Returns:** List[str]

#### split_sentences()
Split text into sentences.

**Returns:** List[str]

#### get_basic_stats()
Get comprehensive statistics.

**Returns:** Dict with keys:
- total_characters
- total_words
- unique_words
- total_sentences
- avg_word_length
- avg_sentence_length
- vocabulary_richness

#### word_frequency(top_n=20, remove_stop_words=True)
Calculate word frequency.

**Parameters:**
- top_n (int) - number of top words
- remove_stop_words (bool) - filter stop-words

**Returns:** Counter object

#### plot_word_frequency(top_n=20, remove_stop_words=True, save=True)
Generate word frequency chart.

#### plot_word_length_distribution(save=True)
Generate word length distribution chart.

#### plot_statistics_summary(save=True)
Generate summary dashboard with 4 panels.

#### generate_report()
Generate detailed text report.

**Returns:** str

#### export_to_csv(frequency, filename)
Export word frequency to CSV.

## Examples

### Example 1: Compare Texts

```python
from text_analyzer import analyze_multiple_files

files = ['text1.txt', 'text2.txt', 'text3.txt']
df = analyze_multiple_files(files, language='en')

print(df)
# Automatically creates comparison chart
```

### Example 2: English Text Analysis

```python
analyzer = TextAnalyzer(language='en')
analyzer.set_text("Your English text here...")
analyzer.tokenize()

# Get statistics
stats = analyzer.get_basic_stats()
print(f"Total words: {stats['total_words']}")
print(f"Unique words: {stats['unique_words']}")

# Word frequency
freq = analyzer.word_frequency(top_n=15, remove_stop_words=True)
for word, count in freq.most_common(10):
    print(f"{word}: {count}")
```

### Example 3: Custom Stop Words

```python
analyzer = TextAnalyzer()
analyzer.stop_words = {'word1', 'word2', 'word3'}

analyzer.set_text(text)
freq = analyzer.word_frequency(remove_stop_words=True)
```

### Example 4: Full Analysis Suite

```python
analyzer = TextAnalyzer(language='en')
analyzer.load_text('document.txt')
analyzer.tokenize()
analyzer.split_sentences()

# Generate all visualizations
analyzer.plot_word_frequency(top_n=15)
analyzer.plot_word_length_distribution()
analyzer.plot_statistics_summary()
analyzer.plot_word_cloud_data(top_n=30)

# Export data
freq = analyzer.word_frequency(top_n=50, remove_stop_words=True)
analyzer.export_to_csv(freq, 'word_frequency.csv')

# Generate report
analyzer.save_report('analysis_report.txt')
```

## Project Structure

```
text-analyzer/
├── text_analyzer.py      # Main module (600+ lines)
├── examples.py           # Usage examples
├── requirements.txt      # Dependencies
├── README.md            # Documentation
├── QUICKSTART.md        # Quick start guide
└── output/              # Output files (auto-created)
    ├── *.png            # Charts
    ├── *.csv            # Data
    └── *.txt            # Reports
```

## Visualization Types

### Word Frequency Chart
Horizontal bar chart showing top N most frequent words with color gradient.

### Word Length Distribution
Bar chart displaying word count by character length, includes average line.

### Statistics Summary Dashboard
Four-panel chart showing:
- Basic metrics (words, unique words, sentences)
- Average values (word length, sentence length)
- Word ratio (unique vs repeated)
- Detailed text information

### Word Visualization
Bubble chart with word sizes proportional to frequency.

### Comparison Chart
When analyzing multiple files, displays comparison across 4 metrics:
- Total word count
- Unique word count
- Vocabulary richness
- Average sentence length

## Report Format

```
============================================================
                    TEXT ANALYSIS REPORT
============================================================

BASIC STATISTICS
------------------------------------------------------------
Total characters:          1,234
Total words:              200
Unique words:             150
Sentences:                15

Average word length:      5.5 characters
Average sentence length:  13.3 words

Vocabulary richness:      75.0%

============================================================

TOP 10 MOST FREQUENT WORDS
------------------------------------------------------------
 1. python              -   12 times
 2. analysis            -    8 times
 ...

============================================================

LONGEST WORDS
------------------------------------------------------------
1. word (15 characters)
2. word (14 characters)
...
```

## Metrics Explained

### Vocabulary Richness
```
(Unique words / Total words) * 100%
```

Higher values indicate more diverse vocabulary.

### Average Word Length
```
Sum of all word lengths / Number of words
```

Indicates lexical complexity.

### Average Sentence Length
```
Number of words / Number of sentences
```

Indicates syntactic complexity.

## Use Cases

### Article Analysis
Analyze news articles, blog posts, or scientific papers for readability and vocabulary.

### Author Comparison
Compare writing styles of different authors based on statistical metrics.

### SEO Analysis
Analyze keyword frequency in content for search engine optimization.

### Education
Assess text complexity for different reading levels.

### Research
Statistical analysis of text corpora for linguistic research.

## Configuration

### Matplotlib Styles

```python
import matplotlib.pyplot as plt
plt.style.use('seaborn')
```

### Chart Size

```python
plt.rcParams['figure.figsize'] = (16, 10)
```

### Export DPI

```python
plt.savefig('graph.png', dpi=300)  # High quality
```

## Performance

### Large Files

For large text files:

```python
# Read in chunks
with open('large_file.txt', 'r') as f:
    for chunk in iter(lambda: f.read(10000), ''):
        process_chunk(chunk)
```

### Memory Optimization

```python
# Use generators instead of lists
words = (word for word in text.split())

# Process in batches
for batch in batched(words, 1000):
    process_batch(batch)
```

## Testing

```bash
# Run all examples
python examples.py

# Check output
ls output/
```

Test scenarios include:
- Basic text analysis
- Word frequency calculation
- File loading
- Visualization generation
- English text processing
- Multiple file comparison
- Data export

## Troubleshooting

### Import errors
```bash
pip install pandas matplotlib seaborn numpy
```

### No output folder
Folder is created automatically on first run.

### Encoding issues
Specify encoding when loading files:
```python
with open('file.txt', 'r', encoding='utf-8') as f:
    text = f.read()
```

### Memory errors
Process large files in chunks or increase available RAM.

## Contributing

1. Fork the repository
2. Create feature branch: `git checkout -b feature/NewFeature`
3. Commit changes: `git commit -m 'Add NewFeature'`
4. Push to branch: `git push origin feature/NewFeature`
5. Open Pull Request

## License

MIT License - see LICENSE file for details

## Author

Your Name
GitHub: github.com/your_username
Email: your@email.com

## Acknowledgments

- pandas - data analysis library
- matplotlib - visualization library
- seaborn - statistical visualization
- numpy - numerical computing

## Support

For issues or questions:
- Create an issue on GitHub
- Email: nazarijsevcuk69@gmail.com

## Related Projects

- Telegram ToDo Bot - Task management bot
- Excel Automation - Automated Excel processing
- News Parser - Web scraping tool
- Currency API - Currency conversion service

---

Last updated: November 2025
Version: 1.0
Status: Production Ready
