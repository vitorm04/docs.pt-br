---
title: Método IMetaDataImport2::EnumMethodSpecs
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6c2122c06c6e4f1137173f02e37fb0982864e7ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448368"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="744ca-102">Método IMetaDataImport2::EnumMethodSpecs</span><span class="sxs-lookup"><span data-stu-id="744ca-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="744ca-103">Obtém um enumerador para uma matriz de tokens MethodSpec associados com a especificada MethodDef ou MemberRef token.</span><span class="sxs-lookup"><span data-stu-id="744ca-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="744ca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="744ca-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="744ca-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="744ca-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="744ca-106">[out no] Um ponteiro para o enumerador para `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="744ca-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="744ca-107">[in] O token de MemberRef ou MethodDef que representa o método cujos MethodSpec tokens são a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="744ca-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="744ca-108">Se o valor de `tk` é 0 (zero), todos os tokens de MethodSpec no escopo serão enumerados.</span><span class="sxs-lookup"><span data-stu-id="744ca-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="744ca-109">[out] A matriz de tokens MethodSpec enumerar.</span><span class="sxs-lookup"><span data-stu-id="744ca-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="744ca-110">[in] O número máximo solicitado de tokens para colocar em `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="744ca-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="744ca-111">[out] O número retornado de tokens são colocados em `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="744ca-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="744ca-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="744ca-112">Return Value</span></span>  
  
|<span data-ttu-id="744ca-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="744ca-113">HRESULT</span></span>|<span data-ttu-id="744ca-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="744ca-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="744ca-115">`EnumMethodSpecs` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="744ca-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="744ca-116">`phEnum` não tem nenhum elemento de membro.</span><span class="sxs-lookup"><span data-stu-id="744ca-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="744ca-117">Nesse caso, `pcMethodSpecs` é definido como 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="744ca-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="744ca-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="744ca-118">Requirements</span></span>  
 <span data-ttu-id="744ca-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="744ca-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="744ca-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="744ca-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="744ca-121">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="744ca-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="744ca-122">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="744ca-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="744ca-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="744ca-123">See Also</span></span>  
 [<span data-ttu-id="744ca-124">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="744ca-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="744ca-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="744ca-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
