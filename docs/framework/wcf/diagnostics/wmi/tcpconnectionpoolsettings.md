---
title: TcpConnectionPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5038d093333eca9ca191c3ecae4cfa889d723276
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="16915-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="16915-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="16915-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="16915-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16915-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="16915-104">Syntax</span></span>  
  
```  
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="16915-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="16915-105">Methods</span></span>  
 <span data-ttu-id="16915-106">A classe TcpConnectionPoolSettings não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="16915-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="16915-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="16915-107">Properties</span></span>  
 <span data-ttu-id="16915-108">A classe TcpConnectionPoolSettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="16915-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="16915-109">Nome de grupo</span><span class="sxs-lookup"><span data-stu-id="16915-109">GroupName</span></span>  
 <span data-ttu-id="16915-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="16915-110">Data type: string</span></span>  
  
 <span data-ttu-id="16915-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="16915-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16915-112">O nome do grupo do pool de conexão usado para o elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="16915-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="16915-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="16915-113">IdleTimeout</span></span>  
 <span data-ttu-id="16915-114">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="16915-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="16915-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="16915-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16915-116">O tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="16915-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="16915-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="16915-117">LeaseTimeout</span></span>  
 <span data-ttu-id="16915-118">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="16915-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="16915-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="16915-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16915-120">O tempo máximo para a operação de concessão seja concluída antes do tempo limite.</span><span class="sxs-lookup"><span data-stu-id="16915-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="16915-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="16915-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="16915-122">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="16915-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="16915-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="16915-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16915-124">O máximo de conexões de saída para cada ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="16915-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16915-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="16915-125">Requirements</span></span>  
  
|<span data-ttu-id="16915-126">MOF</span><span class="sxs-lookup"><span data-stu-id="16915-126">MOF</span></span>|<span data-ttu-id="16915-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="16915-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="16915-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="16915-128">Namespace</span></span>|<span data-ttu-id="16915-129">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="16915-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="16915-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16915-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
