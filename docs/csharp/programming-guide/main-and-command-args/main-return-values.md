---
title: Valores de retorno de Main() – Guia de Programação em C#
ms.custom: seodec18
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: ea6f93e52ade91e61bdfcbc35aeb56de9101e80f
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878924"
---
# <a name="main-return-values-c-programming-guide"></a>Valores retornados de Main() (Guia de Programação em C#)

O método `Main` pode retornar `void`:

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

Ele também pode retornar um `int`:

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

Se o valor retornado de `Main` não for usado, o retorno de `void` permite um código um pouco mais simples. No entanto, o retorno de um inteiro habilita o programa a comunicar informações de status para outros programas ou scripts, que invocam o arquivo executável. O valor retornado de `Main` é tratado como o código de saída para o processo. Se `void` for retornado de `Main`, o código de saída será implicitamente `0`. O exemplo a seguir mostra como o valor retornado de `Main` pode ser acessado.

## <a name="example"></a>Exemplo

Este exemplo usa ferramentas de linha de comando do [.NET Core](../../../core/index.md). Se você não estiver familiarizado com as ferramentas de linha de comando do .NET Core, poderá aprender sobre elas neste [Tópico de introdução](../../../core/tutorials/using-with-xplat-cli.md).

Modifique o método `Main` em *program.cs* da seguinte maneira:

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

Quando um programa é executado no Windows, qualquer valor retornado da função `Main` é armazenado em uma variável de ambiente. Essa variável de ambiente pode ser recuperada usando `ERRORLEVEL` de um arquivo em lotes ou `$LastExitCode` do PowerShell.

Você pode criar o aplicativo usando o comando `dotnet build` da [CLI do dotnet](../../../core/tools/dotnet.md).

Em seguida, crie um script do Powershell para executar o aplicativo e exibir o resultado. Cole o código a seguir em um arquivo de texto e salve-o como `test.ps1` na pasta que contém o projeto. Execute o script do PowerShell digitando `test.ps1` no prompt do PowerShell.

Como o código retorna zero, o arquivo em lotes relatará êxito. No entanto, se você alterar o MainReturnValTest.cs para retornar um valor diferente de zero e recompilar o programa, a execução subsequente do script do PowerShell reportará falha.

```powershell
dotnet run
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a>Saída de exemplo

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a>Valores retornados de Async Main

Os valores retornados de Async Main movem o código clichê necessário para chamar métodos assíncronos em `Main` para o código gerado pelo compilador. Anteriormente, você precisaria gravar esse constructo para chamar código assíncrono e assegurar que o programa fosse executado até que a operação assíncrona fosse concluída:

```csharp
public static void Main()
{
    AsyncConsoleWork().GetAwaiter().GetResult();
}

private static async Task<int> AsyncConsoleWork()
{
    // Main body here
    return 0;
}
```

Agora, isso pode ser substituído por:

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

A vantagem da nova sintaxe é que o compilador sempre gera o código correto.

## <a name="compiler-generated-code"></a>Código gerado pelo compilador

Quando o ponto de entrada do aplicativo retorna um `Task` ou `Task<int>`, o compilador gera um novo ponto de entrada que chama o método de ponto de entrada declarado no código do aplicativo. Supondo que esse ponto de entrada é chamado `$GeneratedMain`, o compilador gera o código a seguir para esses pontos de entrada:

- `static Task Main()` resulta no compilador emitindo o equivalente a `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task Main(string[])` resulta no compilador emitindo o equivalente a `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`
- `static Task<int> Main()` resulta no compilador emitindo o equivalente a `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task<int> Main(string[])` resulta no compilador emitindo o equivalente a `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`

> [!NOTE]
>Se os exemplos usassem o modificador `async` no método `Main`, o compilador geraria o mesmo código.

## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../programming-guide/index.md)
- [Referência de C#](../index.md)
- [Main() e argumentos de linha de comando](index.md)
- [Como: exibir argumentos de linha de comando](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
