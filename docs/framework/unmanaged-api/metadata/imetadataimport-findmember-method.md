---
title: Método IMetaDataImport::FindMember
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type:
- apiref
ms.openlocfilehash: dab155b82d87609b3d3f390133e6490502a43518
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177275"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="25a75-102">Método IMetaDataImport::FindMember</span><span class="sxs-lookup"><span data-stu-id="25a75-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="25a75-103">Obtém um ponteiro para o token MemberDef para campo <xref:System.Type> ou método que está incluído no especificado e que tem o nome especificado e a assinatura de metadados.</span><span class="sxs-lookup"><span data-stu-id="25a75-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25a75-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25a75-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,
   [in]  PCCOR_SIGNATURE   pvSigBlob,
   [in]  ULONG             cbSigBlob,
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25a75-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="25a75-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="25a75-106">[em] O token TypeDef para a classe ou interface que inclui o membro para procurar.</span><span class="sxs-lookup"><span data-stu-id="25a75-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="25a75-107">Se esse `mdTokenNil`valor for, a pesquisa é feita para uma função global variável ou global.</span><span class="sxs-lookup"><span data-stu-id="25a75-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="25a75-108">[em] O nome do membro para procurar.</span><span class="sxs-lookup"><span data-stu-id="25a75-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="25a75-109">[em] Um ponteiro para a assinatura binária de metadados do membro.</span><span class="sxs-lookup"><span data-stu-id="25a75-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="25a75-110">[em] O tamanho em bytes de `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="25a75-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="25a75-111">[fora] Um ponteiro para o token MemberDef correspondente.</span><span class="sxs-lookup"><span data-stu-id="25a75-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25a75-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="25a75-112">Remarks</span></span>  
 <span data-ttu-id="25a75-113">Você especifica o membro usando sua`td`classe ou`szName`interface de fechamento (`pvSigBlob`), seu nome ( ), e opcionalmente sua assinatura ( ).</span><span class="sxs-lookup"><span data-stu-id="25a75-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="25a75-114">Pode haver vários membros com o mesmo nome em uma classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="25a75-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="25a75-115">Nesse caso, passe a assinatura do membro para encontrar a correspondência única.</span><span class="sxs-lookup"><span data-stu-id="25a75-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="25a75-116">A assinatura `FindMember` passada deve ter sido gerada no escopo atual, porque as assinaturas estão vinculadas a um escopo específico.</span><span class="sxs-lookup"><span data-stu-id="25a75-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="25a75-117">Uma assinatura pode incorporar um token que identifica a classe de fechamento ou o tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="25a75-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="25a75-118">O token é um índice na tabela typeDef local.</span><span class="sxs-lookup"><span data-stu-id="25a75-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="25a75-119">Não é possível construir uma assinatura de tempo de execução fora do `FindMember`contexto do escopo atual e usar essa assinatura como entrada para entrada em .</span><span class="sxs-lookup"><span data-stu-id="25a75-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="25a75-120">`FindMember`encontra apenas membros que foram definidos diretamente na classe ou interface; não encontra membros herdados.</span><span class="sxs-lookup"><span data-stu-id="25a75-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25a75-121">`FindMember`é um método auxiliar.</span><span class="sxs-lookup"><span data-stu-id="25a75-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="25a75-122">Ele chama [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); se essa chamada não encontrar `FindMember` uma correspondência, então chama [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="25a75-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25a75-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="25a75-123">Requirements</span></span>  
 <span data-ttu-id="25a75-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25a75-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25a75-125">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="25a75-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="25a75-126">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="25a75-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="25a75-127">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25a75-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25a75-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="25a75-128">See also</span></span>

- [<span data-ttu-id="25a75-129">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="25a75-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="25a75-130">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="25a75-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
