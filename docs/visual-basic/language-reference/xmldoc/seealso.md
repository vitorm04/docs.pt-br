---
title: "&lt;seealso&gt; (Visual Basic) | Microsoft Docs"
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
  - "Marca &lt;seealso&gt; (XML)"
  - "marca XML seealso"
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;seealso&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica um link que aparece na seção Consulte Também.  
  
## Sintaxe  
  
```  
<seealso cref="member"/>  
```  
  
#### Parâmetros  
 `member`  
 Uma referência a um membro ou campo que está disponível para ser chamado a partir do ambiente de compilação atual.  O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome do elemento no XML de saída.  `member`deve aparecer entre aspas duplas \(""\).  
  
## Comentários  
 Use a marca `<seealso>` para especificar o texto que você deseja que apareça em uma seção Consulte Também.  Use [\<see\>](../../../visual-basic/language-reference/xmldoc/see.md) para especificar um link de dentro do texto.  
  
 Compile com [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar os comentários de documentação para um arquivo.  
  
## Exemplo  
 Este exemplo usa a marca `<seealso>` na seção comentários `DoesRecordExist` para referir\-se ao método `UpdateRecord`.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/seealso_1.vb)]  
  
## Consulte também  
 [Marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)