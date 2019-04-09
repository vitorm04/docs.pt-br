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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117320"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="a6ca2-102">Método IMetaDataError::OnError</span><span class="sxs-lookup"><span data-stu-id="a6ca2-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="a6ca2-103">Fornece notificação de erros que ocorrem durante a mesclagem de metadados.</span><span class="sxs-lookup"><span data-stu-id="a6ca2-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6ca2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6ca2-104">Syntax</span></span>  
  
```  
HRESULT OnError (  
    [in] HRESULT   hrError,   
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6ca2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a6ca2-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="a6ca2-106">[in] O valor de erro HRESULT retornado para o método de chamada.</span><span class="sxs-lookup"><span data-stu-id="a6ca2-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="a6ca2-107">[in] O token de metadados do objeto de código que estava sendo mesclado quando ocorreu o erro.</span><span class="sxs-lookup"><span data-stu-id="a6ca2-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6ca2-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a6ca2-108">Requirements</span></span>  
 <span data-ttu-id="a6ca2-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6ca2-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6ca2-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a6ca2-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a6ca2-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a6ca2-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="a6ca2-112">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="a6ca2-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a6ca2-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6ca2-113">See also</span></span>

- [<span data-ttu-id="a6ca2-114">Interface IMetaDataError</span><span class="sxs-lookup"><span data-stu-id="a6ca2-114">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)
