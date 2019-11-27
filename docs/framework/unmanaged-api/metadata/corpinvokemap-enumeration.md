---
title: Enumeração CorPinvokeMap
ms.date: 03/30/2017
api_name:
- CorPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPinvokeMap
helpviewer_keywords:
- CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type:
- apiref
ms.openlocfilehash: 17b7af7016cf88fd3ae263dd952502d515b0c833
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441564"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="b0798-102">Enumeração CorPinvokeMap</span><span class="sxs-lookup"><span data-stu-id="b0798-102">CorPinvokeMap Enumeration</span></span>
<span data-ttu-id="b0798-103">Especifica as opções para uma chamada PInvoke.</span><span class="sxs-lookup"><span data-stu-id="b0798-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0798-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b0798-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="b0798-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b0798-105">Members</span></span>  
  
|<span data-ttu-id="b0798-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="b0798-106">Member</span></span>|<span data-ttu-id="b0798-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b0798-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="b0798-108">Use cada nome de membro conforme especificado.</span><span class="sxs-lookup"><span data-stu-id="b0798-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="b0798-109">Reservado.</span><span class="sxs-lookup"><span data-stu-id="b0798-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="b0798-110">Reservado.</span><span class="sxs-lookup"><span data-stu-id="b0798-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="b0798-111">Realizar marshaling de cadeias de caracteres como cadeias de caracteres de vários bytes.</span><span class="sxs-lookup"><span data-stu-id="b0798-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="b0798-112">Realizar marshaling de cadeias de caracteres como cadeias de caracteres Unicode de 2 bytes.</span><span class="sxs-lookup"><span data-stu-id="b0798-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="b0798-113">Realizar marshaling automático de cadeias de caracteres apropriado para o sistema operacional de destino.</span><span class="sxs-lookup"><span data-stu-id="b0798-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="b0798-114">O padrão é Unicode no Windows NT, Windows 2000, Windows XP e na família Windows Server 2003; o padrão é ANSI no Windows 98 e Windows me.</span><span class="sxs-lookup"><span data-stu-id="b0798-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="b0798-115">Reservado.</span><span class="sxs-lookup"><span data-stu-id="b0798-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="b0798-116">Execute o mapeamento de melhor ajuste de caracteres Unicode que não têm uma correspondência exata no conjunto de caracteres ANSI.</span><span class="sxs-lookup"><span data-stu-id="b0798-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="b0798-117">Não execute o mapeamento de melhor ajuste de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="b0798-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="b0798-118">Nesse caso, todos os caracteres mapeável serão substituídos por um '? '.</span><span class="sxs-lookup"><span data-stu-id="b0798-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="b0798-119">Reservado.</span><span class="sxs-lookup"><span data-stu-id="b0798-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="b0798-120">Reservado.</span><span class="sxs-lookup"><span data-stu-id="b0798-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="b0798-121">Gerar uma exceção quando o marshaling interop encontrar um caractere mapeável.</span><span class="sxs-lookup"><span data-stu-id="b0798-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="b0798-122">Não lance uma exceção quando o marshaling interop encontra um caractere mapeável.</span><span class="sxs-lookup"><span data-stu-id="b0798-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="b0798-123">Reservado</span><span class="sxs-lookup"><span data-stu-id="b0798-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="b0798-124">Permitir que o receptor chame a função de `SetLastError` do Win32 antes de retornar do método atribuído.</span><span class="sxs-lookup"><span data-stu-id="b0798-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="b0798-125">Reservado</span><span class="sxs-lookup"><span data-stu-id="b0798-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="b0798-126">Use a Convenção de chamada de plataforma padrão.</span><span class="sxs-lookup"><span data-stu-id="b0798-126">Use the default platform calling convention.</span></span> <span data-ttu-id="b0798-127">Por exemplo, no Windows, o padrão é `StdCall` e Windows CE .NET é `Cdecl`.</span><span class="sxs-lookup"><span data-stu-id="b0798-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="b0798-128">Use a Convenção de chamada `Cdecl`.</span><span class="sxs-lookup"><span data-stu-id="b0798-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="b0798-129">Nesse caso, o chamador limpa a pilha.</span><span class="sxs-lookup"><span data-stu-id="b0798-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="b0798-130">Isso permite chamar funções com `varargs` (ou seja, funções que aceitam um número variável de parâmetros).</span><span class="sxs-lookup"><span data-stu-id="b0798-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="b0798-131">Use a Convenção de chamada `StdCall`.</span><span class="sxs-lookup"><span data-stu-id="b0798-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="b0798-132">Nesse caso, o receptor limpa a pilha.</span><span class="sxs-lookup"><span data-stu-id="b0798-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="b0798-133">Essa é a convenção padrão para chamar funções não gerenciadas com a invocação da plataforma.</span><span class="sxs-lookup"><span data-stu-id="b0798-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="b0798-134">Use a Convenção de chamada `ThisCall`.</span><span class="sxs-lookup"><span data-stu-id="b0798-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="b0798-135">Nesse caso, o primeiro parâmetro é o ponteiro `this` e é armazenado no Registro ECX.</span><span class="sxs-lookup"><span data-stu-id="b0798-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="b0798-136">Outros parâmetros são enviados por push na pilha.</span><span class="sxs-lookup"><span data-stu-id="b0798-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="b0798-137">A Convenção de chamada `ThisCall` é usada para chamar métodos em classes exportadas de uma DLL não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="b0798-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="b0798-138">Reservado.</span><span class="sxs-lookup"><span data-stu-id="b0798-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="b0798-139">Reservado.</span><span class="sxs-lookup"><span data-stu-id="b0798-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b0798-140">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="b0798-140">Requirements</span></span>  
 <span data-ttu-id="b0798-141">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0798-141">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0798-142">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="b0798-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b0798-143">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0798-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0798-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0798-144">See also</span></span>

- [<span data-ttu-id="b0798-145">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="b0798-145">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
