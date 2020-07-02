---
ms.openlocfilehash: 57f68c10d5d1edc9b8deaca2f4fe7edda2dd69b0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619868"
---
### <a name="systemservicemodelwebwebservicehost-object-no-longer-adds-a-default-endpoint"></a><span data-ttu-id="973d0-101">O objeto System.ServiceModel.Web.WebServiceHost não adiciona mais um ponto de extremidade padrão</span><span class="sxs-lookup"><span data-stu-id="973d0-101">System.ServiceModel.Web.WebServiceHost object no longer adds a default endpoint</span></span>

#### <a name="details"></a><span data-ttu-id="973d0-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="973d0-102">Details</span></span>

<span data-ttu-id="973d0-103">O objeto <xref:System.ServiceModel.Web.WebServiceHost> não adicionará um ponto de extremidade padrão se um ponto de extremidade explícito tiver sido adicionado pelo código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="973d0-103">The <xref:System.ServiceModel.Web.WebServiceHost> object no longer adds a default endpoint if an explicit endpoint has been added by application code.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="973d0-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="973d0-104">Suggestion</span></span>

<span data-ttu-id="973d0-105">Se os usuários forem esperar para poderem se conectar a um ponto de extremidade padrão e outros pontos de extremidade explícitos forem adicionados ao <xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName>, os pontos de extremidade padrão também deverão ser explicitamente adicionados (usando <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="973d0-105">If users will expect to be able to connect to a default endpoint and other explicit endpoints have been added to the <xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName>, default endpoints should also be added explicitly (using <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints?displayProperty=fullName>).</span></span>

| <span data-ttu-id="973d0-106">Name</span><span class="sxs-lookup"><span data-stu-id="973d0-106">Name</span></span>    | <span data-ttu-id="973d0-107">Valor</span><span class="sxs-lookup"><span data-stu-id="973d0-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="973d0-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="973d0-108">Scope</span></span>   |<span data-ttu-id="973d0-109">Secundária</span><span class="sxs-lookup"><span data-stu-id="973d0-109">Minor</span></span>|
|<span data-ttu-id="973d0-110">Versão</span><span class="sxs-lookup"><span data-stu-id="973d0-110">Version</span></span>|<span data-ttu-id="973d0-111">4.5</span><span class="sxs-lookup"><span data-stu-id="973d0-111">4.5</span></span>|
|<span data-ttu-id="973d0-112">Type</span><span class="sxs-lookup"><span data-stu-id="973d0-112">Type</span></span>|<span data-ttu-id="973d0-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="973d0-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="973d0-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="973d0-114">Affected APIs</span></span>

-<xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.ServiceModel.Description.ServiceEndpoint)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType></li></ul>|
