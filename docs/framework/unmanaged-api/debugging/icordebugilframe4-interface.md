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
ms.openlocfilehash: 7f1c5d7a6fdae3e4c5a66c9aa4a82911105f4597
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788498"
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="a626a-102">Interface ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="a626a-102">ICorDebugILFrame4 Interface</span></span>
<span data-ttu-id="a626a-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="a626a-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="a626a-104">Fornece métodos que permitem acessar as variáveis locais e inserir o código em um registro de ativação de código IL.</span><span class="sxs-lookup"><span data-stu-id="a626a-104">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="a626a-105">Um parâmetro especifica se o depurador possui acesso às variáveis e ao código adicionados na instrumentação do criador de perfil ReJIT.</span><span class="sxs-lookup"><span data-stu-id="a626a-105">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a626a-106">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a626a-106">Methods</span></span>  
  
|<span data-ttu-id="a626a-107">Método</span><span class="sxs-lookup"><span data-stu-id="a626a-107">Method</span></span>|<span data-ttu-id="a626a-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="a626a-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a626a-109">Método EnumerateLocalVariablesEx</span><span class="sxs-lookup"><span data-stu-id="a626a-109">EnumerateLocalVariablesEx Method</span></span>](icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="a626a-110">Retorna uma lista das variáveis locais disponíveis em um quadro atual.</span><span class="sxs-lookup"><span data-stu-id="a626a-110">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="a626a-111">Método GetCodeEx</span><span class="sxs-lookup"><span data-stu-id="a626a-111">GetCodeEx Method</span></span>](icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="a626a-112">Retorna o código que esse quadro de pilha está executando.</span><span class="sxs-lookup"><span data-stu-id="a626a-112">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="a626a-113">Método GetLocalVariableEx</span><span class="sxs-lookup"><span data-stu-id="a626a-113">GetLocalVariableEx Method</span></span>](icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="a626a-114">Retorna o valor de uma variável local no quadro IL.</span><span class="sxs-lookup"><span data-stu-id="a626a-114">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a626a-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="a626a-115">Remarks</span></span>  
 <span data-ttu-id="a626a-116">Esses métodos oferecem funcionalidade além da fornecida pelos métodos [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md), [GetCode](icordebugframe-getcode-method.md)e [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a626a-116">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md), [GetCode](icordebugframe-getcode-method.md), and [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="a626a-117">Cada método inclui um parâmetro `flags` que especifica se as variáveis locais adicionais ou o código definido por uma solicitação do ReJIT do criador de perfil estão visíveis.</span><span class="sxs-lookup"><span data-stu-id="a626a-117">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a626a-118">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="a626a-118">Requirements</span></span>  
 <span data-ttu-id="a626a-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a626a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a626a-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a626a-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a626a-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a626a-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a626a-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a626a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a626a-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="a626a-123">See also</span></span>

- [<span data-ttu-id="a626a-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a626a-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a626a-125">Depuração</span><span class="sxs-lookup"><span data-stu-id="a626a-125">Debugging</span></span>](index.md)
