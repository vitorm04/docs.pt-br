---
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
ms.openlocfilehash: 15304630eb8a14e01d4815ddddc84cd32796fdcf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963443"
---
# <a name="localservicesecuritysettings"></a><span data-ttu-id="e5f0e-102">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="e5f0e-102">LocalServiceSecuritySettings</span></span>
<span data-ttu-id="e5f0e-103">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="e5f0e-103">LocalServiceSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5f0e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e5f0e-104">Syntax</span></span>  
  
```csharp
class LocalServiceSecuritySettings  
{  
  boolean DetectReplays;  
  datetime InactivityTimeout;  
  datetime IssuedCookieLifetime;  
  sint32 MaxCachedCookies;  
  datetime MaxClockSkew;  
  sint32 MaxPendingSessions;  
  sint32 MaxStatefulNegotiations;  
  datetime NegotiationTimeout;  
  boolean ReconnectTransportOnFailure;  
  sint32 ReplayCacheSize;  
  datetime ReplayWindow;  
  datetime SessionKeyRenewalInterval;  
  datetime SessionKeyRolloverInterval;  
  datetime TimestampValidityDuration;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e5f0e-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="e5f0e-105">Methods</span></span>  
 <span data-ttu-id="e5f0e-106">A classe LocalServiceSecuritySettings não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="e5f0e-106">The LocalServiceSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e5f0e-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e5f0e-107">Properties</span></span>  
 <span data-ttu-id="e5f0e-108">A classe LocalServiceSecuritySettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="e5f0e-108">The LocalServiceSecuritySettings class has the following properties:</span></span>  
  
### <a name="detectreplays"></a><span data-ttu-id="e5f0e-109">DetectReplays</span><span class="sxs-lookup"><span data-stu-id="e5f0e-109">DetectReplays</span></span>  
 <span data-ttu-id="e5f0e-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="e5f0e-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="e5f0e-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e5f0e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5f0e-112">Um valor booliano que especifica se os ataques de reprodução contra o canal são detectados e tratados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e5f0e-112">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="e5f0e-113">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="e5f0e-113">InactivityTimeout</span></span>  
 <span data-ttu-id="e5f0e-114">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="e5f0e-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="e5f0e-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e5f0e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5f0e-116">O número máximo de sessões de segurança que o serviço suporta pendentes.</span><span class="sxs-lookup"><span data-stu-id="e5f0e-116">The maximum number of pending security sessions that the service supports.</span></span>  
  
### <a name="issuedcookielifetime"></a><span data-ttu-id="e5f0e-117">IssuedCookieLifetime</span><span class="sxs-lookup"><span data-stu-id="e5f0e-117">IssuedCookieLifetime</span></span>  
 <span data-ttu-id="e5f0e-118">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="e5f0e-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="e5f0e-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e5f0e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5f0e-120">Um TimeSpan que especifica o tempo de vida emitido a todos os novos cookies de segurança.</span><span class="sxs-lookup"><span data-stu-id="e5f0e-120">A TimeSpan that specifies the lifetime issued to all new security cookies.</span></span>  
  
### <a name="maxcachedcookies"></a><span data-ttu-id="e5f0e-121">MaxCachedCookies</span><span class="sxs-lookup"><span data-stu-id="e5f0e-121">MaxCachedCookies</span></span>  
 <span data-ttu-id="e5f0e-122">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="e5f0e-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="e5f0e-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e5f0e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5f0e-124">O número máximo de cookies que podem ser armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="e5f0e-124">The maximum number of cookies that can be cached.</span></span>  
  
### <a name="maxclockskew"></a><span data-ttu-id="e5f0e-125">MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="e5f0e-125">MaxClockSkew</span></span>  
 <span data-ttu-id="e5f0e-126">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="e5f0e-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="e5f0e-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e5f0e-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5f0e-128">Um TimeSpan que especifica a diferença máxima de tempo entre os relógios do sistema das duas partes da comunicação.</span><span class="sxs-lookup"><span data-stu-id="e5f0e-128">A TimeSpan that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span>  
  
### <a name="maxpendingsessions"></a><span data-ttu-id="e5f0e-129">MaxPendingSessions</span><span class="sxs-lookup"><span data-stu-id="e5f0e-129">MaxPendingSessions</span></span>  
 <span data-ttu-id="e5f0e-130">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="e5f0e-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="e5f0e-131">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e5f0e-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5f0e-132">O número máximo de conexões pendentes no serviço.</span><span class="sxs-lookup"><span data-stu-id="e5f0e-132">The maximum number of pending connections on the service.</span></span>  
  
### <a name="maxstatefulnegotiations"></a><span data-ttu-id="e5f0e-133">MaxStatefulNegotiations</span><span class="sxs-lookup"><span data-stu-id="e5f0e-133">MaxStatefulNegotiations</span></span>  
 <span data-ttu-id="e5f0e-134">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="e5f0e-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="e5f0e-135">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e5f0e-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5f0e-136">O número de negociações de segurança que podem estar ativas simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="e5f0e-136">The number of security negotiations that can be active concurrently.</span></span>  
  
### <a name="negotiationtimeout"></a><span data-ttu-id="e5f0e-137">NegotiationTimeout</span><span class="sxs-lookup"><span data-stu-id="e5f0e-137">NegotiationTimeout</span></span>  
 <span data-ttu-id="e5f0e-138">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="e5f0e-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="e5f0e-139">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e5f0e-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5f0e-140">Um TimeSpan que especifica a duração máxima para a fase de negociação de segurança entre cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="e5f0e-140">A TimeSpan that specifies the maximum duration for the security negotiation phase between server and client.</span></span>  
  
### <a name="reconnecttransportonfailure"></a><span data-ttu-id="e5f0e-141">ReconnectTransportOnFailure</span><span class="sxs-lookup"><span data-stu-id="e5f0e-141">ReconnectTransportOnFailure</span></span>  
 <span data-ttu-id="e5f0e-142">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="e5f0e-142">Data type: boolean</span></span>  
  
 <span data-ttu-id="e5f0e-143">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e5f0e-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5f0e-144">Um valor booliano que especifica se as conexões que usam mensagens WS-Reliable tentam se reconectar após falhas de transporte.</span><span class="sxs-lookup"><span data-stu-id="e5f0e-144">A Boolean value that specifies whether connections using WS-Reliable messaging attempt to reconnect after transport failures.</span></span>  
  
### <a name="replaycachesize"></a><span data-ttu-id="e5f0e-145">ReplayCacheSize</span><span class="sxs-lookup"><span data-stu-id="e5f0e-145">ReplayCacheSize</span></span>  
 <span data-ttu-id="e5f0e-146">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="e5f0e-146">Data type: sint32</span></span>  
  
 <span data-ttu-id="e5f0e-147">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e5f0e-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5f0e-148">O número de nonces armazenados em cache usados para detecção de reprodução.</span><span class="sxs-lookup"><span data-stu-id="e5f0e-148">The number of cached nonces used for replay detection.</span></span>  
  
### <a name="replaywindow"></a><span data-ttu-id="e5f0e-149">ReplayWindow</span><span class="sxs-lookup"><span data-stu-id="e5f0e-149">ReplayWindow</span></span>  
 <span data-ttu-id="e5f0e-150">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="e5f0e-150">Data type: datetime</span></span>  
  
 <span data-ttu-id="e5f0e-151">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e5f0e-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5f0e-152">Um TimeSpan que especifica a duração na qual nonces de mensagens individuais são válidos.</span><span class="sxs-lookup"><span data-stu-id="e5f0e-152">A TimeSpan that specifies the duration in which individual message nonces are valid.</span></span>  
  
### <a name="sessionkeyrenewalinterval"></a><span data-ttu-id="e5f0e-153">SessionKeyRenewalInterval</span><span class="sxs-lookup"><span data-stu-id="e5f0e-153">SessionKeyRenewalInterval</span></span>  
 <span data-ttu-id="e5f0e-154">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="e5f0e-154">Data type: datetime</span></span>  
  
 <span data-ttu-id="e5f0e-155">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e5f0e-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5f0e-156">Um TimeSpan que especifica a duração após a qual o iniciador renova a chave da sessão de segurança.</span><span class="sxs-lookup"><span data-stu-id="e5f0e-156">A TimeSpan that specifies the duration after which the initiator renews the key for the security session.</span></span>  
  
### <a name="sessionkeyrolloverinterval"></a><span data-ttu-id="e5f0e-157">SessionKeyRolloverInterval</span><span class="sxs-lookup"><span data-stu-id="e5f0e-157">SessionKeyRolloverInterval</span></span>  
 <span data-ttu-id="e5f0e-158">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="e5f0e-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="e5f0e-159">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e5f0e-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5f0e-160">Um TimeSpan que especifica o intervalo de tempo uma chave de sessão anterior é válida nas mensagens de entrada durante uma renovação de chave.</span><span class="sxs-lookup"><span data-stu-id="e5f0e-160">A TimeSpan that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span>  
  
### <a name="timestampvalidityduration"></a><span data-ttu-id="e5f0e-161">TimestampValidityDuration</span><span class="sxs-lookup"><span data-stu-id="e5f0e-161">TimestampValidityDuration</span></span>  
 <span data-ttu-id="e5f0e-162">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="e5f0e-162">Data type: datetime</span></span>  
  
 <span data-ttu-id="e5f0e-163">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e5f0e-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5f0e-164">Um TimeSpan que especifica a duração em que um carimbo de data / hora é válido.</span><span class="sxs-lookup"><span data-stu-id="e5f0e-164">A TimeSpan that specifies the duration in which a time stamp is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5f0e-165">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e5f0e-165">Requirements</span></span>  
  
|<span data-ttu-id="e5f0e-166">MOF</span><span class="sxs-lookup"><span data-stu-id="e5f0e-166">MOF</span></span>|<span data-ttu-id="e5f0e-167">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e5f0e-167">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e5f0e-168">Namespace</span><span class="sxs-lookup"><span data-stu-id="e5f0e-168">Namespace</span></span>|<span data-ttu-id="e5f0e-169">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e5f0e-169">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5f0e-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5f0e-170">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
