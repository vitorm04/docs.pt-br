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
ms.openlocfilehash: 656f5ee20e50ea9ac5c03711adfd0b8264fbcca0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444952"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="110e8-102">Método IMetaDataEmit::SaveToStream</span><span class="sxs-lookup"><span data-stu-id="110e8-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="110e8-103">Salva todos os metadados no escopo atual especificado `IStream`.</span><span class="sxs-lookup"><span data-stu-id="110e8-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="110e8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="110e8-104">Syntax</span></span>  
  
```  
HRESULT SaveToStream (   
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="110e8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="110e8-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="110e8-106">[in] O fluxo gravável para salvar.</span><span class="sxs-lookup"><span data-stu-id="110e8-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="110e8-107">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="110e8-107">[in] Reserved.</span></span> <span data-ttu-id="110e8-108">Deve ser zero.</span><span class="sxs-lookup"><span data-stu-id="110e8-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="110e8-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="110e8-109">Requirements</span></span>  
 <span data-ttu-id="110e8-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="110e8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="110e8-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="110e8-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="110e8-112">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="110e8-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="110e8-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="110e8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="110e8-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="110e8-114">See Also</span></span>  
 [<span data-ttu-id="110e8-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="110e8-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="110e8-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="110e8-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
