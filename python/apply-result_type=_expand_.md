apply-result_type='expand'

data\[\['week','time','begin','end','hours'\]\]= data.apply(lambda x: solve(x\['class\_time'\]),axis=1,result\_type="expand")