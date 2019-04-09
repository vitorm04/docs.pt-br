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
ms.openlocfilehash: f12243571262ad7511795c48721617932fc6b30b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161402"
---
# <a name="imetadatatables2getmetadatastorage-method"></a><span data-ttu-id="0e707-102">Método IMetaDataTables2::GetMetaDataStorage</span><span class="sxs-lookup"><span data-stu-id="0e707-102">IMetaDataTables2::GetMetaDataStorage Method</span></span>
<span data-ttu-id="0e707-103">Obtém o tamanho e o conteúdo dos metadados armazenados na seção especificada.</span><span class="sxs-lookup"><span data-stu-id="0e707-103">Gets the size and contents of the metadata stored in the specified section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e707-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0e707-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataStorage (  
   [in, out] const void   **ppvMd,  
   [out] ULONG   *pcbMd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e707-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0e707-105">Parameters</span></span>  
 `ppvMd`  
 <span data-ttu-id="0e707-106">[no, out] Um ponteiro para uma seção de metadados.</span><span class="sxs-lookup"><span data-stu-id="0e707-106">[in, out] A pointer to a metadata section.</span></span>  
  
 `pcbMd`  
 <span data-ttu-id="0e707-107">[out] O tamanho do fluxo de metadados.</span><span class="sxs-lookup"><span data-stu-id="0e707-107">[out] The size of the metadata stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e707-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0e707-108">Requirements</span></span>  
 <span data-ttu-id="0e707-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e707-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e707-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0e707-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0e707-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0e707-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="0e707-112">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="0e707-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0e707-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e707-113">See also</span></span>

- [<span data-ttu-id="0e707-114">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="0e707-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
- [<span data-ttu-id="0e707-115">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="0e707-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
