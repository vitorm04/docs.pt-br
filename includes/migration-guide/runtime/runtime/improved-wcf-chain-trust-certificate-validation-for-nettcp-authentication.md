---
ms.openlocfilehash: c8f017084fc1ec1eca636ef0178a40559e15b2c5
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496405"
---
### <a name="improved-wcf-chain-trust-certificate-validation-for-nettcp-certificate-authentication"></a><span data-ttu-id="2cd44-101">Melhor validação do certificado de confiança de cadeia do WCF para autenticação de certificado do Net.Tcp</span><span class="sxs-lookup"><span data-stu-id="2cd44-101">Improved WCF chain trust certificate validation for Net.Tcp certificate authentication</span></span>

#### <a name="details"></a><span data-ttu-id="2cd44-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="2cd44-102">Details</span></span>

<span data-ttu-id="2cd44-103">O .NET framework 4.7.2 melhorou a validação do certificado de confiança de cadeia ao usar a autenticação de certificado com a segurança de transporte com o WCF.</span><span class="sxs-lookup"><span data-stu-id="2cd44-103">.NET Framework 4.7.2 improves chain trust certificate validation when using certificate authentication with transport security with WCF.</span></span> <span data-ttu-id="2cd44-104">Com essa melhoria, os certificados do cliente que são usados para autenticar um servidor precisam ser configurados para autenticação do cliente.</span><span class="sxs-lookup"><span data-stu-id="2cd44-104">With this improvement, client certificates that are used to authenticate to a server must be configured for client authentication.</span></span>  <span data-ttu-id="2cd44-105">Da mesma forma, os certificados do servidor usados para autenticar um servidor precisam ser configurados para autenticação do servidor.</span><span class="sxs-lookup"><span data-stu-id="2cd44-105">Similarly server certificates that are for the authenticating a server must be configured for server authentication.</span></span> <span data-ttu-id="2cd44-106">Com essa alteração, se o certificado raiz for desabilitado, a validação da cadeia de certificados falhará.</span><span class="sxs-lookup"><span data-stu-id="2cd44-106">With this change, if the root certificate is disabled, the certificate chain validation fails.</span></span> <span data-ttu-id="2cd44-107">A mesma alteração também foi feita para o .NET Framework 3.5 e as versões posteriores por meio do pacote cumulativo de segurança do Windows.</span><span class="sxs-lookup"><span data-stu-id="2cd44-107">The same change was also made to .NET Framework 3.5 and later versions via Windows security roll-up.</span></span> <span data-ttu-id="2cd44-108">Encontre mais informações [aqui](https://support.microsoft.com/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7). Essa alteração é habilitada por padrão e pode ser desabilitada por uma definição de configuração.</span><span class="sxs-lookup"><span data-stu-id="2cd44-108">You can find more information [here](https://support.microsoft.com/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7).This change is on by default and can be turned off by a configuration setting.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2cd44-109">Sugestão</span><span class="sxs-lookup"><span data-stu-id="2cd44-109">Suggestion</span></span>

<ul><li><span data-ttu-id="2cd44-110">Valide se a certificação do servidor e do cliente têm o OID de EKU necessário.</span><span class="sxs-lookup"><span data-stu-id="2cd44-110">Validate if your server and client certification has the required EKU OID.</span></span> <span data-ttu-id="2cd44-111">Caso contrário, atualize a certificação.</span><span class="sxs-lookup"><span data-stu-id="2cd44-111">If not, update your certification.</span></span></li><li><span data-ttu-id="2cd44-112">Valide se o certificado raiz é inválido.</span><span class="sxs-lookup"><span data-stu-id="2cd44-112">Validate if your root certificate is invalid.</span></span> <span data-ttu-id="2cd44-113">Nesse caso, atualize o certificado raiz.</span><span class="sxs-lookup"><span data-stu-id="2cd44-113">If so, update the root certificate.</span></span></li><li><span data-ttu-id="2cd44-114">Como recusar a alteração: se você não puder atualizar o certificado, contorne temporariamente a alteração da falha com as definições de configuração a seguir. No entanto, recusar a alteração deixará seu sistema vulnerável ao problema de segurança.</span><span class="sxs-lookup"><span data-stu-id="2cd44-114">How to opt out of the change: If you can't update the certificate, you can work around the breaking change temporarily with the following configration setting,  However, opting out of the change will leave your system vulnerable to the security issue.</span></span></li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;wcf:useLegacyCertificateUsagePolicy&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="2cd44-115">Nome</span><span class="sxs-lookup"><span data-stu-id="2cd44-115">Name</span></span>    | <span data-ttu-id="2cd44-116">Valor</span><span class="sxs-lookup"><span data-stu-id="2cd44-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2cd44-117">Escopo</span><span class="sxs-lookup"><span data-stu-id="2cd44-117">Scope</span></span>   |<span data-ttu-id="2cd44-118">Secundária</span><span class="sxs-lookup"><span data-stu-id="2cd44-118">Minor</span></span>|
|<span data-ttu-id="2cd44-119">Versão</span><span class="sxs-lookup"><span data-stu-id="2cd44-119">Version</span></span>|<span data-ttu-id="2cd44-120">4.7.2</span><span class="sxs-lookup"><span data-stu-id="2cd44-120">4.7.2</span></span>|
|<span data-ttu-id="2cd44-121">Tipo</span><span class="sxs-lookup"><span data-stu-id="2cd44-121">Type</span></span>|<span data-ttu-id="2cd44-122">Runtime</span><span class="sxs-lookup"><span data-stu-id="2cd44-122">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="2cd44-123">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="2cd44-123">Affected APIs</span></span>

<span data-ttu-id="2cd44-124">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="2cd44-124">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
