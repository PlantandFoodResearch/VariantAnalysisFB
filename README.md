# Variant Calling Pipeline

## How to use the align pipeline

**Step 0:**

```
curl -fsSL get.nextflow.io | bash 
```

And add NXF_HOME to your .bashrc in case the space in your home directory is restricted:

```
export NXF_HOME=/path/to/.nextflow
```

**Step1:** Run test

The pipeline is preconfigured with test data. INorder to tst whether the pipeline runs through call vc_pipe without command line parameters:

```

./nextflow run  PlantandFoodResearch/VariantAnalysis/align.nf [--help]

```

If the pipeline does not run through, look into teh log file:

```
.nextflow.log
```

and contact the app steward (helge.dzierzon@plantandfood.co.nz).


**Step 2:** Configure file and sample IDs

This is the test data design.config. Adapt to your needs.

```
sample,file,rep,read,experiment,date,comments
HW1,kiwitest.1.R1.fq.gz,1,R1,kiwitest,2016-01-01,This is crap
HW1,kiwitest.1.R2.fq.gz,1,R2,kiwitest,2016-01-01,This is crap
HW2,kiwitest.2.R1.fq.gz,2,R1,kiwitest,2016-01-01,This is crap
HW2,kiwitest.2.R2.fq.gz,2,R2,kiwitest,2016-01-01,This is crap

```

**Step 3:** Run the pipeline

Options:

```
output_dir: publish directory for results ["./"]
inpu_dir: Directory that contains the raw reads ["$baseDir/KiwiTestData"]
genome: Reference genome file (*.fasta) ["$baseDir/KiwiTestData/kiwitest.fasta"]
config: Location of config file ["$baseDir/design.config"]

$baseDir = $HOME/.nextflow/assets/hdzierz/VariantAnalysisFB
```

Typical run with the test data copied to $HOME/KiwiTestData

```
./nextflow run  PlantandFoodResearch/VariantAnalysis/align.nf --input_dir '$HOME/KiwiTestData/' --genome '$HOME/KiwiTestData/kiwitest.fasta'
```






