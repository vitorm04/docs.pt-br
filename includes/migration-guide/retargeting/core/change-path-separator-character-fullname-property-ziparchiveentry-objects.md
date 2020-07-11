---
ms.openlocfilehash: f87d0dbeda6094bd745f5b580772b1161f30d0d5
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86218242"
---
### <a name="change-in-path-separator-character-in-fullname-property-of-ziparchiveentry-objects"></a><span data-ttu-id="0729f-101">Alteração no caractere separador de caminho na propriedade FullName de objetos ZipArchiveEntry</span><span class="sxs-lookup"><span data-stu-id="0729f-101">Change in path separator character in FullName property of ZipArchiveEntry objects</span></span>

#### <a name="details"></a><span data-ttu-id="0729f-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="0729f-102">Details</span></span>

<span data-ttu-id="0729f-103">Para aplicativos direcionados para o .NET Framework 4.6.1 e versões posteriores, o caractere separador de caminho mudou de uma barra invertida (" \\ ") para uma barra "/" ("/") na <xref:System.IO.Compression.ZipArchiveEntry.FullName> propriedade de <xref:System.IO.Compression.ZipArchiveEntry> objetos criados por sobrecargas do <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> método.</span><span class="sxs-lookup"><span data-stu-id="0729f-103">For apps that target the .NET Framework 4.6.1 and later versions, the path separator character has changed from a backslash ("\\") to a forward slash ("/") in the <xref:System.IO.Compression.ZipArchiveEntry.FullName> property of <xref:System.IO.Compression.ZipArchiveEntry>  objects created by overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> method.</span></span> <span data-ttu-id="0729f-104">A alteração traz a implementação do .NET em conformidade com a seção 4.4.17.1 da [Especificação de formato de arquivo .ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) e permite que arquivamentos .ZIP sejam descompactados em sistemas não Windows.</span><span class="sxs-lookup"><span data-stu-id="0729f-104">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span><br /><span data-ttu-id="0729f-105">A descompactação de um arquivo zip criado por um aplicativo direcionado a uma versão anterior do .NET Framework em sistemas operacionais não Windows, como o Macintosh, falha na preservação da estrutura de diretório.</span><span class="sxs-lookup"><span data-stu-id="0729f-105">Decompressing a zip file created by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="0729f-106">Por exemplo, no Macintosh, ela cria um conjunto de arquivos cujo nome de arquivo concatena o caminho do diretório com qualquer caractere de barra invertida ("\\") e o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="0729f-106">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="0729f-107">Consequentemente, a estrutura do diretório de arquivos descompactados não é preservada.</span><span class="sxs-lookup"><span data-stu-id="0729f-107">As a result, the directory structure of decompressed files is not preserved.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0729f-108">Sugestão</span><span class="sxs-lookup"><span data-stu-id="0729f-108">Suggestion</span></span>

<span data-ttu-id="0729f-109">O impacto dessa alteração em. Os arquivos ZIP que são descompactados no sistema operacional Windows por APIs no <xref:System.IO?displayProperty=nameWithType> namespace .NET Framework devem ser mínimos, uma vez que essas APIs podem lidar diretamente com uma barra ("/") ou uma barra invertida (" \\ ") como o caractere separador de caminho.</span><span class="sxs-lookup"><span data-stu-id="0729f-109">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO?displayProperty=nameWithType> namespace should be minimal, since these APIs can seamlessly handle either a forward slash ("/") or a backslash ("\\") as the path separator character.</span></span><br /><span data-ttu-id="0729f-110">Se essa alteração for indesejável, você poderá recusá-la adicionando um parâmetro de configuração à [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) seção do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0729f-110">If this change is undesirable, you can opt out of it by adding a configuration setting to the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="0729f-111">O exemplo a seguir mostra a seção `<runtime>` e a opção de recusa `Switch.System.IO.Compression.ZipFile.UseBackslash`:</span><span class="sxs-lookup"><span data-stu-id="0729f-111">The following example shows both the `<runtime>` section and the `Switch.System.IO.Compression.ZipFile.UseBackslash` opt-out switch:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />
</runtime>
```

<span data-ttu-id="0729f-112">Além disso, os aplicativos que se destinam a versões anteriores do .NET Framework mas que estão em execução no .NET Framework 4.6.1 e versões posteriores podem aceitar esse comportamento adicionando um parâmetro de configuração à [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) seção do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0729f-112">In addition, apps that target previous versions of the .NET Framework but are running on the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="0729f-113">Veja a seguir a seção `<runtime>` e a opção de aceitação `Switch.System.IO.Compression.ZipFile.UseBackslash`.</span><span class="sxs-lookup"><span data-stu-id="0729f-113">The following shows both the `<runtime>` section and the `Switch.System.IO.Compression.ZipFile.UseBackslash` opt-in switch.</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />
</runtime>
```

| <span data-ttu-id="0729f-114">Nome</span><span class="sxs-lookup"><span data-stu-id="0729f-114">Name</span></span>    | <span data-ttu-id="0729f-115">Valor</span><span class="sxs-lookup"><span data-stu-id="0729f-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0729f-116">Escopo</span><span class="sxs-lookup"><span data-stu-id="0729f-116">Scope</span></span>   | <span data-ttu-id="0729f-117">Edge</span><span class="sxs-lookup"><span data-stu-id="0729f-117">Edge</span></span>        |
| <span data-ttu-id="0729f-118">Versão</span><span class="sxs-lookup"><span data-stu-id="0729f-118">Version</span></span> | <span data-ttu-id="0729f-119">4.6.1</span><span class="sxs-lookup"><span data-stu-id="0729f-119">4.6.1</span></span>       |
| <span data-ttu-id="0729f-120">Type</span><span class="sxs-lookup"><span data-stu-id="0729f-120">Type</span></span>    | <span data-ttu-id="0729f-121">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="0729f-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="0729f-122">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="0729f-122">Affected APIs</span></span>

- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean,System.Text.Encoding)?displayProperty=nameWithType>
