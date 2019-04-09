---
title: Método IMetaDataEmit::SaveToStream
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f6b5582b96dfc83eed482def2c4c4abfeb33a4c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207780"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="cd785-102">Método IMetaDataEmit::SaveToStream</span><span class="sxs-lookup"><span data-stu-id="cd785-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="cd785-103">Salva todos os metadados no escopo atual especificado `IStream`.</span><span class="sxs-lookup"><span data-stu-id="cd785-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd785-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd785-104">Syntax</span></span>  
  
```  
HRESULT SaveToStream (   
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd785-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cd785-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="cd785-106">[in] O fluxo gravável para salvar.</span><span class="sxs-lookup"><span data-stu-id="cd785-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="cd785-107">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="cd785-107">[in] Reserved.</span></span> <span data-ttu-id="cd785-108">Deve ser zero.</span><span class="sxs-lookup"><span data-stu-id="cd785-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd785-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cd785-109">Requirements</span></span>  
 <span data-ttu-id="cd785-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd785-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd785-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cd785-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cd785-112">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="cd785-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="cd785-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="cd785-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cd785-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd785-114">See also</span></span>

- [<span data-ttu-id="cd785-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="cd785-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="cd785-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="cd785-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
