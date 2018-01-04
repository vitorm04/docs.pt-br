---
title: "ICorDebugILFrame4::Método EnumerateLocalVariablesEx"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location: mscordbi.dll
api_type: COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c82ecd9045deb772e31e549bf1050f85b148fd0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a><span data-ttu-id="0aa05-102">ICorDebugILFrame4::Método EnumerateLocalVariablesEx</span><span class="sxs-lookup"><span data-stu-id="0aa05-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Method</span></span>
<span data-ttu-id="0aa05-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="0aa05-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="0aa05-104">Obtém um enumerador da variável local no quadro e, opcionalmente, inclui variáveis incluídas na instrumentação ReJIT do criador de perfis.</span><span class="sxs-lookup"><span data-stu-id="0aa05-104">Gets an enumerator for the local variable in the frame, and optionally includes variables added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aa05-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0aa05-105">Syntax</span></span>  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0aa05-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0aa05-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="0aa05-107">[in] Um [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) membro de enumeração que especifica se as variáveis adicionadas no criador de perfil de instrumentação ReJIT são incluídas no quadro.</span><span class="sxs-lookup"><span data-stu-id="0aa05-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether variables added in profiler ReJIT instrumentation are included in the frame.</span></span>  
  
 `ppValueEnum`  
 <span data-ttu-id="0aa05-108">[out] Um ponteiro para o endereço de um objeto de "ICorDebugValueEnum" é o enumerador para as variáveis locais nesse quadro.</span><span class="sxs-lookup"><span data-stu-id="0aa05-108">[out] A pointer to the address of an "ICorDebugValueEnum" object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0aa05-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="0aa05-109">Remarks</span></span>  
 <span data-ttu-id="0aa05-110">Esse método é semelhante do [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) método, exceto que ele acessa opcionalmente variáveis adicionadas ReJIT instrumentação do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="0aa05-110">This method is similar to the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) method, except that it optionally accesses variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="0aa05-111">Configuração `flags` para `ILCODE_ORIGINAL_IL` é equivalente a chamar [Icordebugilframe](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md).</span><span class="sxs-lookup"><span data-stu-id="0aa05-111">Setting `flags` to `ILCODE_ORIGINAL_IL` is equivalent to calling [ICorDebugILFrame::EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md).</span></span> <span data-ttu-id="0aa05-112">Configurar `flags` para `ILCODE_REJIT_IL` permite ao depurador acessar as variáveis locais incluídas na instrumentação ReJIT do criador de perfis.</span><span class="sxs-lookup"><span data-stu-id="0aa05-112">Setting `flags` to `ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="0aa05-113">Se a linguagem intermediária (IL) não estiver instrumentada, a enumeração estará vazia e o método retornará `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="0aa05-113">If the intermediate language (IL) is not instrumented, the enumeration is empty and the method returns `S_OK`.</span></span>  
  
 <span data-ttu-id="0aa05-114">O enumerador poderá não incluir todas as variáveis locais no método em execução, considerando que algumas delas podem não estar ativas.</span><span class="sxs-lookup"><span data-stu-id="0aa05-114">The enumerator may not include all of the local variables in the running method, since some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0aa05-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0aa05-115">Requirements</span></span>  
 <span data-ttu-id="0aa05-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0aa05-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0aa05-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0aa05-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0aa05-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0aa05-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0aa05-119">**Versões do .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0aa05-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aa05-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0aa05-120">See Also</span></span>  
 [<span data-ttu-id="0aa05-121">Interface ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="0aa05-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="0aa05-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="0aa05-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="0aa05-123">ReJIT: Um guia de instruções</span><span class="sxs-lookup"><span data-stu-id="0aa05-123">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
