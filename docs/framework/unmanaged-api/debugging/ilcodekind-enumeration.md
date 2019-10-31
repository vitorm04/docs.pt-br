---
title: Enumeração ILCodeKind
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ILCodeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type:
- apiref
ms.openlocfilehash: b59fbc2acefa907bb3f881b7ed183388d2e4c368
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103367"
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="142e0-102">Enumeração ILCodeKind</span><span class="sxs-lookup"><span data-stu-id="142e0-102">ILCodeKind Enumeration</span></span>
<span data-ttu-id="142e0-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="142e0-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="142e0-104">Fornece valores que especificam se o depurador é capaz de acessar variáveis locais ou o código incluído na instrumentação ReJIT do criador de perfis.</span><span class="sxs-lookup"><span data-stu-id="142e0-104">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="142e0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="142e0-105">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="142e0-106">Membros</span><span class="sxs-lookup"><span data-stu-id="142e0-106">Members</span></span>  
  
|<span data-ttu-id="142e0-107">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="142e0-107">Member name</span></span>|<span data-ttu-id="142e0-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="142e0-108">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="142e0-109">O depurador não tem acesso a informações de instrumentação ReJIT.</span><span class="sxs-lookup"><span data-stu-id="142e0-109">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="142e0-110">O depurador tem acesso a informações de instrumentação ReJIT.</span><span class="sxs-lookup"><span data-stu-id="142e0-110">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="142e0-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="142e0-111">Remarks</span></span>  
 <span data-ttu-id="142e0-112">Um membro da enumeração `ILCodeKind` pode ser passado para os métodos [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) e [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) para determinar se o depurador pode acessar variáveis adicionadas na instrumentação ReJIT do Profiler e ao [GetCodeEx ](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)método para determinar se o depurador pode acessar o Il instrumentado.</span><span class="sxs-lookup"><span data-stu-id="142e0-112">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="142e0-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="142e0-113">Requirements</span></span>  
 <span data-ttu-id="142e0-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="142e0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="142e0-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="142e0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="142e0-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="142e0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="142e0-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="142e0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="142e0-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="142e0-118">See also</span></span>

- [<span data-ttu-id="142e0-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="142e0-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="142e0-120">Interface ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="142e0-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="142e0-121">ReJIT: um guia de instruções</span><span class="sxs-lookup"><span data-stu-id="142e0-121">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
