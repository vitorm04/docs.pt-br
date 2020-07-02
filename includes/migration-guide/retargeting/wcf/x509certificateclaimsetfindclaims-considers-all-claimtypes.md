---
ms.openlocfilehash: abef47c64a7cfd99c5b50bf2100401a2d5fcc5c3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614286"
---
### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a><span data-ttu-id="4b077-101">X509CertificateClaimSet.FindClaims considera todos os claimTypes</span><span class="sxs-lookup"><span data-stu-id="4b077-101">X509CertificateClaimSet.FindClaims Considers All claimTypes</span></span>

#### <a name="details"></a><span data-ttu-id="4b077-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="4b077-102">Details</span></span>

<span data-ttu-id="4b077-103">Em aplicativos destinados ao .NET Framework 4.6.1, se um conjunto de declarações X509 for inicializado de um certificado que tenha várias entradas DNS em seu campo SAN, o método <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> tentará corresponder o argumento claimType a todas as entradas DNS. Em aplicativos destinados a versões anteriores do .NET Framework, o método <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> tenta corresponder o argumento claimType somente com a última entrada DNS.</span><span class="sxs-lookup"><span data-stu-id="4b077-103">In apps that target the .NET Framework 4.6.1, if an X509 claim set is initialized from a certificate that has multiple DNS entries in its SAN field, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> method attempts to match the claimType argument with all the DNS entries.For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> method attempts to match the claimType argument only with the last DNS entry.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4b077-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="4b077-104">Suggestion</span></span>

<span data-ttu-id="4b077-105">Essa alteração afeta apenas aplicativos destinados ao .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="4b077-105">This change only affects applications targeting the .NET Framework 4.6.1.</span></span> <span data-ttu-id="4b077-106">Essa alteração pode ser desabilitada (ou habilitada se destinada a versões anteriores a 4.6.1) com a opção de compatibilidade [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation).</span><span class="sxs-lookup"><span data-stu-id="4b077-106">This change may be disabled (or enabled if targeting pre-4.6.1) with the [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) compatibility switch.</span></span>

| <span data-ttu-id="4b077-107">Name</span><span class="sxs-lookup"><span data-stu-id="4b077-107">Name</span></span>    | <span data-ttu-id="4b077-108">Valor</span><span class="sxs-lookup"><span data-stu-id="4b077-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4b077-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="4b077-109">Scope</span></span>   | <span data-ttu-id="4b077-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="4b077-110">Minor</span></span>       |
| <span data-ttu-id="4b077-111">Versão</span><span class="sxs-lookup"><span data-stu-id="4b077-111">Version</span></span> | <span data-ttu-id="4b077-112">4.6.1</span><span class="sxs-lookup"><span data-stu-id="4b077-112">4.6.1</span></span>       |
| <span data-ttu-id="4b077-113">Type</span><span class="sxs-lookup"><span data-stu-id="4b077-113">Type</span></span>    | <span data-ttu-id="4b077-114">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="4b077-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="4b077-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="4b077-115">Affected APIs</span></span>

- <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType>
