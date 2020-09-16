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
ms.openlocfilehash: db2474741012c4fd1734adafed112821c42c099c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541702"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="a2ba7-102">Método IBindingDisplay::GetCurrentDisplay</span><span class="sxs-lookup"><span data-stu-id="a2ba7-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="a2ba7-103">Retorna as informações de exibição da Associação atual.</span><span class="sxs-lookup"><span data-stu-id="a2ba7-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2ba7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a2ba7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2ba7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a2ba7-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="a2ba7-106">[out, retval] Um ponteiro para um SafeArray que contém as informações de exibição de associação.</span><span class="sxs-lookup"><span data-stu-id="a2ba7-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2ba7-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a2ba7-107">Remarks</span></span>  
 <span data-ttu-id="a2ba7-108">O método [IBindingDisplay:: InitializeForProcess](ibindingdisplay-initializeforprocess-method.md) deve ter êxito anteriormente e o programa deve ser interrompido por um depurador.</span><span class="sxs-lookup"><span data-stu-id="a2ba7-108">The [IBindingDisplay::InitializeForProcess](ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="a2ba7-109">O chamador deve desalocar a `SAFEARRAY` memória retornada usando [SafeArrayDestroy](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span><span class="sxs-lookup"><span data-stu-id="a2ba7-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2ba7-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a2ba7-110">Requirements</span></span>  
 <span data-ttu-id="a2ba7-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2ba7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2ba7-112">**Cabeçalho:** BindingDisplay. h</span><span class="sxs-lookup"><span data-stu-id="a2ba7-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="a2ba7-113">**Biblioteca:** BindingDisplay. idl</span><span class="sxs-lookup"><span data-stu-id="a2ba7-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="a2ba7-114">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2ba7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2ba7-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="a2ba7-115">See also</span></span>

- [<span data-ttu-id="a2ba7-116">Interface IBindingDisplay</span><span class="sxs-lookup"><span data-stu-id="a2ba7-116">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
- [<span data-ttu-id="a2ba7-117">Método InitializeForProcess</span><span class="sxs-lookup"><span data-stu-id="a2ba7-117">InitializeForProcess Method</span></span>](ibindingdisplay-initializeforprocess-method.md)
