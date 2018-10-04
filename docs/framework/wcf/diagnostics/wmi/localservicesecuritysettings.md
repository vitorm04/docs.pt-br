---
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
author: BrucePerlerMS
ms.openlocfilehash: c79eb11fcc1973a3ef25a78afb8b141443d865c3
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48777442"
---
# <a name="localservicesecuritysettings"></a><span data-ttu-id="aa0af-102">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="aa0af-102">LocalServiceSecuritySettings</span></span>
<span data-ttu-id="aa0af-103">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="aa0af-103">LocalServiceSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa0af-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa0af-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="aa0af-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="aa0af-105">Methods</span></span>  
 <span data-ttu-id="aa0af-106">A classe LocalServiceSecuritySettings não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="aa0af-106">The LocalServiceSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="aa0af-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="aa0af-107">Properties</span></span>  
 <span data-ttu-id="aa0af-108">A classe LocalServiceSecuritySettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="aa0af-108">The LocalServiceSecuritySettings class has the following properties:</span></span>  
  
### <a name="detectreplays"></a><span data-ttu-id="aa0af-109">DetectReplays</span><span class="sxs-lookup"><span data-stu-id="aa0af-109">DetectReplays</span></span>  
 <span data-ttu-id="aa0af-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="aa0af-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="aa0af-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="aa0af-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa0af-112">Um valor booliano que especifica se os ataques de reprodução contra o canal são detectados e tratados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="aa0af-112">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="aa0af-113">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="aa0af-113">InactivityTimeout</span></span>  
 <span data-ttu-id="aa0af-114">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="aa0af-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="aa0af-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="aa0af-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa0af-116">O número máximo de sessões de segurança que o serviço suporta pendentes.</span><span class="sxs-lookup"><span data-stu-id="aa0af-116">The maximum number of pending security sessions that the service supports.</span></span>  
  
### <a name="issuedcookielifetime"></a><span data-ttu-id="aa0af-117">IssuedCookieLifetime</span><span class="sxs-lookup"><span data-stu-id="aa0af-117">IssuedCookieLifetime</span></span>  
 <span data-ttu-id="aa0af-118">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="aa0af-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="aa0af-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="aa0af-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa0af-120">Um TimeSpan que especifica o tempo de vida emitido a todos os novos cookies de segurança.</span><span class="sxs-lookup"><span data-stu-id="aa0af-120">A TimeSpan that specifies the lifetime issued to all new security cookies.</span></span>  
  
### <a name="maxcachedcookies"></a><span data-ttu-id="aa0af-121">MaxCachedCookies</span><span class="sxs-lookup"><span data-stu-id="aa0af-121">MaxCachedCookies</span></span>  
 <span data-ttu-id="aa0af-122">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="aa0af-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="aa0af-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="aa0af-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa0af-124">O número máximo de cookies que podem ser armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="aa0af-124">The maximum number of cookies that can be cached.</span></span>  
  
### <a name="maxclockskew"></a><span data-ttu-id="aa0af-125">MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="aa0af-125">MaxClockSkew</span></span>  
 <span data-ttu-id="aa0af-126">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="aa0af-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="aa0af-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="aa0af-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa0af-128">Um TimeSpan que especifica a diferença máxima de tempo entre os relógios do sistema das duas partes da comunicação.</span><span class="sxs-lookup"><span data-stu-id="aa0af-128">A TimeSpan that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span>  
  
### <a name="maxpendingsessions"></a><span data-ttu-id="aa0af-129">MaxPendingSessions</span><span class="sxs-lookup"><span data-stu-id="aa0af-129">MaxPendingSessions</span></span>  
 <span data-ttu-id="aa0af-130">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="aa0af-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="aa0af-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="aa0af-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa0af-132">O número máximo de conexões pendentes no serviço.</span><span class="sxs-lookup"><span data-stu-id="aa0af-132">The maximum number of pending connections on the service.</span></span>  
  
### <a name="maxstatefulnegotiations"></a><span data-ttu-id="aa0af-133">MaxStatefulNegotiations</span><span class="sxs-lookup"><span data-stu-id="aa0af-133">MaxStatefulNegotiations</span></span>  
 <span data-ttu-id="aa0af-134">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="aa0af-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="aa0af-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="aa0af-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa0af-136">O número de negociações de segurança que podem estar ativas simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="aa0af-136">The number of security negotiations that can be active concurrently.</span></span>  
  
### <a name="negotiationtimeout"></a><span data-ttu-id="aa0af-137">NegotiationTimeout</span><span class="sxs-lookup"><span data-stu-id="aa0af-137">NegotiationTimeout</span></span>  
 <span data-ttu-id="aa0af-138">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="aa0af-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="aa0af-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="aa0af-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa0af-140">Um TimeSpan que especifica a duração máxima para a fase de negociação de segurança entre cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="aa0af-140">A TimeSpan that specifies the maximum duration for the security negotiation phase between server and client.</span></span>  
  
### <a name="reconnecttransportonfailure"></a><span data-ttu-id="aa0af-141">ReconnectTransportOnFailure</span><span class="sxs-lookup"><span data-stu-id="aa0af-141">ReconnectTransportOnFailure</span></span>  
 <span data-ttu-id="aa0af-142">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="aa0af-142">Data type: boolean</span></span>  
  
 <span data-ttu-id="aa0af-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="aa0af-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa0af-144">Um valor booliano que especifica se as conexões que usam mensagens WS-Reliable tentam se reconectar após falhas de transporte.</span><span class="sxs-lookup"><span data-stu-id="aa0af-144">A Boolean value that specifies whether connections using WS-Reliable messaging attempt to reconnect after transport failures.</span></span>  
  
### <a name="replaycachesize"></a><span data-ttu-id="aa0af-145">ReplayCacheSize</span><span class="sxs-lookup"><span data-stu-id="aa0af-145">ReplayCacheSize</span></span>  
 <span data-ttu-id="aa0af-146">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="aa0af-146">Data type: sint32</span></span>  
  
 <span data-ttu-id="aa0af-147">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="aa0af-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa0af-148">O número de nonces armazenados em cache usados para detecção de reprodução.</span><span class="sxs-lookup"><span data-stu-id="aa0af-148">The number of cached nonces used for replay detection.</span></span>  
  
### <a name="replaywindow"></a><span data-ttu-id="aa0af-149">ReplayWindow</span><span class="sxs-lookup"><span data-stu-id="aa0af-149">ReplayWindow</span></span>  
 <span data-ttu-id="aa0af-150">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="aa0af-150">Data type: datetime</span></span>  
  
 <span data-ttu-id="aa0af-151">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="aa0af-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa0af-152">Um TimeSpan que especifica a duração na qual nonces de mensagens individuais são válidos.</span><span class="sxs-lookup"><span data-stu-id="aa0af-152">A TimeSpan that specifies the duration in which individual message nonces are valid.</span></span>  
  
### <a name="sessionkeyrenewalinterval"></a><span data-ttu-id="aa0af-153">SessionKeyRenewalInterval</span><span class="sxs-lookup"><span data-stu-id="aa0af-153">SessionKeyRenewalInterval</span></span>  
 <span data-ttu-id="aa0af-154">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="aa0af-154">Data type: datetime</span></span>  
  
 <span data-ttu-id="aa0af-155">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="aa0af-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa0af-156">Um TimeSpan que especifica a duração após a qual o iniciador renova a chave da sessão de segurança.</span><span class="sxs-lookup"><span data-stu-id="aa0af-156">A TimeSpan that specifies the duration after which the initiator renews the key for the security session.</span></span>  
  
### <a name="sessionkeyrolloverinterval"></a><span data-ttu-id="aa0af-157">SessionKeyRolloverInterval</span><span class="sxs-lookup"><span data-stu-id="aa0af-157">SessionKeyRolloverInterval</span></span>  
 <span data-ttu-id="aa0af-158">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="aa0af-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="aa0af-159">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="aa0af-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa0af-160">Um TimeSpan que especifica o intervalo de tempo uma chave de sessão anterior é válida nas mensagens de entrada durante uma renovação de chave.</span><span class="sxs-lookup"><span data-stu-id="aa0af-160">A TimeSpan that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span>  
  
### <a name="timestampvalidityduration"></a><span data-ttu-id="aa0af-161">TimestampValidityDuration</span><span class="sxs-lookup"><span data-stu-id="aa0af-161">TimestampValidityDuration</span></span>  
 <span data-ttu-id="aa0af-162">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="aa0af-162">Data type: datetime</span></span>  
  
 <span data-ttu-id="aa0af-163">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="aa0af-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa0af-164">Um TimeSpan que especifica a duração em que um carimbo de data / hora é válido.</span><span class="sxs-lookup"><span data-stu-id="aa0af-164">A TimeSpan that specifies the duration in which a time stamp is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa0af-165">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aa0af-165">Requirements</span></span>  
  
|<span data-ttu-id="aa0af-166">MOF</span><span class="sxs-lookup"><span data-stu-id="aa0af-166">MOF</span></span>|<span data-ttu-id="aa0af-167">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="aa0af-167">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="aa0af-168">Namespace</span><span class="sxs-lookup"><span data-stu-id="aa0af-168">Namespace</span></span>|<span data-ttu-id="aa0af-169">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="aa0af-169">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa0af-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa0af-170">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
