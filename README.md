# Analysis 
## 1. What are the most in-demand skills for the top 3 most popular data jobs in the United States?
To find the most requested skills from employers for the top 3 most popular roles in the United States.  To do this, I filtered the dataframe to narrow the roles down to the scope of the question and focused on the top 5 most sought roles for each position; this helps me to focus my training based on individual roles.

View my notebook with detailed steps here:
[2_Skill_Demand.ipynb](Project\3_Project\2_Skill_Demand.ipynb)

# Visualize with seaborn


```python


fig, ax = plt.subplots(len(job_titles), 1)

sns.set_theme(style='ticks')

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_percent[df_skills_percent['job_title_short'] == job_title].head(5)
    #df_plot.plot(kind='barh', x='job_skills', y='skill_percent', ax=ax[i], title=job_title)
    sns.barplot(data=df_plot, x='skill_percent', y='job_skills', ax=ax[i], hue='skill_count', palette='dark:b_r')
    #ax[i].invert_yaxis()
    ax[i].set_title(job_title)
    ax[i].set_ylabel('')
    ax[i].set_xlabel('')
    ax[i].set_xlim(0,80)
    ax[i].get_legend().remove()

    # label the figure 
    for n, v in enumerate(df_plot['skill_percent']):
        ax[i].text(v + 1, n, f'{v:.0f}%', va='center')
    
    if i != len(job_titles) - 1:
        ax[i].set_xticks([])
         
fig.suptitle('Percent of Top Skills Required in Top Jobs', size=14)

plt.tight_layout(h_pad=0.5)

plt.show()
```

### Results
![Visualization of Most Sought Skills](Project\3_Project\Images\Skill_Demand_roles.png)

### Insights
SQL and Python are highly-sought in all three roles, though Python is less sought among data analysts.  Likewise, while excel is important for data analysts, it does not even appear in the top skills for the other two roles.  R is important for data scientist positions, but again is more rarely sought among analyst and engineer positions.
