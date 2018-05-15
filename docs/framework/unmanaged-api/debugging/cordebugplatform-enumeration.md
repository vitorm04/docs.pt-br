---
title: Enumeração CorDebugPlatform
ms.date: 03/30/2017
api_name:
- CorDebugPlatformEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugPlatformEnum
helpviewer_keywords:
- CorDebugPlatformEnum enumeration [.NET Framework debugging]
ms.assetid: c5444816-7378-4521-afd3-bf5e4b5303d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d3b8f1e869e90fd3388cc0844e608b7ff40fc89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugplatform-enumeration"></a><span data-ttu-id="b0d96-102">Enumeração CorDebugPlatform</span><span class="sxs-lookup"><span data-stu-id="b0d96-102">CorDebugPlatform Enumeration</span></span>
<span data-ttu-id="b0d96-103">Fornece valores de plataforma de destino que são usados pelo [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="b0d96-103">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0d96-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b0d96-104">Syntax</span></span>  
  
```  
typedef enum CorDebugPlatform  
{  
    CORDB_PLATFORM_WINDOWS_X86,    // Windows on Intel x86  
    CORDB_PLATFORM_WINDOWS_AMD64,  // Windows x64 (AMD64, Intel EM64T)  
    CORDB_PLATFORM_WINDOWS_IA64,   // Windows on Intel IA-64  
    CORDB_PLATFORM_MAC_PPC,        // Macintosh OS on PowerPC  
    CORDB_PLATFORM_MAC_X86,        // Macintosh OS on Intel x86  
    CORDB_PLATFORM_WINDOWS_ARM,    // Windows on ARM  
    CORDB_PLATFORM_MAC_AMD64       // MacOS on Intel x64  
} CorDebugPlatform;  
```  
  
## <a name="members"></a><span data-ttu-id="b0d96-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b0d96-105">Members</span></span>  
  
|<span data-ttu-id="b0d96-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b0d96-106">Member</span></span>|<span data-ttu-id="b0d96-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b0d96-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b0d96-108">CORDB_PLATFORM_WINDOWS_X86</span><span class="sxs-lookup"><span data-stu-id="b0d96-108">CORDB_PLATFORM_WINDOWS_X86</span></span>|<span data-ttu-id="b0d96-109">A plataforma de destino é Windows executando em hardware Intel x86.</span><span class="sxs-lookup"><span data-stu-id="b0d96-109">The target platform is Windows running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="b0d96-110">CORDB_PLATFORM_WINDOWS_AMD64</span><span class="sxs-lookup"><span data-stu-id="b0d96-110">CORDB_PLATFORM_WINDOWS_AMD64</span></span>|<span data-ttu-id="b0d96-111">A plataforma de destino é Windows de 64 bits executando em hardware AMD64 ou Intel EM64T.</span><span class="sxs-lookup"><span data-stu-id="b0d96-111">The target platform is 64 bit Windows running on AMD64 or Intel EM64T hardware.</span></span>|  
|<span data-ttu-id="b0d96-112">CORDB_PLATFORM_WINDOWS_IA64</span><span class="sxs-lookup"><span data-stu-id="b0d96-112">CORDB_PLATFORM_WINDOWS_IA64</span></span>|<span data-ttu-id="b0d96-113">A plataforma de destino é Windows de 32 bits executando em hardware Intel IA-64.</span><span class="sxs-lookup"><span data-stu-id="b0d96-113">The target platform is 32 bit Windows running on Intel IA-64 hardware.</span></span>|  
|<span data-ttu-id="b0d96-114">CORDB_PLATFORM_MAC_PPC</span><span class="sxs-lookup"><span data-stu-id="b0d96-114">CORDB_PLATFORM_MAC_PPC</span></span>|<span data-ttu-id="b0d96-115">A plataforma de destino é o sistema de operacional Macintosh em execução no hardware PowerPC.</span><span class="sxs-lookup"><span data-stu-id="b0d96-115">The target platform is the Macintosh operating system running on PowerPC hardware.</span></span>|  
|<span data-ttu-id="b0d96-116">CORDB_PLATFORM_MAC_X86</span><span class="sxs-lookup"><span data-stu-id="b0d96-116">CORDB_PLATFORM_MAC_X86</span></span>|<span data-ttu-id="b0d96-117">A plataforma de destino é o sistema operacional Macintosh em execução no hardware Intel x86.</span><span class="sxs-lookup"><span data-stu-id="b0d96-117">The target platform is the Macintosh operating system running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="b0d96-118">CORDB_PLATFORM_WINDOWS_ARM</span><span class="sxs-lookup"><span data-stu-id="b0d96-118">CORDB_PLATFORM_WINDOWS_ARM</span></span>|<span data-ttu-id="b0d96-119">A plataforma de destino é o sistema de operacional Macintosh em execução no hardware de ARM do Windows.</span><span class="sxs-lookup"><span data-stu-id="b0d96-119">The target platform is the Macintosh operating system running on Windows ARM hardware.</span></span>|  
|<span data-ttu-id="b0d96-120">CORDB_PLATFORM_MAC_AMD64</span><span class="sxs-lookup"><span data-stu-id="b0d96-120">CORDB_PLATFORM_MAC_AMD64</span></span>|<span data-ttu-id="b0d96-121">A plataforma de destino é o sistema de operacional Macintosh em execução no hardware AMD64.</span><span class="sxs-lookup"><span data-stu-id="b0d96-121">The target platform is the Macintosh operating system running on AMD64 hardware.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b0d96-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b0d96-122">Requirements</span></span>  
 <span data-ttu-id="b0d96-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0d96-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0d96-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0d96-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0d96-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0d96-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0d96-126">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0d96-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
 <span data-ttu-id="b0d96-127">Os membros `CORDB_PLATFORM_WINDOWS_ARM` e `CORDB_PLATFORM_MAC_AMD64` estão disponíveis no .NET Framework 4.5.2 e em versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="b0d96-127">The `CORDB_PLATFORM_WINDOWS_ARM` and `CORDB_PLATFORM_MAC_AMD64` members are available in the .NET Framework 4.5.2 and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0d96-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0d96-128">See Also</span></span>  
 [<span data-ttu-id="b0d96-129">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="b0d96-129">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
