---
title: Interface ICorDebugILFrame4
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame4
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type:
- apiref
ms.openlocfilehash: 010d73309ae21f9a593f72533691bdd95fbd4132
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130844"
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="7b757-102">Interface ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="7b757-102">ICorDebugILFrame4 Interface</span></span>
<span data-ttu-id="7b757-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="7b757-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="7b757-104">Fornece métodos que permitem acessar as variáveis locais e inserir o código em um registro de ativação de código IL.</span><span class="sxs-lookup"><span data-stu-id="7b757-104">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="7b757-105">Um parâmetro especifica se o depurador possui acesso às variáveis e ao código adicionados na instrumentação do criador de perfil ReJIT.</span><span class="sxs-lookup"><span data-stu-id="7b757-105">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7b757-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="7b757-106">Methods</span></span>  
  
|<span data-ttu-id="7b757-107">Método</span><span class="sxs-lookup"><span data-stu-id="7b757-107">Method</span></span>|<span data-ttu-id="7b757-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b757-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7b757-109">Método EnumerateLocalVariablesEx</span><span class="sxs-lookup"><span data-stu-id="7b757-109">EnumerateLocalVariablesEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="7b757-110">Retorna uma lista das variáveis locais disponíveis em um quadro atual.</span><span class="sxs-lookup"><span data-stu-id="7b757-110">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="7b757-111">Método GetCodeEx</span><span class="sxs-lookup"><span data-stu-id="7b757-111">GetCodeEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="7b757-112">Retorna o código que esse quadro de pilha está executando.</span><span class="sxs-lookup"><span data-stu-id="7b757-112">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="7b757-113">Método GetLocalVariableEx</span><span class="sxs-lookup"><span data-stu-id="7b757-113">GetLocalVariableEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="7b757-114">Retorna o valor de uma variável local no quadro IL.</span><span class="sxs-lookup"><span data-stu-id="7b757-114">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b757-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="7b757-115">Remarks</span></span>  
 <span data-ttu-id="7b757-116">Esses métodos oferecem funcionalidade além da fornecida pelos métodos [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)e [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7b757-116">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), and [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="7b757-117">Cada método inclui um parâmetro `flags` que especifica se as variáveis locais adicionais ou o código definido por uma solicitação do ReJIT do criador de perfil estão visíveis.</span><span class="sxs-lookup"><span data-stu-id="7b757-117">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b757-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7b757-118">Requirements</span></span>  
 <span data-ttu-id="7b757-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b757-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b757-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b757-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b757-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b757-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b757-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b757-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b757-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b757-123">See also</span></span>

- [<span data-ttu-id="7b757-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="7b757-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7b757-125">Depuração</span><span class="sxs-lookup"><span data-stu-id="7b757-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
