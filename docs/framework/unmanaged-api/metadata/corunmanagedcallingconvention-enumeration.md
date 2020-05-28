---
title: Enumeração CorUnmanagedCallingConvention
ms.date: 03/30/2017
api_name:
- CorUnmanagedCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnmanagedCallingConvention
helpviewer_keywords:
- CorUnmanagedCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 83058790-160b-4703-a5eb-74b66acbdfa9
topic_type:
- apiref
ms.openlocfilehash: b4c521489f38360d45c2cf8ff3780e057299f0b4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008944"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="5154c-102">Enumeração CorUnmanagedCallingConvention</span><span class="sxs-lookup"><span data-stu-id="5154c-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="5154c-103">Especifica as convenções de chamada para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5154c-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5154c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5154c-104">Syntax</span></span>  
  
```cpp  
typedef enum CorUnmanagedCallingConvention {  
  
    IMAGE_CEE_UNMANAGED_CALLCONV_C         = 0x1,  
    IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL   = 0x2,  
    IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL  = 0x3,  
    IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL  = 0x4,  
  
    IMAGE_CEE_CS_CALLCONV_C                = 0x1,  
    IMAGE_CEE_CS_CALLCONV_STDCALL          = 0x2,  
    IMAGE_CEE_CS_CALLCONV_THISCALL         = 0x3,  
    IMAGE_CEE_CS_CALLCONV_FASTCALL         = 0x4  
  
} CorUnmanagedCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="5154c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="5154c-105">Members</span></span>  
  
|<span data-ttu-id="5154c-106">Membro</span><span class="sxs-lookup"><span data-stu-id="5154c-106">Member</span></span>|<span data-ttu-id="5154c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5154c-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="5154c-108">A Convenção de chamada de linguagem C.</span><span class="sxs-lookup"><span data-stu-id="5154c-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="5154c-109">A Convenção de chamada padrão.</span><span class="sxs-lookup"><span data-stu-id="5154c-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="5154c-110">A Convenção de chamada "This".</span><span class="sxs-lookup"><span data-stu-id="5154c-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="5154c-111">A Convenção de chamada "Fast".</span><span class="sxs-lookup"><span data-stu-id="5154c-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="5154c-112">Não usado.</span><span class="sxs-lookup"><span data-stu-id="5154c-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="5154c-113">Não usado.</span><span class="sxs-lookup"><span data-stu-id="5154c-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="5154c-114">Não usado.</span><span class="sxs-lookup"><span data-stu-id="5154c-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="5154c-115">Não usado.</span><span class="sxs-lookup"><span data-stu-id="5154c-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5154c-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="5154c-116">Remarks</span></span>  
 <span data-ttu-id="5154c-117">O CLR não oferece suporte à Convenção de chamada "rápida" no .NET Framework versão 1,0.</span><span class="sxs-lookup"><span data-stu-id="5154c-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5154c-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5154c-118">Requirements</span></span>  
 <span data-ttu-id="5154c-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5154c-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5154c-120">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="5154c-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="5154c-121">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5154c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5154c-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="5154c-122">See also</span></span>

- [<span data-ttu-id="5154c-123">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="5154c-123">Metadata Enumerations</span></span>](metadata-enumerations.md)
