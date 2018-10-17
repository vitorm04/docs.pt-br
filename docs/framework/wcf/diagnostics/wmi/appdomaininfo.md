---
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: 0b7f8aadbd9a9dfcdd33fc65be3a5a41ea95f5be
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49371570"
---
# <a name="appdomaininfo"></a><span data-ttu-id="18338-102">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="18338-102">AppDomainInfo</span></span>
<span data-ttu-id="18338-103">Informações de domínio de aplicativo</span><span class="sxs-lookup"><span data-stu-id="18338-103">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18338-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="18338-104">Syntax</span></span>  
  
```csharp
class AppDomainInfo  
{  
  sint32 AppDomainId;  
  boolean IsDefault;  
  boolean LogMalformedMessages;  
  boolean LogMessagesAtServiceLevel;  
  boolean LogMessagesAtTransportLevel;  
  TraceListener MessageLoggingTraceListeners[];  
  string Name;  
  string PerformanceCounters;  
  sint32 ProcessId;  
  string ServiceConfigPath;  
  string TraceLevel;  
  TraceListener wmiTraceListeners[];  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="18338-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="18338-105">Methods</span></span>  
 <span data-ttu-id="18338-106">A classe AppDomainInfo não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="18338-106">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="18338-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="18338-107">Properties</span></span>  
 <span data-ttu-id="18338-108">A classe AppDomainInfo tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="18338-108">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="18338-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="18338-109">AppDomainId</span></span>  
 <span data-ttu-id="18338-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="18338-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="18338-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="18338-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18338-112">A Id do appdomain.</span><span class="sxs-lookup"><span data-stu-id="18338-112">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="18338-113">IsDefault</span><span class="sxs-lookup"><span data-stu-id="18338-113">IsDefault</span></span>  
 <span data-ttu-id="18338-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="18338-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="18338-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="18338-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18338-116">Indica se o appdomain é o appdomain padrão.</span><span class="sxs-lookup"><span data-stu-id="18338-116">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="18338-117">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="18338-117">LogMalformedMessages</span></span>  
 <span data-ttu-id="18338-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="18338-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="18338-119">Tipo de acesso: leitura/gravação</span><span class="sxs-lookup"><span data-stu-id="18338-119">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="18338-120">Um valor que especifica se mensagens malformadas são registradas.</span><span class="sxs-lookup"><span data-stu-id="18338-120">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="18338-121">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="18338-121">LogMessagesAtServiceLevel</span></span>  
 <span data-ttu-id="18338-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="18338-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="18338-123">Tipo de acesso: leitura/gravação</span><span class="sxs-lookup"><span data-stu-id="18338-123">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="18338-124">Um valor que especifica se as mensagens são rastreadas no nível de serviço (antes da criptografia e transformações de transporte).</span><span class="sxs-lookup"><span data-stu-id="18338-124">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="18338-125">Logmessagesattransportlevel como</span><span class="sxs-lookup"><span data-stu-id="18338-125">LogMessagesAtTransportLevel</span></span>  
 <span data-ttu-id="18338-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="18338-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="18338-127">Tipo de acesso: leitura/gravação</span><span class="sxs-lookup"><span data-stu-id="18338-127">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="18338-128">Um valor que especifica se as mensagens são rastreadas no nível do transporte.</span><span class="sxs-lookup"><span data-stu-id="18338-128">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="18338-129">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="18338-129">MessageLoggingTraceListeners</span></span>  
 <span data-ttu-id="18338-130">Tipo de dados: matriz TraceListener</span><span class="sxs-lookup"><span data-stu-id="18338-130">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="18338-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="18338-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18338-132">Os ouvintes de rastreamento da coleção que escutam à origem de rastreamento System.Wmi.MessageLogging.</span><span class="sxs-lookup"><span data-stu-id="18338-132">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="18338-133">Nome</span><span class="sxs-lookup"><span data-stu-id="18338-133">Name</span></span>  
 <span data-ttu-id="18338-134">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="18338-134">Data type: string</span></span>  
  
 <span data-ttu-id="18338-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="18338-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18338-136">O nome do appdomain.</span><span class="sxs-lookup"><span data-stu-id="18338-136">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="18338-137">PerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="18338-137">PerformanceCounters</span></span>  
 <span data-ttu-id="18338-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="18338-138">Data type: string</span></span>  
  
 <span data-ttu-id="18338-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="18338-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18338-140">O escopo dos contadores de desempenho do Active Directory no appdomain.</span><span class="sxs-lookup"><span data-stu-id="18338-140">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="18338-141">ProcessId</span><span class="sxs-lookup"><span data-stu-id="18338-141">ProcessId</span></span>  
 <span data-ttu-id="18338-142">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="18338-142">Data type: sint32</span></span>  
  
 <span data-ttu-id="18338-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="18338-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18338-144">O processo de identificação.</span><span class="sxs-lookup"><span data-stu-id="18338-144">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="18338-145">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="18338-145">ServiceConfigPath</span></span>  
 <span data-ttu-id="18338-146">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="18338-146">Data type: string</span></span>  
  
 <span data-ttu-id="18338-147">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="18338-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18338-148">O caminho para a configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="18338-148">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="18338-149">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="18338-149">TraceLevel</span></span>  
 <span data-ttu-id="18338-150">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="18338-150">Data type: string</span></span>  
  
 <span data-ttu-id="18338-151">Tipo de acesso: leitura/gravação</span><span class="sxs-lookup"><span data-stu-id="18338-151">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="18338-152">O nível de rastreamento da origem de rastreamento de System.</span><span class="sxs-lookup"><span data-stu-id="18338-152">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="18338-153">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="18338-153">ServiceModelTraceListeners</span></span>  
 <span data-ttu-id="18338-154">Tipo de dados: matriz TraceListener</span><span class="sxs-lookup"><span data-stu-id="18338-154">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="18338-155">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="18338-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18338-156">Uma coleção de ouvintes da origem de rastreamento de System. ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="18338-156">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18338-157">Requisitos</span><span class="sxs-lookup"><span data-stu-id="18338-157">Requirements</span></span>  
  
|<span data-ttu-id="18338-158">MOF</span><span class="sxs-lookup"><span data-stu-id="18338-158">MOF</span></span>|<span data-ttu-id="18338-159">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="18338-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="18338-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="18338-160">Namespace</span></span>|<span data-ttu-id="18338-161">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="18338-161">Defined in root\ServiceModel</span></span>|
