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
ms.openlocfilehash: a8e30020a8296e037d1dacc8dbaabde7e40032e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445280"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="42b98-102">Método IMetaDataImport::CountEnum</span><span class="sxs-lookup"><span data-stu-id="42b98-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="42b98-103">Obtém o número de elementos na enumeração que foi recuperada pelo enumerador especificado.</span><span class="sxs-lookup"><span data-stu-id="42b98-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42b98-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42b98-104">Syntax</span></span>  
  
```  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,   
   [out] ULONG       *pulCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42b98-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="42b98-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="42b98-106">[in] O identificador para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="42b98-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="42b98-107">[out] O número de elementos enumerados.</span><span class="sxs-lookup"><span data-stu-id="42b98-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42b98-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="42b98-108">Remarks</span></span>  
 <span data-ttu-id="42b98-109">O identificador especificado pelo `hEnum` é obtido do anterior `Enum` *nome* chamar (por exemplo, [: Enumtypedefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="42b98-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42b98-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="42b98-110">Requirements</span></span>  
 <span data-ttu-id="42b98-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42b98-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42b98-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="42b98-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="42b98-113">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="42b98-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="42b98-114">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42b98-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42b98-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42b98-115">See Also</span></span>  
 [<span data-ttu-id="42b98-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="42b98-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="42b98-117">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="42b98-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
