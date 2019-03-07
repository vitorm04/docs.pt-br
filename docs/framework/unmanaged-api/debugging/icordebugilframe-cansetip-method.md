---
title: Método ICorDebugILFrame::CanSetIP
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49cef22e88613fe4c4dfb3fb35a92977977b1827
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473559"
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="f64d0-102">Método ICorDebugILFrame::CanSetIP</span><span class="sxs-lookup"><span data-stu-id="f64d0-102">ICorDebugILFrame::CanSetIP Method</span></span>
<span data-ttu-id="f64d0-103">Obtém um HRESULT que indica se é seguro definir o ponteiro de instrução para o local de deslocamento especificado no código Microsoft Intermediate Language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="f64d0-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f64d0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f64d0-104">Syntax</span></span>  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f64d0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f64d0-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="f64d0-106">[in] A configuração desejada para o ponteiro de instrução.</span><span class="sxs-lookup"><span data-stu-id="f64d0-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f64d0-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f64d0-107">Remarks</span></span>  
 <span data-ttu-id="f64d0-108">Use o `CanSetIP` método antes de chamar o [icordebugilframe:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="f64d0-108">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="f64d0-109">Se `CanSetIP` retorna qualquer HRESULT que não seja S_OK, você ainda pode invocar `ICorDebugILFrame::SetIP`, mas não há nenhuma garantia de que o depurador continuará a execução de segura e correta do código que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="f64d0-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f64d0-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f64d0-110">Requirements</span></span>  
 <span data-ttu-id="f64d0-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f64d0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f64d0-112">**Cabeçalho:** CorDebug.idl, CorDebug,h</span><span class="sxs-lookup"><span data-stu-id="f64d0-112">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="f64d0-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f64d0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f64d0-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f64d0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
