---
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: 6fa68eed241edaea40b66c31240a4201e05779f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093508"
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="2fa22-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="2fa22-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="2fa22-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="2fa22-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fa22-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2fa22-104">Syntax</span></span>  
  
```csharp
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2fa22-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="2fa22-105">Methods</span></span>  
 <span data-ttu-id="2fa22-106">A classe TcpConnectionPoolSettings não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="2fa22-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2fa22-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="2fa22-107">Properties</span></span>  
 <span data-ttu-id="2fa22-108">A classe TcpConnectionPoolSettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="2fa22-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="2fa22-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="2fa22-109">GroupName</span></span>  
 <span data-ttu-id="2fa22-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="2fa22-110">Data type: string</span></span>  
  
 <span data-ttu-id="2fa22-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="2fa22-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fa22-112">O nome de grupo do pool de conexão usado pelo elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="2fa22-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="2fa22-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="2fa22-113">IdleTimeout</span></span>  
 <span data-ttu-id="2fa22-114">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="2fa22-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="2fa22-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="2fa22-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fa22-116">O tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="2fa22-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="2fa22-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="2fa22-117">LeaseTimeout</span></span>  
 <span data-ttu-id="2fa22-118">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="2fa22-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="2fa22-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="2fa22-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fa22-120">O tempo máximo para a operação seja concluída antes de atingir o tempo limite de concessão.</span><span class="sxs-lookup"><span data-stu-id="2fa22-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="2fa22-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="2fa22-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="2fa22-122">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="2fa22-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="2fa22-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="2fa22-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fa22-124">O máximo de conexões de saída para cada ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2fa22-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fa22-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2fa22-125">Requirements</span></span>  
  
|<span data-ttu-id="2fa22-126">MOF</span><span class="sxs-lookup"><span data-stu-id="2fa22-126">MOF</span></span>|<span data-ttu-id="2fa22-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2fa22-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2fa22-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="2fa22-128">Namespace</span></span>|<span data-ttu-id="2fa22-129">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2fa22-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2fa22-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fa22-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
