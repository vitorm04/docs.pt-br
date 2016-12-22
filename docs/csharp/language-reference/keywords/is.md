---
title: "is (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "is_CSharpKeyword"
  - "is"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave is [C#]"
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# is (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Verifica se um objeto é compatível com um determinado tipo.  Por exemplo, o código a seguir pode determinar se um objeto é uma instância da `MyObject` tipo ou um tipo que deriva de `MyObject`:  
  
```  
if (obj is MyObject)  
{  
}  
```  
  
 Um `is` expressão for avaliada como `true` se a expressão fornecida não for nulo, e o objeto fornecido pode ser convertido para o tipo fornecido sem causar uma exceção seja lançada.  
  
 O `is` palavra\-chave faz com que um aviso de tempo de compilação se a expressão é conhecida por ser sempre `true` ou ser sempre `false`, mas normalmente avalia a compatibilidade do tipo em tempo de execução.  
  
 O `is` operador não pode ser sobrecarregado.  
  
 Observe que o `is` operador considera somente conversões de referência, conversões boxing e unboxing conversões.  Outras conversões, como conversões definidas pelo usuário, não são considerados.  
  
 Métodos anônimos não são permitidos no lado esquerdo da `is` operador.  Essa exceção inclui expressões lambda.  
  
## Exemplo  
 [!code-cs[csrefKeywordsOperator#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/is_1.cs)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [typeof](../../../csharp/language-reference/keywords/typeof.md)   
 [as](../../../csharp/language-reference/keywords/as.md)   
 [Palavras\-chave do operador](../../../csharp/language-reference/keywords/operator-keywords.md)