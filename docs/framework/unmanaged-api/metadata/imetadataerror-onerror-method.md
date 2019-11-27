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
ms.openlocfilehash: f10c55abcc044b5bbdbb940001a25f530a4688e4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431227"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="ab6bd-102">Método IMetaDataError::OnError</span><span class="sxs-lookup"><span data-stu-id="ab6bd-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="ab6bd-103">Fornece uma notificação de erros que ocorrem durante a mesclagem de metadados.</span><span class="sxs-lookup"><span data-stu-id="ab6bd-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab6bd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ab6bd-104">Syntax</span></span>  
  
```cpp  
HRESULT OnError (  
    [in] HRESULT   hrError,   
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab6bd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ab6bd-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="ab6bd-106">no O valor de erro HRESULT retornado ao método de chamada.</span><span class="sxs-lookup"><span data-stu-id="ab6bd-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="ab6bd-107">no O token de metadados do objeto de código que estava sendo mesclado quando o erro ocorreu.</span><span class="sxs-lookup"><span data-stu-id="ab6bd-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab6bd-108">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="ab6bd-108">Requirements</span></span>  
 <span data-ttu-id="ab6bd-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab6bd-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab6bd-110">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ab6bd-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ab6bd-111">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ab6bd-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ab6bd-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab6bd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab6bd-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab6bd-113">See also</span></span>

- [<span data-ttu-id="ab6bd-114">Interface IMetaDataError</span><span class="sxs-lookup"><span data-stu-id="ab6bd-114">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)
