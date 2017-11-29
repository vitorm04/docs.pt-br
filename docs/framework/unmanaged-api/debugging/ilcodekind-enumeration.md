---
title: "Enumeração ILCodeKind"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ILCodeKind
api_location: mscordbi.dll
api_type: COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61fd5ad93c198000556e8e0be3a278a842ab5716
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="6e09d-102">Enumeração ILCodeKind</span><span class="sxs-lookup"><span data-stu-id="6e09d-102">ILCodeKind Enumeration</span></span>
<span data-ttu-id="6e09d-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="6e09d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="6e09d-104">Fornece valores que especificam se o depurador é capaz de acessar variáveis locais ou o código incluído na instrumentação ReJIT do criador de perfis.</span><span class="sxs-lookup"><span data-stu-id="6e09d-104">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e09d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6e09d-105">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="6e09d-106">Membros</span><span class="sxs-lookup"><span data-stu-id="6e09d-106">Members</span></span>  
  
|<span data-ttu-id="6e09d-107">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="6e09d-107">Member name</span></span>|<span data-ttu-id="6e09d-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e09d-108">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="6e09d-109">O depurador não tem acesso a informações de instrumentação ReJIT.</span><span class="sxs-lookup"><span data-stu-id="6e09d-109">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="6e09d-110">O depurador tem acesso a informações de instrumentação ReJIT.</span><span class="sxs-lookup"><span data-stu-id="6e09d-110">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e09d-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="6e09d-111">Remarks</span></span>  
 <span data-ttu-id="6e09d-112">Membro de `ILCodeKind` enumeração pode ser passada para o [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) e [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) métodos para determinar se o depurador pode acessar variáveis adicionadas no criador de perfil Instrumentação de ReJIT e o [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) método para determinar se o depurador pode acessar instrumentado IL.</span><span class="sxs-lookup"><span data-stu-id="6e09d-112">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e09d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6e09d-113">Requirements</span></span>  
 <span data-ttu-id="6e09d-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e09d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e09d-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e09d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e09d-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e09d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e09d-117">**Versões do .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e09d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e09d-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e09d-118">See Also</span></span>  
 [<span data-ttu-id="6e09d-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="6e09d-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="6e09d-120">Interface ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="6e09d-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="6e09d-121">ReJIT: Um guia de instruções</span><span class="sxs-lookup"><span data-stu-id="6e09d-121">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
