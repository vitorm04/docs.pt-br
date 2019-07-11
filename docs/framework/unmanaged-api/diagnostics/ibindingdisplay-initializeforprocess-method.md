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
ms.openlocfilehash: c19b49e9e9d4e388706a96ff54d588d5aeff99b3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775952"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="f4196-102">Método IBindingDisplay::InitializeForProcess</span><span class="sxs-lookup"><span data-stu-id="f4196-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="f4196-103">Inicializa o [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="f4196-103">Initializes the [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4196-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f4196-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4196-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4196-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="f4196-106">[in] O identificador de processo.</span><span class="sxs-lookup"><span data-stu-id="f4196-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4196-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f4196-107">Remarks</span></span>  
 <span data-ttu-id="f4196-108">O depurador chama o `InitializeForProcess` método no momento da criação para inicializar a exibição de associação.</span><span class="sxs-lookup"><span data-stu-id="f4196-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="f4196-109">`InitializeForProcess` deve ser chamado no momento da criação antes de qualquer outro método em `IBindingDisplay` é chamado.</span><span class="sxs-lookup"><span data-stu-id="f4196-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4196-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4196-110">Requirements</span></span>  
 <span data-ttu-id="f4196-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4196-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4196-112">**Cabeçalho:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="f4196-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="f4196-113">**Biblioteca:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="f4196-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="f4196-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4196-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4196-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4196-115">See also</span></span>

- [<span data-ttu-id="f4196-116">Interface IBindingDisplay</span><span class="sxs-lookup"><span data-stu-id="f4196-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
