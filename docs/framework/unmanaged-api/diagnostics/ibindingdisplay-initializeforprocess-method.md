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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8e701b49a99b548bbfd0cd6c583b7069bca2142b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711048"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="830ad-102">Método IBindingDisplay::InitializeForProcess</span><span class="sxs-lookup"><span data-stu-id="830ad-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="830ad-103">Inicializa o [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="830ad-103">Initializes the [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="830ad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="830ad-104">Syntax</span></span>  
  
```  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="830ad-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="830ad-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="830ad-106">[in] O identificador de processo.</span><span class="sxs-lookup"><span data-stu-id="830ad-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="830ad-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="830ad-107">Remarks</span></span>  
 <span data-ttu-id="830ad-108">O depurador chama o `InitializeForProcess` método no momento da criação para inicializar a exibição de associação.</span><span class="sxs-lookup"><span data-stu-id="830ad-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="830ad-109">`InitializeForProcess` deve ser chamado no momento da criação antes de qualquer outro método em `IBindingDisplay` é chamado.</span><span class="sxs-lookup"><span data-stu-id="830ad-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="830ad-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="830ad-110">Requirements</span></span>  
 <span data-ttu-id="830ad-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="830ad-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="830ad-112">**Cabeçalho:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="830ad-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="830ad-113">**Biblioteca:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="830ad-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="830ad-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="830ad-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="830ad-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="830ad-115">See also</span></span>
- [<span data-ttu-id="830ad-116">Interface IBindingDisplay</span><span class="sxs-lookup"><span data-stu-id="830ad-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
