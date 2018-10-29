---
title: Serviço
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: c59672b3b7617d9c28d99f7d534b6e7f2f2e9fbb
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50196902"
---
# <a name="service"></a><span data-ttu-id="10c2e-102">Serviço</span><span class="sxs-lookup"><span data-stu-id="10c2e-102">Service</span></span>
<span data-ttu-id="10c2e-103">Serviço</span><span class="sxs-lookup"><span data-stu-id="10c2e-103">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10c2e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10c2e-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="10c2e-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="10c2e-105">Methods</span></span>  
 <span data-ttu-id="10c2e-106">A classe de serviço não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="10c2e-106">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="10c2e-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="10c2e-107">Properties</span></span>  
 <span data-ttu-id="10c2e-108">A classe de serviço tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="10c2e-108">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="10c2e-109">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="10c2e-109">BaseAddresses</span></span>  
 <span data-ttu-id="10c2e-110">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="10c2e-110">Data type: string array</span></span>  
  
 <span data-ttu-id="10c2e-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="10c2e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10c2e-112">Os endereços base usados pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="10c2e-112">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="10c2e-113">Comportamentos</span><span class="sxs-lookup"><span data-stu-id="10c2e-113">Behaviors</span></span>  
 <span data-ttu-id="10c2e-114">Tipo de dados: matriz de comportamento</span><span class="sxs-lookup"><span data-stu-id="10c2e-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="10c2e-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="10c2e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10c2e-116">Os comportamentos associados a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="10c2e-116">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="10c2e-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="10c2e-117">ConfigurationName</span></span>  
 <span data-ttu-id="10c2e-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="10c2e-118">Data type: string</span></span>  
  
 <span data-ttu-id="10c2e-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="10c2e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10c2e-120">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="10c2e-120">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="10c2e-121">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="10c2e-121">CounterInstanceName</span></span>  
 <span data-ttu-id="10c2e-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="10c2e-122">Data type: string</span></span>  
  
 <span data-ttu-id="10c2e-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="10c2e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10c2e-124">Nome da instância da instância dos contadores de desempenho do serviço.</span><span class="sxs-lookup"><span data-stu-id="10c2e-124">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="10c2e-125">DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="10c2e-125">DistinguishedName</span></span>  
 <span data-ttu-id="10c2e-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="10c2e-126">Data type: string</span></span>  
  
 <span data-ttu-id="10c2e-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="10c2e-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10c2e-128">Nome do serviço no endereço.</span><span class="sxs-lookup"><span data-stu-id="10c2e-128">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="10c2e-129">Extensões</span><span class="sxs-lookup"><span data-stu-id="10c2e-129">Extensions</span></span>  
 <span data-ttu-id="10c2e-130">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="10c2e-130">Data type: string array</span></span>  
  
 <span data-ttu-id="10c2e-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="10c2e-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10c2e-132">Os contextos de instância para as extensões da instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="10c2e-132">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="10c2e-133">Metadados</span><span class="sxs-lookup"><span data-stu-id="10c2e-133">Metadata</span></span>  
 <span data-ttu-id="10c2e-134">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="10c2e-134">Data type: string array</span></span>  
  
 <span data-ttu-id="10c2e-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="10c2e-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10c2e-136">As definições de metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="10c2e-136">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="10c2e-137">Nome</span><span class="sxs-lookup"><span data-stu-id="10c2e-137">Name</span></span>  
 <span data-ttu-id="10c2e-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="10c2e-138">Data type: string</span></span>  
  
 <span data-ttu-id="10c2e-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="10c2e-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10c2e-140">O nome exclusivo deste serviço.</span><span class="sxs-lookup"><span data-stu-id="10c2e-140">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="10c2e-141">Namespace</span><span class="sxs-lookup"><span data-stu-id="10c2e-141">Namespace</span></span>  
 <span data-ttu-id="10c2e-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="10c2e-142">Data type: string</span></span>  
  
 <span data-ttu-id="10c2e-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="10c2e-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10c2e-144">O namespace do serviço.</span><span class="sxs-lookup"><span data-stu-id="10c2e-144">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="10c2e-145">Aberto</span><span class="sxs-lookup"><span data-stu-id="10c2e-145">Opened</span></span>  
 <span data-ttu-id="10c2e-146">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="10c2e-146">Data type: datetime</span></span>  
  
 <span data-ttu-id="10c2e-147">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="10c2e-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10c2e-148">A hora em que o serviço foi aberto.</span><span class="sxs-lookup"><span data-stu-id="10c2e-148">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="10c2e-149">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="10c2e-149">OutgoingChannels</span></span>  
 <span data-ttu-id="10c2e-150">Tipo de dados: matriz de canal</span><span class="sxs-lookup"><span data-stu-id="10c2e-150">Data type: Channel array</span></span>  
  
 <span data-ttu-id="10c2e-151">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="10c2e-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10c2e-152">Os canais que estão saindo da instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="10c2e-152">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="10c2e-153">ProcessId</span><span class="sxs-lookup"><span data-stu-id="10c2e-153">ProcessId</span></span>  
 <span data-ttu-id="10c2e-154">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="10c2e-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="10c2e-155">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="10c2e-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10c2e-156">A id do processo do processo que hospeda o serviço.</span><span class="sxs-lookup"><span data-stu-id="10c2e-156">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10c2e-157">Requisitos</span><span class="sxs-lookup"><span data-stu-id="10c2e-157">Requirements</span></span>  
  
|<span data-ttu-id="10c2e-158">MOF</span><span class="sxs-lookup"><span data-stu-id="10c2e-158">MOF</span></span>|<span data-ttu-id="10c2e-159">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="10c2e-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="10c2e-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="10c2e-160">Namespace</span></span>|<span data-ttu-id="10c2e-161">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="10c2e-161">Defined in root\ServiceModel</span></span>|
