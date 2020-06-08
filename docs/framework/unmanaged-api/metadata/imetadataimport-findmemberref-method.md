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
ms.openlocfilehash: 068014732cee91147edaec29fa0f954a741d8b5c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491622"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="2f81c-102">Método IMetaDataImport::FindMemberRef</span><span class="sxs-lookup"><span data-stu-id="2f81c-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="2f81c-103">Obtém um ponteiro para o token de MemberRef para a referência de membro que está entre o especificado <xref:System.Type> e que tem o nome e a assinatura de metadados especificados.</span><span class="sxs-lookup"><span data-stu-id="2f81c-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f81c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2f81c-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f81c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2f81c-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="2f81c-106">no O token TypeRef para a classe ou interface que inclui a referência de membro a ser pesquisada.</span><span class="sxs-lookup"><span data-stu-id="2f81c-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="2f81c-107">Se esse valor for `mdTokenNil` , a pesquisa será feita para uma variável global ou uma referência de função global.</span><span class="sxs-lookup"><span data-stu-id="2f81c-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="2f81c-108">no O nome da referência de membro a ser pesquisada.</span><span class="sxs-lookup"><span data-stu-id="2f81c-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="2f81c-109">no Um ponteiro para a assinatura de metadados binários da referência de membro.</span><span class="sxs-lookup"><span data-stu-id="2f81c-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="2f81c-110">no O tamanho em bytes de `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="2f81c-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="2f81c-111">fora Um ponteiro para o token de MemberRef correspondente.</span><span class="sxs-lookup"><span data-stu-id="2f81c-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f81c-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="2f81c-112">Remarks</span></span>  
 <span data-ttu-id="2f81c-113">Você especifica o membro usando sua classe ou interface delimitadora ( `td` ), seu nome ( `szName` ) e, opcionalmente, sua assinatura ( `pvSigBlob` ).</span><span class="sxs-lookup"><span data-stu-id="2f81c-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="2f81c-114">A assinatura passada para `FindMemberRef` deve ter sido gerada no escopo atual, porque as assinaturas estão associadas a um escopo específico.</span><span class="sxs-lookup"><span data-stu-id="2f81c-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="2f81c-115">Uma assinatura pode inserir um token que identifica a classe de circunscrição ou o tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="2f81c-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="2f81c-116">O token é um índice na tabela de TypeDef local.</span><span class="sxs-lookup"><span data-stu-id="2f81c-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="2f81c-117">Você não pode criar uma assinatura de tempo de execução fora do contexto do escopo atual e usar essa assinatura como entrada para `FindMemberRef` .</span><span class="sxs-lookup"><span data-stu-id="2f81c-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="2f81c-118">`FindMemberRef`localiza somente referências de membros que foram definidas diretamente na classe ou na interface; Ele não localiza referências de membros herdadas.</span><span class="sxs-lookup"><span data-stu-id="2f81c-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f81c-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2f81c-119">Requirements</span></span>  
 <span data-ttu-id="2f81c-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f81c-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f81c-121">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2f81c-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2f81c-122">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2f81c-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2f81c-123">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f81c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f81c-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="2f81c-124">See also</span></span>

- [<span data-ttu-id="2f81c-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="2f81c-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="2f81c-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="2f81c-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
