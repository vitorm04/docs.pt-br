---
ms.openlocfilehash: 9544b65f31772d0f4cee918528a73171fec4de99
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021812"
---
### <a name="change-in-default-value-of-useshellexecute"></a>Alterar o valor padrão do UseShellExecute

<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>tem um valor `false` padrão de .NET Core. No .NET Framework, seu `true`valor padrão é .

#### <a name="change-description"></a>Descrição da alteração

<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>permite que você inicie um aplicativo diretamente, `Process.Start("mspaint.exe")` por exemplo, com código como o que lança o Paint. Ele também permite que você lance <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> indiretamente `true`um aplicativo associado se estiver definido como . No .NET Framework, o <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `true`valor padrão para `Process.Start("mytextfile.txt")` é , o que significa que o código como seria lançado Notepad, se você tiver associado arquivos *.txt* com esse editor. Para evitar a inicialção indireta de um aplicativo <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false`no .NET Framework, você deve definir explicitamente para . No .NET Core, o <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false`valor padrão para é . Isso significa que, por padrão, os aplicativos `Process.Start`associados não são lançados quando você chama .

Essa mudança foi introduzida no .NET Core por razões de desempenho. Normalmente, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> é usado para lançar um aplicativo diretamente. Lançar um aplicativo diretamente não precisa envolver o shell do Windows e incorrer no custo de desempenho associado. Para tornar este caso padrão mais rápido, <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> o `false`.NET Core altera o valor padrão de . Você pode optar pelo caminho mais lento se precisar.

#### <a name="version-introduced"></a>Versão introduzida

2.1

> [!NOTE]
> Em versões anteriores `UseShellExecute` do .NET Core, não foi implementado para windows.

#### <a name="recommended-action"></a>Ação recomendada

Se o seu aplicativo se <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> basear no comportamento antigo, ligue com <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set para `true` o <xref:System.Diagnostics.ProcessStartInfo> objeto.

#### <a name="category"></a>Categoria

Bibliotecas Core .NET

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
