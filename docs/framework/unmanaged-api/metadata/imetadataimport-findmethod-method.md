---
title: Método IMetaDataImport::FindMethod
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
ms.openlocfilehash: 53b3d94e8b1e273fcbc041d25a5bf586a12735c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177260"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="c4c9a-102">Método IMetaDataImport::FindMethod</span><span class="sxs-lookup"><span data-stu-id="c4c9a-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="c4c9a-103">Obtém um ponteiro para o token MethodDef para o <xref:System.Type> método que é incluído pelo especificado e que tem o nome especificado e a assinatura de metadados.</span><span class="sxs-lookup"><span data-stu-id="c4c9a-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4c9a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4c9a-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4c9a-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="c4c9a-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="c4c9a-106">[em] O `mdTypeDef` token para o tipo (uma classe ou interface) que inclui o membro para procurar.</span><span class="sxs-lookup"><span data-stu-id="c4c9a-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="c4c9a-107">Se esse `mdTokenNil`valor for, então a pesquisa é feita para uma função global.</span><span class="sxs-lookup"><span data-stu-id="c4c9a-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="c4c9a-108">[em] O nome do método para procurar.</span><span class="sxs-lookup"><span data-stu-id="c4c9a-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="c4c9a-109">[em] Um ponteiro para a assinatura binária de metadados do método.</span><span class="sxs-lookup"><span data-stu-id="c4c9a-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="c4c9a-110">[em] O tamanho em bytes de `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="c4c9a-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="c4c9a-111">[fora] Um ponteiro para o token MethodDef correspondente.</span><span class="sxs-lookup"><span data-stu-id="c4c9a-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4c9a-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="c4c9a-112">Remarks</span></span>  
 <span data-ttu-id="c4c9a-113">Você especifica o método usando sua`td`classe de`szName`fechamento ou interface (`pvSigBlob`), seu nome ( ), e opcionalmente sua assinatura ( ).</span><span class="sxs-lookup"><span data-stu-id="c4c9a-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="c4c9a-114">Pode haver vários métodos com o mesmo nome em uma classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="c4c9a-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="c4c9a-115">Nesse caso, passe a assinatura do método para encontrar a correspondência única.</span><span class="sxs-lookup"><span data-stu-id="c4c9a-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="c4c9a-116">A assinatura `FindMethod` passada deve ter sido gerada no escopo atual, porque as assinaturas estão vinculadas a um escopo específico.</span><span class="sxs-lookup"><span data-stu-id="c4c9a-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="c4c9a-117">Uma assinatura pode incorporar um token que identifica a classe de fechamento ou o tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="c4c9a-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="c4c9a-118">O token é um índice na tabela typeDef local.</span><span class="sxs-lookup"><span data-stu-id="c4c9a-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="c4c9a-119">Não é possível construir uma assinatura de tempo de execução fora do `FindMethod`contexto do escopo atual e usar essa assinatura como entrada para entrada em .</span><span class="sxs-lookup"><span data-stu-id="c4c9a-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="c4c9a-120">`FindMethod`encontra apenas métodos que foram definidos diretamente na classe ou interface; não encontra métodos herdados.</span><span class="sxs-lookup"><span data-stu-id="c4c9a-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4c9a-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c4c9a-121">Requirements</span></span>  
 <span data-ttu-id="c4c9a-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4c9a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4c9a-123">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c4c9a-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c4c9a-124">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c4c9a-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c4c9a-125">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4c9a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4c9a-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="c4c9a-126">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="c4c9a-127">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="c4c9a-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c4c9a-128">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="c4c9a-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
