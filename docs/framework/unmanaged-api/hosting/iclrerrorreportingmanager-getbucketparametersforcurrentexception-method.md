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
ms.openlocfilehash: 969d74933e908674225684a2e77d5c4804b86122
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615638"
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="1a6d5-102">Método ICLRErrorReportingManager::GetBucketParametersForCurrentException</span><span class="sxs-lookup"><span data-stu-id="1a6d5-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>
<span data-ttu-id="1a6d5-103">Obtém o Bucket do Watson para a exceção atual no thread de chamada.</span><span class="sxs-lookup"><span data-stu-id="1a6d5-103">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="1a6d5-104">Um *Bucket* é uma coleção de dados de erro que está relacionada ao mesmo defeito de código.</span><span class="sxs-lookup"><span data-stu-id="1a6d5-104">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="1a6d5-105">*Watson* refere-se a um conjunto de tecnologias para coletar e analisar dados associados a uma exceção.</span><span class="sxs-lookup"><span data-stu-id="1a6d5-105">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a6d5-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1a6d5-106">Syntax</span></span>  
  
```cpp  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a6d5-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1a6d5-107">Parameters</span></span>  
 `pParams`  
 <span data-ttu-id="1a6d5-108">fora Um ponteiro para uma estrutura [BucketParameters](bucketparameters-structure.md) que contém dados de erro para a exceção.</span><span class="sxs-lookup"><span data-stu-id="1a6d5-108">[out] A pointer to a [BucketParameters](bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a6d5-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1a6d5-109">Requirements</span></span>  
 <span data-ttu-id="1a6d5-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a6d5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a6d5-111">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1a6d5-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1a6d5-112">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1a6d5-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a6d5-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a6d5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a6d5-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="1a6d5-114">See also</span></span>

- [<span data-ttu-id="1a6d5-115">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="1a6d5-115">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
