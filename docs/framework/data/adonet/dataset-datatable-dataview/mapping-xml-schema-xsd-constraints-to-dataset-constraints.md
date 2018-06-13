---
title: Restrições de esquema (XSD) de XML de mapeamento para restrições de conjunto de dados
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: 0a23e7a7ab6456125559ffd8fa19ffa5eba9335d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760980"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a>Restrições de esquema (XSD) de XML de mapeamento para restrições de conjunto de dados
A linguagem de definição de esquema XML (XSD) permite que sejam especificadas em elementos e atributos que define as restrições. Ao mapear um esquema XML para esquema relacional em um <xref:System.Data.DataSet>, restrições de esquema XML são mapeadas para restrições relacionais apropriadas em tabelas e colunas dentro de **conjunto de dados**.  
  
 Esta seção descreve o mapeamento das seguintes restrições de esquema XML:  
  
-   A restrição de exclusividade especificada usando o **exclusivo** elemento.  
  
-   A restrição de chave especificada usando o **chave** elemento.  
  
-   A restrição keyref especificada usando o **keyref** elemento.  
  
 Usando uma restrição em um elemento ou atributo, você pode especificar algumas restrições nos valores do elemento em qualquer instância do documento. Por exemplo, uma restrição de chave em um **CustomerID** elemento filho de um **cliente** elemento no esquema indica que os valores da **CustomerID** elemento filho deve ser exclusivo em qualquer instância de documento, e que não são permitidos valores nulos.  
  
 Restrições também podem ser especificadas entre elementos e atributos em um documento, para estabelecer uma relação de dentro do documento. As restrições de chave e keyref são usadas no esquema para especificar as restrições de dentro do documento, resultando em uma relação entre atributos e elementos de documento.  
  
 O processo de mapeamento converte essas restrições de esquema em restrições apropriadas nas tabelas criadas dentro de **conjunto de dados**.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Mapear restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Descreve os elementos de esquema XML usados para criar restrições exclusivas em um **conjunto de dados**.  
  
 [Mapear restrições de esquema XML (XSD) para restrições de conjunto de dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Descreve os elementos de esquema XML usados para criar restrições de chave (onde os valores nulos não são permitidos restrições exclusivas) em um **conjunto de dados**.  
  
 [Mapear restrições de keyref do esquema XML (XSD) para restrições de conjunto de dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Descreve os elementos de esquema XML usados para criar keyref restrições (chave estrangeira) em um **conjunto de dados**.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Derivando a estrutura relacional do conjunto de dados de esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Descreve a estrutura relacional, ou o esquema, de um **conjunto de dados** que é criado a partir do esquema XSD.  
  
 [Gerando relações de conjunto de dados do esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 Descreve os elementos de esquema XML usados para criar relações entre colunas da tabela em uma **conjunto de dados**.  
  
## <a name="see-also"></a>Consulte também  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
