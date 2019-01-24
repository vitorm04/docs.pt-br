---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 3dddfa878e3cb5bd89fb76009d0dba530debb297
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725071"
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="9f51d-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="9f51d-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="9f51d-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="9f51d-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f51d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f51d-104">Syntax</span></span>  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9f51d-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="9f51d-105">Methods</span></span>  
 <span data-ttu-id="9f51d-106">A classe NamedPipeConnectionPoolSettings não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="9f51d-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9f51d-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="9f51d-107">Properties</span></span>  
 <span data-ttu-id="9f51d-108">A classe NamedPipeConnectionPoolSettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="9f51d-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="9f51d-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="9f51d-109">GroupName</span></span>  
 <span data-ttu-id="9f51d-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9f51d-110">Data type: string</span></span>  
  
 <span data-ttu-id="9f51d-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="9f51d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9f51d-112">O nome de grupo do pool de conexão usado pelo elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="9f51d-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="9f51d-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="9f51d-113">IdleTimeout</span></span>  
 <span data-ttu-id="9f51d-114">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="9f51d-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="9f51d-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="9f51d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9f51d-116">O tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="9f51d-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="9f51d-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="9f51d-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="9f51d-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="9f51d-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="9f51d-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="9f51d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9f51d-120">O número máximo de conexões de saída para cada ponto de extremidade no cliente.</span><span class="sxs-lookup"><span data-stu-id="9f51d-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f51d-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9f51d-121">Requirements</span></span>  
  
|<span data-ttu-id="9f51d-122">MOF</span><span class="sxs-lookup"><span data-stu-id="9f51d-122">MOF</span></span>|<span data-ttu-id="9f51d-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9f51d-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9f51d-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="9f51d-124">Namespace</span></span>|<span data-ttu-id="9f51d-125">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9f51d-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9f51d-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f51d-126">See also</span></span>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
