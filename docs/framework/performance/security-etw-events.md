---
title: Eventos ETW de segurança
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8d09b5b76c39f33848d44beb43d9b09c5e6ed13b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046170"
---
# <a name="security-etw-events"></a><span data-ttu-id="31817-102">Eventos ETW de segurança</span><span class="sxs-lookup"><span data-stu-id="31817-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="31817-103">Eventos de segurança são gerados durante a verificação de nome forte e a verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="31817-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="31817-104">Esta categoria consiste nos seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="31817-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="31817-105">Eventos StrongNameVerificationStart_V1 e StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="31817-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
- [<span data-ttu-id="31817-106">Eventos AuthenticodeVerificationStart_V1 e AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="31817-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="31817-107">Eventos StrongNameVerificationStart_V1 e StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="31817-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="31817-108">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="31817-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="31817-109">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="31817-109">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="31817-110">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="31817-110">Keyword for raising the event</span></span>|<span data-ttu-id="31817-111">Nível</span><span class="sxs-lookup"><span data-stu-id="31817-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="31817-112">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="31817-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="31817-113">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="31817-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="31817-114">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="31817-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="31817-115">evento</span><span class="sxs-lookup"><span data-stu-id="31817-115">Event</span></span>|<span data-ttu-id="31817-116">ID do evento</span><span class="sxs-lookup"><span data-stu-id="31817-116">Event ID</span></span>|<span data-ttu-id="31817-117">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="31817-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="31817-118">181</span><span class="sxs-lookup"><span data-stu-id="31817-118">181</span></span>|<span data-ttu-id="31817-119">Início da verificação de nome forte.</span><span class="sxs-lookup"><span data-stu-id="31817-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="31817-120">182</span><span class="sxs-lookup"><span data-stu-id="31817-120">182</span></span>|<span data-ttu-id="31817-121">Fim da verificação de nome forte.</span><span class="sxs-lookup"><span data-stu-id="31817-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="31817-122">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="31817-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="31817-123">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="31817-123">Field name</span></span>|<span data-ttu-id="31817-124">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="31817-124">Data type</span></span>|<span data-ttu-id="31817-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="31817-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="31817-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="31817-126">VerificationFlags</span></span>|<span data-ttu-id="31817-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="31817-127">win:UInt32</span></span>|<span data-ttu-id="31817-128">Os sinalizadores de verificação.</span><span class="sxs-lookup"><span data-stu-id="31817-128">The verification flags.</span></span>|  
|<span data-ttu-id="31817-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="31817-129">ErrorCode</span></span>|<span data-ttu-id="31817-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="31817-130">win:UInt32</span></span>|<span data-ttu-id="31817-131">O código de erro HResult.</span><span class="sxs-lookup"><span data-stu-id="31817-131">The HResult error code.</span></span>|  
|<span data-ttu-id="31817-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="31817-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="31817-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="31817-133">win:UnicodeString</span></span>|<span data-ttu-id="31817-134">O nome totalmente qualificado do assembly.</span><span class="sxs-lookup"><span data-stu-id="31817-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="31817-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="31817-135">ClrInstanceID</span></span>|<span data-ttu-id="31817-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="31817-136">win:UInt16</span></span>|<span data-ttu-id="31817-137">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="31817-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="31817-138">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="31817-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="31817-139">Eventos AuthenticodeVerificationStart_V1 e AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="31817-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="31817-140">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="31817-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="31817-141">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="31817-141">Keyword for raising the event</span></span>|<span data-ttu-id="31817-142">Nível</span><span class="sxs-lookup"><span data-stu-id="31817-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="31817-143">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="31817-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="31817-144">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="31817-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="31817-145">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="31817-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="31817-146">evento</span><span class="sxs-lookup"><span data-stu-id="31817-146">Event</span></span>|<span data-ttu-id="31817-147">ID do evento</span><span class="sxs-lookup"><span data-stu-id="31817-147">Event ID</span></span>|<span data-ttu-id="31817-148">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="31817-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="31817-149">183</span><span class="sxs-lookup"><span data-stu-id="31817-149">183</span></span>|<span data-ttu-id="31817-150">Início da verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="31817-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="31817-151">184</span><span class="sxs-lookup"><span data-stu-id="31817-151">184</span></span>|<span data-ttu-id="31817-152">Fim da verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="31817-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="31817-153">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="31817-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="31817-154">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="31817-154">Field name</span></span>|<span data-ttu-id="31817-155">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="31817-155">Data type</span></span>|<span data-ttu-id="31817-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="31817-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="31817-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="31817-157">VerificationFlags</span></span>|<span data-ttu-id="31817-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="31817-158">win:UInt32</span></span>|<span data-ttu-id="31817-159">Os sinalizadores de verificação.</span><span class="sxs-lookup"><span data-stu-id="31817-159">The verification flags.</span></span>|  
|<span data-ttu-id="31817-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="31817-160">ErrorCode</span></span>|<span data-ttu-id="31817-161">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="31817-161">win:UInt32</span></span>|<span data-ttu-id="31817-162">O código de erro HResult.</span><span class="sxs-lookup"><span data-stu-id="31817-162">The HResult error code.</span></span>|  
|<span data-ttu-id="31817-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="31817-163">ModulePath</span></span>|<span data-ttu-id="31817-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="31817-164">win:UnicodeString</span></span>|<span data-ttu-id="31817-165">O caminho do módulo.</span><span class="sxs-lookup"><span data-stu-id="31817-165">The module path.</span></span>|  
|<span data-ttu-id="31817-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="31817-166">ClrInstanceID</span></span>|<span data-ttu-id="31817-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="31817-167">win:UInt16</span></span>|<span data-ttu-id="31817-168">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="31817-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="31817-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31817-169">See also</span></span>

- [<span data-ttu-id="31817-170">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="31817-170">CLR ETW Events</span></span>](clr-etw-events.md)
