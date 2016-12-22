---
title: "Propriedade do indexador de extens&#227;o (Visual Basic) | Microsoft Docs"
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
  - "vb.XmlPropertyExtensionIndexer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "indexador de extensão [Visual Basic]"
  - "código do Visual Basic, acessando XML"
  - "XML [Visual Basic], acessando"
  - "indexador de extensão XML [Visual Basic]"
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Propriedade do indexador de extens&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Fornece acesso aos elementos individuais em uma coleção.  
  
## Sintaxe  
  
```  
  
object(index)  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`object`|Obrigatório.  Uma coleção consultável.  Ou seja, uma coleção que implementa <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>.|  
|\(|Obrigatório.  Indica o início da propriedade do indexador.|  
|`index`|Obrigatório.  Uma expressão inteira que especifica a posição de um elemento da coleção baseada em zero.|  
|\)|Obrigatório.  Denota final da propriedade do indexador.|  
  
## Valor de retorno  
 O objeto a partir do local especificado na coleção, ou `Nothing` se o índice estiver fora do intervalo.  
  
## Comentários  
 Você pode usar a propriedade do indexador de extensão para acessar elementos individuais em uma coleção.  Essa propriedade do indexador normalmente é usada na saída das propriedades do eixo XML.  As propriedades do XML filho e do eixo XML descendente retornam coleções de objetos <xref:System.Xml.Linq.XElement> ou um valor de atributo.  
  
 O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador converte propriedades do indexador de extensão para chamadas para o`ElementAtOrDefault` método. Ao contrário de um indexador de matriz, o`ElementAtOrDefault` método retorna `Nothing` se o índice está fora do intervalo.  Esse comportamento é útil quando você não pode facilmente determinar o número de elementos em uma coleção.  
  
 Esta propriedade do indexador é como uma propriedade de extensão para coleções que implementam <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>: Ele é usado somente se a coleção não possui um indexador ou uma propriedade padrão.  
  
 Para acessar o valor do primeiro elemento em uma coleção de objetos <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, você pode usar a propriedade `Value` do XML.  Para obter mais informações, consulte [Propriedade do valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
## Exemplo  
 O exemplo a seguir mostra como usar o indexador de extensão para acessar o segundo nó filho em uma coleção de objetos <xref:System.Xml.Linq.XElement>.  A coleção é acessada através de propriedade do eixo filho, que obtém todos os elementos filho chamados `phone` no objeto `contact`.  
  
 [!CODE [VbXMLSamples#24](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#24)]  
  
 Esse código exibe o texto a seguir:  
  
 `Second phone number: 425-555-0145`  
  
## Consulte também  
 <xref:System.Xml.Linq.XElement>   
 [Propriedades do eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Propriedade do valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)