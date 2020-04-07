---
title: Valores de retorno de Main() – Guia de Programação em C#
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 7061b6c1988da9f6dfac115ee555a914531df863
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805933"
---
# <a name="main-return-values-c-programming-guide"></a>Valores retornados de Main() (Guia de Programação em C#)

O método `Main` pode retornar `void`:

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

Ele também pode retornar um `int`:

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

Se o valor retornado de `Main` não for usado, o retorno de `void` permite um código um pouco mais simples. No entanto, o retorno de um inteiro habilita o programa a comunicar informações de status para outros programas ou scripts, que invocam o arquivo executável. O valor retornado de `Main` é tratado como o código de saída para o processo. Se `void` for devolvido, o código de `Main` `0`saída será implicitamente . O exemplo a seguir mostra como o valor retornado de `Main` pode ser acessado.

## <a name="example"></a>Exemplo

Este exemplo usa ferramentas de linha de comando [.NET Core.](../../../core/index.yml) Se você não estiver familiarizado com as ferramentas de linha de comando .NET Core, você pode aprender sobre elas neste [artigo inicial](../../../core/tutorials/cli-create-console-app.md).

Modifique o método `Main` em *program.cs* da seguinte maneira:

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

Quando um programa é executado no Windows, qualquer valor retornado da função `Main` é armazenado em uma variável de ambiente. Essa variável de ambiente pode ser recuperada usando `ERRORLEVEL` de um arquivo em lotes ou `$LastExitCode` do PowerShell.

Você pode construir o aplicativo usando o comando [DOtnet CLI.](../../../core/tools/dotnet.md) `dotnet build`

Em seguida, crie um script do Powershell para executar o aplicativo e exibir o resultado. Cole o código a seguir em um arquivo de texto e salve-o como `test.ps1` na pasta que contém o projeto. Execute o script do PowerShell digitando `test.ps1` no prompt do PowerShell.

Como o código retorna zero, o arquivo em lotes relatará êxito. No entanto, se você alterar MainReturnValTest.cs para retornar um valor não-zero e, em seguida, recompilar o programa, a execução subseqüente do script powershell reportará falha.

```dotnetcli
dotnet run
```

```powershell
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

## <a name="see-also"></a>Confira também

- [C# Guia de Programação](../index.md)
- [C# Referência](../index.md)
- [Principais() e Argumentos de linha de comando](index.md)
- [Como exibir argumentos de linha de comando](./how-to-display-command-line-arguments.md)
