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
ms.openlocfilehash: f2850e6c9cbb2250a08ab4a0e34c69e377d3a23d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83375849"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="92985-102">Método ICorDebugThread3::CreateStackWalk</span><span class="sxs-lookup"><span data-stu-id="92985-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="92985-103">Cria um objeto [ICorDebugStackWalk](icordebugstackwalk-interface.md) para o thread cuja pilha você deseja desenrolar.</span><span class="sxs-lookup"><span data-stu-id="92985-103">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92985-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92985-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92985-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="92985-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="92985-106">fora Um ponteiro para o endereço do objeto [ICorDebugStackWalk](icordebugstackwalk-interface.md) para o thread cuja pilha você deseja desenrolar.</span><span class="sxs-lookup"><span data-stu-id="92985-106">[out] A pointer to address of the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92985-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="92985-107">Return Value</span></span>  
 <span data-ttu-id="92985-108">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="92985-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="92985-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="92985-109">HRESULT</span></span>|<span data-ttu-id="92985-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="92985-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="92985-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="92985-111">S_OK</span></span>|<span data-ttu-id="92985-112">O `ICorDebugStackWalk` objeto foi criado com êxito.</span><span class="sxs-lookup"><span data-stu-id="92985-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="92985-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="92985-113">E_FAIL</span></span>|<span data-ttu-id="92985-114">O `ICorDebugStackWalk` objeto não foi criado.</span><span class="sxs-lookup"><span data-stu-id="92985-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="92985-115">Exceções</span><span class="sxs-lookup"><span data-stu-id="92985-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92985-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="92985-116">Remarks</span></span>  
 <span data-ttu-id="92985-117">Se o `CreateStackWalk` método tiver sucesso, o `ICorDebugStackWalk` contexto do objeto retornado será definido como o contexto atual do thread.</span><span class="sxs-lookup"><span data-stu-id="92985-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92985-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="92985-118">Requirements</span></span>  
 <span data-ttu-id="92985-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92985-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92985-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92985-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92985-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92985-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92985-122">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92985-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92985-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="92985-123">See also</span></span>

- [<span data-ttu-id="92985-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="92985-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="92985-125">Depuração</span><span class="sxs-lookup"><span data-stu-id="92985-125">Debugging</span></span>](index.md)
