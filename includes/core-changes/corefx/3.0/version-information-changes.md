---
ms.openlocfilehash: 1580c8c8b7bdad91656f494537230293dbaaf93b
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021609"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a><span data-ttu-id="2e410-101">APIs que relatam versão agora relatam produto e não versão de arquivo</span><span class="sxs-lookup"><span data-stu-id="2e410-101">APIs that report version now report product and not file version</span></span>

<span data-ttu-id="2e410-102">Muitas das APIs que retornam versões no .NET Core agora retornam a versão do produto em vez da versão do arquivo.</span><span class="sxs-lookup"><span data-stu-id="2e410-102">Many of the APIs that return versions in .NET Core now return the product version rather than the file version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2e410-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="2e410-103">Change description</span></span>

<span data-ttu-id="2e410-104">Em .NET Core 2.2 e versões anteriores, métodos como <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>e a caixa de diálogo propriedades de arquivo para conjuntos .NET Core refletem a versão do arquivo.</span><span class="sxs-lookup"><span data-stu-id="2e410-104">In .NET Core 2.2 and previous versions, methods such as <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, and the file properties dialog for .NET Core assemblies reflect the file version.</span></span> <span data-ttu-id="2e410-105">A partir do .NET Core 3.0, eles refletem a versão do produto.</span><span class="sxs-lookup"><span data-stu-id="2e410-105">Starting with .NET Core 3.0, they reflect the product version.</span></span>

<span data-ttu-id="2e410-106">A figura a seguir ilustra a diferença nas informações da versão para o conjunto *System.Runtime.dll* para .NET Core 2.2 (à esquerda) e .NET Core 3.0 (à direita) como exibido pela caixa de diálogo propriedades do arquivo **Windows Explorer.**</span><span class="sxs-lookup"><span data-stu-id="2e410-106">The following figure illustrates the difference in version information for the *System.Runtime.dll* assembly for .NET Core 2.2 (on the left) and .NET Core 3.0 (on the right) as displayed by the **Windows Explorer** file properties dialog.</span></span>

![Diferença nas informações da versão do produto](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a><span data-ttu-id="2e410-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="2e410-108">Version introduced</span></span>

<span data-ttu-id="2e410-109">3.0</span><span class="sxs-lookup"><span data-stu-id="2e410-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2e410-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="2e410-110">Recommended action</span></span>

<span data-ttu-id="2e410-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="2e410-111">None.</span></span> <span data-ttu-id="2e410-112">Essa mudança deve tornar a detecção de versão intuitiva em vez de obtusa.</span><span class="sxs-lookup"><span data-stu-id="2e410-112">This change should make version detection intuitive rather than obtuse.</span></span>

#### <a name="category"></a><span data-ttu-id="2e410-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="2e410-113">Category</span></span>

<span data-ttu-id="2e410-114">Bibliotecas Core .NET</span><span class="sxs-lookup"><span data-stu-id="2e410-114">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2e410-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="2e410-115">Affected APIs</span></span>

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
