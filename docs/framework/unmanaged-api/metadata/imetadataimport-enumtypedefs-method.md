---
title: Método IMetaDataImport::EnumTypeDefs
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
ms.openlocfilehash: 2d6e86a7f5a93b900e79907f8ee0762869d7f737
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177293"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="83258-102">Método IMetaDataImport::EnumTypeDefs</span><span class="sxs-lookup"><span data-stu-id="83258-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="83258-103">Enumera tokens TypeDef representando todos os tipos dentro do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="83258-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83258-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83258-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83258-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="83258-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="83258-106">[fora] Um ponteiro para o novo enumerador.</span><span class="sxs-lookup"><span data-stu-id="83258-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="83258-107">Isto deve ser NULO para a primeira chamada deste método.</span><span class="sxs-lookup"><span data-stu-id="83258-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="83258-108">[em] A matriz usada para armazenar os tokens TypeDef.</span><span class="sxs-lookup"><span data-stu-id="83258-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="83258-109">[em] O tamanho máximo `rTypeDefs` da matriz.</span><span class="sxs-lookup"><span data-stu-id="83258-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="83258-110">[fora] O número de tokens TypeDef retornado em `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="83258-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83258-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="83258-111">Return Value</span></span>  
  
|<span data-ttu-id="83258-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="83258-112">HRESULT</span></span>|<span data-ttu-id="83258-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="83258-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="83258-114">`EnumTypeDefs`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="83258-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="83258-115">Não há tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="83258-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="83258-116">Nesse caso, `pcTypeDefs` é zero.</span><span class="sxs-lookup"><span data-stu-id="83258-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83258-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="83258-117">Remarks</span></span>  
 <span data-ttu-id="83258-118">O token TypeDef representa um tipo como uma classe ou uma interface, bem como qualquer tipo adicionado através de um mecanismo de extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="83258-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83258-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="83258-119">Requirements</span></span>  
 <span data-ttu-id="83258-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83258-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83258-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="83258-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83258-122">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="83258-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="83258-123">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83258-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83258-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="83258-124">See also</span></span>

- [<span data-ttu-id="83258-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="83258-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="83258-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="83258-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
