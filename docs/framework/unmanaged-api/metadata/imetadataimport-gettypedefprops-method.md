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
ms.openlocfilehash: 6346b1e34e508e5c173bfd0119ac7451d7eef40e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490790"
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="b7eda-102">Método IMetaDataImport::GetTypeDefProps</span><span class="sxs-lookup"><span data-stu-id="b7eda-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="b7eda-103">Retorna informações de metadados para o <xref:System.Type> representado pelo token de TypeDef especificado.</span><span class="sxs-lookup"><span data-stu-id="b7eda-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7eda-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7eda-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b7eda-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b7eda-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="b7eda-106">no O token de TypeDef que representa o tipo para o qual retornar metadados.</span><span class="sxs-lookup"><span data-stu-id="b7eda-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="b7eda-107">fora Um buffer que contém o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="b7eda-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="b7eda-108">no O tamanho em caracteres largos de `szTypeDef` .</span><span class="sxs-lookup"><span data-stu-id="b7eda-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="b7eda-109">fora O número de caracteres largos retornados em `szTypeDef` .</span><span class="sxs-lookup"><span data-stu-id="b7eda-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="b7eda-110">fora Um ponteiro para quaisquer sinalizadores que modificam a definição de tipo.</span><span class="sxs-lookup"><span data-stu-id="b7eda-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="b7eda-111">Esse valor é um bitmask da enumeração [CorTypeAttr](cortypeattr-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="b7eda-111">This value is a bitmask from the [CorTypeAttr](cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="b7eda-112">fora Um token de metadados TypeDef ou TypeRef que representa o tipo base do tipo solicitado.</span><span class="sxs-lookup"><span data-stu-id="b7eda-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7eda-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b7eda-113">Requirements</span></span>  
 <span data-ttu-id="b7eda-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7eda-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7eda-115">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b7eda-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b7eda-116">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b7eda-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b7eda-117">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7eda-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7eda-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="b7eda-118">See also</span></span>

- [<span data-ttu-id="b7eda-119">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="b7eda-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b7eda-120">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="b7eda-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
