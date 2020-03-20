---
ms.openlocfilehash: e7154919d6a09a04e650d5546feb2ae6c6cc912f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859103"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a><span data-ttu-id="2ab3c-101">HttpRuntime.AppDomainAppPath gera NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="2ab3c-101">HttpRuntime.AppDomainAppPath Throws a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="2ab3c-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="2ab3c-102">Details</span></span>|<span data-ttu-id="2ab3c-103">No .NET Framework 4.6.2, o runtime gera <code>T:System.NullReferenceException</code> ao recuperar um valor <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> que inclui caracteres nulos. No .NET Framework 4.6.1 e versões anteriores, o runtime gera <code>T:System.ArgumentNullException</code>.</span><span class="sxs-lookup"><span data-stu-id="2ab3c-103">In the .NET Framework 4.6.2, the runtime throws a <code>T:System.NullReferenceException</code> when retrieving a <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> value that includes null characters.In the .NET Framework 4.6.1 and earlier versions, the runtime throws an <code>T:System.ArgumentNullException</code>.</span></span>|
|<span data-ttu-id="2ab3c-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="2ab3c-104">Suggestion</span></span>|<span data-ttu-id="2ab3c-105">Você pode fazer o seguinte para responder a essa alteração:</span><span class="sxs-lookup"><span data-stu-id="2ab3c-105">You can do either of the follow to respond to this change:</span></span><ul><li><span data-ttu-id="2ab3c-106">Identifique o <code>T:System.NullReferenceException</code> se o aplicativo estiver sendo executado no .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="2ab3c-106">Handle the <code>T:System.NullReferenceException</code> if you application is running on the .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="2ab3c-107">Atualize para o .NET Framework 4.7, que restaura o comportamento anterior e gera <code>T:System.ArgumentNullException</code>.</span><span class="sxs-lookup"><span data-stu-id="2ab3c-107">Upgrade to the .NET Framework 4.7, which restores the previous behavior and throws an <code>T:System.ArgumentNullException</code>.</span></span></li></ul>|
|<span data-ttu-id="2ab3c-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="2ab3c-108">Scope</span></span>|<span data-ttu-id="2ab3c-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="2ab3c-109">Edge</span></span>|
|<span data-ttu-id="2ab3c-110">Versão</span><span class="sxs-lookup"><span data-stu-id="2ab3c-110">Version</span></span>|<span data-ttu-id="2ab3c-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="2ab3c-111">4.6.2</span></span>|
|<span data-ttu-id="2ab3c-112">Type</span><span class="sxs-lookup"><span data-stu-id="2ab3c-112">Type</span></span>|<span data-ttu-id="2ab3c-113">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="2ab3c-113">Retargeting</span></span>|
|<span data-ttu-id="2ab3c-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="2ab3c-114">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|
