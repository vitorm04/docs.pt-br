---
ms.openlocfilehash: 9520f8c6b6671917f5694bc602293a00e2dab82d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568245"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a>ZipArchiveEntry não lida mais com arquivos com tamanhos de entrada inconsistentes

Arquivos zip listam tamanho compactado e tamanho descompactado no diretório central e no cabeçalho local.  Os dados de entrada em si também indicam seu tamanho.  No .NET Core 2.2 e nas versões anteriores, esses valores nunca foram verificados quanto à consistência. Começando com .NET Core 3.0, eles agora são.

#### <a name="change-description"></a>Descrição da alteração

No .NET Core 2.2 <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> e versões anteriores, o cabeçalho local discorda do cabeçalho central do arquivo zip. Os dados são descompactados até que o fim do fluxo compactado seja atingido, mesmo que seu comprimento exceda o tamanho do arquivo não compactado listado no diretório central/cabeçalho local.

A partir do .NET Core <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> 3.0, o método verifica se o cabeçalho local e o cabeçalho central concordam com tamanhos compactados e não compactados de uma entrada.  Caso isso não o faça, o método lança um <xref:System.IO.InvalidDataException> cabeçalho local do arquivo e/ou tamanhos de lista de descritores de dados que discordam do diretório central do arquivo zip. Ao ler uma entrada, os dados descompactados são truncados para o tamanho do arquivo não compactado listado no cabeçalho.

Essa alteração foi feita <xref:System.IO.Compression.ZipArchiveEntry> para garantir que um representasse corretamente o tamanho de seus dados e que apenas essa quantidade de dados fosse lida.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Reempacote qualquer arquivo zip que exiba esses problemas.

#### <a name="category"></a>Categoria

CoreFx

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.ExtractToDirectory%2A?displayProperty=nameWithType>

<!--

### Affected APIs

`M:System.IO.Compression.ZipArchiveEntry.Open`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A`
`Overload:System.IO.Compression.ZipFile.ExtractToDirectory%2A`

-->
