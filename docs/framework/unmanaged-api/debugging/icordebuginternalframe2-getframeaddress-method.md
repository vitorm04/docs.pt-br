---
title: Método ICorDebugInternalFrame2::GetFrameAddress
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.GetFrameAddress Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::GetFrameAddress
helpviewer_keywords:
- GetFrameAddress method [.NET Framework debugging]
- ICorDebugInternalFrame2::GetFrameAddress method [.NET Framework debugging]
ms.assetid: 4ee8d058-ffc8-4967-9133-a5adfef4e518
topic_type:
- apiref
ms.openlocfilehash: 51c8f9a2b66d7b2553949056f7cdbedcf5ea37d6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209910"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="1f0fd-102">Método ICorDebugInternalFrame2::GetFrameAddress</span><span class="sxs-lookup"><span data-stu-id="1f0fd-102">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>
<span data-ttu-id="1f0fd-103">Retorna o endereço da pilha do quadro interno.</span><span class="sxs-lookup"><span data-stu-id="1f0fd-103">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f0fd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1f0fd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f0fd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1f0fd-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="1f0fd-106">fora Ponteiro para o `CORDB_ADDRESS` para o quadro interno.</span><span class="sxs-lookup"><span data-stu-id="1f0fd-106">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f0fd-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="1f0fd-107">Return Value</span></span>  
 <span data-ttu-id="1f0fd-108">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="1f0fd-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1f0fd-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1f0fd-109">HRESULT</span></span>|<span data-ttu-id="1f0fd-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="1f0fd-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1f0fd-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1f0fd-111">S_OK</span></span>|<span data-ttu-id="1f0fd-112">O endereço do quadro interno foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="1f0fd-112">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="1f0fd-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1f0fd-113">E_FAIL</span></span>|<span data-ttu-id="1f0fd-114">Não foi possível retornar o endereço do quadro interno.</span><span class="sxs-lookup"><span data-stu-id="1f0fd-114">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="1f0fd-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1f0fd-115">E_INVALIDARG</span></span>|<span data-ttu-id="1f0fd-116">`pAddress` é `null`.</span><span class="sxs-lookup"><span data-stu-id="1f0fd-116">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f0fd-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="1f0fd-117">Remarks</span></span>  
 <span data-ttu-id="1f0fd-118">O valor retornado em `pAddress` pode ser usado para determinar o local do quadro interno em relação a outros quadros na pilha.</span><span class="sxs-lookup"><span data-stu-id="1f0fd-118">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="1f0fd-119">Mesmo em computadores baseados em IA-64, o quadro interno reside somente na pilha e não há nenhum ponteiro correspondente para um repositório de backup.</span><span class="sxs-lookup"><span data-stu-id="1f0fd-119">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f0fd-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1f0fd-120">Requirements</span></span>  
 <span data-ttu-id="1f0fd-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f0fd-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f0fd-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f0fd-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f0fd-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f0fd-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f0fd-124">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f0fd-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f0fd-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="1f0fd-125">See also</span></span>

- [<span data-ttu-id="1f0fd-126">Interface ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="1f0fd-126">ICorDebugInternalFrame2 Interface</span></span>](icordebuginternalframe2-interface.md)
- [<span data-ttu-id="1f0fd-127">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1f0fd-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="1f0fd-128">Depuração</span><span class="sxs-lookup"><span data-stu-id="1f0fd-128">Debugging</span></span>](index.md)
