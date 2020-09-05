---
ms.openlocfilehash: 0c3876d30a80501a89f3a37ce24e2f71122c1b44
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497112"
---
### <a name="systemservicemodelwebwebservicehost-object-no-longer-adds-a-default-endpoint"></a><span data-ttu-id="e6af5-101">O objeto System.ServiceModel.Web.WebServiceHost não adiciona mais um ponto de extremidade padrão</span><span class="sxs-lookup"><span data-stu-id="e6af5-101">System.ServiceModel.Web.WebServiceHost object no longer adds a default endpoint</span></span>

#### <a name="details"></a><span data-ttu-id="e6af5-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e6af5-102">Details</span></span>

<span data-ttu-id="e6af5-103">O objeto <xref:System.ServiceModel.Web.WebServiceHost> não adicionará um ponto de extremidade padrão se um ponto de extremidade explícito tiver sido adicionado pelo código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e6af5-103">The <xref:System.ServiceModel.Web.WebServiceHost> object no longer adds a default endpoint if an explicit endpoint has been added by application code.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e6af5-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="e6af5-104">Suggestion</span></span>

<span data-ttu-id="e6af5-105">Se os usuários forem esperar para poderem se conectar a um ponto de extremidade padrão e outros pontos de extremidade explícitos forem adicionados ao <xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName>, os pontos de extremidade padrão também deverão ser explicitamente adicionados (usando <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="e6af5-105">If users will expect to be able to connect to a default endpoint and other explicit endpoints have been added to the <xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName>, default endpoints should also be added explicitly (using <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints?displayProperty=fullName>).</span></span>

| <span data-ttu-id="e6af5-106">Nome</span><span class="sxs-lookup"><span data-stu-id="e6af5-106">Name</span></span>    | <span data-ttu-id="e6af5-107">Valor</span><span class="sxs-lookup"><span data-stu-id="e6af5-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e6af5-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="e6af5-108">Scope</span></span>   |<span data-ttu-id="e6af5-109">Secundária</span><span class="sxs-lookup"><span data-stu-id="e6af5-109">Minor</span></span>|
|<span data-ttu-id="e6af5-110">Versão</span><span class="sxs-lookup"><span data-stu-id="e6af5-110">Version</span></span>|<span data-ttu-id="e6af5-111">4.5</span><span class="sxs-lookup"><span data-stu-id="e6af5-111">4.5</span></span>|
|<span data-ttu-id="e6af5-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="e6af5-112">Type</span></span>|<span data-ttu-id="e6af5-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="e6af5-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="e6af5-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="e6af5-114">Affected APIs</span></span>

- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.ServiceModel.Description.ServiceEndpoint)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String)`
- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri)`
- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String,System.Uri)`
- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)`
- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.ServiceModel.Description.ServiceEndpoint)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String,System.Uri)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)`

-->
