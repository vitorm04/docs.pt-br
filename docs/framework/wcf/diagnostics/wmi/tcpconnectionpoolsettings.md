---
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: 4a30ad3ddfef5d39942345b0e0d5274eeff8e596
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485915"
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="596bc-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="596bc-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="596bc-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="596bc-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="596bc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="596bc-104">Syntax</span></span>  
  
```  
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="596bc-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="596bc-105">Methods</span></span>  
 <span data-ttu-id="596bc-106">A classe TcpConnectionPoolSettings não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="596bc-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="596bc-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="596bc-107">Properties</span></span>  
 <span data-ttu-id="596bc-108">A classe TcpConnectionPoolSettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="596bc-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="596bc-109">Nome de grupo</span><span class="sxs-lookup"><span data-stu-id="596bc-109">GroupName</span></span>  
 <span data-ttu-id="596bc-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="596bc-110">Data type: string</span></span>  
  
 <span data-ttu-id="596bc-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="596bc-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="596bc-112">O nome do grupo do pool de conexão usado para o elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="596bc-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="596bc-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="596bc-113">IdleTimeout</span></span>  
 <span data-ttu-id="596bc-114">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="596bc-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="596bc-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="596bc-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="596bc-116">O tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="596bc-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="596bc-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="596bc-117">LeaseTimeout</span></span>  
 <span data-ttu-id="596bc-118">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="596bc-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="596bc-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="596bc-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="596bc-120">O tempo máximo para a operação de concessão seja concluída antes do tempo limite.</span><span class="sxs-lookup"><span data-stu-id="596bc-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="596bc-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="596bc-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="596bc-122">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="596bc-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="596bc-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="596bc-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="596bc-124">O máximo de conexões de saída para cada ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="596bc-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="596bc-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="596bc-125">Requirements</span></span>  
  
|<span data-ttu-id="596bc-126">MOF</span><span class="sxs-lookup"><span data-stu-id="596bc-126">MOF</span></span>|<span data-ttu-id="596bc-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="596bc-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="596bc-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="596bc-128">Namespace</span></span>|<span data-ttu-id="596bc-129">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="596bc-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="596bc-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="596bc-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
