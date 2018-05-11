---
title: Método IMetaDataTables2::GetMetaDataStorage
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStorage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStorage
helpviewer_keywords:
- GetMetaDataStorage method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStorage method [.NET Framework metadata]
ms.assetid: 667a6d1e-753d-4ea2-8fd8-a8337d1bb9cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 33064fe8292eb7a8079d2f68bcdea767d306be6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatatables2getmetadatastorage-method"></a><span data-ttu-id="fde7d-102">Método IMetaDataTables2::GetMetaDataStorage</span><span class="sxs-lookup"><span data-stu-id="fde7d-102">IMetaDataTables2::GetMetaDataStorage Method</span></span>
<span data-ttu-id="fde7d-103">Obtém o tamanho e o conteúdo dos metadados armazenados na seção especificada.</span><span class="sxs-lookup"><span data-stu-id="fde7d-103">Gets the size and contents of the metadata stored in the specified section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fde7d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fde7d-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataStorage (  
   [in, out] const void   **ppvMd,  
   [out] ULONG   *pcbMd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fde7d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fde7d-105">Parameters</span></span>  
 `ppvMd`  
 <span data-ttu-id="fde7d-106">[out no] Um ponteiro para uma seção de metadados.</span><span class="sxs-lookup"><span data-stu-id="fde7d-106">[in, out] A pointer to a metadata section.</span></span>  
  
 `pcbMd`  
 <span data-ttu-id="fde7d-107">[out] O tamanho do fluxo de metadados.</span><span class="sxs-lookup"><span data-stu-id="fde7d-107">[out] The size of the metadata stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fde7d-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fde7d-108">Requirements</span></span>  
 <span data-ttu-id="fde7d-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fde7d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fde7d-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fde7d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fde7d-111">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="fde7d-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fde7d-112">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fde7d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fde7d-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fde7d-113">See Also</span></span>  
 [<span data-ttu-id="fde7d-114">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="fde7d-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 [<span data-ttu-id="fde7d-115">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="fde7d-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
