# zfin-go-cams

A repository of ZFIN models imported in bulk as part of MOD-imports project. 

models : all the models imported from ZFIN curation interface in .ttl format
source : the ZFIN provided GPAD 2.0 file and the GPAD 2.0 file recreated via ontobio scripts.  

Generate gpad2.0_from_zfin_final.gpad from gpad2.0.zfin_orginal:
% git clone https://github.com/biolink/ontobio
% cd ontobio
% pyvenv venv
% source venv/bin/activate
% export PYTHONPATH=.:$PYTHONPATH
% pip install -r requirements.txt

% bin/validate.py -v gpad2gocams --gpad_path gpad2.0.from_zfin_final.gpad --gpi_path zfin.gpi --target target/zfin_models/ --ontology go.json --ontology ro.json --ttl -modelstate production