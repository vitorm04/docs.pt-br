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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1ae7cdcdc604bef98fdb8a891c9f0118edcffea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421772"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="f2dc0-102">Método ICorDebugThread3::CreateStackWalk</span><span class="sxs-lookup"><span data-stu-id="f2dc0-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="f2dc0-103">Cria um [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objeto para o thread cuja deseja desenrolamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="f2dc0-103">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2dc0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2dc0-104">Syntax</span></span>  
  
```  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2dc0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f2dc0-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="f2dc0-106">[out] Um ponteiro para o endereço do [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objeto para o thread cuja deseja desenrolamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="f2dc0-106">[out] A pointer to address of the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2dc0-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f2dc0-107">Return Value</span></span>  
 <span data-ttu-id="f2dc0-108">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="f2dc0-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f2dc0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f2dc0-109">HRESULT</span></span>|<span data-ttu-id="f2dc0-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="f2dc0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f2dc0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f2dc0-111">S_OK</span></span>|<span data-ttu-id="f2dc0-112">O `ICorDebugStackWalk` objeto foi criado com êxito.</span><span class="sxs-lookup"><span data-stu-id="f2dc0-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="f2dc0-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f2dc0-113">E_FAIL</span></span>|<span data-ttu-id="f2dc0-114">O `ICorDebugStackWalk` objeto não foi criado.</span><span class="sxs-lookup"><span data-stu-id="f2dc0-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="f2dc0-115">Exceções</span><span class="sxs-lookup"><span data-stu-id="f2dc0-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2dc0-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="f2dc0-116">Remarks</span></span>  
 <span data-ttu-id="f2dc0-117">Se o `CreateStackWalk` método for bem-sucedido, retornado `ICorDebugStackWalk` contexto do objeto é definido como o contexto do thread atual.</span><span class="sxs-lookup"><span data-stu-id="f2dc0-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2dc0-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f2dc0-118">Requirements</span></span>  
 <span data-ttu-id="f2dc0-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2dc0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2dc0-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2dc0-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2dc0-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2dc0-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2dc0-122">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2dc0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2dc0-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2dc0-123">See Also</span></span>  
 [<span data-ttu-id="f2dc0-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f2dc0-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f2dc0-125">Depuração</span><span class="sxs-lookup"><span data-stu-id="f2dc0-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
