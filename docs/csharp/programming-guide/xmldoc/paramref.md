---
title: "&lt;paramref&gt; (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "paramref"
  - "<paramref>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Marca &lt;paramref&gt; (XML) C#"
  - "marca XML C# paramref"
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;paramref&gt; (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## Sintaxe  
  
```  
<paramref name="name"/>  
```  
  
#### Parâmetros  
 `name`  
 O nome do parâmetro para se referir a ele.  Envolva o nome em aspas duplas \(" "\).  
  
## Comentários  
 O \<paramref\> marca oferece uma maneira para indicar que uma palavra no código comentários, por exemplo em \<summary\> ou \<remarks\> bloco refere\-se a um parâmetro.  O arquivo XML pode ser processado para formatar essa palavra de alguma maneira distinta, como com uma fonte em negrito ou itálico.  
  
 Compilar com  [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) a comentários de documentação do processo para um arquivo.  
  
## Exemplo  
 [!code-cs[csProgGuideDocComments#7](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/paramref_1.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)