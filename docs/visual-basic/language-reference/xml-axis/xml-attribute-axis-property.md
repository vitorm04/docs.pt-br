---
title: "Propriedade de eixo do atributo XML (Visual Basic) | Microsoft Docs"
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
  - "vb.XmlPropertyAttributeAxis"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "propriedade de eixo de atributo [Visual Basic]"
  - "código do Visual Basic, acessando XML"
  - "XML [Visual Basic], acessando"
  - "propriedade de eixo de atributo XML [Visual Basic]"
  - "eixo XML [Visual Basic], Atributo "
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Propriedade de eixo do atributo XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Fornece acesso ao valor de um atributo para um <xref:System.Xml.Linq.XElement> objeto ou para o primeiro elemento em uma coleção de <xref:System.Xml.Linq.XElement> objetos.  
  
## Sintaxe  
  
```  
  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## Partes  
 `object`  
 Obrigatório.  Um objeto <xref:System.Xml.Linq.XElement> ou uma coleção de objetos <xref:System.Xml.Linq.XElement>.  
  
 .@  
 Obrigatório.  Indica o início de uma propriedade do eixo de atributo.  
  
 \<  
 Opcional.  Indica o início do nome do atributo `attribute` quando não um identificador válido no [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 `attribute`  
 Obrigatório.  Nome do atributo para acessar, do formulário \[`prefix`:\] `name`.  
  
|Parte|Descrição|  
|-----------|---------------|  
|`prefix`|Opcional.  Prefixo para namespace XML para o atributo.  Deve ser um namespace para XML global definido com uma declaração `Imports`.|  
|`name`|Obrigatório.  Nome do Atributo local.  Consulte [Nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 Opcional.  Indica o início do nome do atributo `attribute` quando não um identificador válido no [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## Valor de retorno  
 Uma seqüência de caracteres que contém o valor de `attribute`.  Se não existir, o nome do atributo `Nothing` é retornado.  
  
## Comentários  
 Você pode usar uma propriedade do eixo de atributo XML para acessar o valor de um atributo por nome de um <xref:System.Xml.Linq.XElement> objeto ou do primeiro elemento em uma coleção de <xref:System.Xml.Linq.XElement> objetos.  Você pode recuperar um valor de atributo pelo nome, ou adicionar um novo atributo a um elemento, especificando um novo nome precedido de @ identificador.  
  
 Quando você fazer referência a um atributo XML usando o @ identificador, o valor de atributo é retornado como uma sequência de caracteres e você não será necessário especificar a propriedade <xref:System.Xml.Linq.XAttribute.Value%2A> explicitamente.  
  
 As regras de nomeação para atributos XML são diferentes das regras de nomenclatura para [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] identificadores. Para acessar um atributo XML que tem um nome que não é um identificador válido de Visual Basic, coloque o nome em colchetes angulares \(\< e \>\).  
  
## Namespaces XML  
 O nome em um propriedade do eixo de atributo pode usar somente prefixos namespace para XML declarados usando a instrução `Imports` globalmente.  Não é possível usar prefixos namespace para XML declarados localmente em literais de elemento XML.  Para obter mais informações, consulte [Instrução Imports \(namespace XML\)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## Exemplo  
 O exemplo a seguir mostra como obter os valores dos atributos XML chamados `type` de uma coleção de elementos que são denominados `phone` XML.  
  
 [!CODE [VbXMLSamples#12](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#12)]  
  
 Esse código exibe o texto a seguir:  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## Exemplo  
 O exemplo a seguir mostra como criar atributos para um elemento XML tanto declarativamente, como parte do XML e dinamicamente adicionando um atributo a uma instância de um objeto <xref:System.Xml.Linq.XElement>.  O atributo `type` declarativamente é criado e o `owne` r atributo é criado dinamicamente.  
  
 [!CODE [VbXMLSamples#44](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#44)]  
  
 Esse código exibe o texto a seguir:  
  
```  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## Exemplo  
 O exemplo a seguir usa a sintaxe colchete angular para obter o valor da atributo XML chamado `number-type`,que é Não um identificador válido no [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 [!CODE [VbXMLSamples#13](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#13)]  
  
 Esse código exibe o texto a seguir:  
  
 `Phone type: work`  
  
## Exemplo  
 O exemplo a seguir declara `ns` como um prefixo de namespace para XML.  Ele usa o prefixo de namespace, em seguida, para criar um XML literal e acessar a primeira nó filho com o nome qualificado "`ns:name`" .  
  
 [!CODE [VbXMLSamples#14](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#14)]  
  
 Esse código exibe o texto a seguir:  
  
 `Phone type: home`  
  
## Consulte também  
 <xref:System.Xml.Linq.XElement>   
 [Propriedades do eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)