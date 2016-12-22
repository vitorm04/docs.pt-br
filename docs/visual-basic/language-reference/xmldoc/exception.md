---
title: "&lt;exception&gt; (Visual Basic) | Microsoft Docs"
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
  - "Marca &lt;exception&gt; (XML)"
  - "marca XML exception"
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;exception&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica quais exceções podem ser geradas.  
  
## Sintaxe  
  
```  
<exception cref="member">description</exception>  
```  
  
#### Parâmetros  
 `member`  
 Uma referência a uma exceção que está disponível a partir do atual ambiente de compilação.  O compilador verifica se a exceção apresentada existe e se traduz `member` para o nome do elemento canônico na saída XML.  `member`deve aparecer entre aspas duplas \(""\).  
  
 `description`  
 Uma descrição.  
  
## Comentários  
 Use o `<exception>` marca para especificar quais exceções podem ser geradas.  Esta marca é aplicada a uma definição de método.  
  
 Compile com [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar os comentários de documentação para um arquivo.  
  
## Exemplo  
 Este exemplo usa a `<exception>` marca para descrever uma exceção que o `IntDivide` função pode lançar.  
  
 [!code-vb[VbVbcnXmlDocComments#3](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]  
  
## Consulte também  
 [Marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)