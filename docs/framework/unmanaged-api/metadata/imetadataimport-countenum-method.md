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
ms.openlocfilehash: 0c78ce8192d6456dd1b1be990d87b9209b028e09
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440362"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="7bb92-102">Método IMetaDataImport::CountEnum</span><span class="sxs-lookup"><span data-stu-id="7bb92-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="7bb92-103">Obtém o número de elementos na enumeração que foi recuperado pelo enumerador especificado.</span><span class="sxs-lookup"><span data-stu-id="7bb92-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bb92-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7bb92-104">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,   
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bb92-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7bb92-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="7bb92-106">no O identificador do enumerador.</span><span class="sxs-lookup"><span data-stu-id="7bb92-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="7bb92-107">fora O número de elementos enumerados.</span><span class="sxs-lookup"><span data-stu-id="7bb92-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7bb92-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="7bb92-108">Remarks</span></span>  
 <span data-ttu-id="7bb92-109">O identificador especificado pelo `hEnum` é obtido de uma chamada de *nome* de `Enum`anterior (por exemplo, [IMetaDataImport:: EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="7bb92-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bb92-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7bb92-110">Requirements</span></span>  
 <span data-ttu-id="7bb92-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bb92-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bb92-112">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7bb92-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7bb92-113">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7bb92-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7bb92-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bb92-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bb92-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7bb92-115">See also</span></span>

- [<span data-ttu-id="7bb92-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="7bb92-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7bb92-117">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="7bb92-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
