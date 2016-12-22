---
title: "&lt;c&gt; (Visual Basic) | Microsoft Docs"
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
  - "Marca &lt;c&gt; (XML)"
  - "marca c XML"
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;c&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Indica que o texto dentro uma descrição é o código.  
  
## Sintaxe  
  
```  
<c>text</c>  
```  
  
#### Parâmetros  
  
|||  
|-|-|  
|Parâmetro|Descrição|  
|`text`|O texto você deseja indicar como código.|  
  
## Comentários  
 A marca `<c>` lhe dá uma forma para indicar que o texto dentro uma descrição deve ser marcado como código.  Use [\<código\>](../../../visual-basic/language-reference/xmldoc/code.md) para indicar várias linhas como código.  
  
 Compile com [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar os comentários de documentação para um arquivo.  
  
## Exemplo  
 Este exemplo usa a marca `<c>` na seção de resumo para indicar que `Counter` é código.  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## Consulte também  
 [Marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)