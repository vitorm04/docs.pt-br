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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bd784b470810e16b86ba7537b1f45681ac3e1ed1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="service"></a><span data-ttu-id="23aa4-102">Serviço</span><span class="sxs-lookup"><span data-stu-id="23aa4-102">Service</span></span>
<span data-ttu-id="23aa4-103">Serviço</span><span class="sxs-lookup"><span data-stu-id="23aa4-103">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23aa4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23aa4-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="23aa4-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="23aa4-105">Methods</span></span>  
 <span data-ttu-id="23aa4-106">A classe de serviço não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="23aa4-106">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="23aa4-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="23aa4-107">Properties</span></span>  
 <span data-ttu-id="23aa4-108">A classe de serviço tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="23aa4-108">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="23aa4-109">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="23aa4-109">BaseAddresses</span></span>  
 <span data-ttu-id="23aa4-110">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="23aa4-110">Data type: string array</span></span>  
  
 <span data-ttu-id="23aa4-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="23aa4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23aa4-112">Os endereços base usados pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="23aa4-112">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="23aa4-113">Comportamentos</span><span class="sxs-lookup"><span data-stu-id="23aa4-113">Behaviors</span></span>  
 <span data-ttu-id="23aa4-114">Tipo de dados: matriz de comportamento</span><span class="sxs-lookup"><span data-stu-id="23aa4-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="23aa4-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="23aa4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23aa4-116">Os comportamentos associados a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="23aa4-116">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="23aa4-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="23aa4-117">ConfigurationName</span></span>  
 <span data-ttu-id="23aa4-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="23aa4-118">Data type: string</span></span>  
  
 <span data-ttu-id="23aa4-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="23aa4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23aa4-120">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="23aa4-120">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="23aa4-121">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="23aa4-121">CounterInstanceName</span></span>  
 <span data-ttu-id="23aa4-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="23aa4-122">Data type: string</span></span>  
  
 <span data-ttu-id="23aa4-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="23aa4-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23aa4-124">Nome da instância da instância dos contadores de desempenho do serviço.</span><span class="sxs-lookup"><span data-stu-id="23aa4-124">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="23aa4-125">DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="23aa4-125">DistinguishedName</span></span>  
 <span data-ttu-id="23aa4-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="23aa4-126">Data type: string</span></span>  
  
 <span data-ttu-id="23aa4-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="23aa4-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23aa4-128">Nome do serviço no endereço.</span><span class="sxs-lookup"><span data-stu-id="23aa4-128">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="23aa4-129">Extensões</span><span class="sxs-lookup"><span data-stu-id="23aa4-129">Extensions</span></span>  
 <span data-ttu-id="23aa4-130">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="23aa4-130">Data type: string array</span></span>  
  
 <span data-ttu-id="23aa4-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="23aa4-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23aa4-132">Os contextos da instância para as extensões da instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="23aa4-132">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="23aa4-133">Metadados</span><span class="sxs-lookup"><span data-stu-id="23aa4-133">Metadata</span></span>  
 <span data-ttu-id="23aa4-134">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="23aa4-134">Data type: string array</span></span>  
  
 <span data-ttu-id="23aa4-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="23aa4-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23aa4-136">As definições de metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="23aa4-136">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="23aa4-137">Nome</span><span class="sxs-lookup"><span data-stu-id="23aa4-137">Name</span></span>  
 <span data-ttu-id="23aa4-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="23aa4-138">Data type: string</span></span>  
  
 <span data-ttu-id="23aa4-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="23aa4-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23aa4-140">O nome exclusivo desse serviço.</span><span class="sxs-lookup"><span data-stu-id="23aa4-140">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="23aa4-141">Namespace</span><span class="sxs-lookup"><span data-stu-id="23aa4-141">Namespace</span></span>  
 <span data-ttu-id="23aa4-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="23aa4-142">Data type: string</span></span>  
  
 <span data-ttu-id="23aa4-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="23aa4-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23aa4-144">O namespace do serviço.</span><span class="sxs-lookup"><span data-stu-id="23aa4-144">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="23aa4-145">Aberto</span><span class="sxs-lookup"><span data-stu-id="23aa4-145">Opened</span></span>  
 <span data-ttu-id="23aa4-146">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="23aa4-146">Data type: datetime</span></span>  
  
 <span data-ttu-id="23aa4-147">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="23aa4-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23aa4-148">A hora em que o serviço foi aberto.</span><span class="sxs-lookup"><span data-stu-id="23aa4-148">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="23aa4-149">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="23aa4-149">OutgoingChannels</span></span>  
 <span data-ttu-id="23aa4-150">Tipo de dados: matriz de canal</span><span class="sxs-lookup"><span data-stu-id="23aa4-150">Data type: Channel array</span></span>  
  
 <span data-ttu-id="23aa4-151">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="23aa4-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23aa4-152">Os canais que estão saindo da instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="23aa4-152">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="23aa4-153">ProcessId</span><span class="sxs-lookup"><span data-stu-id="23aa4-153">ProcessId</span></span>  
 <span data-ttu-id="23aa4-154">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="23aa4-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="23aa4-155">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="23aa4-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23aa4-156">A id de processo do processo que hospeda o serviço.</span><span class="sxs-lookup"><span data-stu-id="23aa4-156">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23aa4-157">Requisitos</span><span class="sxs-lookup"><span data-stu-id="23aa4-157">Requirements</span></span>  
  
|<span data-ttu-id="23aa4-158">MOF</span><span class="sxs-lookup"><span data-stu-id="23aa4-158">MOF</span></span>|<span data-ttu-id="23aa4-159">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="23aa4-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="23aa4-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="23aa4-160">Namespace</span></span>|<span data-ttu-id="23aa4-161">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="23aa4-161">Defined in root\ServiceModel</span></span>|
