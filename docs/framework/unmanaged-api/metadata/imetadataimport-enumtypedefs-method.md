---
title: "Método IMetaDataImport::EnumTypeDefs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumTypeDefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aeb0e3c2eab4cde219b050bcf0e50202fe2be3f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="c527c-102">Método IMetaDataImport::EnumTypeDefs</span><span class="sxs-lookup"><span data-stu-id="c527c-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="c527c-103">Enumera os tokens de TypeDef que representa todos os tipos de dentro do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="c527c-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c527c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c527c-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c527c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c527c-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c527c-106">[out] Um ponteiro para o novo enumerador.</span><span class="sxs-lookup"><span data-stu-id="c527c-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="c527c-107">Isso deve ser NULL para a primeira chamada do método.</span><span class="sxs-lookup"><span data-stu-id="c527c-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="c527c-108">[in] A matriz usada para armazenar os tokens de TypeDef.</span><span class="sxs-lookup"><span data-stu-id="c527c-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c527c-109">[in] O tamanho máximo da `rTypeDefs` matriz.</span><span class="sxs-lookup"><span data-stu-id="c527c-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="c527c-110">[out] O número de tokens de TypeDef retornados em `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="c527c-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c527c-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c527c-111">Return Value</span></span>  
  
|<span data-ttu-id="c527c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c527c-112">HRESULT</span></span>|<span data-ttu-id="c527c-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c527c-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c527c-114">`EnumTypeDefs`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="c527c-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c527c-115">Não há nenhum tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="c527c-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="c527c-116">Nesse caso, `pcTypeDefs` é zero.</span><span class="sxs-lookup"><span data-stu-id="c527c-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c527c-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="c527c-117">Remarks</span></span>  
 <span data-ttu-id="c527c-118">O token de TypeDef representa um tipo como uma classe ou uma interface, bem como qualquer tipo adicionados por meio de um mecanismo de extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="c527c-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c527c-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c527c-119">Requirements</span></span>  
 <span data-ttu-id="c527c-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c527c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c527c-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c527c-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c527c-122">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="c527c-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c527c-123">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c527c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c527c-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c527c-124">See Also</span></span>  
 [<span data-ttu-id="c527c-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="c527c-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="c527c-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="c527c-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
