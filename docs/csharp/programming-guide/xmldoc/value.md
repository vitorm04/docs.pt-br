---
title: "&lt;value&gt; (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "<value>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Marca &lt;value&gt; (XML) C#"
  - "marca XML C# value"
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;value&gt; (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## Sintaxe  
  
```  
<value>property-description</value>  
```  
  
#### Parâmetros  
 `property-description`  
 Uma descrição para a propriedade.  
  
## Comentários  
 O \<value\> marca permite descrever o valor que representa a uma propriedade.  Observe que quando você adiciona uma propriedade por meio do Assistente de código no Visual Studio.Ambiente de desenvolvimento NET, ele adicionará um  [\<summary\>](../Topic/%3Csummary%3E%20\(C%23%20Programming%20Guide\).md) a marca para a nova propriedade.  Você deve adicionar manualmente um \<value\> marca para descrever o valor que a propriedade representa.  
  
 Compilar com  [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) a comentários de documentação do processo para um arquivo.  
  
## Exemplo  
 [!code-cs[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)