---
title: "&lt;param&gt; (Visual Basic) | Microsoft Docs"
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
  - "Marca &lt;param&gt; (XML)"
  - "marca XML param"
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;param&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Define o nome e descrição de um parâmetro.  
  
## Sintaxe  
  
```  
<param name="name">description</param>  
```  
  
#### Parâmetros  
 `name`  
 O nome do parâmetro de um método.  Envolva o nome em aspas duplas \(" "\).  
  
 `description`  
 Uma descrição para o parâmetro.  
  
## Comentários  
 A tag `<param>` deveria ser usada no comentário para uma declaração de método para descrever um dos parâmetros do método.  
  
 O texto para a marca de `<param>` aparecerá nos seguintes locais:  
  
-   Informações de parâmetro do IntelliSense.  Para obter mais informações, consulte [Usando IntelliSense](/visual-studio/ide/using-intellisense).  
  
-   pesquisador de objetos.  Para obter mais informações, consulte [Exibindo a estrutura do código](/visual-studio/ide/viewing-the-structure-of-code).  
  
 Compile com [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação a um arquivo.  
  
## Exemplo  
 Este exemplo usa a tag `<param>` para descrever o parâmetro `id`.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## Consulte também  
 [Marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)