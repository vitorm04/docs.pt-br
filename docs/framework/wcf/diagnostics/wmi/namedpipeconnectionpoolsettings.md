---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 8c2d4bfc08a503a8d6eb0e8abf6f1e798b90bc83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963209"
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="4191b-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="4191b-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="4191b-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="4191b-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4191b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4191b-104">Syntax</span></span>  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4191b-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="4191b-105">Methods</span></span>  
 <span data-ttu-id="4191b-106">A classe NamedPipeConnectionPoolSettings não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="4191b-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4191b-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="4191b-107">Properties</span></span>  
 <span data-ttu-id="4191b-108">A classe NamedPipeConnectionPoolSettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="4191b-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="4191b-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="4191b-109">GroupName</span></span>  
 <span data-ttu-id="4191b-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="4191b-110">Data type: string</span></span>  
  
 <span data-ttu-id="4191b-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="4191b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4191b-112">O nome de grupo do pool de conexão usado pelo elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="4191b-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="4191b-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="4191b-113">IdleTimeout</span></span>  
 <span data-ttu-id="4191b-114">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="4191b-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="4191b-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="4191b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4191b-116">O tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="4191b-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="4191b-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="4191b-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="4191b-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="4191b-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="4191b-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="4191b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4191b-120">O número máximo de conexões de saída para cada ponto de extremidade no cliente.</span><span class="sxs-lookup"><span data-stu-id="4191b-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4191b-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4191b-121">Requirements</span></span>  
  
|<span data-ttu-id="4191b-122">MOF</span><span class="sxs-lookup"><span data-stu-id="4191b-122">MOF</span></span>|<span data-ttu-id="4191b-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4191b-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4191b-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="4191b-124">Namespace</span></span>|<span data-ttu-id="4191b-125">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4191b-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4191b-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4191b-126">See also</span></span>

- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
