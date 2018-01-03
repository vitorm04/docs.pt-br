---
title: "Método ICorDebugAppDomain::GetModuleFromMetaDataInterface"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.GetModuleFromMetaDataInterface
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::GetModuleFromMetaDataInterface
helpviewer_keywords:
- ICorDebugAppDomain::GetModuleFromMetaDatainterface method [.NET Framework debugging]
- GetModuleFromMetaDatainterface method [.NET Framework debugging]
ms.assetid: f35225b3-5dda-4d5a-913d-b3373e9ab81e
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9dccf5308216fbeda80213fecf0f7065f3dbe9d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomaingetmodulefrommetadatainterface-method"></a><span data-ttu-id="ae779-102">Método ICorDebugAppDomain::GetModuleFromMetaDataInterface</span><span class="sxs-lookup"><span data-stu-id="ae779-102">ICorDebugAppDomain::GetModuleFromMetaDataInterface Method</span></span>
<span data-ttu-id="ae779-103">Obtém o módulo que corresponda à interface de metadados fornecidos.</span><span class="sxs-lookup"><span data-stu-id="ae779-103">Gets the module that corresponds to the given metadata interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae779-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae779-104">Syntax</span></span>  
  
```  
HRESULT GetModuleFromMetaDataInterface (  
    [in] IUnknown           *pIMetaData,  
    [out] ICorDebugModule  **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae779-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ae779-105">Parameters</span></span>  
 `pIMetaData`  
 <span data-ttu-id="ae779-106">[in] Um ponteiro para um objeto que é uma da [interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="ae779-106">[in] A pointer to an object that is one of the [Metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
 `ppModule`  
 <span data-ttu-id="ae779-107">[out] Um ponteiro para o endereço de um objeto ICorDebugModule que representa o módulo correspondente à interface de metadados fornecidos.</span><span class="sxs-lookup"><span data-stu-id="ae779-107">[out] A pointer to the address of an ICorDebugModule object that represents the module corresponding to the given metadata interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae779-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ae779-108">Requirements</span></span>  
 <span data-ttu-id="ae779-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae779-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae779-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae779-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae779-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae779-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae779-112">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae779-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
