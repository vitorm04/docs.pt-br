---
title: Método IMetaDataImport::FindMemberRef
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
ms.openlocfilehash: d8b8bfd0e70e75c702f32555c10f433a1ff4ae10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175415"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="fdb08-102">Método IMetaDataImport::FindMemberRef</span><span class="sxs-lookup"><span data-stu-id="fdb08-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="fdb08-103">Obtém um ponteiro para o token MemberRef para a <xref:System.Type> referência de membro que está incluído no especificado e que tem o nome especificado e a assinatura de metadados.</span><span class="sxs-lookup"><span data-stu-id="fdb08-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdb08-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fdb08-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdb08-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="fdb08-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="fdb08-106">[em] O token TypeRef para a classe ou interface que inclui a referência do membro à pesquisa.</span><span class="sxs-lookup"><span data-stu-id="fdb08-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="fdb08-107">Se esse `mdTokenNil`valor for, a pesquisa é feita para uma variável global ou uma referência de função global.</span><span class="sxs-lookup"><span data-stu-id="fdb08-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="fdb08-108">[em] O nome da referência do membro para procurar.</span><span class="sxs-lookup"><span data-stu-id="fdb08-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="fdb08-109">[em] Um ponteiro para a assinatura binária de metadados da referência do membro.</span><span class="sxs-lookup"><span data-stu-id="fdb08-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="fdb08-110">[em] O tamanho em bytes de `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="fdb08-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="fdb08-111">[fora] Um ponteiro para o token MemberRef correspondente.</span><span class="sxs-lookup"><span data-stu-id="fdb08-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fdb08-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="fdb08-112">Remarks</span></span>  
 <span data-ttu-id="fdb08-113">Você especifica o membro usando sua`td`classe ou`szName`interface de fechamento (`pvSigBlob`), seu nome ( ), e opcionalmente sua assinatura ( ).</span><span class="sxs-lookup"><span data-stu-id="fdb08-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="fdb08-114">A assinatura `FindMemberRef` passada deve ter sido gerada no escopo atual, porque as assinaturas estão vinculadas a um escopo específico.</span><span class="sxs-lookup"><span data-stu-id="fdb08-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="fdb08-115">Uma assinatura pode incorporar um token que identifica a classe de fechamento ou o tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="fdb08-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="fdb08-116">O token é um índice na tabela typeDef local.</span><span class="sxs-lookup"><span data-stu-id="fdb08-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="fdb08-117">Não é possível construir uma assinatura de tempo de execução fora `FindMemberRef`do contexto do escopo atual e usar essa assinatura como entrada para .</span><span class="sxs-lookup"><span data-stu-id="fdb08-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="fdb08-118">`FindMemberRef`encontra apenas referências de membros que foram definidas diretamente na classe ou interface; não encontra referências de membros herdados.</span><span class="sxs-lookup"><span data-stu-id="fdb08-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdb08-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fdb08-119">Requirements</span></span>  
 <span data-ttu-id="fdb08-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdb08-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdb08-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fdb08-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fdb08-122">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fdb08-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fdb08-123">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdb08-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdb08-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="fdb08-124">See also</span></span>

- [<span data-ttu-id="fdb08-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="fdb08-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="fdb08-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="fdb08-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
