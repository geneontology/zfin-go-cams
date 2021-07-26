# zfin-go-cams

A repository of ZFIN models imported in bulk as part of MOD-imports project. 

- models : all the models imported from ZFIN curation interface in .ttl format
- source : the ZFIN provided GPAD 2.0 file and the GPAD 2.0 file recreated via ontobio scripts.  

### Generate gpad2.0_from_zfin_final.gpad from gpad2.0.zfin_orginal:
```bash
% git clone https://github.com/biolink/ontobio
% cd ontobio
% pyvenv venv
% source venv/bin/activate
% export PYTHONPATH=.:$PYTHONPATH
% pip install -r requirements.txt
% mkdir target/zfin_models
% bin/validate.py -v gpad2gocams --gpad_path gpad2.0.zfin_final_valid.gpad --gpi_path zfin.gpi --target target/zfin_models/ --ontology go.json --ontology ro.json --ttl -modelstate production
```

Run generated models through the shex:
prerequisites:
- docker
  
### spin up a minerva instance.
```bash
 % git clone https://github.com/geneontology/noctua
# base ubuntu image
% docker run --name ubuntu -e HOST_IP=$(ifconfig en0 | awk '/ *inet /{print $2}') -v location/of/noctua/source:/src -P  -t -i ubuntu /bin/bash
% apt-get update
% apt-get install -y curl
% apt-get install git maven emacs nano npm
```

### Do the work on the noctua build README, then:

```bash
% cd /src/noctua-stack/minerva/minerva-cli/bin 
% ./minerva-cli.sh --validate-go-cams --shex -i /src/ontobio/target/zfin_models --ontojournal /tmp/blazegraph-lego.jnl -r /tmp
```