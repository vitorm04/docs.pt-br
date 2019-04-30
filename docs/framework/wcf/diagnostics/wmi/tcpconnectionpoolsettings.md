---
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: 6fa68eed241edaea40b66c31240a4201e05779f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956566"
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="ab0c9-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="ab0c9-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="ab0c9-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="ab0c9-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab0c9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ab0c9-104">Syntax</span></span>  
  
```csharp
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ab0c9-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="ab0c9-105">Methods</span></span>  
 <span data-ttu-id="ab0c9-106">A classe TcpConnectionPoolSettings não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="ab0c9-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ab0c9-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ab0c9-107">Properties</span></span>  
 <span data-ttu-id="ab0c9-108">A classe TcpConnectionPoolSettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="ab0c9-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="ab0c9-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="ab0c9-109">GroupName</span></span>  
 <span data-ttu-id="ab0c9-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ab0c9-110">Data type: string</span></span>  
  
 <span data-ttu-id="ab0c9-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ab0c9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab0c9-112">O nome de grupo do pool de conexão usado pelo elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="ab0c9-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="ab0c9-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="ab0c9-113">IdleTimeout</span></span>  
 <span data-ttu-id="ab0c9-114">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="ab0c9-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="ab0c9-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ab0c9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab0c9-116">O tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="ab0c9-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="ab0c9-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="ab0c9-117">LeaseTimeout</span></span>  
 <span data-ttu-id="ab0c9-118">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="ab0c9-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="ab0c9-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ab0c9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab0c9-120">O tempo máximo para a operação seja concluída antes de atingir o tempo limite de concessão.</span><span class="sxs-lookup"><span data-stu-id="ab0c9-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="ab0c9-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="ab0c9-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="ab0c9-122">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="ab0c9-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="ab0c9-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ab0c9-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab0c9-124">O máximo de conexões de saída para cada ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ab0c9-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab0c9-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ab0c9-125">Requirements</span></span>  
  
|<span data-ttu-id="ab0c9-126">MOF</span><span class="sxs-lookup"><span data-stu-id="ab0c9-126">MOF</span></span>|<span data-ttu-id="ab0c9-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ab0c9-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ab0c9-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="ab0c9-128">Namespace</span></span>|<span data-ttu-id="ab0c9-129">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ab0c9-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab0c9-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab0c9-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
