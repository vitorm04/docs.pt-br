---
title: Serviço
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: c59672b3b7617d9c28d99f7d534b6e7f2f2e9fbb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991439"
---
# <a name="service"></a><span data-ttu-id="d0f9b-102">Serviço</span><span class="sxs-lookup"><span data-stu-id="d0f9b-102">Service</span></span>
<span data-ttu-id="d0f9b-103">Serviço</span><span class="sxs-lookup"><span data-stu-id="d0f9b-103">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0f9b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0f9b-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="d0f9b-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="d0f9b-105">Methods</span></span>  
 <span data-ttu-id="d0f9b-106">A classe de serviço não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="d0f9b-106">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d0f9b-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d0f9b-107">Properties</span></span>  
 <span data-ttu-id="d0f9b-108">A classe de serviço tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="d0f9b-108">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="d0f9b-109">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="d0f9b-109">BaseAddresses</span></span>  
 <span data-ttu-id="d0f9b-110">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="d0f9b-110">Data type: string array</span></span>  
  
 <span data-ttu-id="d0f9b-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="d0f9b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0f9b-112">Os endereços base usados pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="d0f9b-112">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="d0f9b-113">Comportamentos</span><span class="sxs-lookup"><span data-stu-id="d0f9b-113">Behaviors</span></span>  
 <span data-ttu-id="d0f9b-114">Tipo de dados: Matriz de comportamento</span><span class="sxs-lookup"><span data-stu-id="d0f9b-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="d0f9b-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="d0f9b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0f9b-116">Os comportamentos associados a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="d0f9b-116">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="d0f9b-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="d0f9b-117">ConfigurationName</span></span>  
 <span data-ttu-id="d0f9b-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="d0f9b-118">Data type: string</span></span>  
  
 <span data-ttu-id="d0f9b-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="d0f9b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0f9b-120">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="d0f9b-120">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="d0f9b-121">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="d0f9b-121">CounterInstanceName</span></span>  
 <span data-ttu-id="d0f9b-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="d0f9b-122">Data type: string</span></span>  
  
 <span data-ttu-id="d0f9b-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="d0f9b-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0f9b-124">Nome da instância da instância dos contadores de desempenho do serviço.</span><span class="sxs-lookup"><span data-stu-id="d0f9b-124">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="d0f9b-125">DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="d0f9b-125">DistinguishedName</span></span>  
 <span data-ttu-id="d0f9b-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="d0f9b-126">Data type: string</span></span>  
  
 <span data-ttu-id="d0f9b-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="d0f9b-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0f9b-128">Nome do serviço no endereço.</span><span class="sxs-lookup"><span data-stu-id="d0f9b-128">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="d0f9b-129">Extensões</span><span class="sxs-lookup"><span data-stu-id="d0f9b-129">Extensions</span></span>  
 <span data-ttu-id="d0f9b-130">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="d0f9b-130">Data type: string array</span></span>  
  
 <span data-ttu-id="d0f9b-131">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="d0f9b-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0f9b-132">Os contextos de instância para as extensões da instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="d0f9b-132">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="d0f9b-133">Metadados</span><span class="sxs-lookup"><span data-stu-id="d0f9b-133">Metadata</span></span>  
 <span data-ttu-id="d0f9b-134">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="d0f9b-134">Data type: string array</span></span>  
  
 <span data-ttu-id="d0f9b-135">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="d0f9b-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0f9b-136">As definições de metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="d0f9b-136">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="d0f9b-137">Nome</span><span class="sxs-lookup"><span data-stu-id="d0f9b-137">Name</span></span>  
 <span data-ttu-id="d0f9b-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="d0f9b-138">Data type: string</span></span>  
  
 <span data-ttu-id="d0f9b-139">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="d0f9b-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0f9b-140">O nome exclusivo deste serviço.</span><span class="sxs-lookup"><span data-stu-id="d0f9b-140">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="d0f9b-141">Namespace</span><span class="sxs-lookup"><span data-stu-id="d0f9b-141">Namespace</span></span>  
 <span data-ttu-id="d0f9b-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="d0f9b-142">Data type: string</span></span>  
  
 <span data-ttu-id="d0f9b-143">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="d0f9b-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0f9b-144">O namespace do serviço.</span><span class="sxs-lookup"><span data-stu-id="d0f9b-144">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="d0f9b-145">Aberto</span><span class="sxs-lookup"><span data-stu-id="d0f9b-145">Opened</span></span>  
 <span data-ttu-id="d0f9b-146">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="d0f9b-146">Data type: datetime</span></span>  
  
 <span data-ttu-id="d0f9b-147">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="d0f9b-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0f9b-148">A hora em que o serviço foi aberto.</span><span class="sxs-lookup"><span data-stu-id="d0f9b-148">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="d0f9b-149">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="d0f9b-149">OutgoingChannels</span></span>  
 <span data-ttu-id="d0f9b-150">Tipo de dados: Matriz de canal</span><span class="sxs-lookup"><span data-stu-id="d0f9b-150">Data type: Channel array</span></span>  
  
 <span data-ttu-id="d0f9b-151">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="d0f9b-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0f9b-152">Os canais que estão saindo da instância do serviço.</span><span class="sxs-lookup"><span data-stu-id="d0f9b-152">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="d0f9b-153">ProcessId</span><span class="sxs-lookup"><span data-stu-id="d0f9b-153">ProcessId</span></span>  
 <span data-ttu-id="d0f9b-154">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="d0f9b-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="d0f9b-155">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="d0f9b-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0f9b-156">A id do processo do processo que hospeda o serviço.</span><span class="sxs-lookup"><span data-stu-id="d0f9b-156">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0f9b-157">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d0f9b-157">Requirements</span></span>  
  
|<span data-ttu-id="d0f9b-158">MOF</span><span class="sxs-lookup"><span data-stu-id="d0f9b-158">MOF</span></span>|<span data-ttu-id="d0f9b-159">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d0f9b-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d0f9b-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="d0f9b-160">Namespace</span></span>|<span data-ttu-id="d0f9b-161">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d0f9b-161">Defined in root\ServiceModel</span></span>|
