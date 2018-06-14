# GlycoNAVI CarTNa: Carbohydrate Trivial Name

```
SELECT 
 DISTINCT ( str ( ?ID) AS ?CarTNa_ID )
 str (?TrivialName) AS ?Trivial_Name
 str (?TrivialName_Label) AS ?Trivial_Name_Label
 str (?systematic_name) AS ?Systematic_Name
 str (?sequence) AS ?Sequence
 ?DefinedBy
 str (?iupac) AS ?IUPAC
 str (?aglycon_string) AS ?Aglycon
 ?aglycon_label
 str (?seq) AS ?modified_IUPAC
 str (?wurcs) AS ?WURCS

FROM <http://rdf.glycoinfo.org/cartna>
WHERE {

 ?s <http://purl.org/dc/terms/identifier> ?ID .

 ?s <http://semanticscience.org/resource/SIO_000008> ?triv .
 ?s <http://semanticscience.org/resource/SIO_000008>/<http://purl.jp/bio/12/glyco/glycan/has_glycan> ?str .
 OPTIONAL {
    ?s <http://semanticscience.org/resource/SIO_000008>/<http://purl.jp/bio/12/glyco/glycan/has_aglycon> ?aglycon .
 }
 
  OPTIONAL {
 ?triv <http://semanticscience.org/resource/SIO_000300> ?TrivialName .
 ?triv rdfs:label ?TrivialName_Label .
}
 OPTIONAL {
    ?triv <http://semanticscience.org/resource/CHEMINF_000106> ?systematic_name .
 }
 OPTIONAL {
    ?triv skos:altLabel ?sequence .
 }
 OPTIONAL {
    ?triv rdfs:isDefinedBy ?DefinedBy .
 }

 OPTIONAL {
    ?ag <http://purl.jp/bio/12/glyco/glycan/has_aglycon> ?aglycon .
    ?aglycon <http://semanticscience.org/resource/SIO_000300> ?aglycon_string .
    ?aglycon rdfs:label ?aglycon_label .
 }
 OPTIONAL {
    ?gseq_iupac <http://purl.jp/bio/12/glyco/glycan/in_carbohydrate_format> <http://purl.jp/bio/12/glyco/glycan/carbohydrate_format_iupac_condensed> .
    ?gseq_iupac <http://purl.jp/bio/12/glyco/glycan/has_sequence> ?iupac .
    ?str ?p1 ?gseq_iupac .
 }
OPTIONAL {
    ?gseq_seq <http://purl.jp/bio/12/glyco/glycan/in_carbohydrate_format> <http://purl.jp/bio/12/glyco/glycan/carbohydrate_format> .
    ?gseq_seq <http://purl.jp/bio/12/glyco/glycan/has_sequence> ?seq .
    ?str ?p2 ?gseq_seq .
 }
 OPTIONAL {
    ?gseq_wurcs <http://purl.jp/bio/12/glyco/glycan/in_carbohydrate_format> <http://purl.jp/bio/12/glyco/glycan/carbohydrate_format_wurcs> .
    ?gseq_wurcs <http://purl.jp/bio/12/glyco/glycan/has_sequence> ?wurcs .
    ?str ?p3 ?gseq_wurcs .
 }

}
LIMIT 100
```

