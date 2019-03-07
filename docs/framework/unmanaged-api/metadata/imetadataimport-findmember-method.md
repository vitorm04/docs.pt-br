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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 777d7bf51db3e6984f30e31c46ac115301d13faf
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478967"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="c540a-102">Método IMetaDataImport::FindMember</span><span class="sxs-lookup"><span data-stu-id="c540a-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="c540a-103">Obtém um ponteiro para o MemberDef token para o campo ou método que é incluído por especificado <xref:System.Type> e que tenha a assinatura de nome e os metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="c540a-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c540a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c540a-104">Syntax</span></span>  
  
```  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c540a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c540a-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="c540a-106">[in] O token de TypeDef para a classe ou interface que inclui o membro a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="c540a-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="c540a-107">Se esse valor for `mdTokenNil`, a pesquisa é feita para uma variável global ou uma função global.</span><span class="sxs-lookup"><span data-stu-id="c540a-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="c540a-108">[in] O nome do membro a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="c540a-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="c540a-109">[in] Um ponteiro para a assinatura binária metadados do membro.</span><span class="sxs-lookup"><span data-stu-id="c540a-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="c540a-110">[in] O tamanho em bytes do `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="c540a-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="c540a-111">[out] Um ponteiro para o token MemberDef correspondente.</span><span class="sxs-lookup"><span data-stu-id="c540a-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c540a-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="c540a-112">Remarks</span></span>  
 <span data-ttu-id="c540a-113">Você especifica o membro usando a sua classe delimitadora ou interface (`td`), seu nome (`szName`) e, opcionalmente, sua assinatura (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="c540a-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="c540a-114">Pode haver vários membros com o mesmo nome em uma classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="c540a-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="c540a-115">Nesse caso, passe a assinatura do membro para encontrar a correspondência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="c540a-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="c540a-116">A assinatura é passada para `FindMember` devem ter sido gerados no escopo atual, porque as assinaturas são associadas a um determinado escopo.</span><span class="sxs-lookup"><span data-stu-id="c540a-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="c540a-117">Uma assinatura pode inserir um token que identifica o tipo de valor ou classe delimitador.</span><span class="sxs-lookup"><span data-stu-id="c540a-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="c540a-118">O token é um índice na tabela TypeDef local.</span><span class="sxs-lookup"><span data-stu-id="c540a-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="c540a-119">Você não pode criar uma assinatura de tempo de execução fora do contexto do escopo atual e use essa assinatura como entrada para cada entrada `FindMember`.</span><span class="sxs-lookup"><span data-stu-id="c540a-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="c540a-120">`FindMember` localiza apenas os membros que foram definidos diretamente na classe ou interface; ele não localizará os membros herdados.</span><span class="sxs-lookup"><span data-stu-id="c540a-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c540a-121">`FindMember` é um método auxiliar.</span><span class="sxs-lookup"><span data-stu-id="c540a-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="c540a-122">Ele chama [imetadataimport:: Findmethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); se essa chamada não encontra uma correspondência `FindMember` , em seguida, chama [imetadataimport:: Findfield](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="c540a-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c540a-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c540a-123">Requirements</span></span>  
 <span data-ttu-id="c540a-124">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c540a-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c540a-125">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c540a-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c540a-126">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c540a-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c540a-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c540a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c540a-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c540a-128">See also</span></span>
- [<span data-ttu-id="c540a-129">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="c540a-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c540a-130">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="c540a-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
