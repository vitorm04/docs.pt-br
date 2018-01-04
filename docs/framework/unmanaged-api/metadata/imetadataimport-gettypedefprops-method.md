---
title: "Método IMetaDataImport::GetTypeDefProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetTypeDefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3e7f2c2fe602ef3464766b62ef12e8f83767bf4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="16542-102">Método IMetaDataImport::GetTypeDefProps</span><span class="sxs-lookup"><span data-stu-id="16542-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="16542-103">Retorna informações de metadados para o <xref:System.Type> representada pelo token de TypeDef especificado.</span><span class="sxs-lookup"><span data-stu-id="16542-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16542-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="16542-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="16542-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="16542-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="16542-106">[in] O token de TypeDef que representa o tipo para retornar metadados.</span><span class="sxs-lookup"><span data-stu-id="16542-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="16542-107">[out] Um buffer que contém o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="16542-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="16542-108">[in] O tamanho em caracteres largos de `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="16542-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="16542-109">[out] O número de caracteres largos retornados em `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="16542-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="16542-110">[out] Um ponteiro para os sinalizadores que modificar a definição de tipo.</span><span class="sxs-lookup"><span data-stu-id="16542-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="16542-111">Esse valor é um bitmask do [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="16542-111">This value is a bitmask from the [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="16542-112">[out] Um token de metadados de TypeDef ou TypeRef que representa o tipo base do tipo solicitado.</span><span class="sxs-lookup"><span data-stu-id="16542-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16542-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="16542-113">Requirements</span></span>  
 <span data-ttu-id="16542-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16542-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16542-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="16542-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="16542-116">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="16542-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="16542-117">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16542-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16542-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16542-118">See Also</span></span>  
 [<span data-ttu-id="16542-119">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="16542-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="16542-120">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="16542-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
