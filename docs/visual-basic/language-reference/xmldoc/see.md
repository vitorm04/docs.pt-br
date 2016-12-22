---
title: "&lt;see&gt; (Visual Basic) | Microsoft Docs"
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
  - "Marca &lt;see&gt; (XML)"
  - "marca XML see"
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;see&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica um link para outro membro.  
  
## Sintaxe  
  
```  
<see cref="member"/>  
```  
  
#### Parâmetros  
 `member`  
 Uma referência a um membro ou campo que está disponível para ser chamado a partir do ambiente de compilação atual.  O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome do elemento no XML de saída.  `member`deve aparecer entre aspas duplas \(""\).  
  
## Comentários  
 Use a etiqueta `<see>` para especificar um link de dentro do texto.  Use [\<seealso\>](../../../visual-basic/language-reference/xmldoc/seealso.md) para indicar texto que você possa desejar que seja exibido em uma seção " Consulte também ".  
  
 Compile com [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar os comentários de documentação para um arquivo.  
  
## Exemplo  
 Este exemplo usa a marca `<see>` na seção comentários `UpdateRecord` para referir\-se ao método `DoesRecordExist`.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/see_1.vb)]  
  
## Consulte também  
 [Marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)