---
ms.openlocfilehash: 9520f8c6b6671917f5694bc602293a00e2dab82d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568245"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a><span data-ttu-id="0ff8c-101">ZipArchiveEntry não lida mais com arquivos com tamanhos de entrada inconsistentes</span><span class="sxs-lookup"><span data-stu-id="0ff8c-101">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>

<span data-ttu-id="0ff8c-102">Arquivos zip listam tamanho compactado e tamanho descompactado no diretório central e no cabeçalho local.</span><span class="sxs-lookup"><span data-stu-id="0ff8c-102">Zip archives list both compressed size and uncompressed size in the central directory and local header.</span></span>  <span data-ttu-id="0ff8c-103">Os dados de entrada em si também indicam seu tamanho.</span><span class="sxs-lookup"><span data-stu-id="0ff8c-103">The entry data itself also indicates its size.</span></span>  <span data-ttu-id="0ff8c-104">No .NET Core 2.2 e nas versões anteriores, esses valores nunca foram verificados quanto à consistência.</span><span class="sxs-lookup"><span data-stu-id="0ff8c-104">In .NET Core 2.2 and earlier versions, these values were never checked for consistency.</span></span> <span data-ttu-id="0ff8c-105">Começando com .NET Core 3.0, eles agora são.</span><span class="sxs-lookup"><span data-stu-id="0ff8c-105">Starting with .NET Core 3.0, they now are.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0ff8c-106">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="0ff8c-106">Change description</span></span>

<span data-ttu-id="0ff8c-107">No .NET Core 2.2 <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> e versões anteriores, o cabeçalho local discorda do cabeçalho central do arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="0ff8c-107">In .NET Core 2.2 and earlier versions, <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> succeeds even if the local header disagrees with the central header of the zip file.</span></span> <span data-ttu-id="0ff8c-108">Os dados são descompactados até que o fim do fluxo compactado seja atingido, mesmo que seu comprimento exceda o tamanho do arquivo não compactado listado no diretório central/cabeçalho local.</span><span class="sxs-lookup"><span data-stu-id="0ff8c-108">Data is decompressed until the end of the compressed stream is reached, even if its length exceeds the uncompressed file size listed in the central directory/local header.</span></span>

<span data-ttu-id="0ff8c-109">A partir do .NET Core <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> 3.0, o método verifica se o cabeçalho local e o cabeçalho central concordam com tamanhos compactados e não compactados de uma entrada.</span><span class="sxs-lookup"><span data-stu-id="0ff8c-109">Starting with .NET Core 3.0, the <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> method checks that local header and central header agree on compressed and uncompressed sizes of an entry.</span></span>  <span data-ttu-id="0ff8c-110">Caso isso não o faça, o método lança um <xref:System.IO.InvalidDataException> cabeçalho local do arquivo e/ou tamanhos de lista de descritores de dados que discordam do diretório central do arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="0ff8c-110">If they do not, the method throws an <xref:System.IO.InvalidDataException> if the archive's local header and/or data descriptor list sizes that disagree with the central directory of the zip file.</span></span> <span data-ttu-id="0ff8c-111">Ao ler uma entrada, os dados descompactados são truncados para o tamanho do arquivo não compactado listado no cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="0ff8c-111">When reading an entry, decompressed data is truncated to the uncompressed file size listed in the header.</span></span>

<span data-ttu-id="0ff8c-112">Essa alteração foi feita <xref:System.IO.Compression.ZipArchiveEntry> para garantir que um representasse corretamente o tamanho de seus dados e que apenas essa quantidade de dados fosse lida.</span><span class="sxs-lookup"><span data-stu-id="0ff8c-112">This change was made to ensure that a <xref:System.IO.Compression.ZipArchiveEntry> correctly represents the size of its data and that only that amount of data is read.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0ff8c-113">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="0ff8c-113">Version introduced</span></span>

<span data-ttu-id="0ff8c-114">3.0</span><span class="sxs-lookup"><span data-stu-id="0ff8c-114">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0ff8c-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="0ff8c-115">Recommended action</span></span>

<span data-ttu-id="0ff8c-116">Reempacote qualquer arquivo zip que exiba esses problemas.</span><span class="sxs-lookup"><span data-stu-id="0ff8c-116">Repackage any zip archive that exhibits these problems.</span></span>

#### <a name="category"></a><span data-ttu-id="0ff8c-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="0ff8c-117">Category</span></span>

<span data-ttu-id="0ff8c-118">CoreFx</span><span class="sxs-lookup"><span data-stu-id="0ff8c-118">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0ff8c-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="0ff8c-119">Affected APIs</span></span>

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
