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
ms.openlocfilehash: 57d83d1f301cbfd43f8f553d9aef4beb3baf95f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131077"
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="96e52-102">Método ICorDebugILFrame::CanSetIP</span><span class="sxs-lookup"><span data-stu-id="96e52-102">ICorDebugILFrame::CanSetIP Method</span></span>
<span data-ttu-id="96e52-103">Obtém um HRESULT que indica se é seguro definir o ponteiro de instrução para o local de deslocamento especificado no código MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="96e52-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96e52-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96e52-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96e52-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="96e52-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="96e52-106">no A configuração desejada para o ponteiro de instrução.</span><span class="sxs-lookup"><span data-stu-id="96e52-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96e52-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="96e52-107">Remarks</span></span>  
 <span data-ttu-id="96e52-108">Use o método `CanSetIP` antes de chamar o método [ICorDebugILFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) .</span><span class="sxs-lookup"><span data-stu-id="96e52-108">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="96e52-109">Se `CanSetIP` retornar qualquer HRESULT diferente de S_OK, você ainda poderá invocar `ICorDebugILFrame::SetIP`, mas não haverá nenhuma garantia de que o depurador continuará a execução segura e correta do código que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="96e52-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96e52-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="96e52-110">Requirements</span></span>  
 <span data-ttu-id="96e52-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96e52-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96e52-112">**Cabeçalho:** CorDebug. idl, CorDebug, h</span><span class="sxs-lookup"><span data-stu-id="96e52-112">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="96e52-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96e52-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96e52-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96e52-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
