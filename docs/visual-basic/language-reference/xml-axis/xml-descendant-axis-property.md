---
title: "Propriedade de eixo descendente XML (Visual Basic) | Microsoft Docs"
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
  - "vb.XmlPropertyDescendantsAxis"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "propriedade de eixo descendente [Visual Basic]"
  - "código do Visual Basic, acessando XML"
  - "XML [Visual Basic], acessando"
  - "eixo XML [Visual Basic], descendente"
  - "propriedade de eixo descendente XML [Visual Basic]"
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Propriedade de eixo descendente XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Fornece acesso aos descendentes dos seguintes: um objeto <xref:System.Xml.Linq.XElement>, um objeto <xref:System.Xml.Linq.XDocument>, uma coleção de objetos <xref:System.Xml.Linq.XElement> ou uma coleção de objetos <xref:System.Xml.Linq.XDocument>.  
  
## Sintaxe  
  
```  
  
object...<descendant>  
```  
  
## Partes  
 `object`  
 Obrigatório.  Um objeto <xref:System.Xml.Linq.XElement>, um objeto <xref:System.Xml.Linq.XDocument>, uma coleção de objetos <xref:System.Xml.Linq.XElement> ou uma coleção de objetos <xref:System.Xml.Linq.XDocument>.  
  
 ... \<  
 Obrigatório.  Indica o início de uma propriedade de um eixo descendente.  
  
 `descendant`  
 Obrigatório.  Nome dos nós descendentes a serem acessados, do formulário \[`prefix``:`\] `name`.  
  
|Parte|Descrição|  
|-----------|---------------|  
|`prefix`|Opcional.  Prefixo do namespace XML para o nó descendente.  Deve ser um namespace para XML global que é definido usando uma instrução `Imports`.|  
|`name`|Obrigatório.  Nome local do nó descendente.  Consulte [Nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 Obrigatório.  Indica o fim de uma propriedade de um eixo descendente.  
  
## Valor de retorno  
 Uma coleção de objetos <xref:System.Xml.Linq.XElement>.  
  
## Comentários  
 Você pode usar uma propriedade de eixo descendente XML para acessar nós descendentes pelo nome de um objeto <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>, ou de uma coleção de objetos <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>.  Use a propriedade XML `Value` para acessar o valor do primeiro nó descendente na coleção retornada.  Para obter mais informações, consulte [Propriedade do valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
 O compilador [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] converte propriedades de eixo descendente em chamadas para o método <xref:System.Xml.Linq.XContainer.Descendants%2A>.  
  
## Namespaces XML  
 O nome em uma propriedade de eixo descendente pode usar somente namespaces XML declarados globalmente com a instrução `Imports`.  Ele não é possível usar namespaces para XML declarados localmente em literais de elemento XML.  Para obter mais informações, consulte [Instrução Imports \(namespace XML\)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## Exemplo  
 O exemplo a seguir mostra como acessar o valor do primeiro nó descendente chamado `name` e os valores de todos os nós descendentes chamados `phone` do objeto `contacts`.  
  
 [!CODE [VbXMLSamples#25](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#25)]  
  
 Esse código exibe o texto a seguir:  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## Exemplo  
 O exemplo a seguir declara `ns` como um prefixo de namespace para XML.  Ele usa o prefixo de namespace para criar um literal XML e acessar o valor do primeiro nó filho com o nome qualificado "`ns:name`" .  
  
 [!CODE [VbXMLSamples#26](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#26)]  
  
 Esse código exibe o texto a seguir:  
  
 `Name: Patrick Hines`  
  
## Consulte também  
 <xref:System.Xml.Linq.XElement>   
 [Propriedades do eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)