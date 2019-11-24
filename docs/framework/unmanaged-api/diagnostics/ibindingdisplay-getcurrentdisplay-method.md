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
ms.openlocfilehash: 9294dbf1caddd4b607185de54efd2b4764e6ca35
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448496"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="c3775-102">Método IBindingDisplay::GetCurrentDisplay</span><span class="sxs-lookup"><span data-stu-id="c3775-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="c3775-103">Retorna as informações de exibição da Associação atual.</span><span class="sxs-lookup"><span data-stu-id="c3775-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3775-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3775-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3775-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c3775-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="c3775-106">[out, retval] Um ponteiro para um SafeArray que contém as informações de exibição de associação.</span><span class="sxs-lookup"><span data-stu-id="c3775-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3775-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3775-107">Remarks</span></span>  
 <span data-ttu-id="c3775-108">O método [IBindingDisplay:: InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) deve ter êxito anteriormente e o programa deve ser interrompido por um depurador.</span><span class="sxs-lookup"><span data-stu-id="c3775-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="c3775-109">O chamador deve desalocar a memória de `SAFEARRAY` retornada usando [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span><span class="sxs-lookup"><span data-stu-id="c3775-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3775-110">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c3775-110">Requirements</span></span>  
 <span data-ttu-id="c3775-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3775-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3775-112">**Cabeçalho:** BindingDisplay. h</span><span class="sxs-lookup"><span data-stu-id="c3775-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="c3775-113">**Biblioteca:** BindingDisplay. idl</span><span class="sxs-lookup"><span data-stu-id="c3775-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="c3775-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3775-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3775-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3775-115">See also</span></span>

- [<span data-ttu-id="c3775-116">Interface IBindingDisplay</span><span class="sxs-lookup"><span data-stu-id="c3775-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
- [<span data-ttu-id="c3775-117">Método InitializeForProcess</span><span class="sxs-lookup"><span data-stu-id="c3775-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
