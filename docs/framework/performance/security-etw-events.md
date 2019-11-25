---
title: Eventos ETW de segurança
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1dad042595608a805f978673858acaa5c01130f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974872"
---
# <a name="security-etw-events"></a><span data-ttu-id="84616-102">Eventos ETW de segurança</span><span class="sxs-lookup"><span data-stu-id="84616-102">Security ETW Events</span></span>

<span data-ttu-id="84616-103">Os eventos de segurança são gerados durante a verificação de nome forte e a verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="84616-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="84616-104">Eventos StrongNameVerificationStart_V1 e StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="84616-104">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="84616-105">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="84616-105">The following table shows the keyword and level.</span></span> <span data-ttu-id="84616-106">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="84616-106">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="84616-107">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="84616-107">Keyword for raising the event</span></span>|<span data-ttu-id="84616-108">Nível</span><span class="sxs-lookup"><span data-stu-id="84616-108">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="84616-109">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="84616-109">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="84616-110">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="84616-110">Informational(4)</span></span>|  
  
 <span data-ttu-id="84616-111">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="84616-111">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="84616-112">evento</span><span class="sxs-lookup"><span data-stu-id="84616-112">Event</span></span>|<span data-ttu-id="84616-113">ID do evento</span><span class="sxs-lookup"><span data-stu-id="84616-113">Event ID</span></span>|<span data-ttu-id="84616-114">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="84616-114">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="84616-115">181</span><span class="sxs-lookup"><span data-stu-id="84616-115">181</span></span>|<span data-ttu-id="84616-116">Início da verificação de nome forte.</span><span class="sxs-lookup"><span data-stu-id="84616-116">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="84616-117">182</span><span class="sxs-lookup"><span data-stu-id="84616-117">182</span></span>|<span data-ttu-id="84616-118">Fim da verificação de nome forte.</span><span class="sxs-lookup"><span data-stu-id="84616-118">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="84616-119">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="84616-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="84616-120">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="84616-120">Field name</span></span>|<span data-ttu-id="84616-121">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="84616-121">Data type</span></span>|<span data-ttu-id="84616-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="84616-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="84616-123">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="84616-123">VerificationFlags</span></span>|<span data-ttu-id="84616-124">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="84616-124">win:UInt32</span></span>|<span data-ttu-id="84616-125">Os sinalizadores de verificação.</span><span class="sxs-lookup"><span data-stu-id="84616-125">The verification flags.</span></span>|  
|<span data-ttu-id="84616-126">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="84616-126">ErrorCode</span></span>|<span data-ttu-id="84616-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="84616-127">win:UInt32</span></span>|<span data-ttu-id="84616-128">O código de erro HResult.</span><span class="sxs-lookup"><span data-stu-id="84616-128">The HResult error code.</span></span>|  
|<span data-ttu-id="84616-129">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="84616-129">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="84616-130">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="84616-130">win:UnicodeString</span></span>|<span data-ttu-id="84616-131">O nome totalmente qualificado do assembly.</span><span class="sxs-lookup"><span data-stu-id="84616-131">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="84616-132">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="84616-132">ClrInstanceID</span></span>|<span data-ttu-id="84616-133">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="84616-133">win:UInt16</span></span>|<span data-ttu-id="84616-134">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="84616-134">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="84616-135">Eventos AuthenticodeVerificationStart_V1 e AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="84616-135">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="84616-136">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="84616-136">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="84616-137">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="84616-137">Keyword for raising the event</span></span>|<span data-ttu-id="84616-138">Nível</span><span class="sxs-lookup"><span data-stu-id="84616-138">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="84616-139">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="84616-139">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="84616-140">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="84616-140">Informational(4)</span></span>|  
  
 <span data-ttu-id="84616-141">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="84616-141">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="84616-142">evento</span><span class="sxs-lookup"><span data-stu-id="84616-142">Event</span></span>|<span data-ttu-id="84616-143">ID do evento</span><span class="sxs-lookup"><span data-stu-id="84616-143">Event ID</span></span>|<span data-ttu-id="84616-144">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="84616-144">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="84616-145">183</span><span class="sxs-lookup"><span data-stu-id="84616-145">183</span></span>|<span data-ttu-id="84616-146">Início da verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="84616-146">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="84616-147">184</span><span class="sxs-lookup"><span data-stu-id="84616-147">184</span></span>|<span data-ttu-id="84616-148">Fim da verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="84616-148">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="84616-149">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="84616-149">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="84616-150">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="84616-150">Field name</span></span>|<span data-ttu-id="84616-151">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="84616-151">Data type</span></span>|<span data-ttu-id="84616-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="84616-152">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="84616-153">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="84616-153">VerificationFlags</span></span>|<span data-ttu-id="84616-154">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="84616-154">win:UInt32</span></span>|<span data-ttu-id="84616-155">Os sinalizadores de verificação.</span><span class="sxs-lookup"><span data-stu-id="84616-155">The verification flags.</span></span>|  
|<span data-ttu-id="84616-156">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="84616-156">ErrorCode</span></span>|<span data-ttu-id="84616-157">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="84616-157">win:UInt32</span></span>|<span data-ttu-id="84616-158">O código de erro HResult.</span><span class="sxs-lookup"><span data-stu-id="84616-158">The HResult error code.</span></span>|  
|<span data-ttu-id="84616-159">ModulePath</span><span class="sxs-lookup"><span data-stu-id="84616-159">ModulePath</span></span>|<span data-ttu-id="84616-160">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="84616-160">win:UnicodeString</span></span>|<span data-ttu-id="84616-161">O caminho do módulo.</span><span class="sxs-lookup"><span data-stu-id="84616-161">The module path.</span></span>|  
|<span data-ttu-id="84616-162">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="84616-162">ClrInstanceID</span></span>|<span data-ttu-id="84616-163">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="84616-163">win:UInt16</span></span>|<span data-ttu-id="84616-164">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="84616-164">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84616-165">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84616-165">See also</span></span>

- [<span data-ttu-id="84616-166">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="84616-166">CLR ETW Events</span></span>](clr-etw-events.md)
