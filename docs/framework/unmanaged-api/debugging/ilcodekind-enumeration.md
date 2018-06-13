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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0881b3903200c023cfa2fe32bf89f62234da29c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424021"
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="a8aab-102">Enumeração ILCodeKind</span><span class="sxs-lookup"><span data-stu-id="a8aab-102">ILCodeKind Enumeration</span></span>
<span data-ttu-id="a8aab-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="a8aab-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="a8aab-104">Fornece valores que especificam se o depurador é capaz de acessar variáveis locais ou o código incluído na instrumentação ReJIT do criador de perfis.</span><span class="sxs-lookup"><span data-stu-id="a8aab-104">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8aab-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8aab-105">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="a8aab-106">Membros</span><span class="sxs-lookup"><span data-stu-id="a8aab-106">Members</span></span>  
  
|<span data-ttu-id="a8aab-107">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="a8aab-107">Member name</span></span>|<span data-ttu-id="a8aab-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8aab-108">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="a8aab-109">O depurador não tem acesso a informações de instrumentação ReJIT.</span><span class="sxs-lookup"><span data-stu-id="a8aab-109">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="a8aab-110">O depurador tem acesso a informações de instrumentação ReJIT.</span><span class="sxs-lookup"><span data-stu-id="a8aab-110">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8aab-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="a8aab-111">Remarks</span></span>  
 <span data-ttu-id="a8aab-112">Membro de `ILCodeKind` enumeração pode ser passada para o [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) e [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) métodos para determinar se o depurador pode acessar variáveis adicionadas no criador de perfil Instrumentação de ReJIT e o [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) método para determinar se o depurador pode acessar instrumentado IL.</span><span class="sxs-lookup"><span data-stu-id="a8aab-112">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8aab-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a8aab-113">Requirements</span></span>  
 <span data-ttu-id="a8aab-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8aab-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8aab-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a8aab-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8aab-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8aab-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8aab-117">**Versões do .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8aab-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8aab-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8aab-118">See Also</span></span>  
 [<span data-ttu-id="a8aab-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="a8aab-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="a8aab-120">Interface ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="a8aab-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="a8aab-121">ReJIT: Um guia de instruções</span><span class="sxs-lookup"><span data-stu-id="a8aab-121">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
