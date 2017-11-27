---
title: "Método ICLRDebugging::CanUnloadNow"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugging.CanUnloadNow Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDebugging::CanUnloadNow
helpviewer_keywords:
- CanUnloadNow method [.NET Framework debugging]
- ICLRDebugging::CanUnloadNow method [.NET Framework debugging]
ms.assetid: 62e0630c-8cb7-45d2-b622-5a472abfd8cf
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b013231666ca6dfde5ab16e58023da1ae2a72941
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="4a9a2-102">Método ICLRDebugging::CanUnloadNow</span><span class="sxs-lookup"><span data-stu-id="4a9a2-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="4a9a2-103">Determina se uma biblioteca que foi fornecida por um [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface ainda está em uso ou pode ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="4a9a2-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a9a2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a9a2-104">Syntax</span></span>  
  
```  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a9a2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4a9a2-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="4a9a2-106">[in] O endereço base de um módulo no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="4a9a2-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a9a2-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4a9a2-107">Return Value</span></span>  
 <span data-ttu-id="4a9a2-108">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="4a9a2-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4a9a2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4a9a2-109">HRESULT</span></span>|<span data-ttu-id="4a9a2-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a9a2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4a9a2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4a9a2-111">S_OK</span></span>|<span data-ttu-id="4a9a2-112">O módulo que é referenciado por `hmodule` pode ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="4a9a2-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="4a9a2-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="4a9a2-113">S_FALSE</span></span>|<span data-ttu-id="4a9a2-114">O módulo que é referenciado por `hmodule` ainda está em uso.</span><span class="sxs-lookup"><span data-stu-id="4a9a2-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="4a9a2-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="4a9a2-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="4a9a2-116">O módulo indicado não é um módulo CLR.</span><span class="sxs-lookup"><span data-stu-id="4a9a2-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="4a9a2-117">Exceções</span><span class="sxs-lookup"><span data-stu-id="4a9a2-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a9a2-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a9a2-118">Remarks</span></span>  
 <span data-ttu-id="4a9a2-119">Esse método verifica se todas as instâncias do `ICorDebug*` interfaces foram lançadas e nenhum thread está dentro de uma chamada para o [Iclrdebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="4a9a2-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a9a2-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a9a2-120">Requirements</span></span>  
 <span data-ttu-id="4a9a2-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a9a2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a9a2-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a9a2-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a9a2-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a9a2-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a9a2-124">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a9a2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a9a2-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a9a2-125">See Also</span></span>  
 [<span data-ttu-id="4a9a2-126">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="4a9a2-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="4a9a2-127">Depuração</span><span class="sxs-lookup"><span data-stu-id="4a9a2-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
