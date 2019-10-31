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
ms.openlocfilehash: 4eb6682ac5a8b7788d97f752f249d85886fba0b6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111644"
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="40f86-102">Método ICLRDebugging::CanUnloadNow</span><span class="sxs-lookup"><span data-stu-id="40f86-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="40f86-103">Determina se uma biblioteca fornecida por uma interface [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) ainda está em uso ou pode ser descarregada.</span><span class="sxs-lookup"><span data-stu-id="40f86-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40f86-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="40f86-104">Syntax</span></span>  
  
```cpp  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40f86-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="40f86-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="40f86-106">no O endereço base de um módulo no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="40f86-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40f86-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="40f86-107">Return Value</span></span>  
 <span data-ttu-id="40f86-108">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="40f86-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="40f86-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="40f86-109">HRESULT</span></span>|<span data-ttu-id="40f86-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="40f86-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="40f86-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="40f86-111">S_OK</span></span>|<span data-ttu-id="40f86-112">O módulo que é referenciado por `hmodule` pode ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="40f86-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="40f86-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="40f86-113">S_FALSE</span></span>|<span data-ttu-id="40f86-114">O módulo que é referenciado pelo `hmodule` ainda está em uso.</span><span class="sxs-lookup"><span data-stu-id="40f86-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="40f86-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="40f86-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="40f86-116">O módulo indicado não é um módulo CLR.</span><span class="sxs-lookup"><span data-stu-id="40f86-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="40f86-117">Exceções</span><span class="sxs-lookup"><span data-stu-id="40f86-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40f86-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="40f86-118">Remarks</span></span>  
 <span data-ttu-id="40f86-119">Esse método verifica se todas as instâncias de interfaces de `ICorDebug*` foram liberadas e nenhum thread está em uma chamada no método [ICLRDebugging:: OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="40f86-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40f86-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="40f86-120">Requirements</span></span>  
 <span data-ttu-id="40f86-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40f86-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40f86-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="40f86-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40f86-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40f86-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40f86-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40f86-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40f86-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40f86-125">See also</span></span>

- [<span data-ttu-id="40f86-126">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="40f86-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="40f86-127">Depuração</span><span class="sxs-lookup"><span data-stu-id="40f86-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
