---
ms.openlocfilehash: 9520f8c6b6671917f5694bc602293a00e2dab82d
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217055"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a>O ZipArchiveEntry não lida mais com os arquivos mortos com tamanhos de entrada inconsistentes

Os arquivos zip listam Tamanho compactado e Tamanho descompactado no diretório central e no cabeçalho local.  Os próprios dados de entrada também indicam seu tamanho.  No .NET Core 2,2 e versões anteriores, esses valores nunca foram verificados quanto à consistência. A partir do .NET Core 3,0, eles agora são.

#### <a name="change-description"></a>Alterar descrição

No .NET Core 2,2 e versões anteriores, <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> o é bem sucedido mesmo que o cabeçalho local desconcorde com o cabeçalho central do arquivo zip. Os dados são descompactados até que o final do fluxo compactado seja atingido, mesmo que seu comprimento exceda o tamanho do arquivo descompactado listado no cabeçalho do diretório central/local.

A partir do .NET Core 3,0, <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> o método verifica se o cabeçalho local e o cabeçalho central concordam em tamanhos compactados e não compactados de uma entrada.  Se não tiverem, o método lançará um <xref:System.IO.InvalidDataException> se o cabeçalho local do arquivo e/ou os tamanhos da lista do descritor de dados que discordarem com o diretório central do arquivo zip. Ao ler uma entrada, os dados descompactados são truncados para o tamanho de arquivo descompactado listado no cabeçalho.

Essa alteração foi feita para garantir que um <xref:System.IO.Compression.ZipArchiveEntry> represente corretamente o tamanho de seus dados e que apenas essa quantidade de dados seja lida.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Empacote novamente qualquer arquivo zip que exiba esses problemas.

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
