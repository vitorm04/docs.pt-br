---
title: Método IBindingDisplay::GetCurrentDisplay
ms.date: 03/30/2017
api_name:
- IBindingDisplay.GetCurrentDisplay
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0f9cc44db9c93a8b018d0586bc1faeda7cfbc9bc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498426"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="ab3e7-102">Método IBindingDisplay::GetCurrentDisplay</span><span class="sxs-lookup"><span data-stu-id="ab3e7-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="ab3e7-103">Retorna as informações de exibição de associação atual.</span><span class="sxs-lookup"><span data-stu-id="ab3e7-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab3e7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ab3e7-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab3e7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ab3e7-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="ab3e7-106">[out, retval] Um ponteiro para um safearray que contém as informações de exibição de associação.</span><span class="sxs-lookup"><span data-stu-id="ab3e7-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab3e7-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ab3e7-107">Remarks</span></span>  
 <span data-ttu-id="ab3e7-108">O [ibindingdisplay:: Initializeforprocess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) método deve ter anteriormente com êxito e o programa deve ser interrompido por um depurador.</span><span class="sxs-lookup"><span data-stu-id="ab3e7-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="ab3e7-109">O chamador deverá desalocar retornado `SAFEARRAY` memória usando [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span><span class="sxs-lookup"><span data-stu-id="ab3e7-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab3e7-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ab3e7-110">Requirements</span></span>  
 <span data-ttu-id="ab3e7-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab3e7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab3e7-112">**Cabeçalho:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="ab3e7-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="ab3e7-113">**Biblioteca:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="ab3e7-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="ab3e7-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab3e7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab3e7-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab3e7-115">See also</span></span>
- [<span data-ttu-id="ab3e7-116">Interface IBindingDisplay</span><span class="sxs-lookup"><span data-stu-id="ab3e7-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
- [<span data-ttu-id="ab3e7-117">Método InitializeForProcess</span><span class="sxs-lookup"><span data-stu-id="ab3e7-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
