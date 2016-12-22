---
title: "#if (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "#if"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Diretiva #if [C#]"
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# #if (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Quando o compilador C\# encontra uma política de`#if` se houver, seguida por uma diretiva de [\#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) , irá compilar o código entre as diretivas somente se o símbolo especificado está definido.  Diferentemente de C e C\+\+, você não pode atribuir um valor numérico para um símbolo; a instrução \#if em C\# é booleano e testa somente se o símbolo foi definido ou não.  Por exemplo,  
  
```  
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
 Você pode usar os operadores [\=\=](../../../csharp/language-reference/operators/equality-comparison-operator.md) igualdade \(\), [\! \=](../../../csharp/language-reference/operators/not-equal-operator.md) \(desigualdade\) para testar somente para [true](../../../csharp/language-reference/keywords/true.md) ou [false](../../../csharp/language-reference/keywords/false.md) .  os meios verdadeiros o símbolo são definidos.  a instrução `#if DEBUG` tem o mesmo significado que `#if (DEBUG == true)`.  Você pode usar os operadores [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) \(e\), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) \(ou\), e [\!](../../../csharp/language-reference/operators/logical-negation-operator.md) \(não\) para avaliar se vários símbolos foram definidos.  Você também pode agrupar símbolos e operadores com parênteses.  
  
## Comentários  
 `#if`, juntamente com [\#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [\#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), [\#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), [\#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md), e políticas de [\#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) , permite que você inclua ou exclua o código com base na existência de um ou mais símbolos.  Isso pode ser útil ao criar o código para uma construção de depuração ou o para criar uma configuração específica.  
  
 Um início da diretiva condicional com uma política de `#if` deve ser explicitamente terminado com uma política de `#endif` .  
  
 `#define` permite que você defina um símbolo, de forma que, usando o símbolo porque a expressão passada à política de `#if` , a expressão avaliará a `true`.  
  
 Você também pode definir um símbolo com a opção de compilador [\/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) .  você pode undefine um símbolo com [\#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
 Um símbolo que você defina com `/define` ou com `#define` não está em conflito com uma variável com o mesmo nome.  Isto é, um nome de variável não deve ser passado para uma diretiva pré\-processamento e um símbolo só pode ser avaliado por uma diretiva pré\-processamento.  
  
 O escopo de um símbolo é criado com `#define` no arquivo que foi definido.  
  
## Exemplo  
  
```  
// preprocessor_if.cs  
#define DEBUG #define MYTEST  
using System;  
public class MyClass   
{  
    static void Main()   
    {  
#if (DEBUG && !MYTEST)  
        Console.WriteLine("DEBUG is defined");  
#elif (!DEBUG && MYTEST)  
        Console.WriteLine("MYTEST is defined");  
#elif (DEBUG && MYTEST)  
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else  
        Console.WriteLine("DEBUG and MYTEST are not defined");  
#endif  
    }  
}  
```  
  
  **A DEPURAÇÃO e MYTEST são definidos**   
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Diretivas de pré\-processador em C\#](../../../visual-basic/reference/command-line-compiler/index.md)