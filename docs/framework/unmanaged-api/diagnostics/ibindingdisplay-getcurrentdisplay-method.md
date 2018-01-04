---
title: "Método IBindingDisplay::GetCurrentDisplay"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IBindingDisplay.GetCurrentDisplay
api_location: diasymreader.dll
api_type: COM
f1_keywords: IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7013b07d0ebf2709d6c2b6f791960a8e7d35d678
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="26095-102">Método IBindingDisplay::GetCurrentDisplay</span><span class="sxs-lookup"><span data-stu-id="26095-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="26095-103">Retorna as informações de exibição de associação atual.</span><span class="sxs-lookup"><span data-stu-id="26095-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26095-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26095-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26095-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="26095-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="26095-106">[out, retval] Um ponteiro para um safearray que contém as informações de exibição de associação.</span><span class="sxs-lookup"><span data-stu-id="26095-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26095-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="26095-107">Remarks</span></span>  
 <span data-ttu-id="26095-108">O [Ibindingdisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) método deve ter êxito anteriormente, e o programa deve ser interrompido por um depurador.</span><span class="sxs-lookup"><span data-stu-id="26095-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="26095-109">O chamador deve ser desalocada retornado `SAFEARRAY` memória usando [SafeArrayDestroy](http://msdn.microsoft.com/en-us/fc94f7e7-b903-4c78-905c-54df1f8d13fa).</span><span class="sxs-lookup"><span data-stu-id="26095-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](http://msdn.microsoft.com/en-us/fc94f7e7-b903-4c78-905c-54df1f8d13fa).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26095-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="26095-110">Requirements</span></span>  
 <span data-ttu-id="26095-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26095-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26095-112">**Cabeçalho:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="26095-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="26095-113">**Biblioteca:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="26095-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="26095-114">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26095-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26095-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26095-115">See Also</span></span>  
 [<span data-ttu-id="26095-116">Interface IBindingDisplay</span><span class="sxs-lookup"><span data-stu-id="26095-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 [<span data-ttu-id="26095-117">Método InitializeForProcess</span><span class="sxs-lookup"><span data-stu-id="26095-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
