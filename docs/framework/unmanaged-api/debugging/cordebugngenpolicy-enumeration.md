---
title: Enumeração CorDebugNGenPolicy
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugNGenPolicy
helpviewer_keywords:
- CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type:
- apiref
ms.openlocfilehash: 2f8337f96239948189ffd58923d87fd05c79b0c3
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204856"
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="013e1-102">Enumeração CorDebugNGenPolicy</span><span class="sxs-lookup"><span data-stu-id="013e1-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="013e1-103">Fornece um valor que determina se um depurador carrega imagens nativas (NGen) do cache de imagens nativas.</span><span class="sxs-lookup"><span data-stu-id="013e1-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="013e1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="013e1-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="013e1-105">Membros</span><span class="sxs-lookup"><span data-stu-id="013e1-105">Members</span></span>  
  
|<span data-ttu-id="013e1-106">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="013e1-106">Member name</span></span>|<span data-ttu-id="013e1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="013e1-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="013e1-108">In a Windows 8.x Store app, the use of images from the local native image cache is disabled.</span><span class="sxs-lookup"><span data-stu-id="013e1-108">In a Windows 8.x Store app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="013e1-109">In a desktop app, this setting has no effect.</span><span class="sxs-lookup"><span data-stu-id="013e1-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="013e1-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="013e1-110">Remarks</span></span>  
 <span data-ttu-id="013e1-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="013e1-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="013e1-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span><span class="sxs-lookup"><span data-stu-id="013e1-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="013e1-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="013e1-113">Requirements</span></span>  
 <span data-ttu-id="013e1-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="013e1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="013e1-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="013e1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="013e1-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="013e1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="013e1-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="013e1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="013e1-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="013e1-118">See also</span></span>

- [<span data-ttu-id="013e1-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="013e1-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
