---
title: "Método IMetaDataImport::FindField"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3178d3ff3c64de5390e1150445f0c49c560aa32a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="d77db-102">Método IMetaDataImport::FindField</span><span class="sxs-lookup"><span data-stu-id="d77db-102">IMetaDataImport::FindField Method</span></span>
<span data-ttu-id="d77db-103">Obtém um ponteiro para o FieldDef token para o campo que é incluído por especificado <xref:System.Type> e que tem a assinatura de nome e os metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="d77db-103">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d77db-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d77db-104">Syntax</span></span>  
  
```  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d77db-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d77db-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="d77db-106">[in] O token de TypeDef para a classe ou interface que inclui o campo a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="d77db-106">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="d77db-107">Se esse valor for `mdTokenNil`, a pesquisa é feita para uma variável global.</span><span class="sxs-lookup"><span data-stu-id="d77db-107">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="d77db-108">[in] O nome do campo a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="d77db-108">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="d77db-109">[in] Um ponteiro para a assinatura de binários de metadados do campo.</span><span class="sxs-lookup"><span data-stu-id="d77db-109">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="d77db-110">[in] O tamanho em bytes do `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="d77db-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="d77db-111">[out] Um ponteiro para o token FieldDef correspondente.</span><span class="sxs-lookup"><span data-stu-id="d77db-111">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d77db-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="d77db-112">Remarks</span></span>  
 <span data-ttu-id="d77db-113">Especifique o campo usando sua classe ou interface de delimitador (`td`), seu nome (`szName`) e, opcionalmente, sua assinatura (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="d77db-113">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="d77db-114">A assinatura é passado para `FindField` deve foram gerados no escopo atual, porque as assinaturas associadas a um determinado escopo.</span><span class="sxs-lookup"><span data-stu-id="d77db-114">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="d77db-115">Uma assinatura pode inserir um token que identifica o tipo de valor ou classe delimitador.</span><span class="sxs-lookup"><span data-stu-id="d77db-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="d77db-116">(O token é um índice na tabela de TypeDef local).</span><span class="sxs-lookup"><span data-stu-id="d77db-116">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="d77db-117">Você não pode criar uma assinatura de tempo de execução fora do contexto do escopo atual e usar essa assinatura como entrada para `FindField`.</span><span class="sxs-lookup"><span data-stu-id="d77db-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="d77db-118">`FindField`localiza apenas os campos que foram definidos diretamente na classe ou interface. campos herdados não for encontrada.</span><span class="sxs-lookup"><span data-stu-id="d77db-118">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d77db-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d77db-119">Requirements</span></span>  
 <span data-ttu-id="d77db-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d77db-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d77db-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d77db-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d77db-122">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d77db-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d77db-123">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d77db-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d77db-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d77db-124">See Also</span></span>  
 [<span data-ttu-id="d77db-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="d77db-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="d77db-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="d77db-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
