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
ms.openlocfilehash: d2252f58af1a319d953fb320a99fad1cfec3dca0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492688"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="9ef67-102">Método IMetaDataError::OnError</span><span class="sxs-lookup"><span data-stu-id="9ef67-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="9ef67-103">Fornece uma notificação de erros que ocorrem durante a mesclagem de metadados.</span><span class="sxs-lookup"><span data-stu-id="9ef67-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ef67-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ef67-104">Syntax</span></span>  
  
```cpp  
HRESULT OnError (  
    [in] HRESULT   hrError,
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ef67-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9ef67-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="9ef67-106">no O valor de erro HRESULT retornado ao método de chamada.</span><span class="sxs-lookup"><span data-stu-id="9ef67-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="9ef67-107">no O token de metadados do objeto de código que estava sendo mesclado quando o erro ocorreu.</span><span class="sxs-lookup"><span data-stu-id="9ef67-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ef67-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9ef67-108">Requirements</span></span>  
 <span data-ttu-id="9ef67-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ef67-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ef67-110">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9ef67-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9ef67-111">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9ef67-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9ef67-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ef67-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ef67-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="9ef67-113">See also</span></span>

- [<span data-ttu-id="9ef67-114">Interface IMetaDataError</span><span class="sxs-lookup"><span data-stu-id="9ef67-114">IMetaDataError Interface</span></span>](imetadataerror-interface.md)
