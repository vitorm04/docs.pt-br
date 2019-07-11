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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c714915651d8660a739d8ee6518fc3814af4c08d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782408"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="515aa-102">Método IMetaDataImport::GetCustomAttributeProps</span><span class="sxs-lookup"><span data-stu-id="515aa-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="515aa-103">Obtém o valor do atributo personalizado, dado seu token de metadados.</span><span class="sxs-lookup"><span data-stu-id="515aa-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="515aa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="515aa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="515aa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="515aa-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="515aa-106">[in] Um token de metadados que representa o atributo personalizado a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="515aa-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="515aa-107">[out, opcional] Um token de metadados que representa o objeto que modifica o atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="515aa-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="515aa-108">Esse valor pode ser qualquer tipo de token de metadados, exceto `mdCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="515aa-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="515aa-109">[out, opcional] Uma `mdMethodDef` ou `mdMemberRef` metadados token representando o <xref:System.Type> do atributo personalizado retornado.</span><span class="sxs-lookup"><span data-stu-id="515aa-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="515aa-110">[out, opcional] Um ponteiro para uma matriz de dados que é o valor do atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="515aa-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="515aa-111">[out, opcional] O tamanho em bytes dos dados retornados em \*`ppBlob`.</span><span class="sxs-lookup"><span data-stu-id="515aa-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="515aa-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="515aa-112">Remarks</span></span>  
 <span data-ttu-id="515aa-113">Um atributo personalizado é armazenado como uma matriz de dados, o formato que é compreendido pelo mecanismo de metadados.</span><span class="sxs-lookup"><span data-stu-id="515aa-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="515aa-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="515aa-114">Requirements</span></span>  
 <span data-ttu-id="515aa-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="515aa-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="515aa-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="515aa-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="515aa-117">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="515aa-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="515aa-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="515aa-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="515aa-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="515aa-119">See also</span></span>

- [<span data-ttu-id="515aa-120">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="515aa-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="515aa-121">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="515aa-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
