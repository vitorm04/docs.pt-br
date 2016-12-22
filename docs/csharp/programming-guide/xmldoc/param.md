---
title: "&lt;param&gt; (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "param"
  - "<param>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Marca &lt;param&gt; (XML) C#"
  - "marca XML C# param"
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;param&gt; (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

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
 O \<param\> marca deve ser usada no comentário para uma declaração de método para descrever um dos parâmetros do método.  Para documentar os vários parâmetros, use vários \<param\> marcas de formatação.  
  
 O texto para \<param\> marca será exibida no IntelliSense, o Pesquisador de objetos e no relatório da Web de comentário de código.  
  
 Compilar com  [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) a comentários de documentação do processo para um arquivo.  
  
## Exemplo  
 [!code-cs[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)