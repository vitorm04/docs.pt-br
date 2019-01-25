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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 34a6762618780b22bcd8be376209912390524578
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591998"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="23bb2-102">Método IMetaDataImport::EnumMemberRefs</span><span class="sxs-lookup"><span data-stu-id="23bb2-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="23bb2-103">Enumera os tokens de MemberRef que representa os membros do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="23bb2-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23bb2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23bb2-104">Syntax</span></span>  
  
```  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,   
   [in]   mdToken        tkParent,   
   [out]  mdMemberRef    rMemberRefs[],   
   [in]   ULONG          cMax,   
   [out]  ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23bb2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="23bb2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="23bb2-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="23bb2-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="23bb2-107">[in] Um TypeDef, TypeRef, MethodDef ou ModuleRef token para o tipo cujos membros são a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="23bb2-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="23bb2-108">[out] A matriz usada para armazenar os tokens de MemberRef.</span><span class="sxs-lookup"><span data-stu-id="23bb2-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="23bb2-109">[in] O tamanho máximo da `rMemberRefs` matriz.</span><span class="sxs-lookup"><span data-stu-id="23bb2-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="23bb2-110">[out] O número real de tokens de MemberRef retornado no `rMemberRefs`.</span><span class="sxs-lookup"><span data-stu-id="23bb2-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23bb2-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="23bb2-111">Return Value</span></span>  
  
|<span data-ttu-id="23bb2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="23bb2-112">HRESULT</span></span>|<span data-ttu-id="23bb2-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="23bb2-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="23bb2-114">`EnumMemberRefs` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="23bb2-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="23bb2-115">Não há nenhum token MemberRef para enumerar.</span><span class="sxs-lookup"><span data-stu-id="23bb2-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="23bb2-116">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="23bb2-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="23bb2-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="23bb2-117">Requirements</span></span>  
 <span data-ttu-id="23bb2-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23bb2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23bb2-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="23bb2-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="23bb2-120">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="23bb2-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="23bb2-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23bb2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23bb2-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23bb2-122">See also</span></span>
- [<span data-ttu-id="23bb2-123">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="23bb2-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="23bb2-124">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="23bb2-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
