---
title: Método IMetaDataImport::GetTypeDefProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa69eda974187748d7046c792fa16b7729e3deff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446876"
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="fed9c-102">Método IMetaDataImport::GetTypeDefProps</span><span class="sxs-lookup"><span data-stu-id="fed9c-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="fed9c-103">Retorna informações de metadados para o <xref:System.Type> representada pelo token de TypeDef especificado.</span><span class="sxs-lookup"><span data-stu-id="fed9c-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fed9c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fed9c-104">Syntax</span></span>  
  
```  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fed9c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fed9c-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="fed9c-106">[in] O token de TypeDef que representa o tipo para retornar metadados.</span><span class="sxs-lookup"><span data-stu-id="fed9c-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="fed9c-107">[out] Um buffer que contém o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="fed9c-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="fed9c-108">[in] O tamanho em caracteres largos de `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="fed9c-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="fed9c-109">[out] O número de caracteres largos retornados em `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="fed9c-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="fed9c-110">[out] Um ponteiro para os sinalizadores que modificar a definição de tipo.</span><span class="sxs-lookup"><span data-stu-id="fed9c-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="fed9c-111">Esse valor é um bitmask do [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="fed9c-111">This value is a bitmask from the [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="fed9c-112">[out] Um token de metadados de TypeDef ou TypeRef que representa o tipo base do tipo solicitado.</span><span class="sxs-lookup"><span data-stu-id="fed9c-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fed9c-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fed9c-113">Requirements</span></span>  
 <span data-ttu-id="fed9c-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fed9c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fed9c-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fed9c-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fed9c-116">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="fed9c-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fed9c-117">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fed9c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fed9c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fed9c-118">See Also</span></span>  
 [<span data-ttu-id="fed9c-119">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="fed9c-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="fed9c-120">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="fed9c-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
