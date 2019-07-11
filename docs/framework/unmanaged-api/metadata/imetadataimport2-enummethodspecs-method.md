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
ms.openlocfilehash: b8cd086a86d104fdfebf1a8298a22b795cb2389b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782639"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="b45dc-102">Método IMetaDataImport2::EnumMethodSpecs</span><span class="sxs-lookup"><span data-stu-id="b45dc-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="b45dc-103">Obtém um enumerador para uma matriz de tokens MethodSpec associados com a especificada MethodDef ou MemberRef token.</span><span class="sxs-lookup"><span data-stu-id="b45dc-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b45dc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b45dc-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="b45dc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b45dc-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b45dc-106">[no, out] Um ponteiro para o enumerador para `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="b45dc-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="b45dc-107">[in] O token de MemberRef ou MethodDef que representa o método cujos MethodSpec tokens são a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="b45dc-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="b45dc-108">Se o valor de `tk` é 0 (zero), todos os tokens de MethodSpec no escopo serão enumerados.</span><span class="sxs-lookup"><span data-stu-id="b45dc-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="b45dc-109">[out] A matriz de tokens MethodSpec para enumerar.</span><span class="sxs-lookup"><span data-stu-id="b45dc-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b45dc-110">[in] O número máximo solicitado de tokens para colocar em `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="b45dc-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="b45dc-111">[out] O número retornado de tokens são colocados em `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="b45dc-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b45dc-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b45dc-112">Return Value</span></span>  
  
|<span data-ttu-id="b45dc-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b45dc-113">HRESULT</span></span>|<span data-ttu-id="b45dc-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b45dc-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b45dc-115">`EnumMethodSpecs` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b45dc-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b45dc-116">`phEnum` não tem nenhum elemento de membro.</span><span class="sxs-lookup"><span data-stu-id="b45dc-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="b45dc-117">Nesse caso, `pcMethodSpecs` é definido como 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="b45dc-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b45dc-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b45dc-118">Requirements</span></span>  
 <span data-ttu-id="b45dc-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b45dc-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b45dc-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b45dc-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b45dc-121">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b45dc-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b45dc-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b45dc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b45dc-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b45dc-123">See also</span></span>

- [<span data-ttu-id="b45dc-124">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="b45dc-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="b45dc-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="b45dc-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
