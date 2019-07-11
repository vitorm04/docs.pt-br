---
title: Método IMetaDataImport::CloseEnum
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CloseEnum
helpviewer_keywords:
- IMetaDataImport::CloseEnum method [.NET Framework metadata]
- CloseEnum method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 727819d5-1dab-4ebb-ac25-950b4111dc72
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f27955467436d562c6a9acc9d7f666427e4c85b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770707"
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="c3d40-102">Método IMetaDataImport::CloseEnum</span><span class="sxs-lookup"><span data-stu-id="c3d40-102">IMetaDataImport::CloseEnum Method</span></span>
<span data-ttu-id="c3d40-103">Fecha o enumerador que é identificado pelo identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="c3d40-103">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3d40-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3d40-104">Syntax</span></span>  
  
```cpp  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3d40-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c3d40-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="c3d40-106">[in] O identificador para o enumerador fechar.</span><span class="sxs-lookup"><span data-stu-id="c3d40-106">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3d40-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3d40-107">Remarks</span></span>  
 <span data-ttu-id="c3d40-108">O identificador especificado pelo `hEnum` é obtido de um anterior `Enum` *nome* chamar (por exemplo, [imetadataimport:: Enumtypedefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="c3d40-108">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3d40-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3d40-109">Requirements</span></span>  
 <span data-ttu-id="c3d40-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3d40-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3d40-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c3d40-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c3d40-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c3d40-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c3d40-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3d40-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3d40-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3d40-114">See also</span></span>

- [<span data-ttu-id="c3d40-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="c3d40-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c3d40-116">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="c3d40-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
