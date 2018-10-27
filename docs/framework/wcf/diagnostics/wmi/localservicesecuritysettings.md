---
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
ms.openlocfilehash: c1f3abe2d016ccab9b136752c4b2e6697ca59e66
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188840"
---
# <a name="localservicesecuritysettings"></a><span data-ttu-id="2a768-102">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="2a768-102">LocalServiceSecuritySettings</span></span>
<span data-ttu-id="2a768-103">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="2a768-103">LocalServiceSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a768-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a768-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="2a768-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="2a768-105">Methods</span></span>  
 <span data-ttu-id="2a768-106">A classe LocalServiceSecuritySettings não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="2a768-106">The LocalServiceSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2a768-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="2a768-107">Properties</span></span>  
 <span data-ttu-id="2a768-108">A classe LocalServiceSecuritySettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="2a768-108">The LocalServiceSecuritySettings class has the following properties:</span></span>  
  
### <a name="detectreplays"></a><span data-ttu-id="2a768-109">DetectReplays</span><span class="sxs-lookup"><span data-stu-id="2a768-109">DetectReplays</span></span>  
 <span data-ttu-id="2a768-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="2a768-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="2a768-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2a768-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2a768-112">Um valor booliano que especifica se os ataques de reprodução contra o canal são detectados e tratados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="2a768-112">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="2a768-113">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="2a768-113">InactivityTimeout</span></span>  
 <span data-ttu-id="2a768-114">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="2a768-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="2a768-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2a768-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2a768-116">O número máximo de sessões de segurança que o serviço suporta pendentes.</span><span class="sxs-lookup"><span data-stu-id="2a768-116">The maximum number of pending security sessions that the service supports.</span></span>  
  
### <a name="issuedcookielifetime"></a><span data-ttu-id="2a768-117">IssuedCookieLifetime</span><span class="sxs-lookup"><span data-stu-id="2a768-117">IssuedCookieLifetime</span></span>  
 <span data-ttu-id="2a768-118">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="2a768-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="2a768-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2a768-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2a768-120">Um TimeSpan que especifica o tempo de vida emitido a todos os novos cookies de segurança.</span><span class="sxs-lookup"><span data-stu-id="2a768-120">A TimeSpan that specifies the lifetime issued to all new security cookies.</span></span>  
  
### <a name="maxcachedcookies"></a><span data-ttu-id="2a768-121">MaxCachedCookies</span><span class="sxs-lookup"><span data-stu-id="2a768-121">MaxCachedCookies</span></span>  
 <span data-ttu-id="2a768-122">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="2a768-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="2a768-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2a768-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2a768-124">O número máximo de cookies que podem ser armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="2a768-124">The maximum number of cookies that can be cached.</span></span>  
  
### <a name="maxclockskew"></a><span data-ttu-id="2a768-125">MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="2a768-125">MaxClockSkew</span></span>  
 <span data-ttu-id="2a768-126">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="2a768-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="2a768-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2a768-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2a768-128">Um TimeSpan que especifica a diferença máxima de tempo entre os relógios do sistema das duas partes da comunicação.</span><span class="sxs-lookup"><span data-stu-id="2a768-128">A TimeSpan that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span>  
  
### <a name="maxpendingsessions"></a><span data-ttu-id="2a768-129">MaxPendingSessions</span><span class="sxs-lookup"><span data-stu-id="2a768-129">MaxPendingSessions</span></span>  
 <span data-ttu-id="2a768-130">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="2a768-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="2a768-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2a768-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2a768-132">O número máximo de conexões pendentes no serviço.</span><span class="sxs-lookup"><span data-stu-id="2a768-132">The maximum number of pending connections on the service.</span></span>  
  
### <a name="maxstatefulnegotiations"></a><span data-ttu-id="2a768-133">MaxStatefulNegotiations</span><span class="sxs-lookup"><span data-stu-id="2a768-133">MaxStatefulNegotiations</span></span>  
 <span data-ttu-id="2a768-134">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="2a768-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="2a768-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2a768-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2a768-136">O número de negociações de segurança que podem estar ativas simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="2a768-136">The number of security negotiations that can be active concurrently.</span></span>  
  
### <a name="negotiationtimeout"></a><span data-ttu-id="2a768-137">NegotiationTimeout</span><span class="sxs-lookup"><span data-stu-id="2a768-137">NegotiationTimeout</span></span>  
 <span data-ttu-id="2a768-138">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="2a768-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="2a768-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2a768-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2a768-140">Um TimeSpan que especifica a duração máxima para a fase de negociação de segurança entre cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="2a768-140">A TimeSpan that specifies the maximum duration for the security negotiation phase between server and client.</span></span>  
  
### <a name="reconnecttransportonfailure"></a><span data-ttu-id="2a768-141">ReconnectTransportOnFailure</span><span class="sxs-lookup"><span data-stu-id="2a768-141">ReconnectTransportOnFailure</span></span>  
 <span data-ttu-id="2a768-142">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="2a768-142">Data type: boolean</span></span>  
  
 <span data-ttu-id="2a768-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2a768-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2a768-144">Um valor booliano que especifica se as conexões que usam mensagens WS-Reliable tentam se reconectar após falhas de transporte.</span><span class="sxs-lookup"><span data-stu-id="2a768-144">A Boolean value that specifies whether connections using WS-Reliable messaging attempt to reconnect after transport failures.</span></span>  
  
### <a name="replaycachesize"></a><span data-ttu-id="2a768-145">ReplayCacheSize</span><span class="sxs-lookup"><span data-stu-id="2a768-145">ReplayCacheSize</span></span>  
 <span data-ttu-id="2a768-146">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="2a768-146">Data type: sint32</span></span>  
  
 <span data-ttu-id="2a768-147">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2a768-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2a768-148">O número de nonces armazenados em cache usados para detecção de reprodução.</span><span class="sxs-lookup"><span data-stu-id="2a768-148">The number of cached nonces used for replay detection.</span></span>  
  
### <a name="replaywindow"></a><span data-ttu-id="2a768-149">ReplayWindow</span><span class="sxs-lookup"><span data-stu-id="2a768-149">ReplayWindow</span></span>  
 <span data-ttu-id="2a768-150">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="2a768-150">Data type: datetime</span></span>  
  
 <span data-ttu-id="2a768-151">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2a768-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2a768-152">Um TimeSpan que especifica a duração na qual nonces de mensagens individuais são válidos.</span><span class="sxs-lookup"><span data-stu-id="2a768-152">A TimeSpan that specifies the duration in which individual message nonces are valid.</span></span>  
  
### <a name="sessionkeyrenewalinterval"></a><span data-ttu-id="2a768-153">SessionKeyRenewalInterval</span><span class="sxs-lookup"><span data-stu-id="2a768-153">SessionKeyRenewalInterval</span></span>  
 <span data-ttu-id="2a768-154">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="2a768-154">Data type: datetime</span></span>  
  
 <span data-ttu-id="2a768-155">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2a768-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2a768-156">Um TimeSpan que especifica a duração após a qual o iniciador renova a chave da sessão de segurança.</span><span class="sxs-lookup"><span data-stu-id="2a768-156">A TimeSpan that specifies the duration after which the initiator renews the key for the security session.</span></span>  
  
### <a name="sessionkeyrolloverinterval"></a><span data-ttu-id="2a768-157">SessionKeyRolloverInterval</span><span class="sxs-lookup"><span data-stu-id="2a768-157">SessionKeyRolloverInterval</span></span>  
 <span data-ttu-id="2a768-158">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="2a768-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="2a768-159">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2a768-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2a768-160">Um TimeSpan que especifica o intervalo de tempo uma chave de sessão anterior é válida nas mensagens de entrada durante uma renovação de chave.</span><span class="sxs-lookup"><span data-stu-id="2a768-160">A TimeSpan that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span>  
  
### <a name="timestampvalidityduration"></a><span data-ttu-id="2a768-161">TimestampValidityDuration</span><span class="sxs-lookup"><span data-stu-id="2a768-161">TimestampValidityDuration</span></span>  
 <span data-ttu-id="2a768-162">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="2a768-162">Data type: datetime</span></span>  
  
 <span data-ttu-id="2a768-163">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2a768-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2a768-164">Um TimeSpan que especifica a duração em que um carimbo de data / hora é válido.</span><span class="sxs-lookup"><span data-stu-id="2a768-164">A TimeSpan that specifies the duration in which a time stamp is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a768-165">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2a768-165">Requirements</span></span>  
  
|<span data-ttu-id="2a768-166">MOF</span><span class="sxs-lookup"><span data-stu-id="2a768-166">MOF</span></span>|<span data-ttu-id="2a768-167">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2a768-167">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2a768-168">Namespace</span><span class="sxs-lookup"><span data-stu-id="2a768-168">Namespace</span></span>|<span data-ttu-id="2a768-169">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2a768-169">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a768-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a768-170">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
