---
title: "Copiando nós existentes de um documento para outro"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3caa78c1-3448-4b7b-b83c-228ee857635e
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0f20e5bd595c8eb49360e58f281a8cf6eda89acf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="copying-existing-nodes-from-one-document-to-another"></a>Copiando nós existentes de um documento para outro
O **ImportNode** método é o mecanismo pelo qual um nó ou uma subárvore inteira de nó é copiado de um **XmlDocument** para outro. O nó retornado de chamada é uma cópia do nó do documento de origem, incluindo valores de atributo, nome de nó, tipo de nó, e todos os atributos URL relacionados como o prefixo, o nome local, e namespace Uniform Resource Identifier (URI). O documento de origem não é alterado. Depois que você importou o nó, você ainda precisará adicioná-lo à árvore usando um dos métodos usados para nós de inserção.  
  
 Quando o nó é anexado ao novo documento, o novo documento possui o nó. O motivo é que cada nó, quando criado, tem um documento proprietário, mesmo se os nós são criados em partes separados do documento. Isso é um requisito do XML DOM Document Object Model () e é imposto pelo design de criação de fábrica no **XmlDocument** classe. Por exemplo, **CreateElement**, é a única maneira de criar novos nós.  
  
 Dependendo do tipo de nó do nó importado e o valor de *profunda* parâmetro, informações adicionais é copiado conforme apropriado. Este método tenta espelhar o comportamento esperado se um fragmento XML ou de código HTML foi copiado de um documento para outro, responsabilizando-se pelo fato que para XML, os dois documentos pode ter definições de tipos diferentes (DTDs) do documento.  
  
 A tabela a seguir descreve o comportamento específico para cada tipo de nó que pode ser importado.  
  
|Tipo de nó|*profundidade* parâmetro for true|*profundidade* parâmetro é false|  
|---------------|------------------------------|-------------------------------|  
|XmlAttribute|O <xref:System.Xml.XmlAttribute.Specified%2A> é definido como **true** no XmlAttribute. Os descendentes de origem **XmlAttribute** recursivamente importados e os nós resultantes reorganizados para formar a subárvore correspondente.|O *profunda* parâmetro não se aplica a **XmlAttribute** nós, porque eles sempre ter seus nós filho com eles quando importado.|  
|XmlCDataSection|Copia o nó, incluindo seus dados.|Copia o nó, incluindo seus dados.|  
|XmlComment|Copia o nó, incluindo seus dados.|Copia o nó, incluindo seus dados.|  
|XmlDocumentFragment|Os descendentes nó de origem recursivamente serão importados e os nós resultantes são remontados para formar a subárvore correspondente.|Vazio **XmlDocumentFragment** é criado.|  
|XmlDocumentType|Copia o nó, incluindo seu data.*|Copia o nó, incluindo seu data.*|  
|XmlElement|Os descendentes do elemento de origem recursivamente serão importados e os nós resultantes são remontados para formar a subárvore correspondente. **Observação:** atributos padrão não são copiados. Se o documento que está sendo importado define atributos padrão para este nome de elemento, esses são atribuídos.|Especificado como atributo nós de elemento de origem são importados e gerado **XmlAttribute** nós são anexados para o novo elemento. Os nós descendentes não são copiados. **Observação:** atributos padrão não são copiados. Se o documento que está sendo importado define atributos padrão para este nome de elemento, esses são atribuídos.|  
|XmlEntityReference|Como os documentos de origem e de destino podem ter entidades definidas de forma diferente, esse método apenas copia o **XmlEntityReference** nó. O texto de substituição não é incluído. Se o documento de destino tem a entidade definida, o valor é atribuído.|Como os documentos de origem e de destino podem ter entidades definidas de forma diferente, esse método apenas copia o **XmlEntityReference** nó. O texto de substituição não é incluído. Se o documento de destino tem a entidade definida, o valor é atribuído.|  
|XmlProcessingInstruction|Copia o destino e o valor do nó importado.|Copia o destino e o valor do nó importado.|  
|XmlText|Copia o nó, incluindo seus dados.|Copia o nó, incluindo seus dados.|  
|XmlSignificantWhitespace|Copia o nó, incluindo seus dados.|Copia o nó, incluindo seus dados.|  
|XmlWhitespace|Copia o nó, incluindo seus dados.|Copia o nó, incluindo seus dados.|  
|XmlDeclaration|Copia o destino e o valor do nó importado.|Copia o destino e o valor do nó importado.|  
|Todos os outros tipos de nó|Esses tipos de nós não podem ser importados.|Esses tipos de nós não podem ser importados.|  
  
> [!NOTE]
>  Embora os nós de DocumentType possam ser importados, um documento pode ter apenas um DocumentType. Assim, uma vez que você importou o tipo de documento, antes de inseri-lo na árvore você precisará certificar-se que não há documento tipo no documento. Para obter informações sobre como remover nós, consulte [remover nós, conteúdo e os valores de um documento XML](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).  
  
## <a name="see-also"></a>Consulte também  
 [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
