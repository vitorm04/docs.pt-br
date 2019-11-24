---
title: Método IMetaDataImport::GetCustomAttributeProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type:
- apiref
ms.openlocfilehash: 9a80336db4a5a8d7cfdebb7eb8d25bcb8f96e87c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437642"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="d5e43-102">Método IMetaDataImport::GetCustomAttributeProps</span><span class="sxs-lookup"><span data-stu-id="d5e43-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="d5e43-103">Gets the value of the custom attribute, given its metadata token.</span><span class="sxs-lookup"><span data-stu-id="d5e43-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5e43-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5e43-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5e43-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d5e43-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="d5e43-106">[in] A metadata token that represents the custom attribute to be retrieved.</span><span class="sxs-lookup"><span data-stu-id="d5e43-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="d5e43-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span><span class="sxs-lookup"><span data-stu-id="d5e43-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="d5e43-108">This value can be any type of metadata token except `mdCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="d5e43-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="d5e43-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span><span class="sxs-lookup"><span data-stu-id="d5e43-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="d5e43-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span><span class="sxs-lookup"><span data-stu-id="d5e43-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="d5e43-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span><span class="sxs-lookup"><span data-stu-id="d5e43-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5e43-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="d5e43-112">Remarks</span></span>  
 <span data-ttu-id="d5e43-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span><span class="sxs-lookup"><span data-stu-id="d5e43-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5e43-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d5e43-114">Requirements</span></span>  
 <span data-ttu-id="d5e43-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5e43-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5e43-116">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d5e43-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d5e43-117">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d5e43-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d5e43-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5e43-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5e43-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5e43-119">See also</span></span>

- [<span data-ttu-id="d5e43-120">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="d5e43-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d5e43-121">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="d5e43-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
