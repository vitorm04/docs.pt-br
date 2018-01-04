---
title: AppDomainInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed5053dd69628a9f5ff7318ce7fe772f42de6e24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="appdomaininfo"></a><span data-ttu-id="0910a-102">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="0910a-102">AppDomainInfo</span></span>
<span data-ttu-id="0910a-103">Informações de domínio de aplicativo</span><span class="sxs-lookup"><span data-stu-id="0910a-103">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0910a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0910a-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="0910a-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="0910a-105">Methods</span></span>  
 <span data-ttu-id="0910a-106">A classe AppDomainInfo não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="0910a-106">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0910a-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="0910a-107">Properties</span></span>  
 <span data-ttu-id="0910a-108">A classe AppDomainInfo tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="0910a-108">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="0910a-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="0910a-109">AppDomainId</span></span>  
 <span data-ttu-id="0910a-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="0910a-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="0910a-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0910a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0910a-112">A identificação do appdomain.</span><span class="sxs-lookup"><span data-stu-id="0910a-112">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="0910a-113">IsDefault</span><span class="sxs-lookup"><span data-stu-id="0910a-113">IsDefault</span></span>  
 <span data-ttu-id="0910a-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="0910a-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="0910a-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0910a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0910a-116">Indica se o appdomain é o appdomain padrão.</span><span class="sxs-lookup"><span data-stu-id="0910a-116">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="0910a-117">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="0910a-117">LogMalformedMessages</span></span>  
 <span data-ttu-id="0910a-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="0910a-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="0910a-119">Tipo de acesso: leitura/gravação</span><span class="sxs-lookup"><span data-stu-id="0910a-119">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="0910a-120">Um valor que especifica se as mensagens malformadas são registradas.</span><span class="sxs-lookup"><span data-stu-id="0910a-120">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="0910a-121">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="0910a-121">LogMessagesAtServiceLevel</span></span>  
 <span data-ttu-id="0910a-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="0910a-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="0910a-123">Tipo de acesso: leitura/gravação</span><span class="sxs-lookup"><span data-stu-id="0910a-123">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="0910a-124">Um valor que especifica se as mensagens são rastreadas no nível de serviço (antes da criptografia e transformações relacionadas de transporte).</span><span class="sxs-lookup"><span data-stu-id="0910a-124">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="0910a-125">Logmessagesattransportlevel como</span><span class="sxs-lookup"><span data-stu-id="0910a-125">LogMessagesAtTransportLevel</span></span>  
 <span data-ttu-id="0910a-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="0910a-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="0910a-127">Tipo de acesso: leitura/gravação</span><span class="sxs-lookup"><span data-stu-id="0910a-127">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="0910a-128">Um valor que especifica se as mensagens são rastreadas no nível do transporte.</span><span class="sxs-lookup"><span data-stu-id="0910a-128">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="0910a-129">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="0910a-129">MessageLoggingTraceListeners</span></span>  
 <span data-ttu-id="0910a-130">Tipo de dados: matriz TraceListener</span><span class="sxs-lookup"><span data-stu-id="0910a-130">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="0910a-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0910a-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0910a-132">Os ouvintes de rastreamento de coleção que ouvem a origem de rastreamento de System.Wmi.MessageLogging.</span><span class="sxs-lookup"><span data-stu-id="0910a-132">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="0910a-133">Nome</span><span class="sxs-lookup"><span data-stu-id="0910a-133">Name</span></span>  
 <span data-ttu-id="0910a-134">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="0910a-134">Data type: string</span></span>  
  
 <span data-ttu-id="0910a-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0910a-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0910a-136">O nome do appdomain.</span><span class="sxs-lookup"><span data-stu-id="0910a-136">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="0910a-137">performanceCounters</span><span class="sxs-lookup"><span data-stu-id="0910a-137">PerformanceCounters</span></span>  
 <span data-ttu-id="0910a-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="0910a-138">Data type: string</span></span>  
  
 <span data-ttu-id="0910a-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0910a-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0910a-140">O escopo dos contadores de desempenho ativos no appdomain.</span><span class="sxs-lookup"><span data-stu-id="0910a-140">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="0910a-141">ProcessId</span><span class="sxs-lookup"><span data-stu-id="0910a-141">ProcessId</span></span>  
 <span data-ttu-id="0910a-142">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="0910a-142">Data type: sint32</span></span>  
  
 <span data-ttu-id="0910a-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0910a-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0910a-144">O processo de identificação.</span><span class="sxs-lookup"><span data-stu-id="0910a-144">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="0910a-145">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="0910a-145">ServiceConfigPath</span></span>  
 <span data-ttu-id="0910a-146">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="0910a-146">Data type: string</span></span>  
  
 <span data-ttu-id="0910a-147">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0910a-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0910a-148">O caminho para a configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="0910a-148">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="0910a-149">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="0910a-149">TraceLevel</span></span>  
 <span data-ttu-id="0910a-150">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="0910a-150">Data type: string</span></span>  
  
 <span data-ttu-id="0910a-151">Tipo de acesso: leitura/gravação</span><span class="sxs-lookup"><span data-stu-id="0910a-151">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="0910a-152">O nível de rastreamento da origem de rastreamento de System.</span><span class="sxs-lookup"><span data-stu-id="0910a-152">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="0910a-153">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="0910a-153">ServiceModelTraceListeners</span></span>  
 <span data-ttu-id="0910a-154">Tipo de dados: matriz TraceListener</span><span class="sxs-lookup"><span data-stu-id="0910a-154">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="0910a-155">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0910a-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0910a-156">Uma coleção de ouvintes da origem de rastreamento de System. ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="0910a-156">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0910a-157">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0910a-157">Requirements</span></span>  
  
|<span data-ttu-id="0910a-158">MOF</span><span class="sxs-lookup"><span data-stu-id="0910a-158">MOF</span></span>|<span data-ttu-id="0910a-159">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="0910a-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0910a-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="0910a-160">Namespace</span></span>|<span data-ttu-id="0910a-161">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0910a-161">Defined in root\ServiceModel</span></span>|
