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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b57289e1d96a56bc4ab5cb8c07cbcac4b1d98b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416573"
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="9bd2d-102">Interface ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="9bd2d-102">ICorDebugILFrame4 Interface</span></span>
<span data-ttu-id="9bd2d-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="9bd2d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="9bd2d-104">Fornece métodos que permitem acessar as variáveis locais e inserir o código em um registro de ativação de código IL.</span><span class="sxs-lookup"><span data-stu-id="9bd2d-104">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="9bd2d-105">Um parâmetro especifica se o depurador possui acesso às variáveis e ao código adicionados na instrumentação do criador de perfil ReJIT.</span><span class="sxs-lookup"><span data-stu-id="9bd2d-105">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9bd2d-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="9bd2d-106">Methods</span></span>  
  
|<span data-ttu-id="9bd2d-107">Método</span><span class="sxs-lookup"><span data-stu-id="9bd2d-107">Method</span></span>|<span data-ttu-id="9bd2d-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bd2d-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9bd2d-109">Método EnumerateLocalVariablesEx</span><span class="sxs-lookup"><span data-stu-id="9bd2d-109">EnumerateLocalVariablesEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="9bd2d-110">Retorna uma lista das variáveis locais disponíveis em um quadro atual.</span><span class="sxs-lookup"><span data-stu-id="9bd2d-110">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="9bd2d-111">Método GetCodeEx</span><span class="sxs-lookup"><span data-stu-id="9bd2d-111">GetCodeEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="9bd2d-112">Retorna o código que esse quadro de pilha está executando.</span><span class="sxs-lookup"><span data-stu-id="9bd2d-112">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="9bd2d-113">Método GetLocalVariableEx</span><span class="sxs-lookup"><span data-stu-id="9bd2d-113">GetLocalVariableEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="9bd2d-114">Retorna o valor de uma variável local no quadro IL.</span><span class="sxs-lookup"><span data-stu-id="9bd2d-114">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bd2d-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="9bd2d-115">Remarks</span></span>  
 <span data-ttu-id="9bd2d-116">Esses métodos oferecem funcionalidade além fornecida pelo [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), e [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) métodos.</span><span class="sxs-lookup"><span data-stu-id="9bd2d-116">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), and [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="9bd2d-117">Cada método inclui um parâmetro `flags` que especifica se as variáveis locais adicionais ou o código definido por uma solicitação do ReJIT do criador de perfil estão visíveis.</span><span class="sxs-lookup"><span data-stu-id="9bd2d-117">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bd2d-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9bd2d-118">Requirements</span></span>  
 <span data-ttu-id="9bd2d-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bd2d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bd2d-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9bd2d-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9bd2d-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9bd2d-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bd2d-122">**Versões do .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bd2d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bd2d-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bd2d-123">See Also</span></span>  
 [<span data-ttu-id="9bd2d-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="9bd2d-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9bd2d-125">Depuração</span><span class="sxs-lookup"><span data-stu-id="9bd2d-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
