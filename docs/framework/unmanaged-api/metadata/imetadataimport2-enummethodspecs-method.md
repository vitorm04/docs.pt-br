---
title: "Método IMetaDataImport2::EnumMethodSpecs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.EnumMethodSpecs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e134d19eb6699f39e6d538f93f989b87ed8f37d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="b18e8-102">Método IMetaDataImport2::EnumMethodSpecs</span><span class="sxs-lookup"><span data-stu-id="b18e8-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="b18e8-103">Obtém um enumerador para uma matriz de tokens MethodSpec associados com a especificada MethodDef ou MemberRef token.</span><span class="sxs-lookup"><span data-stu-id="b18e8-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b18e8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b18e8-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="b18e8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b18e8-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b18e8-106">[out no] Um ponteiro para o enumerador para `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="b18e8-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="b18e8-107">[in] O token de MemberRef ou MethodDef que representa o método cujos MethodSpec tokens são a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="b18e8-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="b18e8-108">Se o valor de `tk` é 0 (zero), todos os tokens de MethodSpec no escopo serão enumerados.</span><span class="sxs-lookup"><span data-stu-id="b18e8-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="b18e8-109">[out] A matriz de tokens MethodSpec enumerar.</span><span class="sxs-lookup"><span data-stu-id="b18e8-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b18e8-110">[in] O número máximo solicitado de tokens para colocar em `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="b18e8-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="b18e8-111">[out] O número retornado de tokens são colocados em `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="b18e8-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b18e8-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b18e8-112">Return Value</span></span>  
  
|<span data-ttu-id="b18e8-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b18e8-113">HRESULT</span></span>|<span data-ttu-id="b18e8-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b18e8-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b18e8-115">`EnumMethodSpecs`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="b18e8-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b18e8-116">`phEnum`não tem nenhum elemento de membro.</span><span class="sxs-lookup"><span data-stu-id="b18e8-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="b18e8-117">Nesse caso, `pcMethodSpecs` é definido como 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="b18e8-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b18e8-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b18e8-118">Requirements</span></span>  
 <span data-ttu-id="b18e8-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b18e8-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b18e8-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b18e8-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b18e8-121">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b18e8-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b18e8-122">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b18e8-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b18e8-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b18e8-123">See Also</span></span>  
 [<span data-ttu-id="b18e8-124">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="b18e8-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="b18e8-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="b18e8-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
