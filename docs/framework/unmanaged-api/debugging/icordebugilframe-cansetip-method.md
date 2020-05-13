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
ms.openlocfilehash: 2bd4ab4a080461c56b0287d24aa288847445d803
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210313"
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="d9d3e-102">Método ICorDebugILFrame::CanSetIP</span><span class="sxs-lookup"><span data-stu-id="d9d3e-102">ICorDebugILFrame::CanSetIP Method</span></span>
<span data-ttu-id="d9d3e-103">Obtém um HRESULT que indica se é seguro definir o ponteiro de instrução para o local de deslocamento especificado no código MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="d9d3e-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9d3e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9d3e-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9d3e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d9d3e-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="d9d3e-106">no A configuração desejada para o ponteiro de instrução.</span><span class="sxs-lookup"><span data-stu-id="d9d3e-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9d3e-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d9d3e-107">Remarks</span></span>  
 <span data-ttu-id="d9d3e-108">Use o `CanSetIP` método antes de chamar o método [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d9d3e-108">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="d9d3e-109">Se `CanSetIP` o retornar qualquer HRESULT diferente de S_OK, você ainda poderá invocar `ICorDebugILFrame::SetIP` , mas não há nenhuma garantia de que o depurador continuará a execução segura e correta do código que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="d9d3e-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9d3e-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d9d3e-110">Requirements</span></span>  
 <span data-ttu-id="d9d3e-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9d3e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9d3e-112">**Cabeçalho:** CorDebug. idl, CorDebug, h</span><span class="sxs-lookup"><span data-stu-id="d9d3e-112">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="d9d3e-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9d3e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9d3e-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9d3e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
