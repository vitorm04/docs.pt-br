---
title: Main() e argumentos de linha de comando – Guia de Programação em C#
ms.date: 08/02/2017
f1_keywords:
- CS5001
- main_CSharpKeyword
- Main
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
ms.openlocfilehash: 190216b01ea416aedbca270a6d7a5acbf0c2e797
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200113"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main() e argumentos de linha de comando (Guia de Programação em C#)

O método `Main` é o ponto de entrada de um aplicativo C#. (Bibliotecas e serviços não exigem um `Main` método como um ponto de entrada.) Quando o aplicativo é iniciado, o `Main` método é o primeiro método que é invocado.

 Pode haver apenas um ponto de entrada em um programa C#. Se tiver mais de uma classe que tenha um `Main` método, você deverá compilar seu programa com a opção do compilador **/main** para especificar qual método `Main` será usado como ponto de entrada. Para obter mais informações, consulte [-Main (opções do compilador C#)](../../language-reference/compiler-options/main-compiler-option.md).

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a>Visão geral

- O método `Main` é o ponto de entrada de um programa executável; é onde o controle do programa começa e termina.
- `Main` é declarado dentro de uma classe ou struct. O `Main` deve ser [estático](../../language-reference/keywords/static.md) e não precisa ser [público](../../language-reference/keywords/public.md). (No exemplo anterior, ele recebe o acesso padrão de [Private](../../language-reference/keywords/private.md).) A classe ou struct delimitador não precisa ser estático.
- O `Main` pode ter um tipo de retorno `void`, `int` ou, a partir do C# 7.1, `Task` ou `Task<int>`.
- Se e somente se `Main` o retornar `Task` um `Task<int>`ou, a Declaração `Main` de poderá incluir [`async`](../../language-reference/keywords/async.md) o modificador. Observe que isso exclui especificamente um método `async void Main`.
- O método `Main` pode ser declarado com ou sem um parâmetro `string[]` que contém os argumentos de linha de comando. Ao usar o Visual Studio para criar aplicativos do Windows, você pode adicionar o parâmetro manualmente ou, <xref:System.Environment.GetCommandLineArgs> caso contrário, usar o método para obter os [argumentos de linha de comando](command-line-arguments.md). Os parâmetros são lidos como argumentos de linha de comando indexados por zero. Ao contrário de C e C++, o nome do programa não é tratado como o primeiro argumento de linha de comando `args` na matriz, mas é o primeiro elemento do <xref:System.Environment.GetCommandLineArgs> método.

Veja a seguir uma lista de assinaturas `Main` válidas:

```csharp
public static void Main() { }
public static int Main() { }
public static void Main(string[] args) { }
public static int Main(string[] args) { }
public static async Task Main() { }
public static async Task<int> Main() { }
public static async Task Main(string[] args) { }
public static async Task<int> Main(string[] args) { }
```

Todos os exemplos anteriores usam o modificador de acessador público. Isso é típico, mas não é necessário.

A adição dos tipos de retorno `async`, `Task` e `Task<int>` simplifica o código do programa quando os aplicativos do console precisam iniciar e realizar operações assíncronas `await` no `Main`.

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Confira também

- [Compilando pela linha de comando com csc.exe](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Guia de programação C#](../index.md)
- [Métodos](../classes-and-structs/methods.md)
- [Dentro de um programa C#](../inside-a-program/index.md)
