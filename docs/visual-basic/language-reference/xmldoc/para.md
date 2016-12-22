---
title: "&lt;para&gt; (Visual Basic) | Microsoft Docs"
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
  - "Marca &lt;para&gt; (XML)"
  - "marca XML para"
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;para&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica que o conteúdo é formatado como um parágrafo.  
  
## Sintaxe  
  
```  
<para>content</para>  
```  
  
#### Parâmetros  
 `content`  
 O texto do parágrafo.  
  
## Comentários  
 A marca `<para>` é para uso dentro de uma marca, como [\<summary\>](../Topic/%3Csummary%3E%20\(Visual%20Basic\).md), [\<remarks\>](../Topic/%3Cremarks%3E%20\(Visual%20Basic\).md), ou [\<returns\>](../../../visual-basic/language-reference/xmldoc/returns.md) e permite que você adicione estrutura ao texto.  
  
 Compile com [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar os comentários de documentação para um arquivo.  
  
## Exemplo  
 Este exemplo usa a marca `<para>` para dividir a seção Comentários para o método `UpdateRecord` em dois parágrafos.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/para_1.vb)]  
  
## Consulte também  
 [Marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)