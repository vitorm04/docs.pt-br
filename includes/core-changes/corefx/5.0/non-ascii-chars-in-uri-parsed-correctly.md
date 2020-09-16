---
ms.openlocfilehash: faf9459ab9002e6149560e2a3452265fa246bf6b
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720172"
---
### <a name="uri-paths-with-non-ascii-characters-parse-correctly-on-unix"></a>Caminhos de URI com caracteres não ASCII são analisados corretamente no UNIX

Um bug foi corrigido na <xref:System.Uri?displayProperty=fullName> classe, de modo que os caminhos de URI absolutos que contêm caracteres não-ASCII agora são analisados corretamente em plataformas UNIX.

#### <a name="change-description"></a>Descrição das alterações

Nas versões anteriores do .NET, caminhos de URI absolutos que contêm caracteres não ASCII são analisados incorretamente em plataformas UNIX e os segmentos do caminho são duplicados. (Caminhos absolutos são aqueles que começam com "/".) O problema de análise foi corrigido para o .NET 5,0. Se você mudar de uma versão anterior do .NET para o .NET 5,0 ou posterior, você obterá valores diferentes produzidos por <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType> , <xref:System.Uri.ToString?displayProperty=nameWithType> e outros <xref:System.Uri> Membros.

Considere a saída do código a seguir quando executada no UNIX.

```csharp
var myUri = new Uri("/üri");

Console.WriteLine($"AbsoluteUri: {myUri.AbsoluteUri}");
Console.WriteLine($"ToString: {myUri.ToString()}");
```

Saída na versão anterior do .NET:

```text
AbsoluteUri: /%C3%BCri/%C3%BCri
ToString: /üri/üri
```

Saída no .NET 5,0 ou versão posterior:

```text
AbsoluteUri: /%C3%BCri
ToString: /üri
```

#### <a name="version-introduced"></a>Versão introduzida

5,0

#### <a name="recommended-action"></a>Ação recomendada

Se você tiver um código que espera e contas para os segmentos de caminho duplicados, você pode remover esse código.

#### <a name="category"></a>Categoria

Bibliotecas principais do .NET

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->
