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
ms.openlocfilehash: 472e06c3a00762a7bb012fbcb525d8e0b3a9271a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162240"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="1a85a-102">Método IBindingDisplay::GetCurrentDisplay</span><span class="sxs-lookup"><span data-stu-id="1a85a-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="1a85a-103">Retorna as informações de exibição de associação atual.</span><span class="sxs-lookup"><span data-stu-id="1a85a-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a85a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1a85a-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a85a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1a85a-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="1a85a-106">[out, retval] Um ponteiro para um safearray que contém as informações de exibição de associação.</span><span class="sxs-lookup"><span data-stu-id="1a85a-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a85a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="1a85a-107">Remarks</span></span>  
 <span data-ttu-id="1a85a-108">O [ibindingdisplay:: Initializeforprocess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) método deve ter anteriormente com êxito e o programa deve ser interrompido por um depurador.</span><span class="sxs-lookup"><span data-stu-id="1a85a-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="1a85a-109">O chamador deverá desalocar retornado `SAFEARRAY` memória usando [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span><span class="sxs-lookup"><span data-stu-id="1a85a-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a85a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1a85a-110">Requirements</span></span>  
 <span data-ttu-id="1a85a-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a85a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a85a-112">**Cabeçalho:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="1a85a-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="1a85a-113">**Biblioteca:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="1a85a-113">**Library:** BindingDisplay.idl</span></span>  
  
 **<span data-ttu-id="1a85a-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="1a85a-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1a85a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a85a-115">See also</span></span>

- [<span data-ttu-id="1a85a-116">Interface IBindingDisplay</span><span class="sxs-lookup"><span data-stu-id="1a85a-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
- [<span data-ttu-id="1a85a-117">Método InitializeForProcess</span><span class="sxs-lookup"><span data-stu-id="1a85a-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
