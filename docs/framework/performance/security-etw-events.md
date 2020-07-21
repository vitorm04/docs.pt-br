---
title: Eventos ETW de segurança
description: Entenda os eventos ETW de segurança, que são gerados durante a verificação de nome forte e a verificação de Authenticode no .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
ms.openlocfilehash: 2fd2d450223cd16a7791b8f6c67afe6bcb954eb3
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474209"
---
# <a name="security-etw-events"></a><span data-ttu-id="4f4f4-103">Eventos ETW de segurança</span><span class="sxs-lookup"><span data-stu-id="4f4f4-103">Security ETW Events</span></span>

<span data-ttu-id="4f4f4-104"> Eventos de segurança são gerados durante a verificação de nome forte e a verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="4f4f4-104">Security events are raised during strong name verification and Authenticode verification.</span></span>  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="4f4f4-105">Eventos StrongNameVerificationStart_V1 e StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="4f4f4-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="4f4f4-106">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="4f4f4-106">The following table shows the keyword and level.</span></span> <span data-ttu-id="4f4f4-107">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="4f4f4-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="4f4f4-108">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="4f4f4-108">Keyword for raising the event</span></span>|<span data-ttu-id="4f4f4-109">Nível</span><span class="sxs-lookup"><span data-stu-id="4f4f4-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4f4f4-110">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="4f4f4-110">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="4f4f4-111">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="4f4f4-111">Informational(4)</span></span>|  
  
 <span data-ttu-id="4f4f4-112">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="4f4f4-112">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4f4f4-113">Evento</span><span class="sxs-lookup"><span data-stu-id="4f4f4-113">Event</span></span>|<span data-ttu-id="4f4f4-114">ID do evento</span><span class="sxs-lookup"><span data-stu-id="4f4f4-114">Event ID</span></span>|<span data-ttu-id="4f4f4-115">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="4f4f4-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="4f4f4-116">181</span><span class="sxs-lookup"><span data-stu-id="4f4f4-116">181</span></span>|<span data-ttu-id="4f4f4-117">Início da verificação de nome forte.</span><span class="sxs-lookup"><span data-stu-id="4f4f4-117">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="4f4f4-118">182</span><span class="sxs-lookup"><span data-stu-id="4f4f4-118">182</span></span>|<span data-ttu-id="4f4f4-119">Fim da verificação de nome forte.</span><span class="sxs-lookup"><span data-stu-id="4f4f4-119">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="4f4f4-120">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="4f4f4-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="4f4f4-121">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="4f4f4-121">Field name</span></span>|<span data-ttu-id="4f4f4-122">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="4f4f4-122">Data type</span></span>|<span data-ttu-id="4f4f4-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f4f4-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4f4f4-124">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="4f4f4-124">VerificationFlags</span></span>|<span data-ttu-id="4f4f4-125">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4f4f4-125">win:UInt32</span></span>|<span data-ttu-id="4f4f4-126">Os sinalizadores de verificação.</span><span class="sxs-lookup"><span data-stu-id="4f4f4-126">The verification flags.</span></span>|  
|<span data-ttu-id="4f4f4-127">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="4f4f4-127">ErrorCode</span></span>|<span data-ttu-id="4f4f4-128">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4f4f4-128">win:UInt32</span></span>|<span data-ttu-id="4f4f4-129">O código de erro HResult.</span><span class="sxs-lookup"><span data-stu-id="4f4f4-129">The HResult error code.</span></span>|  
|<span data-ttu-id="4f4f4-130">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="4f4f4-130">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="4f4f4-131">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="4f4f4-131">win:UnicodeString</span></span>|<span data-ttu-id="4f4f4-132">O nome totalmente qualificado do assembly.</span><span class="sxs-lookup"><span data-stu-id="4f4f4-132">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="4f4f4-133">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4f4f4-133">ClrInstanceID</span></span>|<span data-ttu-id="4f4f4-134">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4f4f4-134">win:UInt16</span></span>|<span data-ttu-id="4f4f4-135">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4f4f4-135">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="4f4f4-136">Eventos AuthenticodeVerificationStart_V1 e AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="4f4f4-136">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="4f4f4-137">A tabela a seguir mostra a palavra-chave e o nível.</span><span class="sxs-lookup"><span data-stu-id="4f4f4-137">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="4f4f4-138">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="4f4f4-138">Keyword for raising the event</span></span>|<span data-ttu-id="4f4f4-139">Nível</span><span class="sxs-lookup"><span data-stu-id="4f4f4-139">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4f4f4-140">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="4f4f4-140">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="4f4f4-141">Informativo(4)</span><span class="sxs-lookup"><span data-stu-id="4f4f4-141">Informational(4)</span></span>|  
  
 <span data-ttu-id="4f4f4-142">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="4f4f4-142">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4f4f4-143">Evento</span><span class="sxs-lookup"><span data-stu-id="4f4f4-143">Event</span></span>|<span data-ttu-id="4f4f4-144">ID do evento</span><span class="sxs-lookup"><span data-stu-id="4f4f4-144">Event ID</span></span>|<span data-ttu-id="4f4f4-145">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="4f4f4-145">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="4f4f4-146">183</span><span class="sxs-lookup"><span data-stu-id="4f4f4-146">183</span></span>|<span data-ttu-id="4f4f4-147">Início da verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="4f4f4-147">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="4f4f4-148">184</span><span class="sxs-lookup"><span data-stu-id="4f4f4-148">184</span></span>|<span data-ttu-id="4f4f4-149">Fim da verificação de Authenticode.</span><span class="sxs-lookup"><span data-stu-id="4f4f4-149">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="4f4f4-150">A tabela a seguir mostra os dados do evento.</span><span class="sxs-lookup"><span data-stu-id="4f4f4-150">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="4f4f4-151">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="4f4f4-151">Field name</span></span>|<span data-ttu-id="4f4f4-152">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="4f4f4-152">Data type</span></span>|<span data-ttu-id="4f4f4-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f4f4-153">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4f4f4-154">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="4f4f4-154">VerificationFlags</span></span>|<span data-ttu-id="4f4f4-155">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4f4f4-155">win:UInt32</span></span>|<span data-ttu-id="4f4f4-156">Os sinalizadores de verificação.</span><span class="sxs-lookup"><span data-stu-id="4f4f4-156">The verification flags.</span></span>|  
|<span data-ttu-id="4f4f4-157">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="4f4f4-157">ErrorCode</span></span>|<span data-ttu-id="4f4f4-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4f4f4-158">win:UInt32</span></span>|<span data-ttu-id="4f4f4-159">O código de erro HResult.</span><span class="sxs-lookup"><span data-stu-id="4f4f4-159">The HResult error code.</span></span>|  
|<span data-ttu-id="4f4f4-160">ModulePath</span><span class="sxs-lookup"><span data-stu-id="4f4f4-160">ModulePath</span></span>|<span data-ttu-id="4f4f4-161">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="4f4f4-161">win:UnicodeString</span></span>|<span data-ttu-id="4f4f4-162">O caminho do módulo.</span><span class="sxs-lookup"><span data-stu-id="4f4f4-162">The module path.</span></span>|  
|<span data-ttu-id="4f4f4-163">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4f4f4-163">ClrInstanceID</span></span>|<span data-ttu-id="4f4f4-164">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4f4f4-164">win:UInt16</span></span>|<span data-ttu-id="4f4f4-165">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4f4f4-165">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4f4f4-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f4f4-166">See also</span></span>

- [<span data-ttu-id="4f4f4-167">Eventos ETW no CLR</span><span class="sxs-lookup"><span data-stu-id="4f4f4-167">CLR ETW Events</span></span>](clr-etw-events.md)
