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
ms.openlocfilehash: 21890f8130ec677cb88f2f5d7ef648aa19e67e71
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213056"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="3fe68-102">Método ICorDebugNativeFrame::CanSetIP</span><span class="sxs-lookup"><span data-stu-id="3fe68-102">ICorDebugNativeFrame::CanSetIP Method</span></span>
<span data-ttu-id="3fe68-103">Obtém um HRESULT que indica se é seguro definir o ponteiro de instrução (IP) para o local de deslocamento especificado no código nativo.</span><span class="sxs-lookup"><span data-stu-id="3fe68-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fe68-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3fe68-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fe68-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3fe68-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="3fe68-106">no A configuração desejada para o ponteiro de instrução.</span><span class="sxs-lookup"><span data-stu-id="3fe68-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fe68-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="3fe68-107">Remarks</span></span>  
 <span data-ttu-id="3fe68-108">Use o `CanSetIP` método antes de chamar o método [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3fe68-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="3fe68-109">Se `CanSetIP` o retornar qualquer HRESULT diferente de S_OK, você ainda poderá invocar `ICorDebugNativeFrame::SetIP` , mas não há nenhuma garantia de que o depurador continuará a execução segura e correta do código que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="3fe68-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fe68-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3fe68-110">Requirements</span></span>  
 <span data-ttu-id="3fe68-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fe68-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fe68-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3fe68-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fe68-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fe68-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fe68-114">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fe68-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fe68-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="3fe68-115">See also</span></span>
