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
ms.openlocfilehash: 24ad5ff05e4f7fe7fcfc06ff5fe096d47e8b3cbb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468202"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="8b561-102">Método IMetaDataImport2::EnumMethodSpecs</span><span class="sxs-lookup"><span data-stu-id="8b561-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="8b561-103">Obtém um enumerador para uma matriz de tokens MethodSpec associados com a especificada MethodDef ou MemberRef token.</span><span class="sxs-lookup"><span data-stu-id="8b561-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b561-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b561-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="8b561-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8b561-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="8b561-106">[no, out] Um ponteiro para o enumerador para `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="8b561-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="8b561-107">[in] O token de MemberRef ou MethodDef que representa o método cujos MethodSpec tokens são a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="8b561-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="8b561-108">Se o valor de `tk` é 0 (zero), todos os tokens de MethodSpec no escopo serão enumerados.</span><span class="sxs-lookup"><span data-stu-id="8b561-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="8b561-109">[out] A matriz de tokens MethodSpec para enumerar.</span><span class="sxs-lookup"><span data-stu-id="8b561-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8b561-110">[in] O número máximo solicitado de tokens para colocar em `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="8b561-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="8b561-111">[out] O número retornado de tokens são colocados em `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="8b561-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b561-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8b561-112">Return Value</span></span>  
  
|<span data-ttu-id="8b561-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8b561-113">HRESULT</span></span>|<span data-ttu-id="8b561-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b561-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8b561-115">`EnumMethodSpecs` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="8b561-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8b561-116">`phEnum` não tem nenhum elemento de membro.</span><span class="sxs-lookup"><span data-stu-id="8b561-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="8b561-117">Nesse caso, `pcMethodSpecs` é definido como 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="8b561-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8b561-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8b561-118">Requirements</span></span>  
 <span data-ttu-id="8b561-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b561-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b561-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8b561-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b561-121">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8b561-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8b561-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b561-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b561-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b561-123">See also</span></span>
- [<span data-ttu-id="8b561-124">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="8b561-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="8b561-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="8b561-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
