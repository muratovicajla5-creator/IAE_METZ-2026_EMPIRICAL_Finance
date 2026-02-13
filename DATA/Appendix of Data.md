Appendix

# Provenance des data
Les data proviennet de Yahoo Finance avec le package (yfinance)

# Variables 
Les data sont un ETF Vanguard Growth, un ETF Vanguard Value et un taux américain à 5 ans. La période est de 2014-2024

Nous avons calculé le Spread de rentabilité, Variation du taux et le Spread de volatilité 

# Tableau final
Finalement le tableau a été généré avec les Tickers et le nom de chaque colonnes. Le tableau est prêt a être utilisé sur des modèles comme OLS et ML 


Dataset généré : (126, 9)
Ticker             VUG         VTV   ^FVX  ret_growth  ret_value    spread  \
Date                                                                         
2024-08-31  372.925751  167.306747  3.715    2.246129   2.880801 -0.634672   
2024-09-30  381.699219  169.867264  3.577    2.352605   1.530432  0.822172   
2024-10-31  380.695068  167.522186  4.155   -0.263074  -1.380535  1.117462   
2024-11-30  406.752747  176.970596  4.055    6.844764   5.640095  1.204669   
2024-12-31  408.577393  165.692764  4.380    0.448588  -6.372715  6.821304   

Ticker      rate_5y  rate_5y_change  spread_vol  
Date                                             
2024-08-31    3.715          -0.285    4.740609  
2024-09-30    3.577          -0.138    4.403803  
2024-10-31    4.155           0.578    4.388222  
2024-11-30    4.055          -0.100    4.225075  
2024-12-31    4.380           0.325    4.281800 