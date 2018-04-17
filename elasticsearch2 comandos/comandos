POST - Atualiza só nome
POST /catalogo/pessoas/1/_update
{
    "doc": {
        "nome": "Douglas Quintanilha"
    }
}


=====================================================
PUT - 
Como dito anteriormente, o PUT substitui o documento, ou seja, se fizermos:
PUT /catalogo/pessoas/1
{
    "nome": "Douglas Quintanilha"
}
Substituiremos o documento de id, logo ele só conterá o atributo nome.


=====================================================
DELETE -
DELETE /catalogo/pessoas/23
{}

=====================================================
Fazer uma busca:
GEt -
/catalogo/pessoas/_search?q=futebol
/catalogo/pessoas/_search?q=_all:futebol
/catalogo/pessoas/_search?q=estado:SP&size=1
/catalogo/pessoas/_search?size=50
/catalogo/pessoas/_search?q=estado:SP&size=1&from=1
                  _search?q=interesses:futebol&cidade:rio

=====================================================
Mapping

/catalogo/_mapping/pessoas

Output:

{
  "catalogo": {
    "mappings": {
      "pessoas": {
        "properties": {
          "cidade": {
            "type": "string"
          },
          "estado": {
            "type": "string"
          },
          "formacao": {
            "type": "string"
          },
          "formação": {
            "type": "string"
          },
          "interesse": {
            "type": "string"
          },
          "interesses": {
            "type": "string"
          },
          "nome": {
            "type": "string"
          },
          "país": {
            "type": "string"
          }
        }
      }
    }
  }
}

=====================================================

PUT para /catalogo/_mapping/pessoas
{
    "properties": {
        "pulo": {
            "type": "integer"
        }
    }
}

=====================================================

Anayzers
GET /_analyze?analyzer=ANALYZER_AQUI&text=Bem+vindo+ao+curso+de+ElasticSearch+da+Alura


=====================================================

PUT para /catalogo_v2

{
  "settings": {
    "index": {
      "number_of_shards": 3,
      "number_of_replicas": 0
    }
  },
  "mappings": {
    "pessoas_v2": {
      "_all": {
        "type": "string",
        "index": "analyzed",
        "analyzer": "portuguese"
      },
      "properties": {
        "cidade": {
          "type": "string",
          "index": "analyzed",
          "analyzer": "portuguese"
        },
        "estado": {
          "type": "string"
        },
        "formação": {
          "type": "string",
          "index": "analyzed",
          "analyzer": "portuguese"
        },
        "interesses": {
          "type": "string",
          "index": "analyzed",
          "analyzer": "portuguese"
        },
        "nome": {
          "type": "string",
          "index": "analyzed",
          "analyzer": "portuguese"
        },
        "país": {
          "type": "string",
          "index": "analyzed",
          "analyzer": "portuguese"
        }
      }
    }
  }
}

Analyzers Communs

whitespace
simple
standard
portuguese, english

=====================================================

Criando um analyzer customizado

PUT /indice_com_sinonimo_2
{
  "settings": {
    "index": {
      "number_of_shards": 3,
      "number_of_replicas": 0
    },
    "analysis": {
      "filter": {
        "filtro_de_sinonimos": {
            "type": "synonym",
            "synonyms": [
        "futebol => futebol,society",
        "society => society,futebol",
        "esporte => esporte,futebol,society,volei,basquete"
            ]
        }
      },
      "analyzer": {
        "sinonimos": {
          "tokenizer":  "standard",
          "filter": [
            "lowercase",
            "filtro_de_sinonimos"
          ]
        }
      }
    }
  }
}

=====================================================




