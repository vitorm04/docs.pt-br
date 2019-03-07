---
title: ICorDebugILFrame4::Método GetCodeEx
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc7bee8c56d7b904bf881efb652a2517d151c31a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475756"
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="4f4e0-102">ICorDebugILFrame4::Método GetCodeEx</span><span class="sxs-lookup"><span data-stu-id="4f4e0-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="4f4e0-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="4f4e0-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="4f4e0-104">Obtém um ponteiro para o código que este registro de ativação está executando.</span><span class="sxs-lookup"><span data-stu-id="4f4e0-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f4e0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f4e0-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f4e0-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4f4e0-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="4f4e0-107">[in] Uma [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) membro de enumeração que especifica se a IL (linguagem intermediária) definida pela solicitação do ReJIT do criador de perfil é incluída no quadro.</span><span class="sxs-lookup"><span data-stu-id="4f4e0-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="4f4e0-108">[out] Um ponteiro para o endereço de um objeto de "ICorDebugCode" que representa o código que este registro de ativação está em execução.</span><span class="sxs-lookup"><span data-stu-id="4f4e0-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f4e0-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="4f4e0-109">Remarks</span></span>  
 <span data-ttu-id="4f4e0-110">Esse método é semelhante para o [icordebugframe:: Getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) método, exceto que ele acessa opcionalmente definido pela solicitação do ReJIT do criador de perfil de código.</span><span class="sxs-lookup"><span data-stu-id="4f4e0-110">This method is similar to the [ICorDebugFrame::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="4f4e0-111">Chamar esse método com um `flags` valor de `ILCODE_ORIGINAL_IL` é equivalente a chamar [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); se o método for instrumentado, sua IL não estará acessível.</span><span class="sxs-lookup"><span data-stu-id="4f4e0-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="4f4e0-112">`ILCODE_REJIT_IL` permite que o depurador acesse a IL definida pela solicitação ReJIT do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="4f4e0-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="4f4e0-113">Se o IL não for instrumentado, `ppCode` está **nulo**, e o método retornará `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="4f4e0-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f4e0-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4f4e0-114">Requirements</span></span>  
 <span data-ttu-id="4f4e0-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f4e0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f4e0-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f4e0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f4e0-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f4e0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f4e0-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f4e0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f4e0-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f4e0-119">See also</span></span>
- [<span data-ttu-id="4f4e0-120">Interface ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="4f4e0-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="4f4e0-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4f4e0-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="4f4e0-122">ReJIT: Um guia de instruções</span><span class="sxs-lookup"><span data-stu-id="4f4e0-122">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
