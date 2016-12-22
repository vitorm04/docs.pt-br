---
title: "&lt;paramref&gt; (Visual Basic) | Microsoft Docs"
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
  - "Marca &lt;paramref&gt; (XML)"
  - "marca XML paramref"
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;paramref&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Formata uma palavra como parâmetro.  
  
## Sintaxe  
  
```  
<paramref name="name"/>  
```  
  
#### Parâmetros  
 `name`  
 O nome do parâmetro para se referir a ele.  Envolva o nome em aspas duplas \(" "\).  
  
## Comentários  
 A etiqueta `<paramref>` dá a você uma maneira de se indicar que uma palavra é um parâmetro.  O arquivo XML pode ser processado para formatar este parâmetro em alguma forma distinta.  
  
 Compile com [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar os comentários de documentação para um arquivo.  
  
## Exemplo  
 Este uexemplo usa a etiqueta `<paramref>` para referir\-se ao parâmetro `id`.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## Consulte também  
 [Marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)