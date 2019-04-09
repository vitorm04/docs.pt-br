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
ms.openlocfilehash: aa1e85751f90c34d40e88207af5c7eed2dd1bb82
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197850"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="10d83-102">Método IBindingDisplay::InitializeForProcess</span><span class="sxs-lookup"><span data-stu-id="10d83-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="10d83-103">Inicializa o [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="10d83-103">Initializes the [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10d83-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10d83-104">Syntax</span></span>  
  
```  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10d83-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="10d83-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="10d83-106">[in] O identificador de processo.</span><span class="sxs-lookup"><span data-stu-id="10d83-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10d83-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="10d83-107">Remarks</span></span>  
 <span data-ttu-id="10d83-108">O depurador chama o `InitializeForProcess` método no momento da criação para inicializar a exibição de associação.</span><span class="sxs-lookup"><span data-stu-id="10d83-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> `InitializeForProcess` <span data-ttu-id="10d83-109">deve ser chamado no momento da criação antes de qualquer outro método em `IBindingDisplay` é chamado.</span><span class="sxs-lookup"><span data-stu-id="10d83-109">must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10d83-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="10d83-110">Requirements</span></span>  
 <span data-ttu-id="10d83-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10d83-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10d83-112">**Cabeçalho:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="10d83-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="10d83-113">**Biblioteca:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="10d83-113">**Library:** BindingDisplay.idl</span></span>  
  
 **<span data-ttu-id="10d83-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="10d83-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="10d83-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10d83-115">See also</span></span>

- [<span data-ttu-id="10d83-116">Interface IBindingDisplay</span><span class="sxs-lookup"><span data-stu-id="10d83-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
