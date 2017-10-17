# ML
The repo contains Linear Regression and Logistic Regression outputs in Python


#Build the dataset
df = pandas.DataFrame({'emp_name':pandas.Series(['Marianne Becker', 'Evan Abbott', 'Jay Page', 'Seth Reese', 'Maxine Collier'], index=[0,1,2,3,4]), 'mgr_name':pandas.Series(['None', 'Marianne Becker', 'Marianne Becker', 'Marianne Becker', 'Marianne Becker'], index = [0,1,2,3,4])})

#Build the graph
G=nx.DiGraph()   
G.add_nodes_from(df.emp_name)
G.nodes()
G.add_node('None')
#
#Over here, you are manually adding 'None' but in reality
#your nodes are the unique entries of the concatenated
#columns, i.e. emp_name, mgr_name. You could achieve this by
#doing something like
#
#G.add_nodes_from(list(set(list(D.emp_name.values) + list(D.mgr_name.values))))
#
# Which does exactly that, retrieves the contents of the two columns
#concatenates them and then selects the unique names by turning the
#combined list into a set.

#Add edges
subset = df[['mgr_name','emp_name']]
tuples = [tuple(x) for x in subset.values] 
G.add_edges_from(tuples)
G.number_of_edges()

#Perform Graph Drawing
nx.draw_networkx(G)
plt.show()


nx.ancestors(G, "Marianne Becker")
