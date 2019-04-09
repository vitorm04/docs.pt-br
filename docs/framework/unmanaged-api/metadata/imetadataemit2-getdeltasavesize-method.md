---
title: Método IMetaDataEmit2::GetDeltaSaveSize
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.GetDeltaSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69897a7b646eb9f58e6b38588e302287b4241779
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139887"
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="b081c-102">Método IMetaDataEmit2::GetDeltaSaveSize</span><span class="sxs-lookup"><span data-stu-id="b081c-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>
<span data-ttu-id="b081c-103">Obtém um valor que indica qualquer alteração no tamanho de metadados que resulta da sessão atual de editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="b081c-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b081c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b081c-104">Syntax</span></span>  
  
```  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b081c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b081c-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="b081c-106">[in] Um dos [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) valores, que indica o nível de precisão desejado.</span><span class="sxs-lookup"><span data-stu-id="b081c-106">[in] One of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="b081c-107">Para o .NET Framework versão 2.0, esse parâmetro será ignorado.</span><span class="sxs-lookup"><span data-stu-id="b081c-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="b081c-108">[out] A alteração no tamanho dos metadados.</span><span class="sxs-lookup"><span data-stu-id="b081c-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b081c-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b081c-109">Requirements</span></span>  
 <span data-ttu-id="b081c-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b081c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b081c-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b081c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b081c-112">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b081c-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="b081c-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="b081c-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b081c-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b081c-114">See also</span></span>

- [<span data-ttu-id="b081c-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="b081c-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="b081c-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="b081c-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
