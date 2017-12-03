---
title: "Serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 027366e7bf7abd285ef65da2040514b4b9908213
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="service"></a><span data-ttu-id="196ce-102">Serviço</span><span class="sxs-lookup"><span data-stu-id="196ce-102">Service</span></span>
<span data-ttu-id="196ce-103">Serviço</span><span class="sxs-lookup"><span data-stu-id="196ce-103">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="196ce-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="196ce-104">Syntax</span></span>  
  
```  
class Service  
{  
  string BaseAddresses[];  
  Behavior Behaviors[];  
  string ConfigurationName;  
  string CounterInstanceName;  
  string DistinguishedName;  
  string Extensions[];  
  string Metadata[];  
  string Name;  
  string Namespace;  
  datetime Opened;  
  Channel OutgoingChannels[];  
  sint32 ProcessId;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="196ce-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="196ce-105">Methods</span></span>  
 <span data-ttu-id="196ce-106">A classe de serviço não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="196ce-106">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="196ce-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="196ce-107">Properties</span></span>  
 <span data-ttu-id="196ce-108">A classe de serviço tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="196ce-108">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="196ce-109">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="196ce-109">BaseAddresses</span></span>  
 <span data-ttu-id="196ce-110">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="196ce-110">Data type: string array</span></span>  
  
 <span data-ttu-id="196ce-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="196ce-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="196ce-112">Os endereços base usados pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="196ce-112">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="196ce-113">Comportamentos</span><span class="sxs-lookup"><span data-stu-id="196ce-113">Behaviors</span></span>  
 <span data-ttu-id="196ce-114">Tipo de dados: matriz de comportamento</span><span class="sxs-lookup"><span data-stu-id="196ce-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="196ce-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="196ce-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="196ce-116">Os comportamentos associados a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="196ce-116">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="196ce-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="196ce-117">ConfigurationName</span></span>  
 <span data-ttu-id="196ce-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="196ce-118">Data type: string</span></span>  
  
 <span data-ttu-id="196ce-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="196ce-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="196ce-120">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="196ce-120">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="196ce-121">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="196ce-121">CounterInstanceName</span></span>  
 <span data-ttu-id="196ce-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="196ce-122">Data type: string</span></span>  
  
 <span data-ttu-id="196ce-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="196ce-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="196ce-124">Nome da instância da instância dos contadores de desempenho do serviço.</span><span class="sxs-lookup"><span data-stu-id="196ce-124">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="196ce-125">DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="196ce-125">DistinguishedName</span></span>  
 <span data-ttu-id="196ce-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="196ce-126">Data type: string</span></span>  
  
 <span data-ttu-id="196ce-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="196ce-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="196ce-128">Nome do serviço no endereço.</span><span class="sxs-lookup"><span data-stu-id="196ce-128">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="196ce-129">Extensões</span><span class="sxs-lookup"><span data-stu-id="196ce-129">Extensions</span></span>  
 <span data-ttu-id="196ce-130">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="196ce-130">Data type: string array</span></span>  
  
 <span data-ttu-id="196ce-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="196ce-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="196ce-132">Os contextos da instância para as extensões da instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="196ce-132">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="196ce-133">Metadados</span><span class="sxs-lookup"><span data-stu-id="196ce-133">Metadata</span></span>  
 <span data-ttu-id="196ce-134">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="196ce-134">Data type: string array</span></span>  
  
 <span data-ttu-id="196ce-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="196ce-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="196ce-136">As definições de metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="196ce-136">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="196ce-137">Nome</span><span class="sxs-lookup"><span data-stu-id="196ce-137">Name</span></span>  
 <span data-ttu-id="196ce-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="196ce-138">Data type: string</span></span>  
  
 <span data-ttu-id="196ce-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="196ce-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="196ce-140">O nome exclusivo desse serviço.</span><span class="sxs-lookup"><span data-stu-id="196ce-140">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="196ce-141">Namespace</span><span class="sxs-lookup"><span data-stu-id="196ce-141">Namespace</span></span>  
 <span data-ttu-id="196ce-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="196ce-142">Data type: string</span></span>  
  
 <span data-ttu-id="196ce-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="196ce-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="196ce-144">O namespace do serviço.</span><span class="sxs-lookup"><span data-stu-id="196ce-144">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="196ce-145">Aberto</span><span class="sxs-lookup"><span data-stu-id="196ce-145">Opened</span></span>  
 <span data-ttu-id="196ce-146">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="196ce-146">Data type: datetime</span></span>  
  
 <span data-ttu-id="196ce-147">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="196ce-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="196ce-148">A hora em que o serviço foi aberto.</span><span class="sxs-lookup"><span data-stu-id="196ce-148">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="196ce-149">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="196ce-149">OutgoingChannels</span></span>  
 <span data-ttu-id="196ce-150">Tipo de dados: matriz de canal</span><span class="sxs-lookup"><span data-stu-id="196ce-150">Data type: Channel array</span></span>  
  
 <span data-ttu-id="196ce-151">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="196ce-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="196ce-152">Os canais que estão saindo da instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="196ce-152">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="196ce-153">ProcessId</span><span class="sxs-lookup"><span data-stu-id="196ce-153">ProcessId</span></span>  
 <span data-ttu-id="196ce-154">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="196ce-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="196ce-155">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="196ce-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="196ce-156">A id de processo do processo que hospeda o serviço.</span><span class="sxs-lookup"><span data-stu-id="196ce-156">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="196ce-157">Requisitos</span><span class="sxs-lookup"><span data-stu-id="196ce-157">Requirements</span></span>  
  
|<span data-ttu-id="196ce-158">MOF</span><span class="sxs-lookup"><span data-stu-id="196ce-158">MOF</span></span>|<span data-ttu-id="196ce-159">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="196ce-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="196ce-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="196ce-160">Namespace</span></span>|<span data-ttu-id="196ce-161">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="196ce-161">Defined in root\ServiceModel</span></span>|
