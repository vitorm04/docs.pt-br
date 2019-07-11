---
title: Método IMetaDataImport::GetFieldMarshal
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldMarshal
helpviewer_keywords:
- GetFieldMarshal method [.NET Framework metadata]
- IMetaDataImport::GetFieldMarshal method [.NET Framework metadata]
ms.assetid: 4e2d88c6-8a3a-4fbe-900b-b4f4c06bf6bf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 40d1817b9eb7f341899efddb469c7fa17a8f8c0e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782402"
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="be4d7-102">Método IMetaDataImport::GetFieldMarshal</span><span class="sxs-lookup"><span data-stu-id="be4d7-102">IMetaDataImport::GetFieldMarshal Method</span></span>
<span data-ttu-id="be4d7-103">Obtém um ponteiro para o tipo não gerenciado, nativo do campo representado pelo token de metadados de campo especificado.</span><span class="sxs-lookup"><span data-stu-id="be4d7-103">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be4d7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="be4d7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,   
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be4d7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="be4d7-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="be4d7-106">[in] O token de metadados que representa o campo para obter informações de marshaling de interoperabilidade para.</span><span class="sxs-lookup"><span data-stu-id="be4d7-106">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="be4d7-107">[out] Um ponteiro para a assinatura de metadados de tipo nativo do campo.</span><span class="sxs-lookup"><span data-stu-id="be4d7-107">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="be4d7-108">[out] O tamanho em bytes do `ppvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="be4d7-108">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be4d7-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="be4d7-109">Requirements</span></span>  
 <span data-ttu-id="be4d7-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be4d7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be4d7-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="be4d7-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be4d7-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="be4d7-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be4d7-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be4d7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be4d7-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be4d7-114">See also</span></span>

- [<span data-ttu-id="be4d7-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="be4d7-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="be4d7-116">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="be4d7-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
