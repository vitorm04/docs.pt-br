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
ms.openlocfilehash: 0b0a190ce57091434006421e6d8551c78cbe66b8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777172"
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="8bffa-102">Método IMetaDataEmit2::GetDeltaSaveSize</span><span class="sxs-lookup"><span data-stu-id="8bffa-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>
<span data-ttu-id="8bffa-103">Obtém um valor que indica qualquer alteração no tamanho de metadados que resulta da sessão atual de editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="8bffa-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bffa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8bffa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bffa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8bffa-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="8bffa-106">[in] Um dos [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) valores, que indica o nível de precisão desejado.</span><span class="sxs-lookup"><span data-stu-id="8bffa-106">[in] One of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="8bffa-107">Para o .NET Framework versão 2.0, esse parâmetro será ignorado.</span><span class="sxs-lookup"><span data-stu-id="8bffa-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="8bffa-108">[out] A alteração no tamanho dos metadados.</span><span class="sxs-lookup"><span data-stu-id="8bffa-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bffa-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8bffa-109">Requirements</span></span>  
 <span data-ttu-id="8bffa-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bffa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bffa-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8bffa-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8bffa-112">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8bffa-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8bffa-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bffa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bffa-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8bffa-114">See also</span></span>

- [<span data-ttu-id="8bffa-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="8bffa-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="8bffa-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="8bffa-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
