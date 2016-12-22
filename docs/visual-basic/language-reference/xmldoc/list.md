---
title: "&lt;list&gt; (Visual Basic) | Microsoft Docs"
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
  - "Marca &lt;description&gt; (XML)"
  - "Marca &lt;item&gt; (XML)"
  - "Marca &lt;list&gt; (XML)"
  - "Marca &lt;listheader&gt; (XML)"
  - "Marca &lt;term&gt; (XML)"
  - "marca XML description"
  - "marca XML item"
  - "marca XML list"
  - "marca XML listheader"
  - "marca XML term"
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;list&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Define uma lista ou tabela.  
  
## Sintaxe  
  
```  
<list type="type">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
#### Parâmetros  
 `type`  
 O tipo de lista.  Deve ser um "marcador" para uma lista com marcadores, "número" para uma lista numerada, ou "tabela" para uma tabela de duas colunas.  
  
 `term`  
 Usada quando apenas `type` é "tabela". Um termo para definir, que é definido na marca de descrição.  
  
 `description`  
 Quando `type` é "marcador" ou "número", `description` é um item na lista quando `type` é "table", `description` é a definição de `term`.  
  
## Comentários  
 O `<listheader>` bloco define o título de uma tabela ou uma definição de lista.  Ao definir uma tabela, você só precisa fornecer uma entrada para `term` no título.  
  
 Cada item da lista é especificado com um `<item>` bloco.  Ao criar uma lista de definições, você deve especificar ambos `term` e `description`.  No entanto, para uma tabela, uma lista com marcadores ou uma lista numerada, você só precisa fornecer uma entrada para `description`.  
  
 Uma lista ou tabela pode ter quantos `<item>` bloqueia conforme necessário.  
  
 Compile com [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar os comentários de documentação para um arquivo.  
  
## Exemplo  
 Este exemplo usa a `<list>` marca para definir uma lista com marcadores na seção comentários.  
  
 [!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]  
  
## Consulte também  
 [Marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)