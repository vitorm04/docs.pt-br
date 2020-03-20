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
ms.openlocfilehash: 489fa217744e41ccb5d27d088790131c15e1ee52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177394"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="fa50a-102">Método IMetaDataError::OnError</span><span class="sxs-lookup"><span data-stu-id="fa50a-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="fa50a-103">Fornece notificação de erros que ocorrem durante a fusão de metadados.</span><span class="sxs-lookup"><span data-stu-id="fa50a-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa50a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fa50a-104">Syntax</span></span>  
  
```cpp  
HRESULT OnError (  
    [in] HRESULT   hrError,
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa50a-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="fa50a-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="fa50a-106">[em] O valor de erro HRESULT retornou ao método de chamada.</span><span class="sxs-lookup"><span data-stu-id="fa50a-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="fa50a-107">[em] O token de metadados do objeto de código que estava sendo mesclado quando o erro ocorreu.</span><span class="sxs-lookup"><span data-stu-id="fa50a-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa50a-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fa50a-108">Requirements</span></span>  
 <span data-ttu-id="fa50a-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa50a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa50a-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fa50a-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fa50a-111">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fa50a-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fa50a-112">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa50a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa50a-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="fa50a-113">See also</span></span>

- [<span data-ttu-id="fa50a-114">Interface IMetaDataError</span><span class="sxs-lookup"><span data-stu-id="fa50a-114">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)
