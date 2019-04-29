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
ms.openlocfilehash: a482c7a06efe888408206f2de569e0a8739b85b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777485"
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="7c4a4-102">Método IMetaDataImport::GetTypeDefProps</span><span class="sxs-lookup"><span data-stu-id="7c4a4-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="7c4a4-103">Retorna informações de metadados para o <xref:System.Type> representado pelo token de TypeDef especificado.</span><span class="sxs-lookup"><span data-stu-id="7c4a4-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c4a4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c4a4-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="7c4a4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7c4a4-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="7c4a4-106">[in] O token de TypeDef que representa o tipo para retornar metadados.</span><span class="sxs-lookup"><span data-stu-id="7c4a4-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="7c4a4-107">[out] Um buffer que contém o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="7c4a4-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="7c4a4-108">[in] O tamanho em caracteres largos da `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="7c4a4-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="7c4a4-109">[out] O número de caracteres largos retornado no `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="7c4a4-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="7c4a4-110">[out] Um ponteiro para os sinalizadores que modificam a definição de tipo.</span><span class="sxs-lookup"><span data-stu-id="7c4a4-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="7c4a4-111">Esse valor é um bitmask do [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="7c4a4-111">This value is a bitmask from the [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="7c4a4-112">[out] Um token de metadados de TypeDef ou TypeRef que representa o tipo base do tipo solicitado.</span><span class="sxs-lookup"><span data-stu-id="7c4a4-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c4a4-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7c4a4-113">Requirements</span></span>  
 <span data-ttu-id="7c4a4-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c4a4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c4a4-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7c4a4-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7c4a4-116">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="7c4a4-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7c4a4-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c4a4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c4a4-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c4a4-118">See also</span></span>

- [<span data-ttu-id="7c4a4-119">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="7c4a4-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7c4a4-120">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="7c4a4-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
