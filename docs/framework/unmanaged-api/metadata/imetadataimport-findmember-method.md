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
ms.openlocfilehash: 4eefb7ec1e7d0d130ec64531a59d1d5bbce04963
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968928"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="b43c5-102">Método IMetaDataImport::FindMember</span><span class="sxs-lookup"><span data-stu-id="b43c5-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="b43c5-103">Obtém um ponteiro para o token MemberDef para o campo ou método que está incluído pelo especificado <xref:System.Type> e que tem o nome especificado e a assinatura de metadados.</span><span class="sxs-lookup"><span data-stu-id="b43c5-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b43c5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b43c5-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b43c5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b43c5-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="b43c5-106">no O token de TypeDef para a classe ou interface que inclui o membro a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="b43c5-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="b43c5-107">Se esse valor for `mdTokenNil`, a pesquisa será feita para uma global-Variable ou uma função global.</span><span class="sxs-lookup"><span data-stu-id="b43c5-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="b43c5-108">no O nome do membro a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="b43c5-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="b43c5-109">no Um ponteiro para a assinatura de metadados binários do membro.</span><span class="sxs-lookup"><span data-stu-id="b43c5-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="b43c5-110">no O tamanho em bytes de `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="b43c5-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="b43c5-111">fora Um ponteiro para o token MemberDef correspondente.</span><span class="sxs-lookup"><span data-stu-id="b43c5-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b43c5-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="b43c5-112">Remarks</span></span>  
 <span data-ttu-id="b43c5-113">Você especifica o membro usando sua classe ou interface delimitadora`td`(), seu nome`szName`() e, opcionalmente, sua`pvSigBlob`assinatura ().</span><span class="sxs-lookup"><span data-stu-id="b43c5-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="b43c5-114">Pode haver vários membros com o mesmo nome em uma classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="b43c5-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="b43c5-115">Nesse caso, passe a assinatura do membro para localizar a correspondência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="b43c5-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="b43c5-116">A assinatura passada para `FindMember` deve ter sido gerada no escopo atual, porque as assinaturas estão associadas a um escopo específico.</span><span class="sxs-lookup"><span data-stu-id="b43c5-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="b43c5-117">Uma assinatura pode inserir um token que identifica a classe de circunscrição ou o tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="b43c5-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="b43c5-118">O token é um índice na tabela de TypeDef local.</span><span class="sxs-lookup"><span data-stu-id="b43c5-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="b43c5-119">Você não pode criar uma assinatura de tempo de execução fora do contexto do escopo atual e usar essa assinatura como entrada para entrada `FindMember`no.</span><span class="sxs-lookup"><span data-stu-id="b43c5-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="b43c5-120">`FindMember`localiza somente os membros que foram definidos diretamente na classe ou interface; Ele não encontra membros herdados.</span><span class="sxs-lookup"><span data-stu-id="b43c5-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b43c5-121">`FindMember`é um método auxiliar.</span><span class="sxs-lookup"><span data-stu-id="b43c5-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="b43c5-122">Ele chama [IMetaDataImport:: FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); Se essa chamada não encontrar uma correspondência, `FindMember` o chamará [IMetaDataImport:: FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="b43c5-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b43c5-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b43c5-123">Requirements</span></span>  
 <span data-ttu-id="b43c5-124">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b43c5-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b43c5-125">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b43c5-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b43c5-126">**Biblioteca** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b43c5-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b43c5-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b43c5-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b43c5-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b43c5-128">See also</span></span>

- [<span data-ttu-id="b43c5-129">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="b43c5-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b43c5-130">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="b43c5-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
