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
ms.openlocfilehash: 05184ceb3b32eb003951fff5cfdfbfb813992552
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216048"
---
# <a name="cordebuginternalframetype-enumeration"></a><span data-ttu-id="14c83-102">Enumeração CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="14c83-102">CorDebugInternalFrameType Enumeration</span></span>
<span data-ttu-id="14c83-103">Identifica o tipo de quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="14c83-103">Identifies the type of stack frame.</span></span> <span data-ttu-id="14c83-104">Essa enumeração é usada pelo [icordebuginternalframe:: Getframetype](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="14c83-104">This enumeration is used by the [ICorDebugInternalFrame::GetFrameType](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14c83-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="14c83-105">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="14c83-106">Membros</span><span class="sxs-lookup"><span data-stu-id="14c83-106">Members</span></span>  
  
|<span data-ttu-id="14c83-107">Membro</span><span class="sxs-lookup"><span data-stu-id="14c83-107">Member</span></span>|<span data-ttu-id="14c83-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="14c83-108">Description</span></span>|  
|------------|-----------------|  
|`STUBFRAME_NONE`|<span data-ttu-id="14c83-109">Um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="14c83-109">A null value.</span></span> <span data-ttu-id="14c83-110">O `ICorDebugInternalFrame::GetFrameType` método nunca retornará esse valor.</span><span class="sxs-lookup"><span data-stu-id="14c83-110">The `ICorDebugInternalFrame::GetFrameType` method never returns this value.</span></span>|  
|`STUBFRAME_M2U`|<span data-ttu-id="14c83-111">Um quadro de stub para gerenciado.</span><span class="sxs-lookup"><span data-stu-id="14c83-111">A managed-to-unmanaged stub frame.</span></span>|  
|`STUBFRAME_U2M`|<span data-ttu-id="14c83-112">Um quadro de stub não gerenciado para gerenciado.</span><span class="sxs-lookup"><span data-stu-id="14c83-112">An unmanaged-to-managed stub frame.</span></span>|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|<span data-ttu-id="14c83-113">Uma transição entre domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="14c83-113">A transition between application domains.</span></span>|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|<span data-ttu-id="14c83-114">Uma chamada de método leve.</span><span class="sxs-lookup"><span data-stu-id="14c83-114">A lightweight method call.</span></span>|  
|`STUBFRAME_FUNC_EVAL`|<span data-ttu-id="14c83-115">O início da função de avaliação.</span><span class="sxs-lookup"><span data-stu-id="14c83-115">The start of function evaluation.</span></span>|  
|`STUBFRAME_INTERNALCALL`|<span data-ttu-id="14c83-116">Uma chamada interna para o common language runtime.</span><span class="sxs-lookup"><span data-stu-id="14c83-116">An internal call into the common language runtime.</span></span>|  
|`STUBFRAME_CLASS_INIT`|<span data-ttu-id="14c83-117">O início de uma classe de inicialização.</span><span class="sxs-lookup"><span data-stu-id="14c83-117">The start of a class initialization.</span></span>|  
|`STUBFRAME_EXCEPTION`|<span data-ttu-id="14c83-118">Uma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="14c83-118">An exception that is thrown.</span></span>|  
|`STUBFRAME_SECURITY`|<span data-ttu-id="14c83-119">Um quadro usado para a segurança de acesso do código.</span><span class="sxs-lookup"><span data-stu-id="14c83-119">A frame used for code access security.</span></span>|  
|`STUBFRAME_JIT_COMPILATION`|<span data-ttu-id="14c83-120">O tempo de execução é um método com compilação JIT.</span><span class="sxs-lookup"><span data-stu-id="14c83-120">The runtime is JIT-compiling a method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="14c83-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="14c83-121">Requirements</span></span>  
 <span data-ttu-id="14c83-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14c83-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14c83-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14c83-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14c83-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14c83-124">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="14c83-125">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="14c83-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="14c83-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14c83-126">See also</span></span>

- [<span data-ttu-id="14c83-127">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="14c83-127">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
