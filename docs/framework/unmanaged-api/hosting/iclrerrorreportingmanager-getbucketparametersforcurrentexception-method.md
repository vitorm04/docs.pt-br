---
title: "Método ICLRErrorReportingManager::GetBucketParametersForCurrentException"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRErrorReportingManager.GetBucketParametersForCurrentException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::GetBucketParametersForCurrentException
helpviewer_keywords:
- ICLRErrorReportingManager::GetBucketParametersForCurrentException method [.NET Framework hosting]
- GetBucketParametersForCurrentException method [.NET Framework hosting]
ms.assetid: a13ec8a6-8e18-4acb-8054-77f5b1a0e0b9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f920ceb802231112ef1b855fd0a78d3a0e6ca4c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="513a9-102">Método ICLRErrorReportingManager::GetBucketParametersForCurrentException</span><span class="sxs-lookup"><span data-stu-id="513a9-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>
<span data-ttu-id="513a9-103">Obtém o bucket Watson para a exceção atual no thread de chamada.</span><span class="sxs-lookup"><span data-stu-id="513a9-103">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="513a9-104">Um *bucket* é uma coleção de dados de erros relacionados para o mesmo defeito de código.</span><span class="sxs-lookup"><span data-stu-id="513a9-104">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="513a9-105">*Watson* se refere a um conjunto de tecnologias para coletar e analisar os dados que está associados uma exceção.</span><span class="sxs-lookup"><span data-stu-id="513a9-105">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="513a9-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="513a9-106">Syntax</span></span>  
  
```  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="513a9-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="513a9-107">Parameters</span></span>  
 `pParams`  
 <span data-ttu-id="513a9-108">[out] Um ponteiro para um [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) estrutura que contém dados de erro para a exceção.</span><span class="sxs-lookup"><span data-stu-id="513a9-108">[out] A pointer to a [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="513a9-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="513a9-109">Requirements</span></span>  
 <span data-ttu-id="513a9-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="513a9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="513a9-111">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="513a9-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="513a9-112">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="513a9-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="513a9-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="513a9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="513a9-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="513a9-114">See Also</span></span>  
 [<span data-ttu-id="513a9-115">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="513a9-115">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
