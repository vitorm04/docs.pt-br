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
ms.openlocfilehash: d266ec7f82d7d4c7c66f137aafc1c8865d6f8889
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792799"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="22a28-102">Método ICorDebugNativeFrame::CanSetIP</span><span class="sxs-lookup"><span data-stu-id="22a28-102">ICorDebugNativeFrame::CanSetIP Method</span></span>
<span data-ttu-id="22a28-103">Obtém um HRESULT que indica se é seguro definir o ponteiro de instrução (IP) para o local de deslocamento especificado no código nativo.</span><span class="sxs-lookup"><span data-stu-id="22a28-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22a28-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22a28-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22a28-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="22a28-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="22a28-106">no A configuração desejada para o ponteiro de instrução.</span><span class="sxs-lookup"><span data-stu-id="22a28-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22a28-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="22a28-107">Remarks</span></span>  
 <span data-ttu-id="22a28-108">Use o método `CanSetIP` antes de chamar o método [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md) .</span><span class="sxs-lookup"><span data-stu-id="22a28-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="22a28-109">Se `CanSetIP` retornar qualquer HRESULT diferente de S_OK, você ainda poderá invocar `ICorDebugNativeFrame::SetIP`, mas não haverá nenhuma garantia de que o depurador continuará a execução segura e correta do código que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="22a28-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22a28-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="22a28-110">Requirements</span></span>  
 <span data-ttu-id="22a28-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22a28-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22a28-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="22a28-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22a28-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22a28-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22a28-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22a28-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22a28-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="22a28-115">See also</span></span>
