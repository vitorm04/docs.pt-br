---
title: "ICorDebugILFrame4::Método GetCodeEx"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILFrame4.GetLocalVariableEx
api_location: mscordbi.dll
api_type: COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5d1d480014e90d3fea9790b10e0dace5a0847ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="01208-102">ICorDebugILFrame4::Método GetCodeEx</span><span class="sxs-lookup"><span data-stu-id="01208-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="01208-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="01208-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="01208-104">Obtém um ponteiro para o código que este registro de ativação está executando.</span><span class="sxs-lookup"><span data-stu-id="01208-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01208-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="01208-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="01208-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="01208-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="01208-107">[in] Um [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) membro de enumeração que especifica se a linguagem intermediária (IL) definida pela solicitação de ReJIT do criador de perfil está incluída no quadro.</span><span class="sxs-lookup"><span data-stu-id="01208-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="01208-108">[out] Um ponteiro para o endereço de um objeto de "ICorDebugCode" que representa o código que está em execução deste quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="01208-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01208-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="01208-109">Remarks</span></span>  
 <span data-ttu-id="01208-110">Esse método é semelhante do [Icordebugframe](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) método, exceto que ele acessa opcionalmente definido pela solicitação de ReJIT do criador de perfil de código.</span><span class="sxs-lookup"><span data-stu-id="01208-110">This method is similar to the [ICorDebugFrame::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="01208-111">Chamar este método com um `flags` valor `ILCODE_ORIGINAL_IL` é equivalente a chamar [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); se o método é instrumentado, seu IL não estará acessível.</span><span class="sxs-lookup"><span data-stu-id="01208-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="01208-112">`ILCODE_REJIT_IL` permite que o depurador acesse a IL definida pela solicitação ReJIT do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="01208-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="01208-113">Se o IL não está instrumentado, `ppCode` é **nulo**, e o método retornará `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="01208-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01208-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="01208-114">Requirements</span></span>  
 <span data-ttu-id="01208-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01208-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01208-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01208-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01208-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01208-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01208-118">**Versões do .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01208-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01208-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01208-119">See Also</span></span>  
 [<span data-ttu-id="01208-120">Interface ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="01208-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="01208-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="01208-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="01208-122">ReJIT: Um guia de instruções</span><span class="sxs-lookup"><span data-stu-id="01208-122">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
