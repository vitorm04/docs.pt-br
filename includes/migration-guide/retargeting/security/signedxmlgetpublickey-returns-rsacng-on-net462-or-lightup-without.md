---
ms.openlocfilehash: 23e278d38d6904d8afe927e6b54c388d443e41f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616017"
---
### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a><span data-ttu-id="0feae-101">SignedXml.GetPublicKey retorna RSACng em net462 (ou lightup) sem redirecionar a alteração</span><span class="sxs-lookup"><span data-stu-id="0feae-101">SignedXml.GetPublicKey returns RSACng on net462 (or lightup) without retargeting change</span></span>

#### <a name="details"></a><span data-ttu-id="0feae-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="0feae-102">Details</span></span>

<span data-ttu-id="0feae-103">A partir do .NET Framework 4.6.2, o tipo concreto de objeto retornado pelo método <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> foi alterado (sem um quirk) de uma implementação de CryptoServiceProvider para uma implementação de Cng.</span><span class="sxs-lookup"><span data-stu-id="0feae-103">Starting with the .NET Framework 4.6.2, the concrete type of the object returned by the <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> method changed (without a quirk) from a CryptoServiceProvider implementation to a Cng implementation.</span></span> <span data-ttu-id="0feae-104">Isso ocorreu porque a implementação foi alterada: do uso de `certificate.PublicKey.Key` para o uso do `certificate.GetAnyPublicKey` interno, que encaminha para <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0feae-104">This is because the implementation changed from using `certificate.PublicKey.Key` to using the internal `certificate.GetAnyPublicKey` which forwards to <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0feae-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="0feae-105">Suggestion</span></span>

<span data-ttu-id="0feae-106">Começando com aplicativos em execução no .NET Framework 4.7.1, é possível usar a implementação de CryptoServiceProvider usada por padrão no .NET Framework 4.6.1 e versões anteriores adicionando a seguinte opção de configuração à seção [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="0feae-106">Starting with apps running on the .NET Framework 4.7.1, you can use the CryptoServiceProvider implementation used by default in the .NET Framework 4.6.1 and earlier versions by adding the following configuration switch to the [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true" />
```

| <span data-ttu-id="0feae-107">Name</span><span class="sxs-lookup"><span data-stu-id="0feae-107">Name</span></span>    | <span data-ttu-id="0feae-108">Valor</span><span class="sxs-lookup"><span data-stu-id="0feae-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0feae-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="0feae-109">Scope</span></span>   | <span data-ttu-id="0feae-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="0feae-110">Edge</span></span>        |
| <span data-ttu-id="0feae-111">Versão</span><span class="sxs-lookup"><span data-stu-id="0feae-111">Version</span></span> | <span data-ttu-id="0feae-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="0feae-112">4.6.2</span></span>       |
| <span data-ttu-id="0feae-113">Type</span><span class="sxs-lookup"><span data-stu-id="0feae-113">Type</span></span>    | <span data-ttu-id="0feae-114">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="0feae-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="0feae-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="0feae-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType>
