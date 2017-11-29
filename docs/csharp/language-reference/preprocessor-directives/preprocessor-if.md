---
title: "#<a name=\"if-c-reference\"></a>if (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#if'
helpviewer_keywords: '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e4e3b79f64f5190d48d7248726ecdf031ad685e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="if-c-reference"></a>#if (Referência de C#)
Quando o compilador C# encontra uma diretiva `#if`, seguida eventualmente por uma diretiva [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), ele compilará o código entre as diretivas somente se o símbolo especificado for definido.  Diferentemente do C e do C++, não é possível atribuir um valor numérico a um símbolo; a instrução #if em C# é booliana e testa somente se o símbolo foi definido ou não. Por exemplo,  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
 É possível usar os operadores [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) (igualdade), [!=](../../../csharp/language-reference/operators/not-equal-operator.md) (desigualdade) apenas para testar [true](../../../csharp/language-reference/keywords/true.md) ou [false](../../../csharp/language-reference/keywords/false.md). True significa que o símbolo foi definido. A instrução `#if DEBUG` tem o mesmo significado que `#if (DEBUG == true)`. É possível usar os operadores [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) (e), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) (ou) e [!](../../../csharp/language-reference/operators/logical-negation-operator.md) (não) para avaliar se vários símbolos foram definidos. Também é possível agrupar os símbolos e operadores com parênteses.  
  
## <a name="remarks"></a>Comentários  
 `#if`, juntamente com as diretivas [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) e [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md), permite incluir ou excluir código com base na existência de um ou mais símbolos. Isso pode ser útil ao compilar o código para um build de depuração ou ao compilar para uma configuração específica.  
  
 Uma diretiva condicional que começa com uma diretiva `#if` deverá ser explicitamente encerrada com uma diretiva `#endif`.  
  
 `#define` permite definir um símbolo, de modo que, usando o símbolo como a expressão passada para a diretiva `#if`, a expressão será avaliada como `true`.  
  
 Também é possível definir um símbolo com a opção do compilador [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md). É possível excluir um símbolo com [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
 Um símbolo definido com `/define` ou com `#define` não entra em conflito com uma variável do mesmo nome. Ou seja, um nome de variável não deve ser passado para uma diretiva de pré-processador e um símbolo apenas pode ser avaliado por uma diretiva de pré-processador.  
  
 O escopo de um símbolo criado com `#define` é o arquivo no qual ele foi definido.  
  
## <a name="example"></a>Exemplo  
  
```csharp
// preprocessor_if.cs  
#define DEBUG
#define MYTEST  
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
  
 **DEBUG e MYTEST são definidos**  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Diretivas do pré-processador do C#](../../../csharp/language-reference/preprocessor-directives/index.md)
