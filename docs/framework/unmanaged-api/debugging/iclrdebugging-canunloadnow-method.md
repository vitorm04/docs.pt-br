---
title: Método ICLRDebugging::CanUnloadNow
ms.date: 03/30/2017
api_name:
- ICLRDebugging.CanUnloadNow Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::CanUnloadNow
helpviewer_keywords:
- CanUnloadNow method [.NET Framework debugging]
- ICLRDebugging::CanUnloadNow method [.NET Framework debugging]
ms.assetid: 62e0630c-8cb7-45d2-b622-5a472abfd8cf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f18d73a6740d44408acf964c68f0b58e75d3b226
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492082"
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="443f8-102">Método ICLRDebugging::CanUnloadNow</span><span class="sxs-lookup"><span data-stu-id="443f8-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="443f8-103">Determina se uma biblioteca que foi fornecida por um [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface ainda está em uso ou pode ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="443f8-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="443f8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="443f8-104">Syntax</span></span>  
  
```  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="443f8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="443f8-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="443f8-106">[in] O endereço básico de um módulo no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="443f8-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="443f8-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="443f8-107">Return Value</span></span>  
 <span data-ttu-id="443f8-108">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="443f8-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="443f8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="443f8-109">HRESULT</span></span>|<span data-ttu-id="443f8-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="443f8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="443f8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="443f8-111">S_OK</span></span>|<span data-ttu-id="443f8-112">O módulo que é referenciado por `hmodule` pode ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="443f8-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="443f8-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="443f8-113">S_FALSE</span></span>|<span data-ttu-id="443f8-114">O módulo que é referenciado por `hmodule` ainda está em uso.</span><span class="sxs-lookup"><span data-stu-id="443f8-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="443f8-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="443f8-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="443f8-116">O módulo indicado não é um módulo CLR.</span><span class="sxs-lookup"><span data-stu-id="443f8-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="443f8-117">Exceções</span><span class="sxs-lookup"><span data-stu-id="443f8-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="443f8-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="443f8-118">Remarks</span></span>  
 <span data-ttu-id="443f8-119">Esse método verifica se todas as instâncias do `ICorDebug*` interfaces foram lançadas e nenhum thread está atualmente em uma chamada para o [iclrdebugging:: Openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="443f8-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="443f8-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="443f8-120">Requirements</span></span>  
 <span data-ttu-id="443f8-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="443f8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="443f8-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="443f8-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="443f8-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="443f8-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="443f8-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="443f8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="443f8-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="443f8-125">See also</span></span>
- [<span data-ttu-id="443f8-126">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="443f8-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="443f8-127">Depuração</span><span class="sxs-lookup"><span data-stu-id="443f8-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
