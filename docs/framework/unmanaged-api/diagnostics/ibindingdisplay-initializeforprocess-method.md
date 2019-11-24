---
title: Método IBindingDisplay::InitializeForProcess
ms.date: 03/30/2017
api_name:
- IBindingDisplay.InitializeForProcess
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type:
- apiref
ms.openlocfilehash: bb796a12868cc3e44394ab493f7838dc48ab4dc5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448488"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="d7e2c-102">Método IBindingDisplay::InitializeForProcess</span><span class="sxs-lookup"><span data-stu-id="d7e2c-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="d7e2c-103">Initializes the [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) object.</span><span class="sxs-lookup"><span data-stu-id="d7e2c-103">Initializes the [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7e2c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7e2c-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7e2c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d7e2c-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="d7e2c-106">[in] The process identifier.</span><span class="sxs-lookup"><span data-stu-id="d7e2c-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7e2c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d7e2c-107">Remarks</span></span>  
 <span data-ttu-id="d7e2c-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span><span class="sxs-lookup"><span data-stu-id="d7e2c-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="d7e2c-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span><span class="sxs-lookup"><span data-stu-id="d7e2c-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7e2c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d7e2c-110">Requirements</span></span>  
 <span data-ttu-id="d7e2c-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7e2c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7e2c-112">**Header:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="d7e2c-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="d7e2c-113">**Library:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="d7e2c-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="d7e2c-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7e2c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7e2c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7e2c-115">See also</span></span>

- [<span data-ttu-id="d7e2c-116">Interface IBindingDisplay</span><span class="sxs-lookup"><span data-stu-id="d7e2c-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
