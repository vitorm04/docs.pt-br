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
ms.openlocfilehash: 1c177a315a76009b7ac82055cba2d0b23821333b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494868"
---
# <a name="imetadatatables2getmetadatastorage-method"></a><span data-ttu-id="8b5b4-102">Método IMetaDataTables2::GetMetaDataStorage</span><span class="sxs-lookup"><span data-stu-id="8b5b4-102">IMetaDataTables2::GetMetaDataStorage Method</span></span>
<span data-ttu-id="8b5b4-103">Obtém o tamanho e o conteúdo dos metadados armazenados na seção especificada.</span><span class="sxs-lookup"><span data-stu-id="8b5b4-103">Gets the size and contents of the metadata stored in the specified section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b5b4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b5b4-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataStorage (  
   [in, out] const void   **ppvMd,  
   [out] ULONG   *pcbMd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b5b4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8b5b4-105">Parameters</span></span>  
 `ppvMd`  
 <span data-ttu-id="8b5b4-106">[no, out] Um ponteiro para uma seção de metadados.</span><span class="sxs-lookup"><span data-stu-id="8b5b4-106">[in, out] A pointer to a metadata section.</span></span>  
  
 `pcbMd`  
 <span data-ttu-id="8b5b4-107">[out] O tamanho do fluxo de metadados.</span><span class="sxs-lookup"><span data-stu-id="8b5b4-107">[out] The size of the metadata stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b5b4-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8b5b4-108">Requirements</span></span>  
 <span data-ttu-id="8b5b4-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b5b4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b5b4-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8b5b4-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b5b4-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8b5b4-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8b5b4-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b5b4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b5b4-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b5b4-113">See also</span></span>
- [<span data-ttu-id="8b5b4-114">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="8b5b4-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
- [<span data-ttu-id="8b5b4-115">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="8b5b4-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
