---
layout: post
title: "Using the MSU HPC Profile for nf-core Pipelines"
date: 2024-08-03
categories: jekyll update
---

In this blog post, I'll guide you through the process of making a custom profile for the Michigan State University (MSU) HPC system with nf-core pipelines. This setup ensures that nf-core pipelines can run efficiently on the MSU HPC environment using your own data.

## Step-by-Step Guide

### Step 1: Create the Configuration File

First, we need to create the `msu.config` file with the following content:

```groovy
params {
    config_profile_description = 'Michigan State University HPC profile provided by nf-core/configs.'
    config_profile_contact = 'John Vusich (@johnvusich)'
    config_profile_url = 'https://github.com/johnvusich/bulk-rnaseq/blob/main/msu.config'
    max_memory = 250.GB
    max_cpus = 40
    max_time = 168.h // One week in hours
}

singularity {
    enabled = true
    autoMounts = true
}

process {
    executor = 'slurm'
}
```
### Step 2: Add the Config File to Your Repository
Navigate to your repository on GitHub.
Go to the root directory and create a new file named msu.config.
Paste the configuration content into the file and commit the changes.

###Step 3: Clone Your Repository Locally
Open your terminal.

Clone your repository:
```bash
git clone https://github.com/your_github_username/your_repository_name.git
cd your_repository_name
```

### Step 4: Step 4: Install Dependencies
1. Ensure you have Ruby installed. You can download it from ruby-lang.org.
2. Install Bundler, a Ruby gem that manages dependencies for Ruby projects:
```bash
gem install bundler
```
3. Install Jekyll and other dependencies using Bundler:
```bash
bundle install
```
### Step 5: Build and Serve the Site Locally
1. Use Jekyll's built-in server to build and serve the site locally:
```bash
bundle exec jekyll serve
```
2. Open your web browser and go to http://localhost:4000 to see the site in action.

### Step 6: Run nf-core Pipeline with msu.config
1. Load Nextflow on the MSU HPC system:
```bash
module load nextflow
```
2. Run your nf-core pipeline with the msu.config profile. For example, to run the nf-core/rnaseq pipeline:
```bash
nextflow run nf-core/rnaseq --reads '*_R{1,2}.fastq.gz' --genome GRCh37 -profile msu -c msu.config
```

### Conclusion
By following these steps, you can successfully set up and use a custom profile for the MSU HPC system to run nf-core pipelines with your own data. This configuration ensures that your nf-core pipelines run smoothly on the MSU HPC environment.

Stay tuned for more updates and tips on using nf-core and Jekyll!

```vbnet
This markdown file provides a step-by-step guide for users to set up and use the `msu.config` file for running nf-core pipelines on the MSU HPC system.
```
