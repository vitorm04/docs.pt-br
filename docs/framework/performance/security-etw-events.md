---
title: Eventos ETW de segurança
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11a19dce496423883e5fed62375c6db8ed5efdb1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134024"
---
# <a name="security-etw-events"></a><span data-ttu-id="db79d-102">Eventos ETW de segurança</span><span class="sxs-lookup"><span data-stu-id="db79d-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="db79d-103">Eventos de segurança são gerados durante a verificação de nome forte e a verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="db79d-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="db79d-104">Esta categoria consiste nos seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="db79d-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="db79d-105">Eventos StrongNameVerificationStart_V1 e StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="db79d-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="db79d-106">Eventos AuthenticodeVerificationStart_V1 e AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="db79d-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="db79d-107">Eventos StrongNameVerificationStart_V1 e StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="db79d-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="db79d-108">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="db79d-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="db79d-109">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="db79d-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="db79d-110">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="db79d-110">Keyword for raising the event</span></span>|<span data-ttu-id="db79d-111">Nível</span><span class="sxs-lookup"><span data-stu-id="db79d-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="db79d-112">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="db79d-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="db79d-113">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="db79d-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="db79d-114">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="db79d-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="db79d-115">evento</span><span class="sxs-lookup"><span data-stu-id="db79d-115">Event</span></span>|<span data-ttu-id="db79d-116">ID do evento</span><span class="sxs-lookup"><span data-stu-id="db79d-116">Event ID</span></span>|<span data-ttu-id="db79d-117">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="db79d-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="db79d-118">181</span><span class="sxs-lookup"><span data-stu-id="db79d-118">181</span></span>|<span data-ttu-id="db79d-119">Início da verificação de nome forte.</span><span class="sxs-lookup"><span data-stu-id="db79d-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="db79d-120">182</span><span class="sxs-lookup"><span data-stu-id="db79d-120">182</span></span>|<span data-ttu-id="db79d-121">Fim da verificação de nome forte.</span><span class="sxs-lookup"><span data-stu-id="db79d-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="db79d-122">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="db79d-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="db79d-123">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="db79d-123">Field name</span></span>|<span data-ttu-id="db79d-124">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="db79d-124">Data type</span></span>|<span data-ttu-id="db79d-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="db79d-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="db79d-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="db79d-126">VerificationFlags</span></span>|<span data-ttu-id="db79d-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="db79d-127">win:UInt32</span></span>|<span data-ttu-id="db79d-128">Os sinalizadores de verificação.</span><span class="sxs-lookup"><span data-stu-id="db79d-128">The verification flags.</span></span>|  
|<span data-ttu-id="db79d-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="db79d-129">ErrorCode</span></span>|<span data-ttu-id="db79d-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="db79d-130">win:UInt32</span></span>|<span data-ttu-id="db79d-131">O código de erro HResult.</span><span class="sxs-lookup"><span data-stu-id="db79d-131">The HResult error code.</span></span>|  
|<span data-ttu-id="db79d-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="db79d-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="db79d-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="db79d-133">win:UnicodeString</span></span>|<span data-ttu-id="db79d-134">O nome totalmente qualificado do assembly.</span><span class="sxs-lookup"><span data-stu-id="db79d-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="db79d-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="db79d-135">ClrInstanceID</span></span>|<span data-ttu-id="db79d-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="db79d-136">win:UInt16</span></span>|<span data-ttu-id="db79d-137">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="db79d-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="db79d-138">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="db79d-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="db79d-139">Eventos AuthenticodeVerificationStart_V1 e AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="db79d-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="db79d-140">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="db79d-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="db79d-141">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="db79d-141">Keyword for raising the event</span></span>|<span data-ttu-id="db79d-142">Nível</span><span class="sxs-lookup"><span data-stu-id="db79d-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="db79d-143">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="db79d-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="db79d-144">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="db79d-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="db79d-145">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="db79d-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="db79d-146">evento</span><span class="sxs-lookup"><span data-stu-id="db79d-146">Event</span></span>|<span data-ttu-id="db79d-147">ID do evento</span><span class="sxs-lookup"><span data-stu-id="db79d-147">Event ID</span></span>|<span data-ttu-id="db79d-148">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="db79d-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="db79d-149">183</span><span class="sxs-lookup"><span data-stu-id="db79d-149">183</span></span>|<span data-ttu-id="db79d-150">Início da verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="db79d-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="db79d-151">184</span><span class="sxs-lookup"><span data-stu-id="db79d-151">184</span></span>|<span data-ttu-id="db79d-152">Fim da verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="db79d-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="db79d-153">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="db79d-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="db79d-154">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="db79d-154">Field name</span></span>|<span data-ttu-id="db79d-155">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="db79d-155">Data type</span></span>|<span data-ttu-id="db79d-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="db79d-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="db79d-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="db79d-157">VerificationFlags</span></span>|<span data-ttu-id="db79d-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="db79d-158">win:UInt32</span></span>|<span data-ttu-id="db79d-159">Os sinalizadores de verificação.</span><span class="sxs-lookup"><span data-stu-id="db79d-159">The verification flags.</span></span>|  
|<span data-ttu-id="db79d-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="db79d-160">ErrorCode</span></span>|<span data-ttu-id="db79d-161">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="db79d-161">win:UInt32</span></span>|<span data-ttu-id="db79d-162">O código de erro HResult.</span><span class="sxs-lookup"><span data-stu-id="db79d-162">The HResult error code.</span></span>|  
|<span data-ttu-id="db79d-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="db79d-163">ModulePath</span></span>|<span data-ttu-id="db79d-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="db79d-164">win:UnicodeString</span></span>|<span data-ttu-id="db79d-165">O caminho do módulo.</span><span class="sxs-lookup"><span data-stu-id="db79d-165">The module path.</span></span>|  
|<span data-ttu-id="db79d-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="db79d-166">ClrInstanceID</span></span>|<span data-ttu-id="db79d-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="db79d-167">win:UInt16</span></span>|<span data-ttu-id="db79d-168">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="db79d-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="db79d-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db79d-169">See also</span></span>

- [<span data-ttu-id="db79d-170">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="db79d-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
