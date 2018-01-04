---
title: Classe de canal
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 073f0a2a2731a08acd914a7dd85cb2b419d98128
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="channel-class"></a><span data-ttu-id="872cc-102">Classe de canal</span><span class="sxs-lookup"><span data-stu-id="872cc-102">Channel class</span></span>
<span data-ttu-id="872cc-103">Canal</span><span class="sxs-lookup"><span data-stu-id="872cc-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="872cc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="872cc-104">Syntax</span></span>  
  
```  
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="872cc-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="872cc-105">Methods</span></span>  
 <span data-ttu-id="872cc-106">A classe de canal não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="872cc-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="872cc-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="872cc-107">Properties</span></span>  
 <span data-ttu-id="872cc-108">A classe de canal tem as seguintes propriedades.</span><span class="sxs-lookup"><span data-stu-id="872cc-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="872cc-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="872cc-109">LocalAddress</span></span>  
 <span data-ttu-id="872cc-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="872cc-110">Data type: string</span></span>  
  
 <span data-ttu-id="872cc-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="872cc-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="872cc-112">O ponto de extremidade local para o canal.</span><span class="sxs-lookup"><span data-stu-id="872cc-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="872cc-113">ref</span><span class="sxs-lookup"><span data-stu-id="872cc-113">ref</span></span>  
 <span data-ttu-id="872cc-114">Tipo de dados: ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="872cc-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="872cc-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="872cc-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="872cc-116">Uma referência ao ponto de extremidade de canal se conecta ao.</span><span class="sxs-lookup"><span data-stu-id="872cc-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="872cc-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="872cc-117">RemoteAddress</span></span>  
 <span data-ttu-id="872cc-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="872cc-118">Data type: string</span></span>  
  
 <span data-ttu-id="872cc-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="872cc-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="872cc-120">O endereço remoto associado ao canal.</span><span class="sxs-lookup"><span data-stu-id="872cc-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="872cc-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="872cc-121">SessionId</span></span>  
 <span data-ttu-id="872cc-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="872cc-122">Data type: string</span></span>  
  
 <span data-ttu-id="872cc-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="872cc-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="872cc-124">A sessão atual Id, se houver.</span><span class="sxs-lookup"><span data-stu-id="872cc-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="872cc-125">Tipo</span><span class="sxs-lookup"><span data-stu-id="872cc-125">Type</span></span>  
 <span data-ttu-id="872cc-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="872cc-126">Data type: string</span></span>  
  
 <span data-ttu-id="872cc-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="872cc-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="872cc-128">O tipo de canal.</span><span class="sxs-lookup"><span data-stu-id="872cc-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="872cc-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="872cc-129">Requirements</span></span>  
  
|<span data-ttu-id="872cc-130">MOF</span><span class="sxs-lookup"><span data-stu-id="872cc-130">MOF</span></span>|<span data-ttu-id="872cc-131">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="872cc-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="872cc-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="872cc-132">Namespace</span></span>|<span data-ttu-id="872cc-133">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="872cc-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="872cc-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="872cc-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
