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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4225794740b7786c6f758c9a0953d323c31a1081
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782485"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="fd999-102">Método IMetaDataImport::FindMethod</span><span class="sxs-lookup"><span data-stu-id="fd999-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="fd999-103">Obtém um ponteiro para o MethodDef token para o método que é incluído por especificado <xref:System.Type> e que tenha a assinatura de nome e os metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="fd999-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd999-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fd999-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd999-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fd999-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="fd999-106">[in] O `mdTypeDef` token para o tipo (uma classe ou interface) que inclui o membro a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="fd999-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="fd999-107">Se esse valor for `mdTokenNil`, em seguida, a pesquisa é feita para uma função global.</span><span class="sxs-lookup"><span data-stu-id="fd999-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="fd999-108">[in] O nome do método a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="fd999-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="fd999-109">[in] Um ponteiro para a assinatura de metadados de binários do método.</span><span class="sxs-lookup"><span data-stu-id="fd999-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="fd999-110">[in] O tamanho em bytes do `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="fd999-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="fd999-111">[out] Um ponteiro para o token MethodDef correspondente.</span><span class="sxs-lookup"><span data-stu-id="fd999-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd999-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="fd999-112">Remarks</span></span>  
 <span data-ttu-id="fd999-113">Especificar o método usando a sua classe delimitadora ou interface (`td`), seu nome (`szName`) e, opcionalmente, sua assinatura (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="fd999-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="fd999-114">Pode haver vários métodos com o mesmo nome em uma classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="fd999-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="fd999-115">Nesse caso, passe a assinatura do método para encontrar a correspondência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="fd999-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="fd999-116">A assinatura é passada para `FindMethod` devem ter sido gerados no escopo atual, porque as assinaturas são associadas a um determinado escopo.</span><span class="sxs-lookup"><span data-stu-id="fd999-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="fd999-117">Uma assinatura pode inserir um token que identifica o tipo de valor ou classe delimitador.</span><span class="sxs-lookup"><span data-stu-id="fd999-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="fd999-118">O token é um índice na tabela TypeDef local.</span><span class="sxs-lookup"><span data-stu-id="fd999-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="fd999-119">Você não pode criar uma assinatura de tempo de execução fora do contexto do escopo atual e use essa assinatura como entrada para cada entrada `FindMethod`.</span><span class="sxs-lookup"><span data-stu-id="fd999-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="fd999-120">`FindMethod` localiza apenas os métodos que foram definidos diretamente na classe ou interface; ele não localizará os métodos herdados.</span><span class="sxs-lookup"><span data-stu-id="fd999-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd999-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fd999-121">Requirements</span></span>  
 <span data-ttu-id="fd999-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd999-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd999-123">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fd999-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fd999-124">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="fd999-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fd999-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd999-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd999-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd999-126">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="fd999-127">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="fd999-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="fd999-128">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="fd999-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
