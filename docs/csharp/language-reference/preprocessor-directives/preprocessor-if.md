---
title: '#Diretiva de pré-processamento "if" (referência do C#)'
ms.date: 06/30/2018
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: c54a1fe0dba5f6d57b03b2ffeb4f1737fadfe039
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43000931"
---
# <a name="if-c-reference"></a>#if (Referência de C#)

Quando o Compilador do Visual C# encontra uma diretiva `#if`, seguida eventualmente por uma diretiva [#endif](preprocessor-endif.md), ele compila o código entre as diretivas somente quando o símbolo especificado é definido. Ao contrário do C e do C++, não é possível atribuir um valor numérico a um símbolo. A instrução #if em C# é booliana e testa apenas quando o símbolo foi definido ou não. Por exemplo:

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

É possível usar os operadores [==](../operators/equality-comparison-operator.md) (igualdade) e [!=](../operators/not-equal-operator.md) (desigualdade) apenas para testar [true](../keywords/true.md) ou [false](../keywords/false.md). True significa que o símbolo foi definido. A instrução `#if DEBUG` tem o mesmo significado que `#if (DEBUG == true)`. É possível usar os operadores [&&](../operators/conditional-and-operator.md) (e), [&#124;&#124;](../operators/conditional-or-operator.md) (ou) e [!](../operators/logical-negation-operator.md) (não) para avaliar se vários símbolos foram definidos. Também é possível agrupar os símbolos e operadores com parênteses.

## <a name="remarks"></a>Comentários

`#if`, juntamente com as diretivas [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md) e [#undef](preprocessor-undef.md), permite incluir ou excluir código com base na existência de um ou mais símbolos. Isso pode ser útil ao compilar o código para um build de depuração ou ao compilar para uma configuração específica.

Uma diretiva condicional que começa com uma diretiva `#if` deverá ser explicitamente encerrada com uma diretiva `#endif`.

A diretiva `#define` permite definir um símbolo. Ao usar o símbolo como a expressão passada para a diretiva `#if`, a expressão será avaliada como `true`.

Você também pode definir um símbolo com a opção do compilador [-define](../compiler-options/define-compiler-option.md). É possível excluir um símbolo com [#undef](preprocessor-undef.md).

Um símbolo definido com `-define` ou com `#define` não entra em conflito com uma variável do mesmo nome. Ou seja, um nome de variável não deve ser passado para uma diretiva de pré-processamento e um símbolo pode ser avaliado apenas por uma diretiva de pré-processamento.

O escopo de um símbolo criado com `#define` é o arquivo no qual ele foi definido.

O sistema de build também está ciente dos símbolos de pré-processamento predefinidos que representam várias [estruturas de destino](../../../standard/frameworks.md). Eles são úteis ao criar aplicativos que podem direcionar mais de uma implementação ou versão do .NET.

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

As constantes TRACE e DEBUG são exemplos de outros símbolos predefinidos. Para substituir os valores definidos no projeto, use a diretiva `#define`. Por exemplo, o símbolo DEBUG é definido automaticamente, de acordo com as propriedades de configuração do build (Modo de Depuração ou Modo de Versão).

## <a name="examples"></a>Exemplos

O exemplo a seguir mostra como definir um símbolo MYTEST em um arquivo e testar os valores dos símbolos MYTEST e DEBUG. A saída deste exemplo depende do fato de você criar o projeto no modo de configuração de versão ou no modo de configuração de depuração.

```csharp
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

O exemplo a seguir mostra como testar várias estruturas de destino para que você possa usar APIs mais recentes, quando possível:

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        WebClient _client = new WebClient();
#else
        HttpClient _client = new HttpClient();
#endif
    }
    //...
}
```

## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Diretivas do pré-processador do C#](index.md)  
- [Como compilar condicionalmente com Trace e Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).
