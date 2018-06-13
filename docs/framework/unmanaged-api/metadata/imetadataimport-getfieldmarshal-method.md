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
ms.openlocfilehash: 837b2142e200e224fe32c2c673be0f317633452a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445352"
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="0e95b-102">Método IMetaDataImport::GetFieldMarshal</span><span class="sxs-lookup"><span data-stu-id="0e95b-102">IMetaDataImport::GetFieldMarshal Method</span></span>
<span data-ttu-id="0e95b-103">Obtém um ponteiro para o tipo nativo, não gerenciado do campo representado pelo token de metadados de campo especificado.</span><span class="sxs-lookup"><span data-stu-id="0e95b-103">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e95b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0e95b-104">Syntax</span></span>  
  
```  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,   
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e95b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0e95b-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="0e95b-106">[in] O token de metadados que representa o campo para obter informações de marshaling de interoperabilidade para.</span><span class="sxs-lookup"><span data-stu-id="0e95b-106">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="0e95b-107">[out] Um ponteiro para a assinatura de metadados do tipo nativo do campo.</span><span class="sxs-lookup"><span data-stu-id="0e95b-107">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="0e95b-108">[out] O tamanho em bytes do `ppvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="0e95b-108">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e95b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0e95b-109">Requirements</span></span>  
 <span data-ttu-id="0e95b-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e95b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e95b-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0e95b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0e95b-112">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="0e95b-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0e95b-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e95b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e95b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e95b-114">See Also</span></span>  
 [<span data-ttu-id="0e95b-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="0e95b-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="0e95b-116">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="0e95b-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
