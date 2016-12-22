---
title: "&lt;value&gt; (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Marca &lt;value&gt; (XML)"
  - "marca XML de valor"
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;value&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica a descrição de uma propriedade.  
  
## Sintaxe  
  
```  
<value>property-description</value>  
```  
  
#### Parâmetros  
 `property-description`  
 Uma descrição para a propriedade.  
  
## Comentários  
 Use o marcador `<value>` para descrever uma propriedade.  Note que quando você adiciona uma propriedade usando o assistente de código no ambiente de desenvolvimento do Visual Studio, este vai adicionar um marcador [\<summary\>](../Topic/%3Csummary%3E%20\(Visual%20Basic\).md) para a nova propriedade.  Você pode, então, manualmente adicionar um marcador `<value>` para descrever o valor que a propriedade representa.  
  
 Compile com [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar os comentários de documentação para um arquivo.  
  
## Exemplo  
 Este exemplo usa o marcador `<value>` para descrever qual valor a propriedade `Counter` contém.  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## Consulte também  
 [Marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)