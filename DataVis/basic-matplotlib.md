


`
from matplotlib.pyplot import plot, show, draw, figure, cm
import matplotlib.pyplot as plt
import seaborn as sns
from matplotlib.colors import rgb2hex

# Four scatterplots in one
fig, axis = plt.subplots(2, 2, figsize = (16,10))

ax1 = axis[0,0] 
ax1.scatter(nhb_ie['nwrk_i1'], nhb_ie['NHB_IE_Prods'], marker='o', label = 'Income 1')
ax1.set_xlabel('People - Inc 1')
ax1.set_ylabel('NHB IE Prods')

ax2 = axis[0,1]
ax2.scatter(nhb_ie['nper_i2'], nhb_ie['NHB_IE_Prods'], marker='o', label = 'Income 2')
ax2.set_xlabel('People - Inc 2')
ax2.set_ylabel('NHB IE Prods')

ax3 = axis[1,0]
ax3.scatter(nhb_ie['nper_i3'], nhb_ie['NHB_IE_Prods'], marker='o', label = 'Income 3')
ax3.set_xlabel('People - Inc 3')
ax3.set_ylabel('NHB IE Prods')

ax4 = axis[1,1]
ax4.scatter(nhb_ie['nper_i4'], nhb_ie['NHB_IE_Prods'], marker='o', label = 'Income 4')
ax4.set_xlabel('People - Inc 4')
ax4.set_ylabel('NHB IE Prods')

plt.show()

# Q-Q Plot
plt.rc("figure", figsize=(16,10))
res = nhb_ix_lm.resid # residuals
fig = sm.qqplot(res, fit=True, line="s")

# Cook's Influence Plot
fig2 = sm.graphics.influence_plot(nhb_ix_lm, criterion="cooks")

# Histogram
nhb_compare = (nhb_ix_lm.fittedvalues - nhb_ie['NHB_IE_Prods']).fillna(0)

n, bins, patches = plt.hist(nhb_compare, 50, density=True, facecolor='g', alpha=0.75)