---
title: Método ICorDebugNativeFrame::CanSetIP
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93a8c8650822c5d986e21a456d58b2dc0327f05b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479513"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="6d16a-102">Método ICorDebugNativeFrame::CanSetIP</span><span class="sxs-lookup"><span data-stu-id="6d16a-102">ICorDebugNativeFrame::CanSetIP Method</span></span>
<span data-ttu-id="6d16a-103">Obtém um HRESULT que indica se é seguro definir o ponteiro de instrução (IP) para o local de deslocamento especificado em código nativo.</span><span class="sxs-lookup"><span data-stu-id="6d16a-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d16a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6d16a-104">Syntax</span></span>  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d16a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6d16a-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="6d16a-106">[in] A configuração desejada para o ponteiro de instrução.</span><span class="sxs-lookup"><span data-stu-id="6d16a-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d16a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="6d16a-107">Remarks</span></span>  
 <span data-ttu-id="6d16a-108">Use o `CanSetIP` método antes de chamar o [icordebugnativeframe:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="6d16a-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="6d16a-109">Se `CanSetIP` retorna qualquer HRESULT que não seja S_OK, você ainda pode invocar `ICorDebugNativeFrame::SetIP`, mas não há nenhuma garantia de que o depurador continuará a execução de segura e correta do código que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="6d16a-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d16a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6d16a-110">Requirements</span></span>  
 <span data-ttu-id="6d16a-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d16a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d16a-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d16a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d16a-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d16a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d16a-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d16a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d16a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d16a-115">See also</span></span>

