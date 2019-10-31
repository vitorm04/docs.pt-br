---
title: Método ICorDebugThread3::CreateStackWalk
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.CreateStackWalk Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::CreateStackWalk
helpviewer_keywords:
- CreateStackWalk method [.NET Framework debugging]
- ICorDebugThread3::CreateStackWalk method [.NET Framework debugging]
ms.assetid: c55e35d9-f9aa-4268-94b5-dce44c61acf2
topic_type:
- apiref
ms.openlocfilehash: ca5db8c8570cedd9b0412b71058d453112a1831c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140132"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="dbd4e-102">Método ICorDebugThread3::CreateStackWalk</span><span class="sxs-lookup"><span data-stu-id="dbd4e-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="dbd4e-103">Cria um objeto [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) para o thread cuja pilha você deseja desenrolar.</span><span class="sxs-lookup"><span data-stu-id="dbd4e-103">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbd4e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dbd4e-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbd4e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dbd4e-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="dbd4e-106">fora Um ponteiro para o endereço do objeto [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) para o thread cuja pilha você deseja desenrolar.</span><span class="sxs-lookup"><span data-stu-id="dbd4e-106">[out] A pointer to address of the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dbd4e-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="dbd4e-107">Return Value</span></span>  
 <span data-ttu-id="dbd4e-108">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="dbd4e-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="dbd4e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dbd4e-109">HRESULT</span></span>|<span data-ttu-id="dbd4e-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="dbd4e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dbd4e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="dbd4e-111">S_OK</span></span>|<span data-ttu-id="dbd4e-112">O objeto `ICorDebugStackWalk` foi criado com êxito.</span><span class="sxs-lookup"><span data-stu-id="dbd4e-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="dbd4e-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dbd4e-113">E_FAIL</span></span>|<span data-ttu-id="dbd4e-114">O objeto `ICorDebugStackWalk` não foi criado.</span><span class="sxs-lookup"><span data-stu-id="dbd4e-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="dbd4e-115">Exceções</span><span class="sxs-lookup"><span data-stu-id="dbd4e-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbd4e-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="dbd4e-116">Remarks</span></span>  
 <span data-ttu-id="dbd4e-117">Se o método `CreateStackWalk` for executado com sucesso, o contexto do objeto de `ICorDebugStackWalk` retornado será definido como o contexto atual do thread.</span><span class="sxs-lookup"><span data-stu-id="dbd4e-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbd4e-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dbd4e-118">Requirements</span></span>  
 <span data-ttu-id="dbd4e-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbd4e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbd4e-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dbd4e-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dbd4e-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbd4e-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbd4e-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbd4e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbd4e-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dbd4e-123">See also</span></span>

- [<span data-ttu-id="dbd4e-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="dbd4e-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="dbd4e-125">Depuração</span><span class="sxs-lookup"><span data-stu-id="dbd4e-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
