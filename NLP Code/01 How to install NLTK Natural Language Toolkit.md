# NLP Basics: What is Natural Language Processing & the Natural Language Toolkit?

### How to install NLTK on your local machine

Both sets of instructions below assume you already have Python installed. These instructions are taken directly from [http://www.nltk.org/install.html](http://www.nltk.org/install.html).

**Mac/Unix**

From the terminal:
1. Install NLTK: run `pip install -U nltk`
2. Test installation: run `python` then type `import nltk`

**Windows**

1. Install NLTK: [http://pypi.python.org/pypi/nltk](http://pypi.python.org/pypi/nltk)
2. Test installation: `Start>Python35`, then type `import nltk`

### Download NLTK data


```python
import nltk
nltk.download()
```

    showing info https://raw.githubusercontent.com/nltk/nltk_data/gh-pages/index.xml
    




    True




```python
dir(nltk)
```




    ['AbstractLazySequence',
     'AffixTagger',
     'AlignedSent',
     'Alignment',
     'AnnotationTask',
     'ApplicationExpression',
     'Assignment',
     'BigramAssocMeasures',
     'BigramCollocationFinder',
     'BigramTagger',
     'BinaryMaxentFeatureEncoding',
     'BlanklineTokenizer',
     'BllipParser',
     'BottomUpChartParser',
     'BottomUpLeftCornerChartParser',
     'BottomUpProbabilisticChartParser',
     'Boxer',
     'BrillTagger',
     'BrillTaggerTrainer',
     'CFG',
     'CRFTagger',
     'CfgReadingCommand',
     'ChartParser',
     'ChunkParserI',
     'ChunkScore',
     'ClassifierBasedPOSTagger',
     'ClassifierBasedTagger',
     'ClassifierI',
     'ConcordanceIndex',
     'ConditionalExponentialClassifier',
     'ConditionalFreqDist',
     'ConditionalProbDist',
     'ConditionalProbDistI',
     'ConfusionMatrix',
     'ContextIndex',
     'ContextTagger',
     'ContingencyMeasures',
     'CoreNLPDependencyParser',
     'CoreNLPParser',
     'Counter',
     'CrossValidationProbDist',
     'DRS',
     'DecisionTreeClassifier',
     'DefaultTagger',
     'DependencyEvaluator',
     'DependencyGrammar',
     'DependencyGraph',
     'DependencyProduction',
     'DictionaryConditionalProbDist',
     'DictionaryProbDist',
     'DiscourseTester',
     'DrtExpression',
     'DrtGlueReadingCommand',
     'ELEProbDist',
     'EarleyChartParser',
     'Expression',
     'FStructure',
     'FeatDict',
     'FeatList',
     'FeatStruct',
     'FeatStructReader',
     'Feature',
     'FeatureBottomUpChartParser',
     'FeatureBottomUpLeftCornerChartParser',
     'FeatureChartParser',
     'FeatureEarleyChartParser',
     'FeatureIncrementalBottomUpChartParser',
     'FeatureIncrementalBottomUpLeftCornerChartParser',
     'FeatureIncrementalChartParser',
     'FeatureIncrementalTopDownChartParser',
     'FeatureTopDownChartParser',
     'FreqDist',
     'HTTPPasswordMgrWithDefaultRealm',
     'HeldoutProbDist',
     'HiddenMarkovModelTagger',
     'HiddenMarkovModelTrainer',
     'HunposTagger',
     'IBMModel',
     'IBMModel1',
     'IBMModel2',
     'IBMModel3',
     'IBMModel4',
     'IBMModel5',
     'ISRIStemmer',
     'ImmutableMultiParentedTree',
     'ImmutableParentedTree',
     'ImmutableProbabilisticMixIn',
     'ImmutableProbabilisticTree',
     'ImmutableTree',
     'IncrementalBottomUpChartParser',
     'IncrementalBottomUpLeftCornerChartParser',
     'IncrementalChartParser',
     'IncrementalLeftCornerChartParser',
     'IncrementalTopDownChartParser',
     'Index',
     'InsideChartParser',
     'JSONTaggedDecoder',
     'JSONTaggedEncoder',
     'KneserNeyProbDist',
     'LancasterStemmer',
     'LaplaceProbDist',
     'LazyConcatenation',
     'LazyEnumerate',
     'LazyIteratorList',
     'LazyMap',
     'LazySubsequence',
     'LazyZip',
     'LeftCornerChartParser',
     'LidstoneProbDist',
     'LineTokenizer',
     'LogicalExpressionException',
     'LongestChartParser',
     'MLEProbDist',
     'MWETokenizer',
     'Mace',
     'MaceCommand',
     'MaltParser',
     'MaxentClassifier',
     'Model',
     'MultiClassifierI',
     'MultiParentedTree',
     'MutableProbDist',
     'NaiveBayesClassifier',
     'NaiveBayesDependencyScorer',
     'NgramAssocMeasures',
     'NgramTagger',
     'NonprojectiveDependencyParser',
     'Nonterminal',
     'OrderedDict',
     'PCFG',
     'Paice',
     'ParallelProverBuilder',
     'ParallelProverBuilderCommand',
     'ParentedTree',
     'ParserI',
     'PerceptronTagger',
     'PhraseTable',
     'PorterStemmer',
     'PositiveNaiveBayesClassifier',
     'ProbDistI',
     'ProbabilisticDependencyGrammar',
     'ProbabilisticMixIn',
     'ProbabilisticNonprojectiveParser',
     'ProbabilisticProduction',
     'ProbabilisticProjectiveDependencyParser',
     'ProbabilisticTree',
     'Production',
     'ProjectiveDependencyParser',
     'Prover9',
     'Prover9Command',
     'ProxyBasicAuthHandler',
     'ProxyDigestAuthHandler',
     'ProxyHandler',
     'PunktSentenceTokenizer',
     'QuadgramCollocationFinder',
     'RSLPStemmer',
     'RTEFeatureExtractor',
     'RUS_PICKLE',
     'RandomChartParser',
     'RangeFeature',
     'ReadingCommand',
     'RecursiveDescentParser',
     'RegexpChunkParser',
     'RegexpParser',
     'RegexpStemmer',
     'RegexpTagger',
     'RegexpTokenizer',
     'ReppTokenizer',
     'ResolutionProver',
     'ResolutionProverCommand',
     'SExprTokenizer',
     'SLASH',
     'Senna',
     'SennaChunkTagger',
     'SennaNERTagger',
     'SennaTagger',
     'SequentialBackoffTagger',
     'ShiftReduceParser',
     'SimpleGoodTuringProbDist',
     'SklearnClassifier',
     'SlashFeature',
     'SnowballStemmer',
     'SpaceTokenizer',
     'StackDecoder',
     'StanfordNERTagger',
     'StanfordPOSTagger',
     'StanfordSegmenter',
     'StanfordTagger',
     'StemmerI',
     'SteppingChartParser',
     'SteppingRecursiveDescentParser',
     'SteppingShiftReduceParser',
     'TYPE',
     'TabTokenizer',
     'TableauProver',
     'TableauProverCommand',
     'TaggerI',
     'TestGrammar',
     'Text',
     'TextCat',
     'TextCollection',
     'TextTilingTokenizer',
     'TnT',
     'TokenSearcher',
     'ToktokTokenizer',
     'TopDownChartParser',
     'TransitionParser',
     'Tree',
     'TreebankWordTokenizer',
     'Trie',
     'TrigramAssocMeasures',
     'TrigramCollocationFinder',
     'TrigramTagger',
     'TweetTokenizer',
     'TypedMaxentFeatureEncoding',
     'Undefined',
     'UniformProbDist',
     'UnigramTagger',
     'UnsortedChartParser',
     'Valuation',
     'Variable',
     'ViterbiParser',
     'WekaClassifier',
     'WhitespaceTokenizer',
     'WittenBellProbDist',
     'WordNetLemmatizer',
     'WordPunctTokenizer',
     '__author__',
     '__author_email__',
     '__builtins__',
     '__cached__',
     '__classifiers__',
     '__copyright__',
     '__doc__',
     '__file__',
     '__keywords__',
     '__license__',
     '__loader__',
     '__longdescr__',
     '__maintainer__',
     '__maintainer_email__',
     '__name__',
     '__package__',
     '__path__',
     '__spec__',
     '__url__',
     '__version__',
     'absolute_import',
     'accuracy',
     'add_logs',
     'agreement',
     'align',
     'alignment_error_rate',
     'aline',
     'api',
     'app',
     'apply_features',
     'approxrand',
     'arity',
     'association',
     'bigrams',
     'binary_distance',
     'binary_search_file',
     'binding_ops',
     'bisect',
     'blankline_tokenize',
     'bleu',
     'bleu_score',
     'bllip',
     'boolean_ops',
     'boxer',
     'bracket_parse',
     'breadth_first',
     'brill',
     'brill_trainer',
     'build_opener',
     'call_megam',
     'casual',
     'casual_tokenize',
     'ccg',
     'chain',
     'chart',
     'chat',
     'choose',
     'chunk',
     'class_types',
     'classify',
     'clause',
     'clean_html',
     'clean_url',
     'cluster',
     'collections',
     'collocations',
     'combinations',
     'compat',
     'config_java',
     'config_megam',
     'config_weka',
     'conflicts',
     'confusionmatrix',
     'conllstr2tree',
     'conlltags2tree',
     'corenlp',
     'corpus',
     'crf',
     'custom_distance',
     'data',
     'decisiontree',
     'decorator',
     'decorators',
     'defaultdict',
     'demo',
     'dependencygraph',
     'deque',
     'discourse',
     'distance',
     'download',
     'download_gui',
     'download_shell',
     'downloader',
     'draw',
     'drt',
     'earleychart',
     'edit_distance',
     'elementtree_indent',
     'entropy',
     'equality_preds',
     'evaluate',
     'evaluate_sents',
     'everygrams',
     'extract_rels',
     'extract_test_sentences',
     'f_measure',
     'featstruct',
     'featurechart',
     'filestring',
     'find',
     'flatten',
     'fractional_presence',
     'getproxies',
     'ghd',
     'glue',
     'grammar',
     'guess_encoding',
     'help',
     'hmm',
     'hunpos',
     'ibm1',
     'ibm2',
     'ibm3',
     'ibm4',
     'ibm5',
     'ibm_model',
     'ieerstr2tree',
     'improved_close_quote_regex',
     'improved_open_quote_regex',
     'improved_punct_regex',
     'in_idle',
     'induce_pcfg',
     'inference',
     'infile',
     'inspect',
     'install_opener',
     'internals',
     'interpret_sents',
     'interval_distance',
     'invert_dict',
     'invert_graph',
     'is_rel',
     'islice',
     'isri',
     'jaccard_distance',
     'json_tags',
     'jsontags',
     'lancaster',
     'lazyimport',
     'lfg',
     'line_tokenize',
     'linearlogic',
     'load',
     'load_parser',
     'locale',
     'log_likelihood',
     'logic',
     'mace',
     'malt',
     'map_tag',
     'mapping',
     'masi_distance',
     'maxent',
     'megam',
     'memoize',
     'metrics',
     'misc',
     'mwe',
     'naivebayes',
     'ne_chunk',
     'ne_chunk_sents',
     'ngrams',
     'nonprojectivedependencyparser',
     'nonterminals',
     'numpy',
     'os',
     'pad_sequence',
     'paice',
     'parse',
     'parse_sents',
     'pchart',
     'perceptron',
     'pk',
     'porter',
     'pos_tag',
     'pos_tag_sents',
     'positivenaivebayes',
     'pprint',
     'pr',
     'precision',
     'presence',
     'print_function',
     'print_string',
     'probability',
     'projectivedependencyparser',
     'prover9',
     'punkt',
     'py25',
     'py26',
     'py27',
     'pydoc',
     'python_2_unicode_compatible',
     'raise_unorderable_types',
     'ranks_from_scores',
     'ranks_from_sequence',
     're',
     're_show',
     'read_grammar',
     'read_logic',
     'read_valuation',
     'recall',
     'recursivedescent',
     'regexp',
     'regexp_span_tokenize',
     'regexp_tokenize',
     'register_tag',
     'relextract',
     'repp',
     'resolution',
     'ribes',
     'ribes_score',
     'root_semrep',
     'rslp',
     'rte_classifier',
     'rte_classify',
     'rte_features',
     'rtuple',
     'scikitlearn',
     'scores',
     'segmentation',
     'sem',
     'senna',
     'sent_tokenize',
     'sequential',
     'set2rel',
     'set_proxy',
     'sexpr',
     'sexpr_tokenize',
     'shiftreduce',
     'simple',
     'sinica_parse',
     'skipgrams',
     'skolemize',
     'slice_bounds',
     'snowball',
     'spearman',
     'spearman_correlation',
     'stack_decoder',
     'stanford',
     'stanford_segmenter',
     'stem',
     'str2tuple',
     'string_span_tokenize',
     'string_types',
     'subprocess',
     'subsumes',
     'sum_logs',
     'sys',
     'tableau',
     'tadm',
     'tag',
     'tagset_mapping',
     'tagstr2tree',
     'tbl',
     'text',
     'text_type',
     'textcat',
     'texttiling',
     'textwrap',
     'tkinter',
     'tnt',
     'tokenize',
     'tokenwrap',
     'toktok',
     'toolbox',
     'total_ordering',
     'transitionparser',
     'transitive_closure',
     'translate',
     'tree',
     'tree2conllstr',
     'tree2conlltags',
     'treebank',
     'treetransforms',
     'trigrams',
     'tuple2str',
     'types',
     'unify',
     'unique_list',
     'untag',
     'usage',
     'util',
     'version_file',
     'version_info',
     'viterbi',
     'weka',
     'windowdiff',
     'word_tokenize',
     'wordnet',
     'wordpunct_tokenize',
     'wsd']



### What can you do with NLTK?


```python
from nltk.corpus import stopwords

stopwords.words('english')[0:500:25]
```




    ['i', 'herself', 'been', 'with', 'here', 'very', 'doesn', 'won']




```python

```
