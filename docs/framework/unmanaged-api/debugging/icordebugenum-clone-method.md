---
title: "Método ICorDebugEnum::Clone"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEnum.Clone
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEnum::Clone
helpviewer_keywords:
- Clone method, ICorDebugEnum interface [.NET Framework debugging]
- ICorDebugEnum::Clone method [.NET Framework debugging]
ms.assetid: 57eefaf3-75cf-4496-bc94-88c0706861b7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c992410349a7bc1e16b192f564c56e0e17be4a58
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="4f742-102">Método ICorDebugEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="4f742-102">ICorDebugEnum::Clone Method</span></span>
<span data-ttu-id="4f742-103">Cria uma cópia do objeto ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="4f742-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f742-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f742-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f742-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4f742-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="4f742-106">[out] Um ponteiro para o endereço de um `ICorDebugEnum` que é uma cópia deste objeto `ICorDebugEnum` objeto.</span><span class="sxs-lookup"><span data-stu-id="4f742-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f742-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4f742-107">Requirements</span></span>  
 <span data-ttu-id="4f742-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f742-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f742-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f742-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f742-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f742-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f742-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f742-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
