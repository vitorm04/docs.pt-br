---
ms.openlocfilehash: 6ffd4147a99a59d0a2e50d3f88279608e286aed1
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679951"
---
### <a name="cryptostreamdispose-transforms-final-block-only-when-writing"></a><span data-ttu-id="82826-101">CryptoStream. Dispose transforma o bloco final somente durante a gravação</span><span class="sxs-lookup"><span data-stu-id="82826-101">CryptoStream.Dispose transforms final block only when writing</span></span>

<span data-ttu-id="82826-102">O <xref:System.Security.Cryptography.CryptoStream.Dispose%2A?displayProperty=nameWithType> método, que é usado para concluir `CryptoStream` as operações, não tenta mais transformar o bloco final durante a leitura.</span><span class="sxs-lookup"><span data-stu-id="82826-102">The <xref:System.Security.Cryptography.CryptoStream.Dispose%2A?displayProperty=nameWithType> method, which is used to finish `CryptoStream` operations, no longer attempts to transform the final block when reading.</span></span>

#### <a name="change-description"></a><span data-ttu-id="82826-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="82826-103">Change description</span></span>

<span data-ttu-id="82826-104">Nas versões anteriores do .NET, se um usuário realizou uma leitura incompleta ao usar <xref:System.Security.Cryptography.CryptoStream> no <xref:System.Security.Cryptography.CryptoStreamMode.Read> modo, o <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> método poderia gerar uma exceção (por exemplo, ao usar AES com preenchimento).</span><span class="sxs-lookup"><span data-stu-id="82826-104">In previous .NET versions, if a user performed an incomplete read when using <xref:System.Security.Cryptography.CryptoStream> in <xref:System.Security.Cryptography.CryptoStreamMode.Read> mode, the <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> method could throw an exception (for example, when using AES with padding).</span></span> <span data-ttu-id="82826-105">A exceção foi gerada porque o bloco final tentou ser transformado, mas os dados estavam incompletos.</span><span class="sxs-lookup"><span data-stu-id="82826-105">The exception was thrown because the final block was attempted to be transformed but the data was incomplete.</span></span>

<span data-ttu-id="82826-106">No .NET Core 3,0 e versões posteriores, <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> o não tenta mais transformar o bloco final ao ler, o que permite leituras incompletas.</span><span class="sxs-lookup"><span data-stu-id="82826-106">In .NET Core 3.0 and later versions, <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> no longer tries to transform the final block when reading, which allows for incomplete reads.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="82826-107">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="82826-107">Reason for change</span></span>

<span data-ttu-id="82826-108">Essa alteração permite leituras incompletas do fluxo de criptografia quando uma operação de rede é cancelada, sem a necessidade de capturar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="82826-108">This change enables incomplete reads from the crypto stream when a network operation is canceled, without the need to catch an exception.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="82826-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="82826-109">Version introduced</span></span>

<span data-ttu-id="82826-110">3.0</span><span class="sxs-lookup"><span data-stu-id="82826-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="82826-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="82826-111">Recommended action</span></span>

<span data-ttu-id="82826-112">A maioria dos aplicativos não deve ser afetada por essa alteração.</span><span class="sxs-lookup"><span data-stu-id="82826-112">Most apps should not be affected by this change.</span></span>

<span data-ttu-id="82826-113">Se seu aplicativo capturou anteriormente uma exceção no caso de uma leitura incompleta, você pode excluir esse `catch` bloco.</span><span class="sxs-lookup"><span data-stu-id="82826-113">If your application previously caught an exception in case of an incomplete read, you can delete that `catch` block.</span></span>
<span data-ttu-id="82826-114">Se seu aplicativo usou a transformação do bloco final em cenários de hash, talvez seja necessário garantir que todo o fluxo seja lido antes de ser Descartado.</span><span class="sxs-lookup"><span data-stu-id="82826-114">If your app used transforming of the final block in hashing scenarios, you might need to ensure that the entire stream is read before it's disposed.</span></span>

#### <a name="category"></a><span data-ttu-id="82826-115">Categoria</span><span class="sxs-lookup"><span data-stu-id="82826-115">Category</span></span>

<span data-ttu-id="82826-116">Criptografia</span><span class="sxs-lookup"><span data-stu-id="82826-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="82826-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="82826-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.CryptoStream.Dispose%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.CryptoStream.Dispose`

-->
