---
ms.openlocfilehash: 7c0930f6606aa96d2863dc740aef8e9cab724b37
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344853"
---
### <a name="change-in-default-value-of-useshellexecute"></a>Alteração no valor padrão de UseShellExecute

<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> tem um valor padrão de `false` no .NET Core. Em .NET Framework, seu valor padrão é `true`.

#### <a name="change-description"></a>Descrição das alterações

<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> permite que você inicie um aplicativo diretamente, por exemplo, com um código como `Process.Start("mspaint.exe")` que inicia o Paint. Ele também permite que você inicie indiretamente um aplicativo associado se <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> estiver definido como `true`. No .NET Framework, o valor padrão de <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> é `true`, o que significa que o código como `Process.Start("mytextfile.txt")` iniciaria o bloco de notas, se você tiver associado arquivos *. txt* com esse editor. Para evitar a inicialização indireta de um aplicativo no .NET Framework, você deve definir explicitamente <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> como `false`. No .NET Core, o valor padrão para <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> é `false`. Isso significa que, por padrão, os aplicativos associados não são iniciados quando você chama `Process.Start`.

Essa alteração foi introduzida no .NET Core por motivos de desempenho. Normalmente, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> é usado para iniciar um aplicativo diretamente. Iniciar um aplicativo diretamente não precisa envolver o Shell do Windows e incorrer no custo de desempenho associado. Para tornar esse caso padrão mais rápido, o .NET Core altera o valor padrão de <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> para `false`. Você pode aceitar o caminho mais lento se precisar dele.

#### <a name="version-introduced"></a>Versão introduzida

2.1

> [!NOTE]
> Em versões anteriores do .NET Core, `UseShellExecute` não foi implementada para o Windows.

#### <a name="recommended-action"></a>Ação recomendada

Se seu aplicativo depender do comportamento antigo, chame <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> com <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> definido como `true` no objeto <xref:System.Diagnostics.ProcessStartInfo>.

#### <a name="category"></a>Categoria

CoreFx

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
