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
ms.openlocfilehash: b9d27c3e3cd42039aeefcb517ecc81eadeb5c183
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557418"
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="8292f-102">Enumeração ILCodeKind</span><span class="sxs-lookup"><span data-stu-id="8292f-102">ILCodeKind Enumeration</span></span>
<span data-ttu-id="8292f-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="8292f-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="8292f-104">Fornece valores que especificam se o depurador é capaz de acessar variáveis locais ou o código incluído na instrumentação ReJIT do criador de perfis.</span><span class="sxs-lookup"><span data-stu-id="8292f-104">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8292f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8292f-105">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="8292f-106">Membros</span><span class="sxs-lookup"><span data-stu-id="8292f-106">Members</span></span>  
  
|<span data-ttu-id="8292f-107">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="8292f-107">Member name</span></span>|<span data-ttu-id="8292f-108">Description</span><span class="sxs-lookup"><span data-stu-id="8292f-108">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="8292f-109">O depurador não tem acesso a informações de instrumentação ReJIT.</span><span class="sxs-lookup"><span data-stu-id="8292f-109">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="8292f-110">O depurador tem acesso a informações de instrumentação ReJIT.</span><span class="sxs-lookup"><span data-stu-id="8292f-110">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8292f-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="8292f-111">Remarks</span></span>  
 <span data-ttu-id="8292f-112">Um membro da `ILCodeKind` enumeração pode ser passado para os métodos [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) e [GetLocalVariableEx](icordebugilframe4-getlocalvariableex-method.md) para determinar se o depurador pode acessar variáveis adicionadas na instrumentação ReJIT do Profiler e ao método [GetCodeEx](icordebugilframe4-getcodeex-method.md) para determinar se o depurador pode acessar o Il instrumentado.</span><span class="sxs-lookup"><span data-stu-id="8292f-112">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8292f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8292f-113">Requirements</span></span>  
 <span data-ttu-id="8292f-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8292f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8292f-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8292f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8292f-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8292f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8292f-117">**.NET Framework versões:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8292f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8292f-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="8292f-118">See also</span></span>

- [<span data-ttu-id="8292f-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="8292f-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="8292f-120">Interface ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="8292f-120">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="8292f-121">ReJIT: um guia de instruções</span><span class="sxs-lookup"><span data-stu-id="8292f-121">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
