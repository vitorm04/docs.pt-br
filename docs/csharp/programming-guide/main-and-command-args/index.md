---
title: 'Main() e argumentos de linha de comando – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 08/02/2017
f1_keywords:
  - CS5001
  - main_CSharpKeyword
  - Main
helpviewer_keywords:
  - 'Main method [C#]'
  - 'C# language, command-line arguments'
  - 'arguments [C#], command-line'
  - 'command line [C#], arguments'
  - 'command-line arguments [C#], Main method'
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main() e argumentos de linha de comando (Guia de Programação em C#)

O método `Main` é o ponto de entrada de um aplicativo C#. (Bibliotecas e serviços não exigem um método `Main` como um ponto de entrada.) Quando o aplicativo é iniciado, o método `Main` é o primeiro método invocado.

 Pode haver apenas um ponto de entrada em um programa C#. Se tiver mais de uma classe que tenha um `Main` método, você deverá compilar seu programa com a opção do compilador **/main** para especificar qual método `Main` será usado como ponto de entrada. Para obter mais informações, consulte [/main (opções do compilador C#)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).

 [!code-csharp[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]

## <a name="overview"></a>Visão geral

- O método `Main` é o ponto de entrada de um programa executável; é onde o controle do programa começa e termina.
- `Main` é declarado dentro de uma classe ou struct. O `Main` deve ser [estático](../../../csharp/language-reference/keywords/static.md) e não precisa ser [público](../../../csharp/language-reference/keywords/public.md). (No exemplo anterior, ele recebe o acesso padrão de [particular](../../../csharp/language-reference/keywords/private.md).) A classe delimitadora ou struct não deve ser estático.
- O `Main` pode ter um tipo de retorno `void`, `int` ou, a partir do C# 7.1, `Task` ou `Task<int>`.
- Se e somente se `Main` retornar um `Task` ou `Task<int>`, a declaração de `Main` pode incluir o modificador [`async`](../../language-reference/keywords/async.md). Observe que isso exclui especificamente um método `async void Main`.
- O método `Main` pode ser declarado com ou sem um parâmetro `string[]` que contém os argumentos de linha de comando. Ao usar o Visual Studio para criar aplicativos do Windows, você pode adicionar o parâmetro manualmente ou usar a classe <xref:System.Environment> para obter os argumentos de linha de comando. Os parâmetros são lidos como argumentos de linha de comando indexados por zero. Ao contrário de C e C++, o nome do programa não é tratado como o primeiro argumento de linha de comando.

A adição dos tipos de retorno `async`, `Task` e `Task<int>` simplifica o código do programa quando os aplicativos do console precisam iniciar e realizar operações assíncronas `await` no `Main`.

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Build pela linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [Por dentro de um programa em C#](../../../csharp/programming-guide/inside-a-program/index.md)
