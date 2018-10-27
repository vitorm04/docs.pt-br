---
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: f9e1c043579f632f16a7cf36bf34c2467a743e47
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50189557"
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="9e298-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="9e298-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="9e298-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="9e298-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e298-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e298-104">Syntax</span></span>  
  
```csharp
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9e298-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="9e298-105">Methods</span></span>  
 <span data-ttu-id="9e298-106">A classe TcpConnectionPoolSettings não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="9e298-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9e298-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="9e298-107">Properties</span></span>  
 <span data-ttu-id="9e298-108">A classe TcpConnectionPoolSettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="9e298-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="9e298-109">Nome de grupo</span><span class="sxs-lookup"><span data-stu-id="9e298-109">GroupName</span></span>  
 <span data-ttu-id="9e298-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9e298-110">Data type: string</span></span>  
  
 <span data-ttu-id="9e298-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="9e298-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e298-112">O nome de grupo do pool de conexão usado pelo elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="9e298-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="9e298-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="9e298-113">IdleTimeout</span></span>  
 <span data-ttu-id="9e298-114">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="9e298-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="9e298-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="9e298-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e298-116">O tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="9e298-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="9e298-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="9e298-117">LeaseTimeout</span></span>  
 <span data-ttu-id="9e298-118">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="9e298-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="9e298-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="9e298-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e298-120">O tempo máximo para a operação seja concluída antes de atingir o tempo limite de concessão.</span><span class="sxs-lookup"><span data-stu-id="9e298-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="9e298-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="9e298-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="9e298-122">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="9e298-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="9e298-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="9e298-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e298-124">O máximo de conexões de saída para cada ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="9e298-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e298-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9e298-125">Requirements</span></span>  
  
|<span data-ttu-id="9e298-126">MOF</span><span class="sxs-lookup"><span data-stu-id="9e298-126">MOF</span></span>|<span data-ttu-id="9e298-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9e298-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9e298-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="9e298-128">Namespace</span></span>|<span data-ttu-id="9e298-129">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9e298-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9e298-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e298-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
