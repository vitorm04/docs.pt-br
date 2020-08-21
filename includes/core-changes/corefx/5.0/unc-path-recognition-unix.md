---
ms.openlocfilehash: 0246f325a6274082b7fb0d5590cec7c80687ae85
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720170"
---
### <a name="uri-recognition-of-unc-paths-on-unix"></a><span data-ttu-id="5da8a-101">Reconhecimento de URI de caminhos UNC no UNIX</span><span class="sxs-lookup"><span data-stu-id="5da8a-101">Uri recognition of UNC paths on Unix</span></span>

<span data-ttu-id="5da8a-102">A <xref:System.Uri> classe agora reconhece cadeias de caracteres que começam com duas barras ( `//` ) como caminhos UNC (Convenção de nomenclatura universal) em sistemas operacionais UNIX.</span><span class="sxs-lookup"><span data-stu-id="5da8a-102">The <xref:System.Uri> class now recognizes strings that start with two forward slashes (`//`) as universal naming convention (UNC) paths on Unix operating systems.</span></span> <span data-ttu-id="5da8a-103">Essa alteração torna o comportamento de tais cadeias de caracteres consistentes em todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="5da8a-103">This change makes the behavior for such strings consistent across all platforms.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5da8a-104">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="5da8a-104">Change description</span></span>

<span data-ttu-id="5da8a-105">Nas versões anteriores do .NET, a <xref:System.Uri> classe reconhece cadeias de caracteres que começam com com duas barras, por exemplo, `//contoso` como caminhos de arquivo absolutos em sistemas operacionais UNIX.</span><span class="sxs-lookup"><span data-stu-id="5da8a-105">In previous versions of .NET, the <xref:System.Uri> class recognizes strings that start with with two forward slashes, for example, `//contoso`, as absolute file paths on Unix operating systems.</span></span> <span data-ttu-id="5da8a-106">No entanto, no Windows, essas cadeias de caracteres são reconhecidas como caminhos UNC.</span><span class="sxs-lookup"><span data-stu-id="5da8a-106">However, on Windows, such strings are recognized as UNC paths.</span></span>

<span data-ttu-id="5da8a-107">A partir do .NET 5,0, a <xref:System.Uri> classe reconhece cadeias de caracteres que começam com com duas barras para frente como caminhos UNC em todas as plataformas, incluindo UNIX.</span><span class="sxs-lookup"><span data-stu-id="5da8a-107">Starting in .NET 5.0,  the <xref:System.Uri> class recognizes strings that start with with two forward slashes as UNC paths on all platforms, including Unix.</span></span> <span data-ttu-id="5da8a-108">Além disso, as propriedades se comportam de acordo com a semântica UNC:</span><span class="sxs-lookup"><span data-stu-id="5da8a-108">In addition, properties behave according to UNC semantics:</span></span>

- <span data-ttu-id="5da8a-109"><xref:System.Uri.IsUnc?displayProperty=nameWithType> retorna `true`.</span><span class="sxs-lookup"><span data-stu-id="5da8a-109"><xref:System.Uri.IsUnc?displayProperty=nameWithType> returns `true`.</span></span>
- <span data-ttu-id="5da8a-110">As barras invertidas no caminho são substituídas por barras "/".</span><span class="sxs-lookup"><span data-stu-id="5da8a-110">Backslashes in the path are replaced with forward slashes.</span></span> <span data-ttu-id="5da8a-111">Por exemplo, `//first\second` torna-se `//first/second`.</span><span class="sxs-lookup"><span data-stu-id="5da8a-111">For example, `//first\second` becomes `//first/second`.</span></span>
- <span data-ttu-id="5da8a-112"><xref:System.Uri.LocalPath?displayProperty=nameWithType> Não codificar caracteres por porcentagem.</span><span class="sxs-lookup"><span data-stu-id="5da8a-112"><xref:System.Uri.LocalPath?displayProperty=nameWithType> doesn't percent-encode characters.</span></span> <span data-ttu-id="5da8a-113">Por exemplo, `//first/\uFFF0` *não* é convertido em `//first/%EF%BF%B0` .</span><span class="sxs-lookup"><span data-stu-id="5da8a-113">For example, `//first/\uFFF0` is *not* converted to `//first/%EF%BF%B0`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5da8a-114">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="5da8a-114">Version introduced</span></span>

<span data-ttu-id="5da8a-115">5,0</span><span class="sxs-lookup"><span data-stu-id="5da8a-115">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5da8a-116">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="5da8a-116">Recommended action</span></span>

<span data-ttu-id="5da8a-117">Nenhuma ação é necessária na parte do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="5da8a-117">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="5da8a-118">Categoria</span><span class="sxs-lookup"><span data-stu-id="5da8a-118">Category</span></span>

<span data-ttu-id="5da8a-119">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="5da8a-119">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5da8a-120">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="5da8a-120">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->
