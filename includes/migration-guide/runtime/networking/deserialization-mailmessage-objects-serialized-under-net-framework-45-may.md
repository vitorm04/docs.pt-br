---
ms.openlocfilehash: ad953a1562db407c04d7860c60eb5964fe6fe2ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619803"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a><span data-ttu-id="df5f9-101">Desserialização de objetos MailMessage serializados no .NET Framework 4.5 pode falhar</span><span class="sxs-lookup"><span data-stu-id="df5f9-101">Deserialization of MailMessage objects serialized under the .NET Framework 4.5 may fail</span></span>

#### <a name="details"></a><span data-ttu-id="df5f9-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="df5f9-102">Details</span></span>

<span data-ttu-id="df5f9-103">A partir do .NET Framework 4.5, os objetos <xref:System.Web.Mail.MailMessage> podem incluir caracteres não ASCII.</span><span class="sxs-lookup"><span data-stu-id="df5f9-103">Starting with the .NET Framework 4.5, <xref:System.Web.Mail.MailMessage> objects can include non-ASCII characters.</span></span> <span data-ttu-id="df5f9-104">No .NET Framework 4, somente caracteres ASCII têm suporte.</span><span class="sxs-lookup"><span data-stu-id="df5f9-104">In the .NET Framework 4, only ASCII characters are supported.</span></span> <span data-ttu-id="df5f9-105">Os objetos <xref:System.Web.Mail.MailMessage> que contêm caracteres não ASCII e são serializados no .NET Framework 4.5 ou versões posteriores não podem ser desserializados no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="df5f9-105"><xref:System.Web.Mail.MailMessage> objects that contain non-ASCII characters and that are serialized under the .NET Framework 4.5 or later cannot be deserialized under the .NET Framework 4.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="df5f9-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="df5f9-106">Suggestion</span></span>

<span data-ttu-id="df5f9-107">Verifique se o seu código fornece tratamento de exceção ao desserializar um objeto <xref:System.Web.Mail.MailMessage>.</span><span class="sxs-lookup"><span data-stu-id="df5f9-107">Ensure that your code provides exception handling when deserializing a <xref:System.Web.Mail.MailMessage> object.</span></span>

| <span data-ttu-id="df5f9-108">Name</span><span class="sxs-lookup"><span data-stu-id="df5f9-108">Name</span></span>    | <span data-ttu-id="df5f9-109">Valor</span><span class="sxs-lookup"><span data-stu-id="df5f9-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="df5f9-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="df5f9-110">Scope</span></span>   |<span data-ttu-id="df5f9-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="df5f9-111">Minor</span></span>|
|<span data-ttu-id="df5f9-112">Versão</span><span class="sxs-lookup"><span data-stu-id="df5f9-112">Version</span></span>|<span data-ttu-id="df5f9-113">4.5</span><span class="sxs-lookup"><span data-stu-id="df5f9-113">4.5</span></span>|
|<span data-ttu-id="df5f9-114">Type</span><span class="sxs-lookup"><span data-stu-id="df5f9-114">Type</span></span>|<span data-ttu-id="df5f9-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="df5f9-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="df5f9-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="df5f9-116">Affected APIs</span></span>

-<xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
