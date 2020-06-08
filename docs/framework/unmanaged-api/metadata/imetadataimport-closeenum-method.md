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
ms.openlocfilehash: 5de62db4180a6a9160193053fe42e39cebc34d0e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492467"
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="f9723-102">Método IMetaDataImport::CloseEnum</span><span class="sxs-lookup"><span data-stu-id="f9723-102">IMetaDataImport::CloseEnum Method</span></span>
<span data-ttu-id="f9723-103">Fecha o enumerador que é identificado pelo identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="f9723-103">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9723-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9723-104">Syntax</span></span>  
  
```cpp  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9723-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f9723-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="f9723-106">no O identificador do enumerador a ser fechado.</span><span class="sxs-lookup"><span data-stu-id="f9723-106">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9723-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f9723-107">Remarks</span></span>  
 <span data-ttu-id="f9723-108">O identificador especificado por `hEnum` é obtido de uma chamada de `Enum` *nome* anterior (por exemplo, [IMetaDataImport:: EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="f9723-108">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9723-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f9723-109">Requirements</span></span>  
 <span data-ttu-id="f9723-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9723-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9723-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f9723-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f9723-112">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f9723-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f9723-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9723-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9723-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="f9723-114">See also</span></span>

- [<span data-ttu-id="f9723-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="f9723-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="f9723-116">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="f9723-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
