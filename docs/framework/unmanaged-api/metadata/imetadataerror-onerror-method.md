---
title: Método IMetaDataError::OnError
ms.date: 03/30/2017
api_name:
- IMetaDataError.OnError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError::OnError
helpviewer_keywords:
- IMetaDataError::OnError method [.NET Framework metadata]
- OnError method, IMetaDataError interface [.NET Framework metadata]
ms.assetid: c1e744b8-a6fb-4d9c-a971-8babc875d8f0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 68fe41afa1999295a32b930b779991e2bbddb19a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042757"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="430d8-102">Método IMetaDataError::OnError</span><span class="sxs-lookup"><span data-stu-id="430d8-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="430d8-103">Fornece notificação de erros que ocorrem durante a mesclagem de metadados.</span><span class="sxs-lookup"><span data-stu-id="430d8-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="430d8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="430d8-104">Syntax</span></span>  
  
```  
HRESULT OnError (  
    [in] HRESULT   hrError,   
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="430d8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="430d8-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="430d8-106">[in] O valor de erro HRESULT retornado para o método de chamada.</span><span class="sxs-lookup"><span data-stu-id="430d8-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="430d8-107">[in] O token de metadados do objeto de código que estava sendo mesclado quando ocorreu o erro.</span><span class="sxs-lookup"><span data-stu-id="430d8-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="430d8-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="430d8-108">Requirements</span></span>  
 <span data-ttu-id="430d8-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="430d8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="430d8-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="430d8-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="430d8-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="430d8-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="430d8-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="430d8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="430d8-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="430d8-113">See also</span></span>

- [<span data-ttu-id="430d8-114">Interface IMetaDataError</span><span class="sxs-lookup"><span data-stu-id="430d8-114">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)
