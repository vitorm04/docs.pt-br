---
ms.openlocfilehash: d48519443aeee05617538cf2cc12bea49ad3e16d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858506"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="03161-101">Agora, o X509Certificate2.ToString(Boolean) não é gerado quando o .NET não pode tratar o certificado</span><span class="sxs-lookup"><span data-stu-id="03161-101">X509Certificate2.ToString(Boolean) does not throw now when .NET cannot handle the certificate</span></span>

|   |   |
|---|---|
|<span data-ttu-id="03161-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="03161-102">Details</span></span>|<span data-ttu-id="03161-103">No .NET Framework 4.5.2 e nas versões anteriores, esse método era gerado quando <code>true</code> era passado para o parâmetro verbose e havia certificados instalados que não eram compatíveis com o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="03161-103">In .NET Framework 4.5.2 and earlier versions, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="03161-104">Agora, o método será bem-sucedido e retornará uma cadeia de caracteres válida que omita as partes inacessíveis do certificado.</span><span class="sxs-lookup"><span data-stu-id="03161-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>|
|<span data-ttu-id="03161-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="03161-105">Suggestion</span></span>|<span data-ttu-id="03161-106">Qualquer código dependente do <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> deve ser atualizado para esperar que a cadeia de caracteres retornada possa excluir alguns dados do certificado (como chave pública, chave privada e extensões) em alguns casos nos quais a API teria sido gerada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="03161-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>|
|<span data-ttu-id="03161-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="03161-107">Scope</span></span>|<span data-ttu-id="03161-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="03161-108">Edge</span></span>|
|<span data-ttu-id="03161-109">Versão</span><span class="sxs-lookup"><span data-stu-id="03161-109">Version</span></span>|<span data-ttu-id="03161-110">4.6</span><span class="sxs-lookup"><span data-stu-id="03161-110">4.6</span></span>|
|<span data-ttu-id="03161-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="03161-111">Type</span></span>|<span data-ttu-id="03161-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="03161-112">Runtime</span></span>|
|<span data-ttu-id="03161-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="03161-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|

