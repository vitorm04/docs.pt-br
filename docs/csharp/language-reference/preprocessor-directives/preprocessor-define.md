---
title: '##define – Referência de C#'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: 3b543181e3d836226759e77f0d56ed3c3e57e7ea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696198"
---
# <a name="define-c-reference"></a>#define (Referência de C#)
Use `#define` para definir um símbolo. Quando você usa o símbolo como a expressão passada para a diretiva [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), a expressão será avaliada como `true`, conforme mostra o exemplo a seguir:  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  A diretiva `#define` não pode ser usada para declarar valores constantes como normalmente é feito em C e C++. As constantes em C# são mais bem definidas como membros estáticos de uma classe ou struct. Se você tiver várias dessas constantes, considere criar uma classe "Constantes" separada para guardá-las.  
  
 Os símbolos podem ser usados para especificar condições para compilação. É possível testar o símbolo com [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ou [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md). Você também pode usar o <xref:System.Diagnostics.ConditionalAttribute> para executar uma compilação condicional.  
  
 É possível definir um símbolo, mas não é possível atribuir um valor a um símbolo. A diretiva `#define` deve ser exibida no arquivo antes de usar as instruções que também não são diretivas de pré-processador.  
  
 Você também pode definir um símbolo com a opção do compilador [-define](../../../csharp/language-reference/compiler-options/define-compiler-option.md). É possível excluir um símbolo com [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
 Um símbolo definido com `-define` ou com `#define` não entra em conflito com uma variável do mesmo nome. Ou seja, um nome de variável não deve ser passado para uma diretiva de pré-processador e um símbolo apenas pode ser avaliado por uma diretiva de pré-processador.  
  
 O escopo de um símbolo criado usando `#define` é o arquivo no qual o símbolo foi definido.  
  
 Como mostra o exemplo a seguir, é necessário colocar as diretivas `#define` na parte superior do arquivo.  
  
```csharp  
#define DEBUG  
//#define TRACE  
#undef TRACE  
  
using System;  
  
public class TestDefine  
{  
    static void Main()  
    {  
#if (DEBUG)  
        Console.WriteLine("Debugging is enabled.");  
#endif  
  
#if (TRACE)  
     Console.WriteLine("Tracing is enabled.");  
#endif  
    }  
}  
// Output:  
// Debugging is enabled.  
```  
  
 Para obter um exemplo de como excluir um símbolo, consulte [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Diretivas do pré-processador do C#](../../../csharp/language-reference/preprocessor-directives/index.md)
- [const](../../../csharp/language-reference/keywords/const.md)
- [Como: compilar condicionalmente com Trace e Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)
- [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
