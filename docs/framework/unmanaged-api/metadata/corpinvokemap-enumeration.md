---
title: "Enumeração CorPinvokeMap"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorPinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: CorPinvokeMap
helpviewer_keywords: CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9c6e1a49d18cde768884ab3d92eaa6593e2955c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="f76c2-102">Enumeração CorPinvokeMap</span><span class="sxs-lookup"><span data-stu-id="f76c2-102">CorPinvokeMap Enumeration</span></span>
<span data-ttu-id="f76c2-103">Especifica opções para uma chamada de PInvoke.</span><span class="sxs-lookup"><span data-stu-id="f76c2-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f76c2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f76c2-104">Syntax</span></span>  
  
```  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,   
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a><span data-ttu-id="f76c2-105">Membros</span><span class="sxs-lookup"><span data-stu-id="f76c2-105">Members</span></span>  
  
|<span data-ttu-id="f76c2-106">Membro</span><span class="sxs-lookup"><span data-stu-id="f76c2-106">Member</span></span>|<span data-ttu-id="f76c2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f76c2-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="f76c2-108">Use o nome de cada membro conforme especificado.</span><span class="sxs-lookup"><span data-stu-id="f76c2-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="f76c2-109">Reservado.</span><span class="sxs-lookup"><span data-stu-id="f76c2-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="f76c2-110">Reservado.</span><span class="sxs-lookup"><span data-stu-id="f76c2-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="f76c2-111">Realizar marshaling de cadeias de caracteres como cadeias de caracteres de vários bytes.</span><span class="sxs-lookup"><span data-stu-id="f76c2-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="f76c2-112">Realizar marshaling de cadeias de caracteres como cadeias de caracteres Unicode de 2 bytes.</span><span class="sxs-lookup"><span data-stu-id="f76c2-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="f76c2-113">Realizar marshaling automático de cadeias de caracteres apropriado para o sistema operacional de destino.</span><span class="sxs-lookup"><span data-stu-id="f76c2-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="f76c2-114">O padrão é Unicode no Windows NT, Windows 2000, Windows XP e a família Windows Server 2003. o padrão é ANSI no Windows 98 e Windows Me.</span><span class="sxs-lookup"><span data-stu-id="f76c2-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="f76c2-115">Reservado.</span><span class="sxs-lookup"><span data-stu-id="f76c2-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="f76c2-116">Execute o mapeamento de melhor ajuste de caracteres Unicode que não têm uma correspondência exata no conjunto de caracteres ANSI.</span><span class="sxs-lookup"><span data-stu-id="f76c2-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="f76c2-117">Não execute o mapeamento de melhor ajuste de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="f76c2-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="f76c2-118">Nesse caso, todos os caracteres não mapeável serão substituídos por um '?'.</span><span class="sxs-lookup"><span data-stu-id="f76c2-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="f76c2-119">Reservado.</span><span class="sxs-lookup"><span data-stu-id="f76c2-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="f76c2-120">Reservado.</span><span class="sxs-lookup"><span data-stu-id="f76c2-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="f76c2-121">Gera uma exceção quando interop marshaler encontra um caractere não mapeável.</span><span class="sxs-lookup"><span data-stu-id="f76c2-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="f76c2-122">Não gera uma exceção quando interop marshaler encontra um caractere não mapeável.</span><span class="sxs-lookup"><span data-stu-id="f76c2-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="f76c2-123">Reservado</span><span class="sxs-lookup"><span data-stu-id="f76c2-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="f76c2-124">Permitir que o receptor chamar o Win32 `SetLastError` função antes de retornar do método atribuído.</span><span class="sxs-lookup"><span data-stu-id="f76c2-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="f76c2-125">Reservado</span><span class="sxs-lookup"><span data-stu-id="f76c2-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="f76c2-126">Use a plataforma padrão convenção de chamada.</span><span class="sxs-lookup"><span data-stu-id="f76c2-126">Use the default platform calling convention.</span></span> <span data-ttu-id="f76c2-127">Por exemplo, no Windows o padrão é `StdCall` e no Windows CE .NET é `Cdecl`.</span><span class="sxs-lookup"><span data-stu-id="f76c2-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="f76c2-128">Use o `Cdecl` convenção de chamada.</span><span class="sxs-lookup"><span data-stu-id="f76c2-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="f76c2-129">Nesse caso, o chamador limpa a pilha.</span><span class="sxs-lookup"><span data-stu-id="f76c2-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="f76c2-130">Isso permite que as funções de chamada com `varargs` (ou seja, funções que aceitam um número variável de parâmetros).</span><span class="sxs-lookup"><span data-stu-id="f76c2-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="f76c2-131">Use o `StdCall` convenção de chamada.</span><span class="sxs-lookup"><span data-stu-id="f76c2-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="f76c2-132">Nesse caso, o receptor limpa a pilha.</span><span class="sxs-lookup"><span data-stu-id="f76c2-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="f76c2-133">Essa é a convenção padrão para chamar funções não gerenciadas com a invocação da plataforma.</span><span class="sxs-lookup"><span data-stu-id="f76c2-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="f76c2-134">Use o `ThisCall` convenção de chamada.</span><span class="sxs-lookup"><span data-stu-id="f76c2-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="f76c2-135">Nesse caso, o primeiro parâmetro é o `this` ponteiro e é armazenado no registro ECX.</span><span class="sxs-lookup"><span data-stu-id="f76c2-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="f76c2-136">Outros parâmetros são enviados por push na pilha.</span><span class="sxs-lookup"><span data-stu-id="f76c2-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="f76c2-137">O `ThisCall` convenção de chamada é usada para chamar métodos em classes exportadas de uma DLL não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="f76c2-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="f76c2-138">Reservado.</span><span class="sxs-lookup"><span data-stu-id="f76c2-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="f76c2-139">Reservado.</span><span class="sxs-lookup"><span data-stu-id="f76c2-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f76c2-140">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f76c2-140">Requirements</span></span>  
 <span data-ttu-id="f76c2-141">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f76c2-141">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f76c2-142">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="f76c2-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f76c2-143">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f76c2-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f76c2-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f76c2-144">See Also</span></span>  
 [<span data-ttu-id="f76c2-145">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="f76c2-145">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
