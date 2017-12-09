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
ms.openlocfilehash: a7e28eeabecfe0f1043328618f6e1be143f198a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="security-etw-events"></a><span data-ttu-id="f99be-102">Eventos ETW de segurança</span><span class="sxs-lookup"><span data-stu-id="f99be-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="f99be-103">Eventos de segurança são gerados durante a verificação de nome forte e a verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="f99be-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="f99be-104">Esta categoria consiste nos seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="f99be-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="f99be-105">Eventos StrongNameVerificationStart_V1 e StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="f99be-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="f99be-106">Eventos AuthenticodeVerificationStart_V1 e AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="f99be-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="f99be-107">Eventos StrongNameVerificationStart_V1 e StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="f99be-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="f99be-108">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="f99be-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="f99be-109">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="f99be-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="f99be-110">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="f99be-110">Keyword for raising the event</span></span>|<span data-ttu-id="f99be-111">Nível</span><span class="sxs-lookup"><span data-stu-id="f99be-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f99be-112">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="f99be-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="f99be-113">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="f99be-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="f99be-114">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="f99be-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f99be-115">Evento</span><span class="sxs-lookup"><span data-stu-id="f99be-115">Event</span></span>|<span data-ttu-id="f99be-116">ID do evento</span><span class="sxs-lookup"><span data-stu-id="f99be-116">Event ID</span></span>|<span data-ttu-id="f99be-117">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="f99be-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="f99be-118">181</span><span class="sxs-lookup"><span data-stu-id="f99be-118">181</span></span>|<span data-ttu-id="f99be-119">Início da verificação de nome forte.</span><span class="sxs-lookup"><span data-stu-id="f99be-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="f99be-120">182</span><span class="sxs-lookup"><span data-stu-id="f99be-120">182</span></span>|<span data-ttu-id="f99be-121">Fim da verificação de nome forte.</span><span class="sxs-lookup"><span data-stu-id="f99be-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="f99be-122">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="f99be-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f99be-123">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="f99be-123">Field name</span></span>|<span data-ttu-id="f99be-124">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="f99be-124">Data type</span></span>|<span data-ttu-id="f99be-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="f99be-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f99be-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="f99be-126">VerificationFlags</span></span>|<span data-ttu-id="f99be-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f99be-127">win:UInt32</span></span>|<span data-ttu-id="f99be-128">Os sinalizadores de verificação.</span><span class="sxs-lookup"><span data-stu-id="f99be-128">The verification flags.</span></span>|  
|<span data-ttu-id="f99be-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="f99be-129">ErrorCode</span></span>|<span data-ttu-id="f99be-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f99be-130">win:UInt32</span></span>|<span data-ttu-id="f99be-131">O código de erro HResult.</span><span class="sxs-lookup"><span data-stu-id="f99be-131">The HResult error code.</span></span>|  
|<span data-ttu-id="f99be-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="f99be-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="f99be-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f99be-133">win:UnicodeString</span></span>|<span data-ttu-id="f99be-134">O nome totalmente qualificado do assembly.</span><span class="sxs-lookup"><span data-stu-id="f99be-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="f99be-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f99be-135">ClrInstanceID</span></span>|<span data-ttu-id="f99be-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f99be-136">win:UInt16</span></span>|<span data-ttu-id="f99be-137">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f99be-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="f99be-138">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="f99be-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="f99be-139">Eventos AuthenticodeVerificationStart_V1 e AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="f99be-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="f99be-140">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="f99be-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f99be-141">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="f99be-141">Keyword for raising the event</span></span>|<span data-ttu-id="f99be-142">Nível</span><span class="sxs-lookup"><span data-stu-id="f99be-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f99be-143">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="f99be-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="f99be-144">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="f99be-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="f99be-145">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="f99be-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f99be-146">Evento</span><span class="sxs-lookup"><span data-stu-id="f99be-146">Event</span></span>|<span data-ttu-id="f99be-147">ID do evento</span><span class="sxs-lookup"><span data-stu-id="f99be-147">Event ID</span></span>|<span data-ttu-id="f99be-148">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="f99be-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="f99be-149">183</span><span class="sxs-lookup"><span data-stu-id="f99be-149">183</span></span>|<span data-ttu-id="f99be-150">Início da verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="f99be-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="f99be-151">184</span><span class="sxs-lookup"><span data-stu-id="f99be-151">184</span></span>|<span data-ttu-id="f99be-152">Fim da verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="f99be-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="f99be-153">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="f99be-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f99be-154">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="f99be-154">Field name</span></span>|<span data-ttu-id="f99be-155">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="f99be-155">Data type</span></span>|<span data-ttu-id="f99be-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="f99be-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f99be-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="f99be-157">VerificationFlags</span></span>|<span data-ttu-id="f99be-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f99be-158">win:UInt32</span></span>|<span data-ttu-id="f99be-159">Os sinalizadores de verificação.</span><span class="sxs-lookup"><span data-stu-id="f99be-159">The verification flags.</span></span>|  
|<span data-ttu-id="f99be-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="f99be-160">ErrorCode</span></span>|<span data-ttu-id="f99be-161">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f99be-161">win:UInt32</span></span>|<span data-ttu-id="f99be-162">O código de erro HResult.</span><span class="sxs-lookup"><span data-stu-id="f99be-162">The HResult error code.</span></span>|  
|<span data-ttu-id="f99be-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="f99be-163">ModulePath</span></span>|<span data-ttu-id="f99be-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f99be-164">win:UnicodeString</span></span>|<span data-ttu-id="f99be-165">O caminho do módulo.</span><span class="sxs-lookup"><span data-stu-id="f99be-165">The module path.</span></span>|  
|<span data-ttu-id="f99be-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f99be-166">ClrInstanceID</span></span>|<span data-ttu-id="f99be-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f99be-167">win:UInt16</span></span>|<span data-ttu-id="f99be-168">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f99be-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f99be-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f99be-169">See Also</span></span>  
 [<span data-ttu-id="f99be-170">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="f99be-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
