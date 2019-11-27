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
ms.openlocfilehash: 743b6bed1a5d62f5214b8366b1a3c6e4ebecb98b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441711"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="3ac23-102">Método IMetaDataImport::EnumMemberRefs</span><span class="sxs-lookup"><span data-stu-id="3ac23-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="3ac23-103">Enumera os tokens de MemberRef que representam os membros do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="3ac23-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ac23-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ac23-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,   
   [in]   mdToken        tkParent,   
   [out]  mdMemberRef    rMemberRefs[],   
   [in]   ULONG          cMax,   
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ac23-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3ac23-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3ac23-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="3ac23-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="3ac23-107">no Um token de TypeDef, TypeRef, MethodDef ou ModuleRef para o tipo cujos membros devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="3ac23-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="3ac23-108">fora A matriz usada para armazenar tokens de MemberRef.</span><span class="sxs-lookup"><span data-stu-id="3ac23-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3ac23-109">no O tamanho máximo da matriz de `rMemberRefs`.</span><span class="sxs-lookup"><span data-stu-id="3ac23-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="3ac23-110">fora O número real de tokens de MemberRef retornado em `rMemberRefs`.</span><span class="sxs-lookup"><span data-stu-id="3ac23-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ac23-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3ac23-111">Return Value</span></span>  
  
|<span data-ttu-id="3ac23-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3ac23-112">HRESULT</span></span>|<span data-ttu-id="3ac23-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ac23-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3ac23-114">`EnumMemberRefs` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="3ac23-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3ac23-115">Não há tokens de MemberRef para enumerar.</span><span class="sxs-lookup"><span data-stu-id="3ac23-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="3ac23-116">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="3ac23-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3ac23-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3ac23-117">Requirements</span></span>  
 <span data-ttu-id="3ac23-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ac23-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ac23-119">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3ac23-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3ac23-120">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3ac23-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3ac23-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ac23-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ac23-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ac23-122">See also</span></span>

- [<span data-ttu-id="3ac23-123">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="3ac23-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3ac23-124">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="3ac23-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
