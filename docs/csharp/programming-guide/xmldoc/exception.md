---
title: "&lt;exception&gt; (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "exception"
  - "<exception>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Marca &lt;exception&gt; (XML) C#"
  - "marca XML C# exception"
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;exception&gt; (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## Sintaxe  
  
```  
<exception cref="member">description</exception>  
```  
  
#### Parâmetros  
 cref \= " `member`"  
 Uma referência a uma exceção que está disponível a partir do atual ambiente de compilação.  O compilador verifica se a exceção apresentada existe e se traduz `member` para o nome do elemento canônico na saída XML.  `member`deve aparecer entre aspas duplas \(""\).  
  
 Para obter mais informações sobre como criar uma referência de cref para um tipo genérico, consulte [\<see\>](../../../csharp/programming-guide/xmldoc/see.md).  
  
 `description`  
 Uma descrição da exceção.  
  
## Comentários  
 O \<exception\> marca permite especificar quais exceções podem ser geradas.  Essa marca pode ser aplicada às definições de métodos, propriedades, indexadores e eventos.  
  
 Compilar com  [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) a comentários de documentação do processo para um arquivo.  
  
 Para obter mais informações sobre o tratamento de exceções, consulte [Exceções e manipulação de exceções](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md).  
  
## Exemplo  
 [!code-cs[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)