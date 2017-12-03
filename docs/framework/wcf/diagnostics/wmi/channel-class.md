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
ms.openlocfilehash: 93632d6a178c0f58143fc148a0e1eb51be94ed17
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="channel-class"></a><span data-ttu-id="f01e1-102">Classe de canal</span><span class="sxs-lookup"><span data-stu-id="f01e1-102">Channel class</span></span>
<span data-ttu-id="f01e1-103">Canal</span><span class="sxs-lookup"><span data-stu-id="f01e1-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f01e1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f01e1-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="f01e1-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="f01e1-105">Methods</span></span>  
 <span data-ttu-id="f01e1-106">A classe de canal não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="f01e1-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f01e1-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="f01e1-107">Properties</span></span>  
 <span data-ttu-id="f01e1-108">A classe de canal tem as seguintes propriedades.</span><span class="sxs-lookup"><span data-stu-id="f01e1-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="f01e1-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="f01e1-109">LocalAddress</span></span>  
 <span data-ttu-id="f01e1-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="f01e1-110">Data type: string</span></span>  
  
 <span data-ttu-id="f01e1-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="f01e1-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f01e1-112">O ponto de extremidade local para o canal.</span><span class="sxs-lookup"><span data-stu-id="f01e1-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="f01e1-113">ref</span><span class="sxs-lookup"><span data-stu-id="f01e1-113">ref</span></span>  
 <span data-ttu-id="f01e1-114">Tipo de dados: ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="f01e1-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="f01e1-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="f01e1-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f01e1-116">Uma referência ao ponto de extremidade de canal se conecta ao.</span><span class="sxs-lookup"><span data-stu-id="f01e1-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="f01e1-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="f01e1-117">RemoteAddress</span></span>  
 <span data-ttu-id="f01e1-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="f01e1-118">Data type: string</span></span>  
  
 <span data-ttu-id="f01e1-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="f01e1-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f01e1-120">O endereço remoto associado ao canal.</span><span class="sxs-lookup"><span data-stu-id="f01e1-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="f01e1-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="f01e1-121">SessionId</span></span>  
 <span data-ttu-id="f01e1-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="f01e1-122">Data type: string</span></span>  
  
 <span data-ttu-id="f01e1-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="f01e1-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f01e1-124">A sessão atual Id, se houver.</span><span class="sxs-lookup"><span data-stu-id="f01e1-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="f01e1-125">Tipo</span><span class="sxs-lookup"><span data-stu-id="f01e1-125">Type</span></span>  
 <span data-ttu-id="f01e1-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="f01e1-126">Data type: string</span></span>  
  
 <span data-ttu-id="f01e1-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="f01e1-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f01e1-128">O tipo de canal.</span><span class="sxs-lookup"><span data-stu-id="f01e1-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f01e1-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f01e1-129">Requirements</span></span>  
  
|<span data-ttu-id="f01e1-130">MOF</span><span class="sxs-lookup"><span data-stu-id="f01e1-130">MOF</span></span>|<span data-ttu-id="f01e1-131">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f01e1-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f01e1-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="f01e1-132">Namespace</span></span>|<span data-ttu-id="f01e1-133">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f01e1-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f01e1-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f01e1-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
