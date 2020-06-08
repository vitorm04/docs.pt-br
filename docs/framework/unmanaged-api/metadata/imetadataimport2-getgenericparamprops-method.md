---
title: Método IMetaDataImport2::GetGenericParamProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
ms.openlocfilehash: 7e97b2d4ad1fec4675d1484959b115a4d4b87e90
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490608"
---
# <a name="imetadataimport2getgenericparamprops-method"></a><span data-ttu-id="d82b5-102">Método IMetaDataImport2::GetGenericParamProps</span><span class="sxs-lookup"><span data-stu-id="d82b5-102">IMetaDataImport2::GetGenericParamProps Method</span></span>
<span data-ttu-id="d82b5-103">Obtém os metadados associados ao parâmetro genérico representado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="d82b5-103">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d82b5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d82b5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d82b5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d82b5-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="d82b5-106">no O token que representa o parâmetro genérico para o qual retornar metadados.</span><span class="sxs-lookup"><span data-stu-id="d82b5-106">[in] The token that represents the generic parameter for which to return metadata.</span></span>  
  
 `pulParamSeq`  
 <span data-ttu-id="d82b5-107">fora A posição ordinal do `Type` parâmetro no construtor ou método pai.</span><span class="sxs-lookup"><span data-stu-id="d82b5-107">[out] The ordinal position of the `Type` parameter in the parent constructor or method.</span></span>  
  
 `pdwParamFlags`  
 <span data-ttu-id="d82b5-108">fora Um valor da enumeração [CorGenericParamAttr](corgenericparamattr-enumeration.md) que descreve o `Type` para o parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="d82b5-108">[out] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the `Type` for the generic parameter.</span></span>  
  
 `ptOwner`  
 <span data-ttu-id="d82b5-109">fora Um TypeDef ou token MethodDef que representa o proprietário do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d82b5-109">[out] A TypeDef or MethodDef token that represents the owner of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="d82b5-110">fora Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="d82b5-110">[out] Reserved for future extensibility.</span></span>  
  
 `wzName`  
 <span data-ttu-id="d82b5-111">fora O nome do parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="d82b5-111">[out] The name of the generic parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="d82b5-112">no O tamanho do `wzName` buffer.</span><span class="sxs-lookup"><span data-stu-id="d82b5-112">[in] The size of the `wzName` buffer.</span></span>  
  
 `pchName`  
 <span data-ttu-id="d82b5-113">fora O tamanho retornado do nome, em caracteres largos.</span><span class="sxs-lookup"><span data-stu-id="d82b5-113">[out] The returned size of the name, in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d82b5-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d82b5-114">Requirements</span></span>  
 <span data-ttu-id="d82b5-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d82b5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d82b5-116">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d82b5-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d82b5-117">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d82b5-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d82b5-118">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d82b5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d82b5-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="d82b5-119">See also</span></span>

- [<span data-ttu-id="d82b5-120">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="d82b5-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="d82b5-121">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="d82b5-121">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
