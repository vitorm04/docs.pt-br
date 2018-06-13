---
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 8f80af782c474ccf3a232ab353125fa223d4f5d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486891"
---
# <a name="localservicesecuritysettings"></a><span data-ttu-id="79689-102">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="79689-102">LocalServiceSecuritySettings</span></span>
<span data-ttu-id="79689-103">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="79689-103">LocalServiceSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79689-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="79689-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="79689-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="79689-105">Methods</span></span>  
 <span data-ttu-id="79689-106">A classe LocalServiceSecuritySettings não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="79689-106">The LocalServiceSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="79689-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="79689-107">Properties</span></span>  
 <span data-ttu-id="79689-108">A classe LocalServiceSecuritySettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="79689-108">The LocalServiceSecuritySettings class has the following properties:</span></span>  
  
### <a name="detectreplays"></a><span data-ttu-id="79689-109">DetectReplays</span><span class="sxs-lookup"><span data-stu-id="79689-109">DetectReplays</span></span>  
 <span data-ttu-id="79689-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="79689-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="79689-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79689-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79689-112">Um valor booleano que especifica se os ataques por repetição contra o canal são detectados e lidados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="79689-112">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="79689-113">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="79689-113">InactivityTimeout</span></span>  
 <span data-ttu-id="79689-114">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="79689-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="79689-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79689-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79689-116">O número máximo de pendente sessões de segurança que o serviço oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="79689-116">The maximum number of pending security sessions that the service supports.</span></span>  
  
### <a name="issuedcookielifetime"></a><span data-ttu-id="79689-117">IssuedCookieLifetime</span><span class="sxs-lookup"><span data-stu-id="79689-117">IssuedCookieLifetime</span></span>  
 <span data-ttu-id="79689-118">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="79689-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="79689-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79689-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79689-120">Um TimeSpan que especifica o tempo de vida concedido a todos os novos cookies de segurança.</span><span class="sxs-lookup"><span data-stu-id="79689-120">A TimeSpan that specifies the lifetime issued to all new security cookies.</span></span>  
  
### <a name="maxcachedcookies"></a><span data-ttu-id="79689-121">MaxCachedCookies</span><span class="sxs-lookup"><span data-stu-id="79689-121">MaxCachedCookies</span></span>  
 <span data-ttu-id="79689-122">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="79689-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="79689-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79689-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79689-124">O número máximo de cookies que podem ser armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="79689-124">The maximum number of cookies that can be cached.</span></span>  
  
### <a name="maxclockskew"></a><span data-ttu-id="79689-125">MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="79689-125">MaxClockSkew</span></span>  
 <span data-ttu-id="79689-126">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="79689-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="79689-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79689-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79689-128">Um TimeSpan que especifica a diferença máxima de tempo entre os relógios do sistema das duas partes da comunicação.</span><span class="sxs-lookup"><span data-stu-id="79689-128">A TimeSpan that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span>  
  
### <a name="maxpendingsessions"></a><span data-ttu-id="79689-129">MaxPendingSessions</span><span class="sxs-lookup"><span data-stu-id="79689-129">MaxPendingSessions</span></span>  
 <span data-ttu-id="79689-130">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="79689-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="79689-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79689-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79689-132">O número máximo de conexões pendentes no serviço.</span><span class="sxs-lookup"><span data-stu-id="79689-132">The maximum number of pending connections on the service.</span></span>  
  
### <a name="maxstatefulnegotiations"></a><span data-ttu-id="79689-133">MaxStatefulNegotiations</span><span class="sxs-lookup"><span data-stu-id="79689-133">MaxStatefulNegotiations</span></span>  
 <span data-ttu-id="79689-134">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="79689-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="79689-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79689-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79689-136">O número de negociações de segurança que podem estar ativas simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="79689-136">The number of security negotiations that can be active concurrently.</span></span>  
  
### <a name="negotiationtimeout"></a><span data-ttu-id="79689-137">NegotiationTimeout</span><span class="sxs-lookup"><span data-stu-id="79689-137">NegotiationTimeout</span></span>  
 <span data-ttu-id="79689-138">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="79689-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="79689-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79689-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79689-140">Um TimeSpan que especifica a duração máxima para a fase de negociação de segurança entre cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="79689-140">A TimeSpan that specifies the maximum duration for the security negotiation phase between server and client.</span></span>  
  
### <a name="reconnecttransportonfailure"></a><span data-ttu-id="79689-141">ReconnectTransportOnFailure</span><span class="sxs-lookup"><span data-stu-id="79689-141">ReconnectTransportOnFailure</span></span>  
 <span data-ttu-id="79689-142">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="79689-142">Data type: boolean</span></span>  
  
 <span data-ttu-id="79689-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79689-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79689-144">Um valor booleano que especifica se as conexões usando mensagens WS-Reliable tentam se reconectar após falhas de transporte.</span><span class="sxs-lookup"><span data-stu-id="79689-144">A Boolean value that specifies whether connections using WS-Reliable messaging attempt to reconnect after transport failures.</span></span>  
  
### <a name="replaycachesize"></a><span data-ttu-id="79689-145">ReplayCacheSize</span><span class="sxs-lookup"><span data-stu-id="79689-145">ReplayCacheSize</span></span>  
 <span data-ttu-id="79689-146">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="79689-146">Data type: sint32</span></span>  
  
 <span data-ttu-id="79689-147">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79689-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79689-148">O número de momentos em cache usados para detecção de repetição.</span><span class="sxs-lookup"><span data-stu-id="79689-148">The number of cached nonces used for replay detection.</span></span>  
  
### <a name="replaywindow"></a><span data-ttu-id="79689-149">ReplayWindow</span><span class="sxs-lookup"><span data-stu-id="79689-149">ReplayWindow</span></span>  
 <span data-ttu-id="79689-150">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="79689-150">Data type: datetime</span></span>  
  
 <span data-ttu-id="79689-151">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79689-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79689-152">Um TimeSpan que especifica a duração em que momentos de mensagens individuais são válidos.</span><span class="sxs-lookup"><span data-stu-id="79689-152">A TimeSpan that specifies the duration in which individual message nonces are valid.</span></span>  
  
### <a name="sessionkeyrenewalinterval"></a><span data-ttu-id="79689-153">SessionKeyRenewalInterval</span><span class="sxs-lookup"><span data-stu-id="79689-153">SessionKeyRenewalInterval</span></span>  
 <span data-ttu-id="79689-154">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="79689-154">Data type: datetime</span></span>  
  
 <span data-ttu-id="79689-155">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79689-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79689-156">Um TimeSpan que especifica a duração após a qual o iniciador renova a chave da sessão de segurança.</span><span class="sxs-lookup"><span data-stu-id="79689-156">A TimeSpan that specifies the duration after which the initiator renews the key for the security session.</span></span>  
  
### <a name="sessionkeyrolloverinterval"></a><span data-ttu-id="79689-157">SessionKeyRolloverInterval</span><span class="sxs-lookup"><span data-stu-id="79689-157">SessionKeyRolloverInterval</span></span>  
 <span data-ttu-id="79689-158">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="79689-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="79689-159">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79689-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79689-160">Um TimeSpan que especifica o intervalo de tempo uma chave de sessão anterior é válida nas mensagens de entrada durante uma renovação de chave.</span><span class="sxs-lookup"><span data-stu-id="79689-160">A TimeSpan that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span>  
  
### <a name="timestampvalidityduration"></a><span data-ttu-id="79689-161">TimestampValidityDuration</span><span class="sxs-lookup"><span data-stu-id="79689-161">TimestampValidityDuration</span></span>  
 <span data-ttu-id="79689-162">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="79689-162">Data type: datetime</span></span>  
  
 <span data-ttu-id="79689-163">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79689-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79689-164">Um TimeSpan que especifica a duração na qual um carimbo de data / hora é válido.</span><span class="sxs-lookup"><span data-stu-id="79689-164">A TimeSpan that specifies the duration in which a time stamp is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79689-165">Requisitos</span><span class="sxs-lookup"><span data-stu-id="79689-165">Requirements</span></span>  
  
|<span data-ttu-id="79689-166">MOF</span><span class="sxs-lookup"><span data-stu-id="79689-166">MOF</span></span>|<span data-ttu-id="79689-167">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="79689-167">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="79689-168">Namespace</span><span class="sxs-lookup"><span data-stu-id="79689-168">Namespace</span></span>|<span data-ttu-id="79689-169">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="79689-169">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79689-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79689-170">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
