---
title: "&lt;example&gt; (Visual Basic) | Microsoft Docs"
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
  - "Marca &lt;example&gt; (XML)"
  - "marca XML example"
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;example&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica um exemplo para o membro.  
  
## Sintaxe  
  
```  
<example>description</example>  
```  
  
#### Parâmetros  
 `description`  
 Uma descrição do código de exemplo.  
  
## Comentários  
 A marca `<example>` permite que você especifique um exemplo de como usar um método ou outro membro da biblioteca.  Isso normalmente envolve usar a marca [\<código\>](../../../visual-basic/language-reference/xmldoc/code.md).  
  
 Compile com [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar os comentários de documentação para um arquivo.  
  
## Exemplo  
 Este exemplo usa a marca `<example>` para incluir um exemplo para usar o campo `ID`.  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/example_1.vb)]  
  
## Consulte também  
 [Marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)