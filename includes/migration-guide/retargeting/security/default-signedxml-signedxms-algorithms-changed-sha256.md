---
ms.openlocfilehash: e2ae329d027d605e6331afe422e550990fab1042
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614298"
---
### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a><span data-ttu-id="63b69-101">Algoritmos SignedXML e SignedXMS padrão alterados para SHA256</span><span class="sxs-lookup"><span data-stu-id="63b69-101">Default SignedXML and SignedXMS algorithms changed to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="63b69-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="63b69-102">Details</span></span>

<span data-ttu-id="63b69-103">No .NET Framework 4.7 e anteriores, SignedXML e SignedCMS usam SHA1 como padrão para algumas operações. A partir do .NET Framework 4.7.1, SHA256 é habilitado por padrão para essas operações.</span><span class="sxs-lookup"><span data-stu-id="63b69-103">In the .NET Framework 4.7 and earlier, SignedXML and SignedCMS default to SHA1 for some operations.Starting with the .NET Framework 4.7.1, SHA256 is enabled by default for these operations.</span></span> <span data-ttu-id="63b69-104">Essa alteração é necessária porque SHA1 não é mais considerado seguro.</span><span class="sxs-lookup"><span data-stu-id="63b69-104">This change is necessary because SHA1 is no longer considered to be secure.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="63b69-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="63b69-105">Suggestion</span></span>

<span data-ttu-id="63b69-106">Há dois novos valores de alternância de contexto para controlar se SHA1 (inseguro) ou SHA256 é usado por padrão:</span><span class="sxs-lookup"><span data-stu-id="63b69-106">There are two new context switch values to control whether SHA1 (insecure) or SHA256 is used by default:</span></span>

- <span data-ttu-id="63b69-107">Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms</span><span class="sxs-lookup"><span data-stu-id="63b69-107">Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms</span></span>
- <span data-ttu-id="63b69-108">Switch.System. Security. Cryptography. Pkcs. UseInsecureHashAlgorithms para aplicativos direcionados ao .NET Framework 4.7.1 e versões posteriores, se o uso de SHA256 for indesejável, você poderá restaurar o padrão para SHA1 adicionando a opção de configuração a seguir à seção de [tempo de execução](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do seu arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="63b69-108">Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms For applications that target the .NET Framework 4.7.1 and later versions, if the use of SHA256 is undesirable, you can restore the default to SHA1 by adding the following configuration switch to the [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true" />
```

<span data-ttu-id="63b69-109">Para aplicativos destinados ao .NET Framework 4.7 e a versões anteriores, é possível aceitar essa alteração adicionando a seguinte opção de configuração à seção do [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração de seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="63b69-109">For applications that target the .NET Framework 4.7 and earlier versions, you can opt into this change by adding the following configuration switch to the [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false" />
```

| <span data-ttu-id="63b69-110">Name</span><span class="sxs-lookup"><span data-stu-id="63b69-110">Name</span></span>    | <span data-ttu-id="63b69-111">Valor</span><span class="sxs-lookup"><span data-stu-id="63b69-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="63b69-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="63b69-112">Scope</span></span>   | <span data-ttu-id="63b69-113">Secundária</span><span class="sxs-lookup"><span data-stu-id="63b69-113">Minor</span></span>       |
| <span data-ttu-id="63b69-114">Versão</span><span class="sxs-lookup"><span data-stu-id="63b69-114">Version</span></span> | <span data-ttu-id="63b69-115">4.7.1</span><span class="sxs-lookup"><span data-stu-id="63b69-115">4.7.1</span></span>       |
| <span data-ttu-id="63b69-116">Type</span><span class="sxs-lookup"><span data-stu-id="63b69-116">Type</span></span>    | <span data-ttu-id="63b69-117">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="63b69-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="63b69-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="63b69-118">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType>
