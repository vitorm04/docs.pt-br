---
ms.openlocfilehash: a6f93bbdf39a1b525e2daeb12afc3a6392a66e30
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235110"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a><span data-ttu-id="514d7-101">Desserialização de objetos MailMessage serializados no .NET Framework 4.5 pode falhar</span><span class="sxs-lookup"><span data-stu-id="514d7-101">Deserialization of MailMessage objects serialized under the .NET Framework 4.5 may fail</span></span>

|   |   |
|---|---|
|<span data-ttu-id="514d7-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="514d7-102">Details</span></span>|<span data-ttu-id="514d7-103">A partir do .NET Framework 4.5, os objetos <xref:System.Web.Mail.MailMessage> podem incluir caracteres não ASCII.</span><span class="sxs-lookup"><span data-stu-id="514d7-103">Starting with the .NET Framework 4.5, <xref:System.Web.Mail.MailMessage> objects can include non-ASCII characters.</span></span> <span data-ttu-id="514d7-104">No .NET Framework 4, somente caracteres ASCII têm suporte.</span><span class="sxs-lookup"><span data-stu-id="514d7-104">In the .NET Framework 4, only ASCII characters are supported.</span></span> <span data-ttu-id="514d7-105">Os objetos <xref:System.Web.Mail.MailMessage> que contêm caracteres não ASCII e são serializados no .NET Framework 4.5 ou versões posteriores não podem ser desserializados no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="514d7-105"><xref:System.Web.Mail.MailMessage> objects that contain non-ASCII characters and that are serialized under the .NET Framework 4.5 or later cannot be deserialized under the .NET Framework 4.</span></span>|
|<span data-ttu-id="514d7-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="514d7-106">Suggestion</span></span>|<span data-ttu-id="514d7-107">Verifique se o seu código fornece tratamento de exceção ao desserializar um objeto <xref:System.Web.Mail.MailMessage>.</span><span class="sxs-lookup"><span data-stu-id="514d7-107">Ensure that your code provides exception handling when deserializing a <xref:System.Web.Mail.MailMessage> object.</span></span>|
|<span data-ttu-id="514d7-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="514d7-108">Scope</span></span>|<span data-ttu-id="514d7-109">Secundário</span><span class="sxs-lookup"><span data-stu-id="514d7-109">Minor</span></span>|
|<span data-ttu-id="514d7-110">Versão</span><span class="sxs-lookup"><span data-stu-id="514d7-110">Version</span></span>|<span data-ttu-id="514d7-111">4.5</span><span class="sxs-lookup"><span data-stu-id="514d7-111">4.5</span></span>|
|<span data-ttu-id="514d7-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="514d7-112">Type</span></span>|<span data-ttu-id="514d7-113">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="514d7-113">Runtime</span></span>|
|<span data-ttu-id="514d7-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="514d7-114">Affected APIs</span></span>|<ul><li><xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
