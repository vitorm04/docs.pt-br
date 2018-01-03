---
title: "Eventos ETW de segurança"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: abf6e6896267b6d1c8449b020230381923f38f1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="security-etw-events"></a><span data-ttu-id="f9685-102">Eventos ETW de segurança</span><span class="sxs-lookup"><span data-stu-id="f9685-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="f9685-103">Eventos de segurança são gerados durante a verificação de nome forte e a verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="f9685-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="f9685-104">Esta categoria consiste nos seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="f9685-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="f9685-105">Eventos StrongNameVerificationStart_V1 e StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="f9685-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="f9685-106">Eventos AuthenticodeVerificationStart_V1 e AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="f9685-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="f9685-107">Eventos StrongNameVerificationStart_V1 e StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="f9685-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="f9685-108">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="f9685-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="f9685-109">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="f9685-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="f9685-110">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="f9685-110">Keyword for raising the event</span></span>|<span data-ttu-id="f9685-111">Nível</span><span class="sxs-lookup"><span data-stu-id="f9685-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f9685-112">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="f9685-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="f9685-113">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="f9685-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="f9685-114">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="f9685-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f9685-115">evento</span><span class="sxs-lookup"><span data-stu-id="f9685-115">Event</span></span>|<span data-ttu-id="f9685-116">ID do evento</span><span class="sxs-lookup"><span data-stu-id="f9685-116">Event ID</span></span>|<span data-ttu-id="f9685-117">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="f9685-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="f9685-118">181</span><span class="sxs-lookup"><span data-stu-id="f9685-118">181</span></span>|<span data-ttu-id="f9685-119">Início da verificação de nome forte.</span><span class="sxs-lookup"><span data-stu-id="f9685-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="f9685-120">182</span><span class="sxs-lookup"><span data-stu-id="f9685-120">182</span></span>|<span data-ttu-id="f9685-121">Fim da verificação de nome forte.</span><span class="sxs-lookup"><span data-stu-id="f9685-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="f9685-122">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="f9685-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f9685-123">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="f9685-123">Field name</span></span>|<span data-ttu-id="f9685-124">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="f9685-124">Data type</span></span>|<span data-ttu-id="f9685-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9685-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f9685-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="f9685-126">VerificationFlags</span></span>|<span data-ttu-id="f9685-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f9685-127">win:UInt32</span></span>|<span data-ttu-id="f9685-128">Os sinalizadores de verificação.</span><span class="sxs-lookup"><span data-stu-id="f9685-128">The verification flags.</span></span>|  
|<span data-ttu-id="f9685-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="f9685-129">ErrorCode</span></span>|<span data-ttu-id="f9685-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f9685-130">win:UInt32</span></span>|<span data-ttu-id="f9685-131">O código de erro HResult.</span><span class="sxs-lookup"><span data-stu-id="f9685-131">The HResult error code.</span></span>|  
|<span data-ttu-id="f9685-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="f9685-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="f9685-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f9685-133">win:UnicodeString</span></span>|<span data-ttu-id="f9685-134">O nome totalmente qualificado do assembly.</span><span class="sxs-lookup"><span data-stu-id="f9685-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="f9685-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f9685-135">ClrInstanceID</span></span>|<span data-ttu-id="f9685-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f9685-136">win:UInt16</span></span>|<span data-ttu-id="f9685-137">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f9685-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="f9685-138">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="f9685-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="f9685-139">Eventos AuthenticodeVerificationStart_V1 e AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="f9685-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="f9685-140">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="f9685-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f9685-141">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="f9685-141">Keyword for raising the event</span></span>|<span data-ttu-id="f9685-142">Nível</span><span class="sxs-lookup"><span data-stu-id="f9685-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f9685-143">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="f9685-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="f9685-144">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="f9685-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="f9685-145">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="f9685-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f9685-146">evento</span><span class="sxs-lookup"><span data-stu-id="f9685-146">Event</span></span>|<span data-ttu-id="f9685-147">ID do evento</span><span class="sxs-lookup"><span data-stu-id="f9685-147">Event ID</span></span>|<span data-ttu-id="f9685-148">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="f9685-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="f9685-149">183</span><span class="sxs-lookup"><span data-stu-id="f9685-149">183</span></span>|<span data-ttu-id="f9685-150">Início da verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="f9685-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="f9685-151">184</span><span class="sxs-lookup"><span data-stu-id="f9685-151">184</span></span>|<span data-ttu-id="f9685-152">Fim da verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="f9685-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="f9685-153">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="f9685-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f9685-154">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="f9685-154">Field name</span></span>|<span data-ttu-id="f9685-155">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="f9685-155">Data type</span></span>|<span data-ttu-id="f9685-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9685-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f9685-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="f9685-157">VerificationFlags</span></span>|<span data-ttu-id="f9685-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f9685-158">win:UInt32</span></span>|<span data-ttu-id="f9685-159">Os sinalizadores de verificação.</span><span class="sxs-lookup"><span data-stu-id="f9685-159">The verification flags.</span></span>|  
|<span data-ttu-id="f9685-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="f9685-160">ErrorCode</span></span>|<span data-ttu-id="f9685-161">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f9685-161">win:UInt32</span></span>|<span data-ttu-id="f9685-162">O código de erro HResult.</span><span class="sxs-lookup"><span data-stu-id="f9685-162">The HResult error code.</span></span>|  
|<span data-ttu-id="f9685-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="f9685-163">ModulePath</span></span>|<span data-ttu-id="f9685-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f9685-164">win:UnicodeString</span></span>|<span data-ttu-id="f9685-165">O caminho do módulo.</span><span class="sxs-lookup"><span data-stu-id="f9685-165">The module path.</span></span>|  
|<span data-ttu-id="f9685-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f9685-166">ClrInstanceID</span></span>|<span data-ttu-id="f9685-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f9685-167">win:UInt16</span></span>|<span data-ttu-id="f9685-168">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f9685-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9685-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9685-169">See Also</span></span>  
 [<span data-ttu-id="f9685-170">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="f9685-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
