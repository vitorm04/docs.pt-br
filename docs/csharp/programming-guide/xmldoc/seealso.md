---
title: "&lt;seealso&gt; (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "cref"
  - "<seealso>"
  - "seealso"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Marca &lt;seealso&gt; (XML) C#"
  - "cref [C#]"
  - "cref [C#], consulte também"
  - "referências cruzadas [C#], marcas"
  - "consulte também marca XML C#"
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;seealso&gt; (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## Sintaxe  
  
```  
<seealso cref="member"/>  
```  
  
#### Parâmetros  
 cref \= " `member`"  
 Uma referência a um membro ou campo que está disponível para ser chamado a partir do ambiente de compilação atual.  O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome do elemento no XML de saída.`member` deve aparecer entre aspas duplas \(""\).  
  
 Para obter informações sobre como criar uma referência de cref para um tipo genérico, consulte [\<see\>](../../../csharp/programming-guide/xmldoc/see.md).  
  
## Comentários  
 O \<seealso\> marca permite especificar o texto que você talvez queira aparecem na seção Consulte também.  Use  [\<see\>](../../../csharp/programming-guide/xmldoc/see.md) para especificar um link a partir do texto.  
  
 Compilar com  [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) a comentários de documentação do processo para um arquivo.  
  
## Exemplo  
 Consulte  [\<summary\>](../Topic/%3Csummary%3E%20\(C%23%20Programming%20Guide\).md) para obter um exemplo do uso de \<seealso\>.  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)