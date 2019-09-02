---
title: Mapeamento de restrições de esquema XML (XSD) para restrições de DataSet
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: b0082b534b8df10ac5277cf2f5aa5b2d2e40c11b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204627"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapeamento de restrições de esquema XML (XSD) para restrições de DataSet
A linguagem de definição de esquema XML (XSD) permite que as restrições sejam especificadas nos elementos e atributos que ele define. Ao mapear um esquema XML para o esquema relacional <xref:System.Data.DataSet>em um, as restrições de esquema XML são mapeadas para as restrições relacionais apropriadas nas tabelas e colunas dentro do **conjunto**de um.  
  
 Esta seção discute o mapeamento das seguintes restrições de esquema XML:  
  
- A restrição de exclusividade especificada usando o elemento **exclusivo** .  
  
- A restrição de chave especificada usando o elemento de **chave** .  
  
- A restrição keyref especificada usando o elemento **keyref** .  
  
 Usando uma restrição em um elemento ou atributo, você especifica determinadas restrições nos valores do elemento em qualquer instância do documento. Por exemplo, uma restrição de chave em um elemento filho **CustomerID** de um elemento **Customer** no esquema indica que os valores do elemento filho **CustomerID** devem ser exclusivos em qualquer instância de documento e que os valores nulos não são permitidos.  
  
 As restrições também podem ser especificadas entre elementos e atributos em um documento, a fim de estabelecer uma relação dentro do documento. As restrições Key e keyref são usadas no esquema para especificar as restrições dentro do documento, resultando em uma relação entre elementos de documento e atributos.  
  
 O processo de mapeamento converte essas restrições de esquema em restrições apropriadas nas tabelas criadas no **conjunto**de um.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Mapear restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados](map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Descreve os elementos de esquema XML usados para criar restrições exclusivas em um **DataSet**.  
  
 [Mapear restrições de esquema XML (XSD) para restrições de conjunto de dados](map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Descreve os elementos de esquema XML usados para criar restrições de chave (restrições exclusivas em que valores NULL não são permitidos) em um **DataSet**.  
  
 [Mapear restrições de keyref do esquema XML (XSD) para restrições de conjunto de dados](map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Descreve os elementos de esquema XML usados para criar restrições keyref (Foreign Key) em um **DataSet**.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Derivando a estrutura relacional do conjunto de dados de esquema XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Descreve a estrutura relacional, ou esquema, de um **conjunto** de dados que é criado a partir do esquema XSD.  
  
 [Gerando relações de conjunto de dados do esquema XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)  
 Descreve os elementos de esquema XML usados para criar relações entre colunas de tabela em um **conjunto**de uma.  
  
## <a name="see-also"></a>Consulte também

- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
