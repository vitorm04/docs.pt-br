---
title: '#Diretiva de pré-processamento "if" – Referência de C#'
ms.date: 10/27/2019
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: d047b88f202341a795834809d0b601706c30fcb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75899847"
---
# <a name="if-c-reference"></a>#if (referência C#)

Quando o Compilador do Visual C# encontra uma diretiva `#if`, seguida eventualmente por uma diretiva [#endif](preprocessor-endif.md), ele compila o código entre as diretivas somente quando o símbolo especificado é definido. Ao contrário do C e do C++, não é possível atribuir um valor numérico a um símbolo. A `#if` declaração em C# é booleana e só testa se o símbolo foi definido ou não. Por exemplo: 

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

Você pode usar [==](../operators/equality-operators.md#equality-operator-) os operadores (igualdade) e [!=](../operators/equality-operators.md#inequality-operator-) (desigualdade) apenas `true` para `false`testar os valores [bool](../builtin-types/bool.md) ou . `true`significa que o símbolo é definido. A instrução `#if DEBUG` tem o mesmo significado que `#if (DEBUG == true)`. Você pode usar o [&& (e)](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) [&#124;&#124; (ou)](../operators/boolean-logical-operators.md#conditional-logical-or-operator-)e [! (não)](../operators/boolean-logical-operators.md#logical-negation-operator-) operadores para avaliar se vários símbolos foram definidos. Também é possível agrupar os símbolos e operadores com parênteses.

## <a name="remarks"></a>Comentários

`#if`, juntamente com as [diretivas #else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md)e [#undef,](preprocessor-undef.md) permite incluir ou excluir código com base na existência de um ou mais símbolos. Isso pode ser útil ao compilar o código para um build de depuração ou ao compilar para uma configuração específica.

Uma diretiva condicional que começa com uma diretiva `#if` deverá ser explicitamente encerrada com uma diretiva `#endif`.

A diretiva `#define` permite definir um símbolo. Ao usar o símbolo como a expressão passada para a diretiva `#if`, a expressão será avaliada como `true`.

Você também pode definir um símbolo com a opção [-definir](../compiler-options/define-compiler-option.md) compilador. É possível excluir um símbolo com [#undef](preprocessor-undef.md).

Um símbolo definido com `-define` ou com `#define` não entra em conflito com uma variável do mesmo nome. Ou seja, um nome de variável não deve ser passado para uma diretiva de pré-processamento e um símbolo pode ser avaliado apenas por uma diretiva de pré-processamento.

O escopo de um símbolo criado com `#define` é o arquivo no qual ele foi definido.

O sistema de compilação também está ciente de símbolos predefinidos de pré-processador que representam [diferentes frameworks de destino](../../../standard/frameworks.md) em projetos no estilo SDK. Eles são úteis ao criar aplicativos que podem direcionar mais de uma implementação ou versão do .NET.

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> Para projetos tradicionais do .NET Framework, você deve configurar manualmente os símbolos de compilação condicional para as diferentes estruturas de destino no Visual Studio através das páginas de propriedades do projeto.

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

## <a name="see-also"></a>Confira também

- [C# Referência](../index.md)
- [C# Guia de Programação](../../programming-guide/index.md)
- [C# Diretivas de pré-processador](index.md)
- [Como compilar condicionalmente com Trace e Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
