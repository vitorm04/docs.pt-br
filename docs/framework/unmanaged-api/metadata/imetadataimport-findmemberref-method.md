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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 057dd7c25821aedddeee57a31200cf35c6df1273
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498509"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="ffb15-102">Método IMetaDataImport::FindMemberRef</span><span class="sxs-lookup"><span data-stu-id="ffb15-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="ffb15-103">Obtém um ponteiro para o token MemberRef para o membro de referência que é delimitada por especificado <xref:System.Type> e que tenha a assinatura de nome e os metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="ffb15-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffb15-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ffb15-104">Syntax</span></span>  
  
```  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ffb15-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ffb15-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="ffb15-106">[in] O token TypeRef para a classe ou interface que inclui a referência de membro a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="ffb15-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="ffb15-107">Se esse valor for `mdTokenNil`, a pesquisa é feita para uma variável global ou uma referência de função global.</span><span class="sxs-lookup"><span data-stu-id="ffb15-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="ffb15-108">[in] O nome da referência de membro a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="ffb15-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="ffb15-109">[in] Um ponteiro para a assinatura binária metadados da referência de membro.</span><span class="sxs-lookup"><span data-stu-id="ffb15-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="ffb15-110">[in] O tamanho em bytes do `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="ffb15-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="ffb15-111">[out] Um ponteiro para o token MemberRef correspondente.</span><span class="sxs-lookup"><span data-stu-id="ffb15-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffb15-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="ffb15-112">Remarks</span></span>  
 <span data-ttu-id="ffb15-113">Você especifica o membro usando a sua classe delimitadora ou interface (`td`), seu nome (`szName`) e, opcionalmente, sua assinatura (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="ffb15-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="ffb15-114">A assinatura é passada para `FindMemberRef` devem ter sido gerados no escopo atual, porque as assinaturas são associadas a um determinado escopo.</span><span class="sxs-lookup"><span data-stu-id="ffb15-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="ffb15-115">Uma assinatura pode inserir um token que identifica o tipo de valor ou classe delimitador.</span><span class="sxs-lookup"><span data-stu-id="ffb15-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="ffb15-116">O token é um índice na tabela TypeDef local.</span><span class="sxs-lookup"><span data-stu-id="ffb15-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="ffb15-117">Você não pode criar uma assinatura de tempo de execução fora do contexto do escopo atual e usar essa assinatura como entrada para `FindMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="ffb15-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="ffb15-118">`FindMemberRef` localiza apenas as referências de membro que foram definidas diretamente na classe ou interface; ele não encontra referências do membro herdado.</span><span class="sxs-lookup"><span data-stu-id="ffb15-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffb15-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ffb15-119">Requirements</span></span>  
 <span data-ttu-id="ffb15-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffb15-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffb15-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ffb15-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ffb15-122">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ffb15-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ffb15-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffb15-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffb15-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ffb15-124">See also</span></span>
- [<span data-ttu-id="ffb15-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="ffb15-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ffb15-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="ffb15-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
