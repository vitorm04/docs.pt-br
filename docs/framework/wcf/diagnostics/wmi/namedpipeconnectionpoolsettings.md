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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cf9c39334289cb30d1a01917c0be37da02fcdc5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="6a6d7-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="6a6d7-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="6a6d7-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="6a6d7-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a6d7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6a6d7-104">Syntax</span></span>  
  
```  
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6a6d7-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="6a6d7-105">Methods</span></span>  
 <span data-ttu-id="6a6d7-106">A classe NamedPipeConnectionPoolSettings não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="6a6d7-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6a6d7-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="6a6d7-107">Properties</span></span>  
 <span data-ttu-id="6a6d7-108">A classe NamedPipeConnectionPoolSettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="6a6d7-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="6a6d7-109">Nome de grupo</span><span class="sxs-lookup"><span data-stu-id="6a6d7-109">GroupName</span></span>  
 <span data-ttu-id="6a6d7-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="6a6d7-110">Data type: string</span></span>  
  
 <span data-ttu-id="6a6d7-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="6a6d7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6a6d7-112">O nome do grupo do pool de conexão usado para o elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="6a6d7-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="6a6d7-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="6a6d7-113">IdleTimeout</span></span>  
 <span data-ttu-id="6a6d7-114">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="6a6d7-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="6a6d7-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="6a6d7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6a6d7-116">O tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="6a6d7-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="6a6d7-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="6a6d7-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="6a6d7-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="6a6d7-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="6a6d7-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="6a6d7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6a6d7-120">O número máximo de conexões de saída para cada ponto de extremidade no cliente.</span><span class="sxs-lookup"><span data-stu-id="6a6d7-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a6d7-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6a6d7-121">Requirements</span></span>  
  
|<span data-ttu-id="6a6d7-122">MOF</span><span class="sxs-lookup"><span data-stu-id="6a6d7-122">MOF</span></span>|<span data-ttu-id="6a6d7-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="6a6d7-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6a6d7-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="6a6d7-124">Namespace</span></span>|<span data-ttu-id="6a6d7-125">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6a6d7-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6a6d7-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a6d7-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
