---
title: "Método ICorDebugVariableHome::GetCode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetCode
helpviewer_keywords:
- ICorDebugVariableHome::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: ef002890-4a7b-4a5d-abbf-16c60083f794
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fdf2051ffc9e6f2bc006637f2dce8029e72977cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="82af9-102">Método ICorDebugVariableHome::GetCode</span><span class="sxs-lookup"><span data-stu-id="82af9-102">ICorDebugVariableHome::GetCode Method</span></span>
<span data-ttu-id="82af9-103">Obtém a instância de "ICorDebugCode" que contém essa [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="82af9-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82af9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82af9-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82af9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="82af9-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="82af9-106">[out] Um ponteiro para o endereço da instância de "ICorDebugCode" que contém essa [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="82af9-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82af9-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="82af9-107">Requirements</span></span>  
 <span data-ttu-id="82af9-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82af9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82af9-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82af9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82af9-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82af9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82af9-111">**Versões do .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82af9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82af9-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82af9-112">See Also</span></span>  
 [<span data-ttu-id="82af9-113">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="82af9-113">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 
