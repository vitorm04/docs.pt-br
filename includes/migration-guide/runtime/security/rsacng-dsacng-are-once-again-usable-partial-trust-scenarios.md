---
ms.openlocfilehash: 4788f5b80306116e63ee56584d65b862ce0606ee
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497423"
---
### <a name="rsacng-and-dsacng-are-once-again-usable-in-partial-trust-scenarios"></a><span data-ttu-id="8be78-101">RSACng e DSACng podem ser usados novamente em cenários de confiança parcial</span><span class="sxs-lookup"><span data-stu-id="8be78-101">RSACng and DSACng are once again usable in Partial Trust scenarios</span></span>

#### <a name="details"></a><span data-ttu-id="8be78-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8be78-102">Details</span></span>

<span data-ttu-id="8be78-103">CngLightup (usado em várias APIs de criptografia de nível mais elevado, como <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType>) e <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType>, em alguns casos, dependem da confiança total.</span><span class="sxs-lookup"><span data-stu-id="8be78-103">CngLightup (used in several higher-level crypto apis, such as <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType>) and <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> in some cases rely on full trust.</span></span> <span data-ttu-id="8be78-104">Eles incluem P/Invokes sem declarar permissões de <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> e caminhos de código em que <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> tem demandas de permissão de <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8be78-104">These include P/Invokes without asserting <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> permissions, and code paths where <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> has permission demands for <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8be78-105">A partir do .NET Framework 4.6.2, CngLightup foi usado para mudar para <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="8be78-105">Starting with the .NET Framework 4.6.2, CngLightup was used to switch to <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> wherever possible.</span></span> <span data-ttu-id="8be78-106">Como resultado, aplicativos de confiança parcial que usavam <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> com êxito começaram a falhar e a lançar exceções <xref:System.Security.SecurityException>. Essa alteração adiciona as declarações necessárias para que todas as funções que usam CngLightup tenham as permissões necessárias.</span><span class="sxs-lookup"><span data-stu-id="8be78-106">As a result, partial trust apps that successfully used <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> began to fail and throw <xref:System.Security.SecurityException> exceptions.This change adds the required asserts so that all functions using CngLightup have the required permissions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8be78-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="8be78-107">Suggestion</span></span>

<span data-ttu-id="8be78-108">Se essa alteração do .NET Framework 4.6.2 tiver afetado seus aplicativos de confiança parcial de forma negativa, atualize para o .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="8be78-108">If this change in the .NET Framework 4.6.2 has negatively impacted your partial trust apps, upgrade to the .NET Framework 4.7.1.</span></span>

| <span data-ttu-id="8be78-109">Nome</span><span class="sxs-lookup"><span data-stu-id="8be78-109">Name</span></span>    | <span data-ttu-id="8be78-110">Valor</span><span class="sxs-lookup"><span data-stu-id="8be78-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8be78-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="8be78-111">Scope</span></span>   |<span data-ttu-id="8be78-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="8be78-112">Edge</span></span>|
|<span data-ttu-id="8be78-113">Versão</span><span class="sxs-lookup"><span data-stu-id="8be78-113">Version</span></span>|<span data-ttu-id="8be78-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="8be78-114">4.6.2</span></span>|
|<span data-ttu-id="8be78-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="8be78-115">Type</span></span>|<span data-ttu-id="8be78-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="8be78-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="8be78-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8be78-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.DSACng.%23ctor(System.Security.Cryptography.CngKey)>
- <xref:System.Security.Cryptography.DSACng.Key?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSACng.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSACng.CreateSignature(System.Byte[])?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSACng.VerifySignature(System.Byte[],System.Byte[])?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACng.%23ctor(System.Security.Cryptography.CngKey)>
- <xref:System.Security.Cryptography.RSACng.Key?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACng.Decrypt(System.Byte[],System.Security.Cryptography.RSAEncryptionPadding)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACng.SignHash(System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.DSACng.#ctor(System.Security.Cryptography.CngKey)`
- `P:System.Security.Cryptography.DSACng.Key`
- `P:System.Security.Cryptography.DSACng.LegalKeySizes`
- `M:System.Security.Cryptography.DSACng.CreateSignature(System.Byte[])`
- `M:System.Security.Cryptography.DSACng.VerifySignature(System.Byte[],System.Byte[])`
- `M:System.Security.Cryptography.RSACng.#ctor(System.Security.Cryptography.CngKey)`
- `P:System.Security.Cryptography.RSACng.Key`
- `M:System.Security.Cryptography.RSACng.Decrypt(System.Byte[],System.Security.Cryptography.RSAEncryptionPadding)`
- `M:System.Security.Cryptography.RSACng.SignHash(System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)`

-->
