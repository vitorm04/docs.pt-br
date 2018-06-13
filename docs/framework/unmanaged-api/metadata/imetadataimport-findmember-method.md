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
ms.openlocfilehash: 79c9a54a44ae1751cb8b1b57379ccfd6485f6e6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448185"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="040ed-102">Método IMetaDataImport::FindMember</span><span class="sxs-lookup"><span data-stu-id="040ed-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="040ed-103">Obtém um ponteiro para o MemberDef token para o campo ou método que é incluído por especificado <xref:System.Type> e que tem a assinatura de nome e os metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="040ed-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="040ed-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="040ed-104">Syntax</span></span>  
  
```  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="040ed-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="040ed-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="040ed-106">[in] O token de TypeDef para a classe ou interface que inclui o membro a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="040ed-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="040ed-107">Se esse valor for `mdTokenNil`, a pesquisa é feita para uma variável global ou a função global.</span><span class="sxs-lookup"><span data-stu-id="040ed-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="040ed-108">[in] O nome do membro a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="040ed-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="040ed-109">[in] Um ponteiro para a assinatura de binários de metadados do membro.</span><span class="sxs-lookup"><span data-stu-id="040ed-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="040ed-110">[in] O tamanho em bytes do `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="040ed-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="040ed-111">[out] Um ponteiro para o token MemberDef correspondente.</span><span class="sxs-lookup"><span data-stu-id="040ed-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="040ed-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="040ed-112">Remarks</span></span>  
 <span data-ttu-id="040ed-113">Especifique o membro usando sua classe ou interface de delimitador (`td`), seu nome (`szName`) e, opcionalmente, sua assinatura (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="040ed-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="040ed-114">Pode haver vários membros com o mesmo nome em uma classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="040ed-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="040ed-115">Nesse caso, passe a assinatura do membro para encontrar a correspondência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="040ed-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="040ed-116">A assinatura é passado para `FindMember` deve foram gerados no escopo atual, porque as assinaturas associadas a um determinado escopo.</span><span class="sxs-lookup"><span data-stu-id="040ed-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="040ed-117">Uma assinatura pode inserir um token que identifica o tipo de valor ou classe delimitador.</span><span class="sxs-lookup"><span data-stu-id="040ed-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="040ed-118">O token é um índice na tabela de TypeDef local.</span><span class="sxs-lookup"><span data-stu-id="040ed-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="040ed-119">Você não pode criar uma assinatura de tempo de execução fora do contexto do escopo atual e use essa assinatura como entrada para cada entrada `FindMember`.</span><span class="sxs-lookup"><span data-stu-id="040ed-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="040ed-120">`FindMember` localiza apenas os membros que foram definidos diretamente na classe ou interface. membros herdados não for encontrada.</span><span class="sxs-lookup"><span data-stu-id="040ed-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="040ed-121">`FindMember` é um método auxiliar.</span><span class="sxs-lookup"><span data-stu-id="040ed-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="040ed-122">Ele chama [: Findmethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); se essa chamada não encontrar uma correspondência, `FindMember` , em seguida, chama [: Findfield](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="040ed-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="040ed-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="040ed-123">Requirements</span></span>  
 <span data-ttu-id="040ed-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="040ed-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="040ed-125">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="040ed-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="040ed-126">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="040ed-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="040ed-127">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="040ed-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="040ed-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="040ed-128">See Also</span></span>  
 [<span data-ttu-id="040ed-129">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="040ed-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="040ed-130">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="040ed-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
