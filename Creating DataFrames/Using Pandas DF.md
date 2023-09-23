```python
# works well when you want to create a darafram form list of dictionaries with missing value. First create Pandas DF, then convert to Spark DF.
import pandas as pd
pd.DataFrame(users)

spark.createDataFrame(pd.DataFrame(users))

```
