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
ms.openlocfilehash: 2be827e12db765485ee889d6a4a19a982dad5d54
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778362"
---
# <a name="cordebuginternalframetype-enumeration"></a><span data-ttu-id="bcc59-102">Enumeração CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="bcc59-102">CorDebugInternalFrameType Enumeration</span></span>
<span data-ttu-id="bcc59-103">Identifica o tipo de quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="bcc59-103">Identifies the type of stack frame.</span></span> <span data-ttu-id="bcc59-104">Essa enumeração é usada pelo método [ICorDebugInternalFrame:: GetFrameType](icordebuginternalframe-getframetype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bcc59-104">This enumeration is used by the [ICorDebugInternalFrame::GetFrameType](icordebuginternalframe-getframetype-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcc59-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bcc59-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="bcc59-106">Membros</span><span class="sxs-lookup"><span data-stu-id="bcc59-106">Members</span></span>  
  
|<span data-ttu-id="bcc59-107">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="bcc59-107">Member</span></span>|<span data-ttu-id="bcc59-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="bcc59-108">Description</span></span>|  
|------------|-----------------|  
|`STUBFRAME_NONE`|<span data-ttu-id="bcc59-109">Um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bcc59-109">A null value.</span></span> <span data-ttu-id="bcc59-110">O método `ICorDebugInternalFrame::GetFrameType` nunca retorna esse valor.</span><span class="sxs-lookup"><span data-stu-id="bcc59-110">The `ICorDebugInternalFrame::GetFrameType` method never returns this value.</span></span>|  
|`STUBFRAME_M2U`|<span data-ttu-id="bcc59-111">Um quadro de stub gerenciado para não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="bcc59-111">A managed-to-unmanaged stub frame.</span></span>|  
|`STUBFRAME_U2M`|<span data-ttu-id="bcc59-112">Um quadro de stub não gerenciado para gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="bcc59-112">An unmanaged-to-managed stub frame.</span></span>|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|<span data-ttu-id="bcc59-113">Uma transição entre domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bcc59-113">A transition between application domains.</span></span>|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|<span data-ttu-id="bcc59-114">Uma chamada de método leve.</span><span class="sxs-lookup"><span data-stu-id="bcc59-114">A lightweight method call.</span></span>|  
|`STUBFRAME_FUNC_EVAL`|<span data-ttu-id="bcc59-115">O início da avaliação da função.</span><span class="sxs-lookup"><span data-stu-id="bcc59-115">The start of function evaluation.</span></span>|  
|`STUBFRAME_INTERNALCALL`|<span data-ttu-id="bcc59-116">Uma chamada interna para o Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="bcc59-116">An internal call into the common language runtime.</span></span>|  
|`STUBFRAME_CLASS_INIT`|<span data-ttu-id="bcc59-117">O início de uma inicialização de classe.</span><span class="sxs-lookup"><span data-stu-id="bcc59-117">The start of a class initialization.</span></span>|  
|`STUBFRAME_EXCEPTION`|<span data-ttu-id="bcc59-118">Uma exceção que é lançada.</span><span class="sxs-lookup"><span data-stu-id="bcc59-118">An exception that is thrown.</span></span>|  
|`STUBFRAME_SECURITY`|<span data-ttu-id="bcc59-119">Um quadro usado para segurança de acesso ao código.</span><span class="sxs-lookup"><span data-stu-id="bcc59-119">A frame used for code access security.</span></span>|  
|`STUBFRAME_JIT_COMPILATION`|<span data-ttu-id="bcc59-120">O tempo de execução é a compilação JIT de um método.</span><span class="sxs-lookup"><span data-stu-id="bcc59-120">The runtime is JIT-compiling a method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bcc59-121">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="bcc59-121">Requirements</span></span>  
 <span data-ttu-id="bcc59-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcc59-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcc59-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bcc59-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bcc59-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bcc59-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcc59-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcc59-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcc59-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="bcc59-126">See also</span></span>

- [<span data-ttu-id="bcc59-127">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="bcc59-127">Debugging Enumerations</span></span>](debugging-enumerations.md)
