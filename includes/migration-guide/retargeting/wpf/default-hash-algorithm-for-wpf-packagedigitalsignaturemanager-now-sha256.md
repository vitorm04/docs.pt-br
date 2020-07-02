---
ms.openlocfilehash: d3e0a61601f60a389b662f6f74934b6e6dc6e663
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614313"
---
### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a><span data-ttu-id="b6c3f-101">O algoritmo de hash padrão para o PackageDigitalSignatureManager do WPF agora é SHA256</span><span class="sxs-lookup"><span data-stu-id="b6c3f-101">The default hash algorithm for WPF PackageDigitalSignatureManager is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="b6c3f-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="b6c3f-102">Details</span></span>

<span data-ttu-id="b6c3f-103">O `System.IO.Packaging.PackageDigitalSignatureManager` fornece funcionalidade para assinaturas digitais em relação a pacotes do WPF.</span><span class="sxs-lookup"><span data-stu-id="b6c3f-103">The `System.IO.Packaging.PackageDigitalSignatureManager` provides functionality for digital signatures in relation to WPF packages.</span></span>  <span data-ttu-id="b6c3f-104">No .NET Framework 4.7 e em versões anteriores, o algoritmo padrão (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) usado para assinar partes de um pacote era SHA1.</span><span class="sxs-lookup"><span data-stu-id="b6c3f-104">In the .NET Framework 4.7 and earlier versions, the default algorithm (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) used for signing parts of a package was SHA1.</span></span>  <span data-ttu-id="b6c3f-105">Devido a questões de segurança recentes com SHA1, esse padrão foi alterado para o SHA256 a partir do .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="b6c3f-105">Due to recent security concerns with SHA1, this default has been changed to SHA256 starting with the .NET Framework 4.7.1.</span></span>  <span data-ttu-id="b6c3f-106">Esta alteração afeta a assinatura de todos os pacotes, incluindo documentos XPS.</span><span class="sxs-lookup"><span data-stu-id="b6c3f-106">This change affects all package signing, including XPS documents.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b6c3f-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="b6c3f-107">Suggestion</span></span>

<span data-ttu-id="b6c3f-108">O desenvolvedor que desejará utilizar essa alteração ao direcionar a uma versão do framework abaixo do .NET 4.7.1 ou que precisar da funcionalidade anterior ao direcionar ao .NET 4.7.1 ou posteriores poderá definir o seguinte sinalizador de AppContext adequadamente.</span><span class="sxs-lookup"><span data-stu-id="b6c3f-108">A developer who wants to utilize this change while targeting a framework version below .NET Framework 4.7.1 or a developer who requires the previous functionality while targeting .NET Framework 4.7.1 or greater can set the following AppContext flag appropriately.</span></span>  <span data-ttu-id="b6c3f-109">O valor true fará com que SHA1 seja usado como algoritmo padrão; false fará com que SHA256 seja usado.</span><span class="sxs-lookup"><span data-stu-id="b6c3f-109">A value of true will result in SHA1 being used as the default algorithm; false results in SHA256.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="b6c3f-110">Name</span><span class="sxs-lookup"><span data-stu-id="b6c3f-110">Name</span></span>    | <span data-ttu-id="b6c3f-111">Valor</span><span class="sxs-lookup"><span data-stu-id="b6c3f-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b6c3f-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="b6c3f-112">Scope</span></span>   | <span data-ttu-id="b6c3f-113">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="b6c3f-113">Edge</span></span>        |
| <span data-ttu-id="b6c3f-114">Versão</span><span class="sxs-lookup"><span data-stu-id="b6c3f-114">Version</span></span> | <span data-ttu-id="b6c3f-115">4.7.1</span><span class="sxs-lookup"><span data-stu-id="b6c3f-115">4.7.1</span></span>       |
| <span data-ttu-id="b6c3f-116">Type</span><span class="sxs-lookup"><span data-stu-id="b6c3f-116">Type</span></span>    | <span data-ttu-id="b6c3f-117">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="b6c3f-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="b6c3f-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="b6c3f-118">Affected APIs</span></span>

- <xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>
