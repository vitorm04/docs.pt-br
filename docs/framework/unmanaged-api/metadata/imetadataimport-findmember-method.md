---
title: "Método IMetaDataImport::FindMember"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindMember
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a47060575d14e1206e715ea2bfd2ea750bd49c91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="7269a-102">Método IMetaDataImport::FindMember</span><span class="sxs-lookup"><span data-stu-id="7269a-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="7269a-103">Obtém um ponteiro para o MemberDef token para o campo ou método que é incluído por especificado <xref:System.Type> e que tem a assinatura de nome e os metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="7269a-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7269a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7269a-104">Syntax</span></span>  
  
```  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7269a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7269a-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="7269a-106">[in] O token de TypeDef para a classe ou interface que inclui o membro a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="7269a-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="7269a-107">Se esse valor for `mdTokenNil`, a pesquisa é feita para uma variável global ou a função global.</span><span class="sxs-lookup"><span data-stu-id="7269a-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="7269a-108">[in] O nome do membro a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="7269a-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="7269a-109">[in] Um ponteiro para a assinatura de binários de metadados do membro.</span><span class="sxs-lookup"><span data-stu-id="7269a-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="7269a-110">[in] O tamanho em bytes do `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="7269a-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="7269a-111">[out] Um ponteiro para o token MemberDef correspondente.</span><span class="sxs-lookup"><span data-stu-id="7269a-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7269a-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="7269a-112">Remarks</span></span>  
 <span data-ttu-id="7269a-113">Especifique o membro usando sua classe ou interface de delimitador (`td`), seu nome (`szName`) e, opcionalmente, sua assinatura (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="7269a-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="7269a-114">Pode haver vários membros com o mesmo nome em uma classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="7269a-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="7269a-115">Nesse caso, passe a assinatura do membro para encontrar a correspondência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="7269a-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="7269a-116">A assinatura é passado para `FindMember` deve foram gerados no escopo atual, porque as assinaturas associadas a um determinado escopo.</span><span class="sxs-lookup"><span data-stu-id="7269a-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="7269a-117">Uma assinatura pode inserir um token que identifica o tipo de valor ou classe delimitador.</span><span class="sxs-lookup"><span data-stu-id="7269a-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="7269a-118">O token é um índice na tabela de TypeDef local.</span><span class="sxs-lookup"><span data-stu-id="7269a-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="7269a-119">Você não pode criar uma assinatura de tempo de execução fora do contexto do escopo atual e use essa assinatura como entrada para cada entrada `FindMember`.</span><span class="sxs-lookup"><span data-stu-id="7269a-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="7269a-120">`FindMember`localiza apenas os membros que foram definidos diretamente na classe ou interface. membros herdados não for encontrada.</span><span class="sxs-lookup"><span data-stu-id="7269a-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7269a-121">`FindMember`é um método auxiliar.</span><span class="sxs-lookup"><span data-stu-id="7269a-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="7269a-122">Ele chama [: Findmethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); se essa chamada não encontrar uma correspondência, `FindMember` , em seguida, chama [: Findfield](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="7269a-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7269a-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7269a-123">Requirements</span></span>  
 <span data-ttu-id="7269a-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7269a-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7269a-125">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7269a-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7269a-126">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="7269a-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7269a-127">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7269a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7269a-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7269a-128">See Also</span></span>  
 [<span data-ttu-id="7269a-129">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="7269a-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="7269a-130">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="7269a-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
