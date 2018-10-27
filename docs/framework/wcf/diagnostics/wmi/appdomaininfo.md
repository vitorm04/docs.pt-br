---
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: 0b7f8aadbd9a9dfcdd33fc65be3a5a41ea95f5be
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50170218"
---
# <a name="appdomaininfo"></a><span data-ttu-id="edc87-102">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="edc87-102">AppDomainInfo</span></span>
<span data-ttu-id="edc87-103">Informações de domínio de aplicativo</span><span class="sxs-lookup"><span data-stu-id="edc87-103">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edc87-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="edc87-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="edc87-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="edc87-105">Methods</span></span>  
 <span data-ttu-id="edc87-106">A classe AppDomainInfo não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="edc87-106">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="edc87-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="edc87-107">Properties</span></span>  
 <span data-ttu-id="edc87-108">A classe AppDomainInfo tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="edc87-108">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="edc87-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="edc87-109">AppDomainId</span></span>  
 <span data-ttu-id="edc87-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="edc87-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="edc87-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="edc87-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="edc87-112">A Id do appdomain.</span><span class="sxs-lookup"><span data-stu-id="edc87-112">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="edc87-113">IsDefault</span><span class="sxs-lookup"><span data-stu-id="edc87-113">IsDefault</span></span>  
 <span data-ttu-id="edc87-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="edc87-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="edc87-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="edc87-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="edc87-116">Indica se o appdomain é o appdomain padrão.</span><span class="sxs-lookup"><span data-stu-id="edc87-116">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="edc87-117">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="edc87-117">LogMalformedMessages</span></span>  
 <span data-ttu-id="edc87-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="edc87-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="edc87-119">Tipo de acesso: leitura/gravação</span><span class="sxs-lookup"><span data-stu-id="edc87-119">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="edc87-120">Um valor que especifica se mensagens malformadas são registradas.</span><span class="sxs-lookup"><span data-stu-id="edc87-120">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="edc87-121">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="edc87-121">LogMessagesAtServiceLevel</span></span>  
 <span data-ttu-id="edc87-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="edc87-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="edc87-123">Tipo de acesso: leitura/gravação</span><span class="sxs-lookup"><span data-stu-id="edc87-123">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="edc87-124">Um valor que especifica se as mensagens são rastreadas no nível de serviço (antes da criptografia e transformações de transporte).</span><span class="sxs-lookup"><span data-stu-id="edc87-124">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="edc87-125">Logmessagesattransportlevel como</span><span class="sxs-lookup"><span data-stu-id="edc87-125">LogMessagesAtTransportLevel</span></span>  
 <span data-ttu-id="edc87-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="edc87-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="edc87-127">Tipo de acesso: leitura/gravação</span><span class="sxs-lookup"><span data-stu-id="edc87-127">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="edc87-128">Um valor que especifica se as mensagens são rastreadas no nível do transporte.</span><span class="sxs-lookup"><span data-stu-id="edc87-128">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="edc87-129">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="edc87-129">MessageLoggingTraceListeners</span></span>  
 <span data-ttu-id="edc87-130">Tipo de dados: matriz TraceListener</span><span class="sxs-lookup"><span data-stu-id="edc87-130">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="edc87-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="edc87-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="edc87-132">Os ouvintes de rastreamento da coleção que escutam à origem de rastreamento System.Wmi.MessageLogging.</span><span class="sxs-lookup"><span data-stu-id="edc87-132">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="edc87-133">Nome</span><span class="sxs-lookup"><span data-stu-id="edc87-133">Name</span></span>  
 <span data-ttu-id="edc87-134">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="edc87-134">Data type: string</span></span>  
  
 <span data-ttu-id="edc87-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="edc87-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="edc87-136">O nome do appdomain.</span><span class="sxs-lookup"><span data-stu-id="edc87-136">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="edc87-137">PerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="edc87-137">PerformanceCounters</span></span>  
 <span data-ttu-id="edc87-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="edc87-138">Data type: string</span></span>  
  
 <span data-ttu-id="edc87-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="edc87-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="edc87-140">O escopo dos contadores de desempenho do Active Directory no appdomain.</span><span class="sxs-lookup"><span data-stu-id="edc87-140">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="edc87-141">ProcessId</span><span class="sxs-lookup"><span data-stu-id="edc87-141">ProcessId</span></span>  
 <span data-ttu-id="edc87-142">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="edc87-142">Data type: sint32</span></span>  
  
 <span data-ttu-id="edc87-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="edc87-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="edc87-144">O processo de identificação.</span><span class="sxs-lookup"><span data-stu-id="edc87-144">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="edc87-145">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="edc87-145">ServiceConfigPath</span></span>  
 <span data-ttu-id="edc87-146">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="edc87-146">Data type: string</span></span>  
  
 <span data-ttu-id="edc87-147">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="edc87-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="edc87-148">O caminho para a configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="edc87-148">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="edc87-149">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="edc87-149">TraceLevel</span></span>  
 <span data-ttu-id="edc87-150">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="edc87-150">Data type: string</span></span>  
  
 <span data-ttu-id="edc87-151">Tipo de acesso: leitura/gravação</span><span class="sxs-lookup"><span data-stu-id="edc87-151">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="edc87-152">O nível de rastreamento da origem de rastreamento de System.</span><span class="sxs-lookup"><span data-stu-id="edc87-152">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="edc87-153">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="edc87-153">ServiceModelTraceListeners</span></span>  
 <span data-ttu-id="edc87-154">Tipo de dados: matriz TraceListener</span><span class="sxs-lookup"><span data-stu-id="edc87-154">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="edc87-155">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="edc87-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="edc87-156">Uma coleção de ouvintes da origem de rastreamento de System. ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="edc87-156">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edc87-157">Requisitos</span><span class="sxs-lookup"><span data-stu-id="edc87-157">Requirements</span></span>  
  
|<span data-ttu-id="edc87-158">MOF</span><span class="sxs-lookup"><span data-stu-id="edc87-158">MOF</span></span>|<span data-ttu-id="edc87-159">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="edc87-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="edc87-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="edc87-160">Namespace</span></span>|<span data-ttu-id="edc87-161">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="edc87-161">Defined in root\ServiceModel</span></span>|
