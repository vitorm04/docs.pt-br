---
title: Serviço
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: c59672b3b7617d9c28d99f7d534b6e7f2f2e9fbb
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49374203"
---
# <a name="service"></a><span data-ttu-id="915c7-102">Serviço</span><span class="sxs-lookup"><span data-stu-id="915c7-102">Service</span></span>
<span data-ttu-id="915c7-103">Serviço</span><span class="sxs-lookup"><span data-stu-id="915c7-103">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="915c7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="915c7-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="915c7-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="915c7-105">Methods</span></span>  
 <span data-ttu-id="915c7-106">A classe de serviço não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="915c7-106">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="915c7-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="915c7-107">Properties</span></span>  
 <span data-ttu-id="915c7-108">A classe de serviço tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="915c7-108">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="915c7-109">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="915c7-109">BaseAddresses</span></span>  
 <span data-ttu-id="915c7-110">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="915c7-110">Data type: string array</span></span>  
  
 <span data-ttu-id="915c7-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="915c7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="915c7-112">Os endereços base usados pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="915c7-112">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="915c7-113">Comportamentos</span><span class="sxs-lookup"><span data-stu-id="915c7-113">Behaviors</span></span>  
 <span data-ttu-id="915c7-114">Tipo de dados: matriz de comportamento</span><span class="sxs-lookup"><span data-stu-id="915c7-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="915c7-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="915c7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="915c7-116">Os comportamentos associados a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="915c7-116">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="915c7-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="915c7-117">ConfigurationName</span></span>  
 <span data-ttu-id="915c7-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="915c7-118">Data type: string</span></span>  
  
 <span data-ttu-id="915c7-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="915c7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="915c7-120">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="915c7-120">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="915c7-121">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="915c7-121">CounterInstanceName</span></span>  
 <span data-ttu-id="915c7-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="915c7-122">Data type: string</span></span>  
  
 <span data-ttu-id="915c7-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="915c7-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="915c7-124">Nome da instância da instância dos contadores de desempenho do serviço.</span><span class="sxs-lookup"><span data-stu-id="915c7-124">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="915c7-125">DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="915c7-125">DistinguishedName</span></span>  
 <span data-ttu-id="915c7-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="915c7-126">Data type: string</span></span>  
  
 <span data-ttu-id="915c7-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="915c7-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="915c7-128">Nome do serviço no endereço.</span><span class="sxs-lookup"><span data-stu-id="915c7-128">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="915c7-129">Extensões</span><span class="sxs-lookup"><span data-stu-id="915c7-129">Extensions</span></span>  
 <span data-ttu-id="915c7-130">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="915c7-130">Data type: string array</span></span>  
  
 <span data-ttu-id="915c7-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="915c7-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="915c7-132">Os contextos de instância para as extensões da instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="915c7-132">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="915c7-133">Metadados</span><span class="sxs-lookup"><span data-stu-id="915c7-133">Metadata</span></span>  
 <span data-ttu-id="915c7-134">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="915c7-134">Data type: string array</span></span>  
  
 <span data-ttu-id="915c7-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="915c7-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="915c7-136">As definições de metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="915c7-136">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="915c7-137">Nome</span><span class="sxs-lookup"><span data-stu-id="915c7-137">Name</span></span>  
 <span data-ttu-id="915c7-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="915c7-138">Data type: string</span></span>  
  
 <span data-ttu-id="915c7-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="915c7-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="915c7-140">O nome exclusivo deste serviço.</span><span class="sxs-lookup"><span data-stu-id="915c7-140">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="915c7-141">Namespace</span><span class="sxs-lookup"><span data-stu-id="915c7-141">Namespace</span></span>  
 <span data-ttu-id="915c7-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="915c7-142">Data type: string</span></span>  
  
 <span data-ttu-id="915c7-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="915c7-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="915c7-144">O namespace do serviço.</span><span class="sxs-lookup"><span data-stu-id="915c7-144">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="915c7-145">Aberto</span><span class="sxs-lookup"><span data-stu-id="915c7-145">Opened</span></span>  
 <span data-ttu-id="915c7-146">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="915c7-146">Data type: datetime</span></span>  
  
 <span data-ttu-id="915c7-147">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="915c7-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="915c7-148">A hora em que o serviço foi aberto.</span><span class="sxs-lookup"><span data-stu-id="915c7-148">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="915c7-149">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="915c7-149">OutgoingChannels</span></span>  
 <span data-ttu-id="915c7-150">Tipo de dados: matriz de canal</span><span class="sxs-lookup"><span data-stu-id="915c7-150">Data type: Channel array</span></span>  
  
 <span data-ttu-id="915c7-151">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="915c7-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="915c7-152">Os canais que estão saindo da instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="915c7-152">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="915c7-153">ProcessId</span><span class="sxs-lookup"><span data-stu-id="915c7-153">ProcessId</span></span>  
 <span data-ttu-id="915c7-154">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="915c7-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="915c7-155">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="915c7-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="915c7-156">A id do processo do processo que hospeda o serviço.</span><span class="sxs-lookup"><span data-stu-id="915c7-156">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="915c7-157">Requisitos</span><span class="sxs-lookup"><span data-stu-id="915c7-157">Requirements</span></span>  
  
|<span data-ttu-id="915c7-158">MOF</span><span class="sxs-lookup"><span data-stu-id="915c7-158">MOF</span></span>|<span data-ttu-id="915c7-159">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="915c7-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="915c7-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="915c7-160">Namespace</span></span>|<span data-ttu-id="915c7-161">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="915c7-161">Defined in root\ServiceModel</span></span>|
