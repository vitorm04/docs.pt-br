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
ms.openlocfilehash: 41b2e009f8f017a72147232015ea2357ae922ca1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793645"
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="ac07e-102">Método ICLRDebugging::CanUnloadNow</span><span class="sxs-lookup"><span data-stu-id="ac07e-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="ac07e-103">Determina se uma biblioteca fornecida por uma interface [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) ainda está em uso ou pode ser descarregada.</span><span class="sxs-lookup"><span data-stu-id="ac07e-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac07e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac07e-104">Syntax</span></span>  
  
```cpp  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac07e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac07e-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="ac07e-106">no O endereço base de um módulo no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="ac07e-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac07e-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ac07e-107">Return Value</span></span>  
 <span data-ttu-id="ac07e-108">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="ac07e-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ac07e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac07e-109">HRESULT</span></span>|<span data-ttu-id="ac07e-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac07e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ac07e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ac07e-111">S_OK</span></span>|<span data-ttu-id="ac07e-112">O módulo que é referenciado por `hmodule` pode ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="ac07e-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="ac07e-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ac07e-113">S_FALSE</span></span>|<span data-ttu-id="ac07e-114">O módulo que é referenciado pelo `hmodule` ainda está em uso.</span><span class="sxs-lookup"><span data-stu-id="ac07e-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="ac07e-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="ac07e-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="ac07e-116">O módulo indicado não é um módulo CLR.</span><span class="sxs-lookup"><span data-stu-id="ac07e-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="ac07e-117">Exceções</span><span class="sxs-lookup"><span data-stu-id="ac07e-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac07e-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="ac07e-118">Remarks</span></span>  
 <span data-ttu-id="ac07e-119">Esse método verifica se todas as instâncias de interfaces de `ICorDebug*` foram liberadas e nenhum thread está em uma chamada no método [ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ac07e-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac07e-120">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="ac07e-120">Requirements</span></span>  
 <span data-ttu-id="ac07e-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac07e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac07e-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac07e-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac07e-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac07e-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac07e-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac07e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac07e-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="ac07e-125">See also</span></span>

- [<span data-ttu-id="ac07e-126">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ac07e-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ac07e-127">Depuração</span><span class="sxs-lookup"><span data-stu-id="ac07e-127">Debugging</span></span>](index.md)
