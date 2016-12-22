---
title: "Propriedade do valor XML (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.XmlPropertyExtensionValue"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "propriedade Value [Visual Basic]"
  - "código do Visual Basic, acessando XML"
  - "eixo XML [Visual Basic], Valor"
  - "propriedade XML Value [Visual Basic]"
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Propriedade do valor XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Fornece acesso ao valor do primeiro elemento de uma coleção de objetos <xref:System.Xml.Linq.XElement>.  
  
## Sintaxe  
  
```  
  
object.Value  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`object`|Obrigatório.  Coleção de objetos <xref:System.Xml.Linq.XElement>.|  
  
## Valor de retorno  
 Um `String` que contém o valor do primeiro elemento da coleção, ou `Nothing` se a coleção estiver vazia.  
  
## Comentários  
 A propriedade <xref:System.Xml.Linq.XElement.Value%2A> torna fácil acessar o valor do primeiro elemento em uma coleção de objetos <xref:System.Xml.Linq.XElement>.  Essa propriedade primeiro verifica se a coleção contém pelo menos um objeto.  Se a coleção está vazia, essa propriedade retornará `Nothing`.  Caso contrário, essa propriedade retorna o valor da propriedade <xref:System.Xml.Linq.XElement.Value%2A> do primeiro elemento na coleção.  
  
> [!NOTE]
>  Quando você acessa o valor de um atributo XML usando o identificador '@', o valor do atributo é retornado como um `String` e você não precisa especificar explicitamente o <xref:System.Xml.Linq.XAttribute.Value%2A> propriedade.  
  
 Para acessar outros elementos em uma coleção, você pode use a propriedade indexador de extensão XML.  Para obter mais informações, consulte [Propriedade do indexador de extensão](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).  
  
## Herança  
 A maioria dos usuários não será necessário implementar <xref:System.Collections.Generic.IEnumerable%601> e, portanto, pode ignorar esta seção.  
  
 A propriedade <xref:System.Xml.Linq.XElement.Value%2A> é uma propriedade de extensão para tipos que implementam `IEnumerable(Of XElement)`.  A vinculação da propriedade essa extensão é como a vinculação dos métodos de extensão: se um tipo implementa uma das interfaces e define uma propriedade que tem o nome "Valor", essa propriedade tem precedência sobre a propriedade de extensão.  Em outras palavras, essa propriedade <xref:System.Xml.Linq.XElement.Value%2A> pode ser substituída ao definir uma nova propriedade em uma classe que implementa `IEnumerable(Of XElement)`.  
  
## Exemplo  
 O exemplo a seguir mostra como usar a propriedade <xref:System.Xml.Linq.XElement.Value%2A> para acessar o primeiro nó em uma coleção de objetos <xref:System.Xml.Linq.XElement>.  O exemplo usa o propriedade do eixo filho para obter a coleção de todos os nós chamado `phone` que estão no `contact` objeto filho.  
  
 [!CODE [VbXMLSamples#15](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#15)]  
  
 Esse código exibe o texto a seguir:  
  
 `Phone number: 206-555-0144`  
  
## Exemplo  
 O exemplo a seguir mostra como obter o valor de um atributo XML de uma coleção de objetos <xref:System.Xml.Linq.XAttribute>.  O exemplo usa o propriedade do eixo de atributo para exibir o valor do atributo `type` para todos os elementos `phone`.  
  
 [!CODE [VbXMLSamples#16](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#16)]  
  
 Esse código exibe o texto a seguir:  
  
 `home`  
  
 `work`  
  
## Consulte também  
 <xref:System.Xml.Linq.XElement>   
 <xref:System.Collections.Generic.IEnumerable%601>   
 [Propriedades do eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Métodos de extensão](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)   
 [Propriedade do indexador de extensão](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)   
 [Propriedade do eixo filho XML](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)   
 [Propriedade de eixo do atributo XML](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)