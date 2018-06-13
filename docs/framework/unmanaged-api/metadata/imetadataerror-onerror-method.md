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
ms.openlocfilehash: 1ed9e097dccd0fcb81ea9023cc9b84906589ccb0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446252"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="cec50-102">Método IMetaDataError::OnError</span><span class="sxs-lookup"><span data-stu-id="cec50-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="cec50-103">Fornece notificação de erros que ocorrem durante a mesclagem de metadados.</span><span class="sxs-lookup"><span data-stu-id="cec50-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cec50-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cec50-104">Syntax</span></span>  
  
```  
HRESULT OnError (  
    [in] HRESULT   hrError,   
    [in] mdToken   token  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cec50-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cec50-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="cec50-106">[in] O valor de erro HRESULT retornado para o método de chamada.</span><span class="sxs-lookup"><span data-stu-id="cec50-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="cec50-107">[in] O token de metadados do objeto de código que estava sendo mesclado quando ocorreu o erro.</span><span class="sxs-lookup"><span data-stu-id="cec50-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cec50-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cec50-108">Requirements</span></span>  
 <span data-ttu-id="cec50-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cec50-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cec50-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cec50-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cec50-111">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="cec50-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cec50-112">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cec50-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cec50-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cec50-113">See Also</span></span>  
 [<span data-ttu-id="cec50-114">Interface IMetaDataError</span><span class="sxs-lookup"><span data-stu-id="cec50-114">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)
