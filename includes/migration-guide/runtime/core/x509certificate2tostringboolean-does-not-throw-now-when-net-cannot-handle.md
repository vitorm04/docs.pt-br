---
ms.openlocfilehash: 51208762cea2a5688c5d43e5d444d4e014e5f0b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621035"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="186a5-101">Agora, o X509Certificate2.ToString(Boolean) não é gerado quando o .NET não pode tratar o certificado</span><span class="sxs-lookup"><span data-stu-id="186a5-101">X509Certificate2.ToString(Boolean) does not throw now when .NET cannot handle the certificate</span></span>

#### <a name="details"></a><span data-ttu-id="186a5-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="186a5-102">Details</span></span>

<span data-ttu-id="186a5-103">No .NET Framework 4.5.2 e nas versões anteriores, esse método era gerado quando <code>true</code> era passado para o parâmetro verbose e havia certificados instalados que não eram compatíveis com o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="186a5-103">In .NET Framework 4.5.2 and earlier versions, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="186a5-104">Agora, o método será bem-sucedido e retornará uma cadeia de caracteres válida que omita as partes inacessíveis do certificado.</span><span class="sxs-lookup"><span data-stu-id="186a5-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="186a5-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="186a5-105">Suggestion</span></span>

<span data-ttu-id="186a5-106">Qualquer código dependente do <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> deve ser atualizado para esperar que a cadeia de caracteres retornada possa excluir alguns dados do certificado (como chave pública, chave privada e extensões) em alguns casos nos quais a API teria sido gerada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="186a5-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>

| <span data-ttu-id="186a5-107">Name</span><span class="sxs-lookup"><span data-stu-id="186a5-107">Name</span></span>    | <span data-ttu-id="186a5-108">Valor</span><span class="sxs-lookup"><span data-stu-id="186a5-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="186a5-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="186a5-109">Scope</span></span>   |<span data-ttu-id="186a5-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="186a5-110">Edge</span></span>|
|<span data-ttu-id="186a5-111">Versão</span><span class="sxs-lookup"><span data-stu-id="186a5-111">Version</span></span>|<span data-ttu-id="186a5-112">4.6</span><span class="sxs-lookup"><span data-stu-id="186a5-112">4.6</span></span>|
|<span data-ttu-id="186a5-113">Type</span><span class="sxs-lookup"><span data-stu-id="186a5-113">Type</span></span>|<span data-ttu-id="186a5-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="186a5-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="186a5-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="186a5-115">Affected APIs</span></span>

-<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
