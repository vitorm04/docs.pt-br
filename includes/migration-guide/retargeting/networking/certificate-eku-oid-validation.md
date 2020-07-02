---
ms.openlocfilehash: c996dafcf65b1fd428be908be346de603ead6e0b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615593"
---
### <a name="certificate-eku-oid-validation"></a><span data-ttu-id="e0b51-101">Validação dos certificados de EKU do OID</span><span class="sxs-lookup"><span data-stu-id="e0b51-101">Certificate EKU OID validation</span></span>

#### <a name="details"></a><span data-ttu-id="e0b51-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e0b51-102">Details</span></span>

<span data-ttu-id="e0b51-103">A partir do .NET Framework 4.6, as classes <xref:System.Net.Security.SslStream> ou <xref:System.Net.ServicePointManager> executarão a validação do EKU (uso avançado de chave) do OID (identificador de objeto).</span><span class="sxs-lookup"><span data-stu-id="e0b51-103">Starting with .NET Framework 4.6, the <xref:System.Net.Security.SslStream> or <xref:System.Net.ServicePointManager> classes perform enhanced key use (EKU) object identifier (OID) validation.</span></span> <span data-ttu-id="e0b51-104">Uma extensão de EKU (uso avançado de chave) é uma coleção de OIDs (identificadores de objeto) que indicam os aplicativos que usam a chave.</span><span class="sxs-lookup"><span data-stu-id="e0b51-104">An enhanced key usage (EKU) extension is a collection of object identifiers (OIDs) that indicate the applications that use the key.</span></span> <span data-ttu-id="e0b51-105">A validação do EKU do OID usa retornos de chamada de certificado remoto para garantir que o certificado remoto tenha o OID correto para a finalidade pretendida.</span><span class="sxs-lookup"><span data-stu-id="e0b51-105">EKU OID validation uses remote certificate callbacks to ensure that the remote certificate has the correct OIDs for the intended purpose.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e0b51-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="e0b51-106">Suggestion</span></span>

<span data-ttu-id="e0b51-107">Se essa alteração for indesejável, você poderá desabilitar a validação de OID de EKU de certificado adicionando a seguinte opção ao [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) no [\`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de seu arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="e0b51-107">If this change is undesirable, you can disable certificate EKU OID validation by adding the following switch to the [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) in the [\`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) of your app configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontCheckCertificateEKUs=true" />
</runtime>
```

> [!IMPORTANT]
> <span data-ttu-id="e0b51-108">Essa configuração é fornecida apenas para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="e0b51-108">This setting is provided for backward compatibility only.</span></span> <span data-ttu-id="e0b51-109">Caso contrário, seu uso não é recomendado.</span><span class="sxs-lookup"><span data-stu-id="e0b51-109">Its use is otherwise not recommended.</span></span>

| <span data-ttu-id="e0b51-110">Name</span><span class="sxs-lookup"><span data-stu-id="e0b51-110">Name</span></span>    | <span data-ttu-id="e0b51-111">Valor</span><span class="sxs-lookup"><span data-stu-id="e0b51-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e0b51-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="e0b51-112">Scope</span></span>   | <span data-ttu-id="e0b51-113">Secundária</span><span class="sxs-lookup"><span data-stu-id="e0b51-113">Minor</span></span>       |
| <span data-ttu-id="e0b51-114">Versão</span><span class="sxs-lookup"><span data-stu-id="e0b51-114">Version</span></span> | <span data-ttu-id="e0b51-115">4.6</span><span class="sxs-lookup"><span data-stu-id="e0b51-115">4.6</span></span>         |
| <span data-ttu-id="e0b51-116">Type</span><span class="sxs-lookup"><span data-stu-id="e0b51-116">Type</span></span>    | <span data-ttu-id="e0b51-117">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="e0b51-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="e0b51-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="e0b51-118">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
