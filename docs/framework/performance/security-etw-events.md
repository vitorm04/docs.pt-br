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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134024"
---
# <a name="security-etw-events"></a><span data-ttu-id="9135c-102">Eventos ETW de segurança</span><span class="sxs-lookup"><span data-stu-id="9135c-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="9135c-103">Eventos de segurança são gerados durante a verificação de nome forte e a verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="9135c-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="9135c-104">Esta categoria consiste nos seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="9135c-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="9135c-105">Eventos StrongNameVerificationStart_V1 e StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="9135c-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="9135c-106">Eventos AuthenticodeVerificationStart_V1 e AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="9135c-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="9135c-107">Eventos StrongNameVerificationStart_V1 e StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="9135c-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="9135c-108">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="9135c-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="9135c-109">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="9135c-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="9135c-110">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="9135c-110">Keyword for raising the event</span></span>|<span data-ttu-id="9135c-111">Nível</span><span class="sxs-lookup"><span data-stu-id="9135c-111">Level</span></span>|  
|-----------------------------------|-----------|  
|`SecurityKeyword` <span data-ttu-id="9135c-112">(0x400)</span><span class="sxs-lookup"><span data-stu-id="9135c-112">(0x400)</span></span>|<span data-ttu-id="9135c-113">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="9135c-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="9135c-114">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="9135c-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="9135c-115">evento</span><span class="sxs-lookup"><span data-stu-id="9135c-115">Event</span></span>|<span data-ttu-id="9135c-116">ID do evento</span><span class="sxs-lookup"><span data-stu-id="9135c-116">Event ID</span></span>|<span data-ttu-id="9135c-117">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="9135c-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="9135c-118">181</span><span class="sxs-lookup"><span data-stu-id="9135c-118">181</span></span>|<span data-ttu-id="9135c-119">Início da verificação de nome forte.</span><span class="sxs-lookup"><span data-stu-id="9135c-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="9135c-120">182</span><span class="sxs-lookup"><span data-stu-id="9135c-120">182</span></span>|<span data-ttu-id="9135c-121">Fim da verificação de nome forte.</span><span class="sxs-lookup"><span data-stu-id="9135c-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="9135c-122">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="9135c-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="9135c-123">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="9135c-123">Field name</span></span>|<span data-ttu-id="9135c-124">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="9135c-124">Data type</span></span>|<span data-ttu-id="9135c-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="9135c-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="9135c-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="9135c-126">VerificationFlags</span></span>|<span data-ttu-id="9135c-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="9135c-127">win:UInt32</span></span>|<span data-ttu-id="9135c-128">Os sinalizadores de verificação.</span><span class="sxs-lookup"><span data-stu-id="9135c-128">The verification flags.</span></span>|  
|<span data-ttu-id="9135c-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="9135c-129">ErrorCode</span></span>|<span data-ttu-id="9135c-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="9135c-130">win:UInt32</span></span>|<span data-ttu-id="9135c-131">O código de erro HResult.</span><span class="sxs-lookup"><span data-stu-id="9135c-131">The HResult error code.</span></span>|  
|<span data-ttu-id="9135c-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="9135c-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="9135c-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="9135c-133">win:UnicodeString</span></span>|<span data-ttu-id="9135c-134">O nome totalmente qualificado do assembly.</span><span class="sxs-lookup"><span data-stu-id="9135c-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="9135c-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9135c-135">ClrInstanceID</span></span>|<span data-ttu-id="9135c-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="9135c-136">win:UInt16</span></span>|<span data-ttu-id="9135c-137">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="9135c-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="9135c-138">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="9135c-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="9135c-139">Eventos AuthenticodeVerificationStart_V1 e AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="9135c-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="9135c-140">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="9135c-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="9135c-141">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="9135c-141">Keyword for raising the event</span></span>|<span data-ttu-id="9135c-142">Nível</span><span class="sxs-lookup"><span data-stu-id="9135c-142">Level</span></span>|  
|-----------------------------------|-----------|  
|`SecurityKeyword` <span data-ttu-id="9135c-143">(0x400)</span><span class="sxs-lookup"><span data-stu-id="9135c-143">(0x400)</span></span>|<span data-ttu-id="9135c-144">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="9135c-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="9135c-145">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="9135c-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="9135c-146">evento</span><span class="sxs-lookup"><span data-stu-id="9135c-146">Event</span></span>|<span data-ttu-id="9135c-147">ID do evento</span><span class="sxs-lookup"><span data-stu-id="9135c-147">Event ID</span></span>|<span data-ttu-id="9135c-148">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="9135c-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="9135c-149">183</span><span class="sxs-lookup"><span data-stu-id="9135c-149">183</span></span>|<span data-ttu-id="9135c-150">Início da verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="9135c-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="9135c-151">184</span><span class="sxs-lookup"><span data-stu-id="9135c-151">184</span></span>|<span data-ttu-id="9135c-152">Fim da verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="9135c-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="9135c-153">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="9135c-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="9135c-154">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="9135c-154">Field name</span></span>|<span data-ttu-id="9135c-155">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="9135c-155">Data type</span></span>|<span data-ttu-id="9135c-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="9135c-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="9135c-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="9135c-157">VerificationFlags</span></span>|<span data-ttu-id="9135c-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="9135c-158">win:UInt32</span></span>|<span data-ttu-id="9135c-159">Os sinalizadores de verificação.</span><span class="sxs-lookup"><span data-stu-id="9135c-159">The verification flags.</span></span>|  
|<span data-ttu-id="9135c-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="9135c-160">ErrorCode</span></span>|<span data-ttu-id="9135c-161">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="9135c-161">win:UInt32</span></span>|<span data-ttu-id="9135c-162">O código de erro HResult.</span><span class="sxs-lookup"><span data-stu-id="9135c-162">The HResult error code.</span></span>|  
|<span data-ttu-id="9135c-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="9135c-163">ModulePath</span></span>|<span data-ttu-id="9135c-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="9135c-164">win:UnicodeString</span></span>|<span data-ttu-id="9135c-165">O caminho do módulo.</span><span class="sxs-lookup"><span data-stu-id="9135c-165">The module path.</span></span>|  
|<span data-ttu-id="9135c-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9135c-166">ClrInstanceID</span></span>|<span data-ttu-id="9135c-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="9135c-167">win:UInt16</span></span>|<span data-ttu-id="9135c-168">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="9135c-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9135c-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9135c-169">See also</span></span>

- [<span data-ttu-id="9135c-170">Eventos ETW no CLR</span><span class="sxs-lookup"><span data-stu-id="9135c-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
