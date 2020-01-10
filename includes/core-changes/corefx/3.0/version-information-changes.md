---
ms.openlocfilehash: 5612ebce67946e22aaeeba861115ce4f8967e1f5
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344446"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a><span data-ttu-id="e07ce-101">As APIs que relatam versão agora relatam produto e não versão de arquivo</span><span class="sxs-lookup"><span data-stu-id="e07ce-101">APIs that report version now report product and not file version</span></span>

<span data-ttu-id="e07ce-102">Muitas das APIs que retornam versões no .NET Core agora retornam a versão do produto em vez da versão do arquivo.</span><span class="sxs-lookup"><span data-stu-id="e07ce-102">Many of the APIs that return versions in .NET Core now return the product version rather than the file version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e07ce-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="e07ce-103">Change description</span></span>

<span data-ttu-id="e07ce-104">No .NET Core 2,2 e em versões anteriores, métodos como <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>e a caixa de diálogo Propriedades do arquivo para assemblies do .NET Core refletem a versão do arquivo.</span><span class="sxs-lookup"><span data-stu-id="e07ce-104">In .NET Core 2.2 and previous versions, methods such as <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, and the file properties dialog for .NET Core assemblies reflect the file version.</span></span> <span data-ttu-id="e07ce-105">A partir do .NET Core 3,0, eles refletem a versão do produto.</span><span class="sxs-lookup"><span data-stu-id="e07ce-105">Starting with .NET Core 3.0, they reflect the product version.</span></span>

<span data-ttu-id="e07ce-106">A figura a seguir ilustra a diferença nas informações de versão do assembly *System. Runtime. dll* para .net Core 2,2 (à esquerda) e do .net Core 3,0 (à direita), conforme exibido pela caixa de diálogo Propriedades de arquivo do **Windows Explorer** .</span><span class="sxs-lookup"><span data-stu-id="e07ce-106">The following figure illustrates the difference in version information for the *System.Runtime.dll* assembly for .NET Core 2.2 (on the left) and .NET Core 3.0 (on the right) as displayed by the **Windows Explorer** file properties dialog.</span></span>

![Diferença nas informações de versão do produto](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a><span data-ttu-id="e07ce-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="e07ce-108">Version introduced</span></span>

<span data-ttu-id="e07ce-109">3.0</span><span class="sxs-lookup"><span data-stu-id="e07ce-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e07ce-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="e07ce-110">Recommended action</span></span>

<span data-ttu-id="e07ce-111">Nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e07ce-111">None.</span></span> <span data-ttu-id="e07ce-112">Essa alteração deve tornar a detecção de versão intuitiva, em vez de obtuso.</span><span class="sxs-lookup"><span data-stu-id="e07ce-112">This change should make version detection intuitive rather than obtuse.</span></span>

#### <a name="category"></a><span data-ttu-id="e07ce-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="e07ce-113">Category</span></span>

<span data-ttu-id="e07ce-114">CoreFx</span><span class="sxs-lookup"><span data-stu-id="e07ce-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e07ce-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="e07ce-115">Affected APIs</span></span>

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
