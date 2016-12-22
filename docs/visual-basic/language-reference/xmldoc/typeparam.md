---
title: "&lt;typeparam&gt; (Visual Basic) | Microsoft Docs"
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
  - "Marca &lt;typeparam&gt; (XML)"
  - "marca XML typeparam"
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;typeparam&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Define o nome e a descrição de um parâmetro de tipo.  
  
## Sintaxe  
  
```  
<typeparam name="name">description</typeparam>  
```  
  
#### Parâmetros  
 `name`  
 Nome do parâmetro de tipo.  Envolva o nome em aspas duplas \(" "\).  
  
 `description`  
 Uma descrição do parâmetro de tipo.  
  
## Comentários  
 Use a marca `<typeparam>` no comentário de um tipo genérico ou declaração de membro genérico para descrever um dos parâmetros de tipo.  
  
 Compile com [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar os comentários de documentação para um arquivo.  
  
## Exemplo  
 Este exemplo usa a tag `<typeparam>` para descrever o parâmetro `id`.  
  
 [!code-vb[VbVbcnXmlDocComments#8](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/typeparam_1.vb)]  
  
## Consulte também  
 [Marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)