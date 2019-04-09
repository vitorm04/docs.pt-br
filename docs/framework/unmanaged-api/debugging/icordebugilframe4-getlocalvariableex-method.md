---
title: ICorDebugILFrame4::Método GetLocalVariableEx
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetCodeEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6594bb72ce9cd2fbfa9cdafebc152a90618b810
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193077"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="281ef-102">ICorDebugILFrame4::Método GetLocalVariableEx</span><span class="sxs-lookup"><span data-stu-id="281ef-102">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>
<span data-ttu-id="281ef-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="281ef-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="281ef-104">Obtém o valor da variável local especificada neste quadro de pilha de linguagem intermediária (IL) e, opcionalmente, acessa uma variável adicionada na instrumentação do criador de perfil ReJIT.</span><span class="sxs-lookup"><span data-stu-id="281ef-104">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="281ef-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="281ef-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="281ef-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="281ef-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="281ef-107">[in] Uma [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) membro de enumeração que especifica se uma variável adicionada na instrumentação ReJIT do criador está incluída no quadro.</span><span class="sxs-lookup"><span data-stu-id="281ef-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="281ef-108">[in] O índice da variável local no quadro de pilha IL.</span><span class="sxs-lookup"><span data-stu-id="281ef-108">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="281ef-109">[out] Um ponteiro para o endereço de um objeto de "ICorDebugValue" que representa o valor recuperado.</span><span class="sxs-lookup"><span data-stu-id="281ef-109">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="281ef-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="281ef-110">Remarks</span></span>  
 <span data-ttu-id="281ef-111">Esse método é semelhante para o [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) método, exceto que ele acessa, opcionalmente, uma variável adicionada na instrumentação ReJIT do criador.</span><span class="sxs-lookup"><span data-stu-id="281ef-111">This method is similar to the [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="281ef-112">Chamar esse método com um `flags` valor de `ILCODE_ORIGINAL_IL` é equivalente a chamar [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); se o método for instrumentado com variáveis locais adicionais, essas variáveis não podem ser acessadas.</span><span class="sxs-lookup"><span data-stu-id="281ef-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> `ILCODE_REJIT_IL` <span data-ttu-id="281ef-113">permite ao depurador acessar as variáveis locais adicionadas na instrumentação ReJIT do criador.</span><span class="sxs-lookup"><span data-stu-id="281ef-113">allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="281ef-114">Se o IL não for instrumentado, o método retorna `E_INVALIDARG`.</span><span class="sxs-lookup"><span data-stu-id="281ef-114">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="281ef-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="281ef-115">Requirements</span></span>  
 <span data-ttu-id="281ef-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="281ef-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="281ef-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="281ef-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="281ef-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="281ef-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="281ef-119">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="281ef-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="281ef-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="281ef-120">See also</span></span>

- [<span data-ttu-id="281ef-121">Interface ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="281ef-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="281ef-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="281ef-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="281ef-123">ReJIT: Um guia de instruções</span><span class="sxs-lookup"><span data-stu-id="281ef-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
