---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 3548a1f19672a98ad0fc81eec15d5be29e5170bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486263"
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="e6b59-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="e6b59-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="e6b59-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="e6b59-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6b59-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6b59-104">Syntax</span></span>  
  
```  
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e6b59-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="e6b59-105">Methods</span></span>  
 <span data-ttu-id="e6b59-106">A classe NamedPipeConnectionPoolSettings não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="e6b59-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e6b59-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e6b59-107">Properties</span></span>  
 <span data-ttu-id="e6b59-108">A classe NamedPipeConnectionPoolSettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="e6b59-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="e6b59-109">Nome de grupo</span><span class="sxs-lookup"><span data-stu-id="e6b59-109">GroupName</span></span>  
 <span data-ttu-id="e6b59-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e6b59-110">Data type: string</span></span>  
  
 <span data-ttu-id="e6b59-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="e6b59-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e6b59-112">O nome do grupo do pool de conexão usado para o elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="e6b59-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="e6b59-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="e6b59-113">IdleTimeout</span></span>  
 <span data-ttu-id="e6b59-114">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="e6b59-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="e6b59-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="e6b59-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e6b59-116">O tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="e6b59-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="e6b59-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="e6b59-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="e6b59-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="e6b59-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="e6b59-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="e6b59-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e6b59-120">O número máximo de conexões de saída para cada ponto de extremidade no cliente.</span><span class="sxs-lookup"><span data-stu-id="e6b59-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6b59-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e6b59-121">Requirements</span></span>  
  
|<span data-ttu-id="e6b59-122">MOF</span><span class="sxs-lookup"><span data-stu-id="e6b59-122">MOF</span></span>|<span data-ttu-id="e6b59-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e6b59-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e6b59-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="e6b59-124">Namespace</span></span>|<span data-ttu-id="e6b59-125">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e6b59-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6b59-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6b59-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
