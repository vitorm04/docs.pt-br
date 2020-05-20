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
ms.openlocfilehash: 8645878132359b6218cd62b1ff707208de53704b
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442144"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="6cbbb-102">Método IBindingDisplay::InitializeForProcess</span><span class="sxs-lookup"><span data-stu-id="6cbbb-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="6cbbb-103">Inicializa o objeto [IBindingDisplay](ibindingdisplay-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="6cbbb-103">Initializes the [IBindingDisplay](ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cbbb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6cbbb-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cbbb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6cbbb-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="6cbbb-106">no O identificador do processo.</span><span class="sxs-lookup"><span data-stu-id="6cbbb-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cbbb-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="6cbbb-107">Remarks</span></span>  
 <span data-ttu-id="6cbbb-108">O depurador chama o `InitializeForProcess` método no momento da criação para inicializar a exibição da associação.</span><span class="sxs-lookup"><span data-stu-id="6cbbb-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="6cbbb-109">`InitializeForProcess`deve ser chamado no momento da criação antes que qualquer outro método em `IBindingDisplay` seja chamado.</span><span class="sxs-lookup"><span data-stu-id="6cbbb-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cbbb-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6cbbb-110">Requirements</span></span>  
 <span data-ttu-id="6cbbb-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cbbb-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cbbb-112">**Cabeçalho:** BindingDisplay. h</span><span class="sxs-lookup"><span data-stu-id="6cbbb-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="6cbbb-113">**Biblioteca:** BindingDisplay. idl</span><span class="sxs-lookup"><span data-stu-id="6cbbb-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="6cbbb-114">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cbbb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cbbb-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="6cbbb-115">See also</span></span>

- [<span data-ttu-id="6cbbb-116">Interface IBindingDisplay</span><span class="sxs-lookup"><span data-stu-id="6cbbb-116">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
