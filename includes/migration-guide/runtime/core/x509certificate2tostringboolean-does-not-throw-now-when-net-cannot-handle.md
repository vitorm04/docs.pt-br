---
ms.openlocfilehash: 7f8f97adcca7e66fa5756212bb977daadd92b8b6
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497443"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="5d750-101">Agora, o X509Certificate2.ToString(Boolean) não é gerado quando o .NET não pode tratar o certificado</span><span class="sxs-lookup"><span data-stu-id="5d750-101">X509Certificate2.ToString(Boolean) does not throw now when .NET cannot handle the certificate</span></span>

#### <a name="details"></a><span data-ttu-id="5d750-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="5d750-102">Details</span></span>

<span data-ttu-id="5d750-103">No .NET Framework 4.5.2 e nas versões anteriores, esse método era gerado quando <code>true</code> era passado para o parâmetro verbose e havia certificados instalados que não eram compatíveis com o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5d750-103">In .NET Framework 4.5.2 and earlier versions, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="5d750-104">Agora, o método será bem-sucedido e retornará uma cadeia de caracteres válida que omita as partes inacessíveis do certificado.</span><span class="sxs-lookup"><span data-stu-id="5d750-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5d750-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="5d750-105">Suggestion</span></span>

<span data-ttu-id="5d750-106">Qualquer código dependente do <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> deve ser atualizado para esperar que a cadeia de caracteres retornada possa excluir alguns dados do certificado (como chave pública, chave privada e extensões) em alguns casos nos quais a API teria sido gerada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="5d750-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>

| <span data-ttu-id="5d750-107">Nome</span><span class="sxs-lookup"><span data-stu-id="5d750-107">Name</span></span>    | <span data-ttu-id="5d750-108">Valor</span><span class="sxs-lookup"><span data-stu-id="5d750-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5d750-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="5d750-109">Scope</span></span>   |<span data-ttu-id="5d750-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="5d750-110">Edge</span></span>|
|<span data-ttu-id="5d750-111">Versão</span><span class="sxs-lookup"><span data-stu-id="5d750-111">Version</span></span>|<span data-ttu-id="5d750-112">4.6</span><span class="sxs-lookup"><span data-stu-id="5d750-112">4.6</span></span>|
|<span data-ttu-id="5d750-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="5d750-113">Type</span></span>|<span data-ttu-id="5d750-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="5d750-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="5d750-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="5d750-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)`

-->
