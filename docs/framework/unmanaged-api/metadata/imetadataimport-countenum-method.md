---
title: Método IMetaDataImport::CountEnum
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CountEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5015dc42497d269cdc2de944f14454558be6c07
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142981"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="4ec11-102">Método IMetaDataImport::CountEnum</span><span class="sxs-lookup"><span data-stu-id="4ec11-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="4ec11-103">Obtém o número de elementos na enumeração que foi recuperada pelo enumerador especificado.</span><span class="sxs-lookup"><span data-stu-id="4ec11-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ec11-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4ec11-104">Syntax</span></span>  
  
```  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,   
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ec11-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4ec11-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="4ec11-106">[in] O identificador para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="4ec11-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="4ec11-107">[out] O número de elementos enumerados.</span><span class="sxs-lookup"><span data-stu-id="4ec11-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ec11-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="4ec11-108">Remarks</span></span>  
 <span data-ttu-id="4ec11-109">O identificador especificado pelo `hEnum` é obtido de um anterior `Enum` *nome* chamar (por exemplo, [imetadataimport:: Enumtypedefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="4ec11-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ec11-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4ec11-110">Requirements</span></span>  
 <span data-ttu-id="4ec11-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ec11-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ec11-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4ec11-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4ec11-113">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="4ec11-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="4ec11-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="4ec11-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4ec11-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ec11-115">See also</span></span>

- [<span data-ttu-id="4ec11-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="4ec11-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4ec11-117">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="4ec11-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
