---
title: "&lt;code&gt; (Visual Basic) | Microsoft Docs"
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
  - "Marca &lt;code&gt; (XML)"
  - "marca XML code"
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;code&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Indica que o texto tem várias linhas de código.  
  
## Sintaxe  
  
```  
<code>content</code>  
```  
  
#### Parâmetros  
 `content`  
 O texto a se marcar como código.  
  
## Comentários  
 Use a marca `<code>` para indicar que várias linhas são código.  Use [\<c\>](../../../visual-basic/language-reference/xmldoc/c.md) para indicar que o texto dentro uma descrição deve ser marcado como código.  
  
 Compile com [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar os comentários de documentação para um arquivo.  
  
## Exemplo  
 Este exemplo usa a marca \<código\> para incluir exemplo de código para usar o campo `ID`.  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## Consulte também  
 [Marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)