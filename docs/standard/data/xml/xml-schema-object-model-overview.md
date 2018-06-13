---
title: Visão geral do modelo de objeto de esquema XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 896a1e12-5655-42c6-8cdd-89c12862b34b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd25cf94a8a57f20b42f5e14c92b3b43e3378844
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572103"
---
# <a name="xml-schema-object-model-overview"></a>Visão geral do modelo de objeto de esquema XML
O modelo de objeto (SOM) de esquema no Microsoft.NET Framework é ricos API que permite a você criar, editar, e validar esquemas programaticamente. O SOM opera sobre documentos de esquema XML de forma semelhante à forma como Document Object Model (DOM) opera sobre documentos XML. Documentos de esquema XML são arquivos XML válidos, que carregados uma vez no SOM, transmitem significar sobre a estrutura e a validade de outros documentos XML que estão de acordo com o esquema.  
  
 Um esquema é um documento XML que define uma classe de documentos XML especificando a estrutura ou modelo de documentos XML para um esquema específico. Um esquema identifica as restrições no conteúdo de documentos XML, vocabulários e descreve regras (ou gramática) que documentos XML correspondentes devem seguir para ser considerado válidos esquema- com o esquema específico. Validação de um documento XML é o processo que garante que o documento está de acordo com a gramática especificada pelo esquema.  
  
 Os seguintes são maneiras que o SOM API no .NET Framework permite criar, editar, e para validar esquemas.  
  
-   Esquemas válidos de carregar e de salvar a e arquivos.  
  
-   Criar esquemas de memória usando classes fortemente tipadas.  
  
-   Interagir com a classe de <xref:System.Xml.Schema.XmlSchemaSet> para armazenar em cachê, compilar, e recuperar esquemas.  
  
-   Interagir com o método de <xref:System.Xml.XmlReader.Create%2A> da classe de <xref:System.Xml.XmlReader> para validar instância de documentos XML com esquemas.  
  
-   Criar editores para criar e esquemas de manutenções.  
  
-   Editar dinamicamente um esquema que pode ser seguido e salvo para uso na validação de instância de documentos XML.  
  
## <a name="the-schema-object-model"></a>O modelo de objeto de esquema  
 O SOM consiste em um extenso conjunto de classes no namespace de <xref:System.Xml.Schema?displayProperty=nameWithType> que corresponde a elementos em um esquema XML. Por exemplo, os mapeamentos de elemento de `<xsd:schema>...</xsd:schema>` a <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> classe, e qualquer informação que pode ser contido em um elemento de `<xsd:schema/>` pode ser representadas usando a classe de <xref:System.Xml.Schema.XmlSchema> . Da mesma forma, `<xsd:element>...</xsd:element>` e os elementos de `<xsd:attribute>...</xsd:attribute>` a classes de <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> e de <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> respectivamente. Esse mapeamento continua para todos os elementos de um esquema XML que cria um modelo de objeto de esquema XML no espaço de <xref:System.Xml.Schema> ilustrada no diagrama a seguir.  
  
 ![System.Xml.Schema Object Model](../../../../docs/standard/data/xml/media/xmlschemaobjmodeloverview.gif "XMLSchemaObjModelOverview")  
  
 Para obter mais informações sobre cada classe no namespace de <xref:System.Xml.Schema> , consulte a documentação de referência do <xref:System.Xml.Schema> na biblioteca de classes do .NET Framework.  
  
## <a name="see-also"></a>Consulte também  
 [Lendo e gravando esquemas XML](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [Compilando esquemas XML](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [Percorrer esquemas XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [Edição de esquemas XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [Incluindo ou importando esquemas XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [XmlSchemaSet para compilação de esquema](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [Infoset de compilação pós-esquema](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
