---
title: Método IMetaDataImport::EnumMemberRefs
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMemberRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMemberRefs
helpviewer_keywords:
- EnumMemberRefs method [.NET Framework metadata]
- IMetaDataImport::EnumMemberRefs method [.NET Framework metadata]
ms.assetid: e97c97a6-6e4f-41f5-9af1-9b3cf3bdbd6b
topic_type:
- apiref
ms.openlocfilehash: b8a65b0748fec0e474d8b3b5dc03473fbd716108
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177329"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="207e5-102">Método IMetaDataImport::EnumMemberRefs</span><span class="sxs-lookup"><span data-stu-id="207e5-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="207e5-103">Enumera os tokens MemberRef representando membros do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="207e5-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="207e5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="207e5-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,
   [in]   mdToken        tkParent,
   [out]  mdMemberRef    rMemberRefs[],
   [in]   ULONG          cMax,
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="207e5-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="207e5-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="207e5-106">[dentro, fora] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="207e5-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="207e5-107">[em] Um token TypeDef, TypeRef, MethodDef ou ModuleRef para o tipo cujos membros devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="207e5-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="207e5-108">[fora] A matriz usada para armazenar tokens MemberRef.</span><span class="sxs-lookup"><span data-stu-id="207e5-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="207e5-109">[em] O tamanho máximo `rMemberRefs` da matriz.</span><span class="sxs-lookup"><span data-stu-id="207e5-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="207e5-110">[fora] O número real de tokens `rMemberRefs`MemberRef retornou em .</span><span class="sxs-lookup"><span data-stu-id="207e5-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="207e5-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="207e5-111">Return Value</span></span>  
  
|<span data-ttu-id="207e5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="207e5-112">HRESULT</span></span>|<span data-ttu-id="207e5-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="207e5-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="207e5-114">`EnumMemberRefs`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="207e5-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="207e5-115">Não há tokens MemberRef para enumerar.</span><span class="sxs-lookup"><span data-stu-id="207e5-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="207e5-116">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="207e5-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="207e5-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="207e5-117">Requirements</span></span>  
 <span data-ttu-id="207e5-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="207e5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="207e5-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="207e5-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="207e5-120">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="207e5-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="207e5-121">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="207e5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="207e5-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="207e5-122">See also</span></span>

- [<span data-ttu-id="207e5-123">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="207e5-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="207e5-124">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="207e5-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
