---
ms.openlocfilehash: bb264e406c6604c3606e564d99018eda0f9e8d89
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721028"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a><span data-ttu-id="79b3e-101">As APIs que relatam versão agora relatam produto e não versão de arquivo</span><span class="sxs-lookup"><span data-stu-id="79b3e-101">APIs that report version now report product and not file version</span></span>

<span data-ttu-id="79b3e-102">Muitas das APIs que retornam versões no .NET Core agora retornam a versão do produto em vez da versão do arquivo.</span><span class="sxs-lookup"><span data-stu-id="79b3e-102">Many of the APIs that return versions in .NET Core now return the product version rather than the file version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="79b3e-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="79b3e-103">Change description</span></span>

<span data-ttu-id="79b3e-104">No .NET Core 2,2 e em versões anteriores, métodos como <xref:System.Environment.Version?displayProperty=nameWithType> , <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> e a caixa de diálogo Propriedades do arquivo para assemblies do .NET Core refletem a versão do arquivo.</span><span class="sxs-lookup"><span data-stu-id="79b3e-104">In .NET Core 2.2 and previous versions, methods such as <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, and the file properties dialog for .NET Core assemblies reflect the file version.</span></span> <span data-ttu-id="79b3e-105">A partir do .NET Core 3,0, eles refletem a versão do produto.</span><span class="sxs-lookup"><span data-stu-id="79b3e-105">Starting with .NET Core 3.0, they reflect the product version.</span></span>

<span data-ttu-id="79b3e-106">A figura a seguir ilustra a diferença nas informações de versão do assembly *System. Runtime. dll* para .net Core 2,2 (à esquerda) e do .net Core 3,0 (à direita), conforme exibido pela caixa de diálogo Propriedades de arquivo do **Windows Explorer** .</span><span class="sxs-lookup"><span data-stu-id="79b3e-106">The following figure illustrates the difference in version information for the *System.Runtime.dll* assembly for .NET Core 2.2 (on the left) and .NET Core 3.0 (on the right) as displayed by the **Windows Explorer** file properties dialog.</span></span>

![Diferença nas informações de versão do produto](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a><span data-ttu-id="79b3e-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="79b3e-108">Version introduced</span></span>

<span data-ttu-id="79b3e-109">3.0</span><span class="sxs-lookup"><span data-stu-id="79b3e-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="79b3e-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="79b3e-110">Recommended action</span></span>

<span data-ttu-id="79b3e-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="79b3e-111">None.</span></span> <span data-ttu-id="79b3e-112">Essa alteração deve tornar a detecção de versão intuitiva, em vez de obtuso.</span><span class="sxs-lookup"><span data-stu-id="79b3e-112">This change should make version detection intuitive rather than obtuse.</span></span>

#### <a name="category"></a><span data-ttu-id="79b3e-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="79b3e-113">Category</span></span>

<span data-ttu-id="79b3e-114">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="79b3e-114">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="79b3e-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="79b3e-115">Affected APIs</span></span>

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
