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
ms.openlocfilehash: fdb03b9244d3cb351735f5f2214248a08a399188
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795736"
---
# <a name="cordebugplatform-enumeration"></a><span data-ttu-id="4baab-102">Enumeração CorDebugPlatform</span><span class="sxs-lookup"><span data-stu-id="4baab-102">CorDebugPlatform Enumeration</span></span>
<span data-ttu-id="4baab-103">Fornece valores de plataforma de destino que são usados pelo método [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4baab-103">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4baab-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4baab-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="4baab-105">Membros</span><span class="sxs-lookup"><span data-stu-id="4baab-105">Members</span></span>  
  
|<span data-ttu-id="4baab-106">Membro</span><span class="sxs-lookup"><span data-stu-id="4baab-106">Member</span></span>|<span data-ttu-id="4baab-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="4baab-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4baab-108">CORDB_PLATFORM_WINDOWS_X86</span><span class="sxs-lookup"><span data-stu-id="4baab-108">CORDB_PLATFORM_WINDOWS_X86</span></span>|<span data-ttu-id="4baab-109">A plataforma de destino é Windows executando em hardware Intel x86.</span><span class="sxs-lookup"><span data-stu-id="4baab-109">The target platform is Windows running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="4baab-110">CORDB_PLATFORM_WINDOWS_AMD64</span><span class="sxs-lookup"><span data-stu-id="4baab-110">CORDB_PLATFORM_WINDOWS_AMD64</span></span>|<span data-ttu-id="4baab-111">A plataforma de destino é Windows de 64 bits executando em hardware AMD64 ou Intel EM64T.</span><span class="sxs-lookup"><span data-stu-id="4baab-111">The target platform is 64 bit Windows running on AMD64 or Intel EM64T hardware.</span></span>|  
|<span data-ttu-id="4baab-112">CORDB_PLATFORM_WINDOWS_IA64</span><span class="sxs-lookup"><span data-stu-id="4baab-112">CORDB_PLATFORM_WINDOWS_IA64</span></span>|<span data-ttu-id="4baab-113">A plataforma de destino é Windows de 32 bits executando em hardware Intel IA-64.</span><span class="sxs-lookup"><span data-stu-id="4baab-113">The target platform is 32 bit Windows running on Intel IA-64 hardware.</span></span>|  
|<span data-ttu-id="4baab-114">CORDB_PLATFORM_MAC_PPC</span><span class="sxs-lookup"><span data-stu-id="4baab-114">CORDB_PLATFORM_MAC_PPC</span></span>|<span data-ttu-id="4baab-115">A plataforma de destino é o sistema operacional Macintosh em execução em hardware PowerPC.</span><span class="sxs-lookup"><span data-stu-id="4baab-115">The target platform is the Macintosh operating system running on PowerPC hardware.</span></span>|  
|<span data-ttu-id="4baab-116">CORDB_PLATFORM_MAC_X86</span><span class="sxs-lookup"><span data-stu-id="4baab-116">CORDB_PLATFORM_MAC_X86</span></span>|<span data-ttu-id="4baab-117">A plataforma de destino é o sistema operacional Macintosh em execução no hardware Intel x86.</span><span class="sxs-lookup"><span data-stu-id="4baab-117">The target platform is the Macintosh operating system running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="4baab-118">CORDB_PLATFORM_WINDOWS_ARM</span><span class="sxs-lookup"><span data-stu-id="4baab-118">CORDB_PLATFORM_WINDOWS_ARM</span></span>|<span data-ttu-id="4baab-119">A plataforma de destino é o sistema operacional Macintosh em execução no hardware ARM do Windows.</span><span class="sxs-lookup"><span data-stu-id="4baab-119">The target platform is the Macintosh operating system running on Windows ARM hardware.</span></span>|  
|<span data-ttu-id="4baab-120">CORDB_PLATFORM_MAC_AMD64</span><span class="sxs-lookup"><span data-stu-id="4baab-120">CORDB_PLATFORM_MAC_AMD64</span></span>|<span data-ttu-id="4baab-121">A plataforma de destino é o sistema operacional Macintosh em execução no hardware AMD64.</span><span class="sxs-lookup"><span data-stu-id="4baab-121">The target platform is the Macintosh operating system running on AMD64 hardware.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4baab-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4baab-122">Requirements</span></span>  
 <span data-ttu-id="4baab-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4baab-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4baab-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4baab-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4baab-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4baab-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4baab-126">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4baab-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
 <span data-ttu-id="4baab-127">Os membros `CORDB_PLATFORM_WINDOWS_ARM` e `CORDB_PLATFORM_MAC_AMD64` estão disponíveis no .NET Framework 4.5.2 e em versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="4baab-127">The `CORDB_PLATFORM_WINDOWS_ARM` and `CORDB_PLATFORM_MAC_AMD64` members are available in the .NET Framework 4.5.2 and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4baab-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4baab-128">See also</span></span>

- [<span data-ttu-id="4baab-129">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="4baab-129">Debugging Enumerations</span></span>](debugging-enumerations.md)
