---
title: Método ICLRErrorReportingManager::GetBucketParametersForCurrentException
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3877f00a22c43ef5f22974b621b32b78ce15d795
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494461"
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="cc092-102">Método ICLRErrorReportingManager::GetBucketParametersForCurrentException</span><span class="sxs-lookup"><span data-stu-id="cc092-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>
<span data-ttu-id="cc092-103">Obtém o número de buckets Watson para a exceção atual no thread de chamada.</span><span class="sxs-lookup"><span data-stu-id="cc092-103">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="cc092-104">Um *bucket* é uma coleção de dados de erro relacionados para o mesmo defeito do código.</span><span class="sxs-lookup"><span data-stu-id="cc092-104">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="cc092-105">*Watson* refere-se a um conjunto de tecnologias para coletar e analisar os dados que está associados com uma exceção.</span><span class="sxs-lookup"><span data-stu-id="cc092-105">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc092-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cc092-106">Syntax</span></span>  
  
```  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc092-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cc092-107">Parameters</span></span>  
 `pParams`  
 <span data-ttu-id="cc092-108">[out] Um ponteiro para um [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) estrutura que contém dados de erro da exceção.</span><span class="sxs-lookup"><span data-stu-id="cc092-108">[out] A pointer to a [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc092-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cc092-109">Requirements</span></span>  
 <span data-ttu-id="cc092-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc092-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc092-111">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cc092-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc092-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="cc092-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc092-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc092-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc092-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc092-114">See also</span></span>
- [<span data-ttu-id="cc092-115">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="cc092-115">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
