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
ms.openlocfilehash: 3cb2a8d2a4e089d16b6c2129c165a9d8b6828f3f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141720"
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="5b02e-102">Método ICLRErrorReportingManager::GetBucketParametersForCurrentException</span><span class="sxs-lookup"><span data-stu-id="5b02e-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>
<span data-ttu-id="5b02e-103">Obtém o número de buckets Watson para a exceção atual no thread de chamada.</span><span class="sxs-lookup"><span data-stu-id="5b02e-103">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="5b02e-104">Um *bucket* é uma coleção de dados de erro relacionados para o mesmo defeito do código.</span><span class="sxs-lookup"><span data-stu-id="5b02e-104">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="5b02e-105">*Watson* refere-se a um conjunto de tecnologias para coletar e analisar os dados que está associados com uma exceção.</span><span class="sxs-lookup"><span data-stu-id="5b02e-105">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b02e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5b02e-106">Syntax</span></span>  
  
```  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b02e-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5b02e-107">Parameters</span></span>  
 `pParams`  
 <span data-ttu-id="5b02e-108">[out] Um ponteiro para um [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) estrutura que contém dados de erro da exceção.</span><span class="sxs-lookup"><span data-stu-id="5b02e-108">[out] A pointer to a [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b02e-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5b02e-109">Requirements</span></span>  
 <span data-ttu-id="5b02e-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b02e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b02e-111">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5b02e-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5b02e-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5b02e-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="5b02e-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="5b02e-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5b02e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b02e-114">See also</span></span>

- [<span data-ttu-id="5b02e-115">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="5b02e-115">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
