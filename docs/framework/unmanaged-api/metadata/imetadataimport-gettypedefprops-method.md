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
ms.openlocfilehash: c9ac624e17223def206e86fd92ee4fd2de7f6082
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436753"
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="51585-102">Método IMetaDataImport::GetTypeDefProps</span><span class="sxs-lookup"><span data-stu-id="51585-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="51585-103">Retorna informações de metadados para o <xref:System.Type> representado pelo token de TypeDef especificado.</span><span class="sxs-lookup"><span data-stu-id="51585-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51585-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51585-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51585-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="51585-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="51585-106">no O token de TypeDef que representa o tipo para o qual retornar metadados.</span><span class="sxs-lookup"><span data-stu-id="51585-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="51585-107">fora Um buffer que contém o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="51585-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="51585-108">no O tamanho em caracteres largos de `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="51585-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="51585-109">fora O número de caracteres largos retornados em `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="51585-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="51585-110">fora Um ponteiro para quaisquer sinalizadores que modificam a definição de tipo.</span><span class="sxs-lookup"><span data-stu-id="51585-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="51585-111">Esse valor é um bitmask da enumeração [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="51585-111">This value is a bitmask from the [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="51585-112">fora Um token de metadados TypeDef ou TypeRef que representa o tipo base do tipo solicitado.</span><span class="sxs-lookup"><span data-stu-id="51585-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51585-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="51585-113">Requirements</span></span>  
 <span data-ttu-id="51585-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51585-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51585-115">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="51585-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="51585-116">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="51585-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="51585-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51585-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51585-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51585-118">See also</span></span>

- [<span data-ttu-id="51585-119">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="51585-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="51585-120">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="51585-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
