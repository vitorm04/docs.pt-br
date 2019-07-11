---
title: Enumeração CorDebugInternalFrameType
ms.date: 03/30/2017
api_name:
- CorDebugInternalFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInternalFrameType
helpviewer_keywords:
- CorDebugInternalFrameType enumeration [.NET Framework debugging]
ms.assetid: e4412dc2-c338-4cfb-94d8-f682095dd2b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1dcbd8bb566331a6a2d4217eeec0441fbd3e6ff6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739865"
---
# <a name="cordebuginternalframetype-enumeration"></a><span data-ttu-id="8f2ff-102">Enumeração CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="8f2ff-102">CorDebugInternalFrameType Enumeration</span></span>
<span data-ttu-id="8f2ff-103">Identifica o tipo de quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="8f2ff-103">Identifies the type of stack frame.</span></span> <span data-ttu-id="8f2ff-104">Essa enumeração é usada pelo [icordebuginternalframe:: Getframetype](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="8f2ff-104">This enumeration is used by the [ICorDebugInternalFrame::GetFrameType](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f2ff-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f2ff-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugInternalFrameType {  
  
    STUBFRAME_NONE                 = 0x00000000,  
    STUBFRAME_M2U                  = 0x00000001,  
    STUBFRAME_U2M                  = 0x00000002,  
    STUBFRAME_APPDOMAIN_TRANSITION = 0x00000003,  
    STUBFRAME_LIGHTWEIGHT_FUNCTION = 0x00000004,  
    STUBFRAME_FUNC_EVAL            = 0x00000005,  
    STUBFRAME_INTERNALCALL         = 0x00000006,  
    STUBFRAME_CLASS_INIT           = 0x00000007,  
    STUBFRAME_EXCEPTION            = 0x00000008,  
    STUBFRAME_SECURITY             = 0x00000009,  
    STUBFRAME_JIT_COMPILATION     = 0x0000000a,  
} CorDebugInternalFrameType;  
```  
  
## <a name="members"></a><span data-ttu-id="8f2ff-106">Membros</span><span class="sxs-lookup"><span data-stu-id="8f2ff-106">Members</span></span>  
  
|<span data-ttu-id="8f2ff-107">Membro</span><span class="sxs-lookup"><span data-stu-id="8f2ff-107">Member</span></span>|<span data-ttu-id="8f2ff-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f2ff-108">Description</span></span>|  
|------------|-----------------|  
|`STUBFRAME_NONE`|<span data-ttu-id="8f2ff-109">Um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="8f2ff-109">A null value.</span></span> <span data-ttu-id="8f2ff-110">O `ICorDebugInternalFrame::GetFrameType` método nunca retornará esse valor.</span><span class="sxs-lookup"><span data-stu-id="8f2ff-110">The `ICorDebugInternalFrame::GetFrameType` method never returns this value.</span></span>|  
|`STUBFRAME_M2U`|<span data-ttu-id="8f2ff-111">Um quadro de stub para gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8f2ff-111">A managed-to-unmanaged stub frame.</span></span>|  
|`STUBFRAME_U2M`|<span data-ttu-id="8f2ff-112">Um quadro de stub não gerenciado para gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8f2ff-112">An unmanaged-to-managed stub frame.</span></span>|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|<span data-ttu-id="8f2ff-113">Uma transição entre domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8f2ff-113">A transition between application domains.</span></span>|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|<span data-ttu-id="8f2ff-114">Uma chamada de método leve.</span><span class="sxs-lookup"><span data-stu-id="8f2ff-114">A lightweight method call.</span></span>|  
|`STUBFRAME_FUNC_EVAL`|<span data-ttu-id="8f2ff-115">O início da função de avaliação.</span><span class="sxs-lookup"><span data-stu-id="8f2ff-115">The start of function evaluation.</span></span>|  
|`STUBFRAME_INTERNALCALL`|<span data-ttu-id="8f2ff-116">Uma chamada interna para o common language runtime.</span><span class="sxs-lookup"><span data-stu-id="8f2ff-116">An internal call into the common language runtime.</span></span>|  
|`STUBFRAME_CLASS_INIT`|<span data-ttu-id="8f2ff-117">O início de uma classe de inicialização.</span><span class="sxs-lookup"><span data-stu-id="8f2ff-117">The start of a class initialization.</span></span>|  
|`STUBFRAME_EXCEPTION`|<span data-ttu-id="8f2ff-118">Uma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="8f2ff-118">An exception that is thrown.</span></span>|  
|`STUBFRAME_SECURITY`|<span data-ttu-id="8f2ff-119">Um quadro usado para a segurança de acesso do código.</span><span class="sxs-lookup"><span data-stu-id="8f2ff-119">A frame used for code access security.</span></span>|  
|`STUBFRAME_JIT_COMPILATION`|<span data-ttu-id="8f2ff-120">O tempo de execução é um método com compilação JIT.</span><span class="sxs-lookup"><span data-stu-id="8f2ff-120">The runtime is JIT-compiling a method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8f2ff-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8f2ff-121">Requirements</span></span>  
 <span data-ttu-id="8f2ff-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f2ff-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f2ff-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f2ff-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f2ff-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f2ff-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f2ff-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f2ff-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f2ff-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f2ff-126">See also</span></span>

- [<span data-ttu-id="8f2ff-127">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="8f2ff-127">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
