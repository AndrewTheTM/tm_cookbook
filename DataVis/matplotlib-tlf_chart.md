---
layout: recipe
title: Matplotlib Trip Length Frequency Plot
language: Python
author: Andrew Rohne
libraries-needed: matplotlib
category: Data Visualization
---

This function draws a fairly standard trip length frequency chart (which is a little bit of a misnomer
in this case, since this is the distance to work). This is setup with fairly standard ActivitySim output
fields, including `is_out_of_home_worker`, which is a boolean value to show if a person works out of
the home. 

This function takes a county name or 'Total', the use of this is much larger than what I am showing here.

```
def tlf_chart(county):
    if county == 'Total':
        plot_title = 'Regional Distance-To-Work'
        model_summary = persons[persons['is_out_of_home_worker']].groupby('distbin').agg(model = ('person_id', 'count')) / persons[persons['is_out_of_home_worker']].shape[0]
    else:
        plot_title = f'Distance-To-Work for {county}'
        model_summary = persons[(persons['home_county'] == county) & (persons['is_worker'])].groupby('distbin').agg(model = ('person_id', 'count')) / persons[(persons['home_county'] == county) & (persons['is_worker'])].shape[0] 
    plot_data = survey_tlfd[['distbin', county]].copy()
    plot_data['survey'] = plot_data[county] / plot_data[county].sum()
    plot_data = plot_data[['distbin', 'survey']].merge(model_summary[['model']], how = 'outer', left_on = 'distbin', right_index = True).fillna(0)
    fig = plt.figure(figsize=(16,10))
    ax = fig.add_subplot()
    ax.plot(plot_data.distbin, plot_data.survey, label = 'Survey')
    ax.plot(plot_data.distbin, plot_data.model, label = 'ActivitySim')
    plt.legend(loc='upper right')
    plt.title(plot_title)
    ax.set_xlabel('Distance (miles)')
    ax.set_ylabel('Number of Trips')

tlf_chart('Total')
```