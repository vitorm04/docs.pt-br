---
title: "Propriedade do eixo filho XML (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.XmlPropertyChildAxis"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "propriedade de eixo filho [Visual Basic]"
  - "código do Visual Basic, acessando XML"
  - "XML [Visual Basic], acessando"
  - "eixo XML [Visual Basic], filho"
  - "propriedade de eixo filho XML [Visual Basic]"
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Propriedade do eixo filho XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Fornece acesso aos descendentes de um dos seguintes: um objeto de <xref:System.Xml.Linq.XElement> , um objeto de <xref:System.Xml.Linq.XDocument> , uma coleção de objetos <xref:System.Xml.Linq.XElement> , ou uma coleção de <xref:System.Xml.Linq.XDocument> objeto.  
  
## Sintaxe  
  
```  
  
object.<child>  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`object`|Obrigatório.  Uma <xref:System.Xml.Linq.XElement> objeto, um <xref:System.Xml.Linq.XDocument> objeto, uma coleção de <xref:System.Xml.Linq.XElement> objetos ou uma coleção de <xref:System.Xml.Linq.XDocument> objetos.|  
|.\<|Obrigatório.  Indica o início de uma propriedade de eixo filho.|  
|`child`|Obrigatório.  Nome de nós filho para acessar, do formulário \[`prefix``:`\]`name`.<br /><br /> -   `Prefix` \-Opcional.  Prefixo de namespace XML para o nó filho.  Deve ser um namespace XML global definido com um `Imports` instrução.<br />-   `Name` \-Necessário.  Nome do nó filho local.  Consulte [Nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
|\>|Obrigatório.  Indica o início de uma propriedade de eixo filho.|  
  
## Valor de retorno  
 Uma coleção de objetos <xref:System.Xml.Linq.XElement> .  
  
## Comentários  
 Você pode usar uma propriedade de eixo filho XML para acessar os nós filho por nome de um <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> objeto, ou de uma coleção de <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> objetos.  Use o XML `Value` propriedade para acessar o valor do primeiro nó filho na coleção retornada.  Para obter mais informações, consulte [Propriedade do valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
 O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador converte propriedades de eixo filho em chamadas para o <xref:System.Xml.Linq.XContainer.Elements%2A> método.  
  
## Namespaces XML  
 O nome em uma propriedade de eixo filho pode usar somente prefixos de namespace XML declarados globalmente com a `Imports` instrução.  Ele não é possível usar prefixos de namespace XML declarados localmente em literais de elemento XML.  Para obter mais informações, consulte [Instrução Imports \(namespace XML\)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## Exemplo  
 O exemplo a seguir mostra como acessar os nós filho chamados `phone` do `contact` objeto.  
  
 [!CODE [VbXMLSamples#17](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#17)]  
  
 Esse código exibe o seguinte texto:  
  
 `Home Phone = 206-555-0144`  
  
## Exemplo  
 O exemplo a seguir mostra como acessar os nós filho chamados `phone` da coleção retornada pelo `contact` propriedade de eixo filho do `contacts` objeto.  
  
 [!CODE [VbXMLSamples#18](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#18)]  
  
 Esse código exibe o seguinte texto:  
  
 `Home Phone = 206-555-0144`  
  
## Exemplo  
 O exemplo a seguir declara `ns` como um prefixo de namespace XML.  Ele usa o prefixo de namespace para criar um literal XML e acessar o primeiro nó filho com o nome qualificado `ns:name`.  
  
 [!CODE [VbXMLSamples#19](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#19)]  
  
 Esse código exibe o seguinte texto:  
  
 `Patrick Hines`  
  
## Consulte também  
 <xref:System.Xml.Linq.XElement>   
 [Propriedades do eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)