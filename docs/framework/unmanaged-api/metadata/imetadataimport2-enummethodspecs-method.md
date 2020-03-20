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
ms.openlocfilehash: 2df53ba53c64e042abc54a1d2ac043d301acdde9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177182"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="c9707-102">Método IMetaDataImport2::EnumMethodSpecs</span><span class="sxs-lookup"><span data-stu-id="c9707-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="c9707-103">Obtém um enumerador para uma matriz de tokens MethodSpec associados ao token MethodDef ou MemberRef especificado.</span><span class="sxs-lookup"><span data-stu-id="c9707-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9707-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9707-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="c9707-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="c9707-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c9707-106">[dentro, fora] Um ponteiro para o enumerador para `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="c9707-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="c9707-107">[em] O token MemberRef ou MethodDef que representa o método cujos tokens MethodSpec devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="c9707-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="c9707-108">Se o `tk` valor for 0 (zero), todos os tokens MethodSpec no escopo serão enumerados.</span><span class="sxs-lookup"><span data-stu-id="c9707-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="c9707-109">[fora] A matriz de tokens MethodSpec para enumerar.</span><span class="sxs-lookup"><span data-stu-id="c9707-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c9707-110">[em] O número máximo solicitado de tokens para colocar em `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="c9707-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="c9707-111">[fora] O número retornado de tokens colocados em `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="c9707-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9707-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c9707-112">Return Value</span></span>  
  
|<span data-ttu-id="c9707-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9707-113">HRESULT</span></span>|<span data-ttu-id="c9707-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9707-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c9707-115">`EnumMethodSpecs`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="c9707-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c9707-116">`phEnum`não tem elementos membros.</span><span class="sxs-lookup"><span data-stu-id="c9707-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="c9707-117">Neste caso, `pcMethodSpecs` está definido como 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="c9707-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9707-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c9707-118">Requirements</span></span>  
 <span data-ttu-id="c9707-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9707-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9707-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c9707-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c9707-121">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9707-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c9707-122">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9707-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9707-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="c9707-123">See also</span></span>

- [<span data-ttu-id="c9707-124">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="c9707-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="c9707-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="c9707-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
