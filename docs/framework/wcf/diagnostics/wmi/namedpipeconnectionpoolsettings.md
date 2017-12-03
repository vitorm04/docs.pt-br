---
title: NamedPipeConnectionPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18740c4c87aaeafcd0a28991376e0c45fe688223
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="7bbb8-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="7bbb8-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="7bbb8-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="7bbb8-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bbb8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7bbb8-104">Syntax</span></span>  
  
```  
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7bbb8-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="7bbb8-105">Methods</span></span>  
 <span data-ttu-id="7bbb8-106">A classe NamedPipeConnectionPoolSettings não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7bbb8-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="7bbb8-107">Properties</span></span>  
 <span data-ttu-id="7bbb8-108">A classe NamedPipeConnectionPoolSettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="7bbb8-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="7bbb8-109">Nome de grupo</span><span class="sxs-lookup"><span data-stu-id="7bbb8-109">GroupName</span></span>  
 <span data-ttu-id="7bbb8-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7bbb8-110">Data type: string</span></span>  
  
 <span data-ttu-id="7bbb8-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="7bbb8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7bbb8-112">O nome do grupo do pool de conexão usado para o elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="7bbb8-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="7bbb8-113">IdleTimeout</span></span>  
 <span data-ttu-id="7bbb8-114">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="7bbb8-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="7bbb8-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="7bbb8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7bbb8-116">O tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="7bbb8-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="7bbb8-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="7bbb8-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="7bbb8-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="7bbb8-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="7bbb8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7bbb8-120">O número máximo de conexões de saída para cada ponto de extremidade no cliente.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bbb8-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7bbb8-121">Requirements</span></span>  
  
|<span data-ttu-id="7bbb8-122">MOF</span><span class="sxs-lookup"><span data-stu-id="7bbb8-122">MOF</span></span>|<span data-ttu-id="7bbb8-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7bbb8-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7bbb8-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="7bbb8-124">Namespace</span></span>|<span data-ttu-id="7bbb8-125">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7bbb8-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7bbb8-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7bbb8-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
