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
ms.openlocfilehash: 28aa8313e7ba0c071187d0f1f6d78431b16fc005
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164795"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="0746f-102">Método IMetaDataImport::FindMethod</span><span class="sxs-lookup"><span data-stu-id="0746f-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="0746f-103">Obtém um ponteiro para o MethodDef token para o método que é incluído por especificado <xref:System.Type> e que tenha a assinatura de nome e os metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="0746f-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0746f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0746f-104">Syntax</span></span>  
  
```  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0746f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0746f-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="0746f-106">[in] O `mdTypeDef` token para o tipo (uma classe ou interface) que inclui o membro a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="0746f-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="0746f-107">Se esse valor for `mdTokenNil`, em seguida, a pesquisa é feita para uma função global.</span><span class="sxs-lookup"><span data-stu-id="0746f-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="0746f-108">[in] O nome do método a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="0746f-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="0746f-109">[in] Um ponteiro para a assinatura de metadados de binários do método.</span><span class="sxs-lookup"><span data-stu-id="0746f-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="0746f-110">[in] O tamanho em bytes do `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="0746f-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="0746f-111">[out] Um ponteiro para o token MethodDef correspondente.</span><span class="sxs-lookup"><span data-stu-id="0746f-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0746f-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="0746f-112">Remarks</span></span>  
 <span data-ttu-id="0746f-113">Especificar o método usando a sua classe delimitadora ou interface (`td`), seu nome (`szName`) e, opcionalmente, sua assinatura (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="0746f-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="0746f-114">Pode haver vários métodos com o mesmo nome em uma classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="0746f-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="0746f-115">Nesse caso, passe a assinatura do método para encontrar a correspondência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="0746f-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="0746f-116">A assinatura é passada para `FindMethod` devem ter sido gerados no escopo atual, porque as assinaturas são associadas a um determinado escopo.</span><span class="sxs-lookup"><span data-stu-id="0746f-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="0746f-117">Uma assinatura pode inserir um token que identifica o tipo de valor ou classe delimitador.</span><span class="sxs-lookup"><span data-stu-id="0746f-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="0746f-118">O token é um índice na tabela TypeDef local.</span><span class="sxs-lookup"><span data-stu-id="0746f-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="0746f-119">Você não pode criar uma assinatura de tempo de execução fora do contexto do escopo atual e use essa assinatura como entrada para cada entrada `FindMethod`.</span><span class="sxs-lookup"><span data-stu-id="0746f-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 `FindMethod` <span data-ttu-id="0746f-120">localiza apenas os métodos que foram definidos diretamente na classe ou interface; ele não localizará os métodos herdados.</span><span class="sxs-lookup"><span data-stu-id="0746f-120">finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0746f-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0746f-121">Requirements</span></span>  
 <span data-ttu-id="0746f-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0746f-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0746f-123">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0746f-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0746f-124">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0746f-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="0746f-125">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="0746f-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0746f-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0746f-126">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="0746f-127">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="0746f-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0746f-128">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="0746f-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
