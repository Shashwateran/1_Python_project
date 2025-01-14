# The Analysis

## 1. What are the most demanded skills for the top 3 most popular data roles?

To find the most demanded skills for the top 3 most popular data roles. I filtered out those positions by which ones were the most popular, and got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills, showing which skills I should pay attention to depending on the role I'm targating.

View my notebook with detailed steps here: [2_Skills_Demand.ipynb](Project\2_Skills_Demand.ipynb)

```python

fig , ax = plt.subplots(len(job_titles), 1)
sns.set_theme(style= 'ticks')

for i , title in enumerate(job_titles):
    df_plot = df_merged[df_merged['job_title_short'] == title].head(5)
    sns.barplot(data= df_plot, x = 'skills %', y = 'job_skills', ax = ax[i], hue = 'value counts', palette= 'dark:g', legend= False)
    # ax[i].invert_yaxis()
    ax[i].set_ylabel('')
    ax[i].set_xlabel('')
    ax[i].set_title(title, fontweight = 'bold')
    ax[i].set_xlim(0, 75)
    
    
    for n , v in enumerate(df_plot['skills %']):
        ax[i].text(v+1, n + 0.1, f'{v:.0f}%', va ='center')

    if i != len(job_titles) - 1:
        ax[i].set_xticks([])

    
    
fig.suptitle(f'Count of Top Skills in Job Postings({country})', fontweight ='bold', fontsize = 18)
fig.tight_layout()

```

### Results

![Visualization of Top Skills for Data Nerds](Project\Images\Top3_Skills_demand.png)

### Insights

## 2. How are in-demand skills trending for Data Analysts?


