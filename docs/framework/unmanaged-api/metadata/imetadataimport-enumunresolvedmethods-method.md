---
title: "Método IMetaDataImport::EnumUnresolvedMethods"
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
- IMetaDataImport.EnumUnresolvedMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d4e77453fc11b77b602d4a89f0d90540c06b0a08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="3c14b-102">Método IMetaDataImport::EnumUnresolvedMethods</span><span class="sxs-lookup"><span data-stu-id="3c14b-102">IMetaDataImport::EnumUnresolvedMethods Method</span></span>
<span data-ttu-id="3c14b-103">Enumera os tokens de MemberDef que representa os métodos não resolvidos no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="3c14b-103">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c14b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3c14b-104">Syntax</span></span>  
  
```  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c14b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3c14b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3c14b-106">[out no] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="3c14b-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="3c14b-107">Isso deve ser NULL para a primeira chamada do método.</span><span class="sxs-lookup"><span data-stu-id="3c14b-107">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="3c14b-108">[out] A matriz usada para armazenar os tokens de MemberDef.</span><span class="sxs-lookup"><span data-stu-id="3c14b-108">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3c14b-109">[in] O tamanho máximo da `rMethods` matriz.</span><span class="sxs-lookup"><span data-stu-id="3c14b-109">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="3c14b-110">[out] O número de tokens MemberDef retornado em `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="3c14b-110">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c14b-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3c14b-111">Return Value</span></span>  
  
|<span data-ttu-id="3c14b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3c14b-112">HRESULT</span></span>|<span data-ttu-id="3c14b-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="3c14b-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3c14b-114">`EnumUnresolvedMethods`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="3c14b-114">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3c14b-115">Não há nenhum tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="3c14b-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="3c14b-116">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="3c14b-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c14b-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="3c14b-117">Remarks</span></span>  
 <span data-ttu-id="3c14b-118">Um método não resolvido é aquele que foi declarada mas não foi implementado.</span><span class="sxs-lookup"><span data-stu-id="3c14b-118">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="3c14b-119">Um método é incluído na enumeração, se o método está marcado como `miForwardRef` e `mdPinvokeImpl` ou `miRuntime` é definido como zero.</span><span class="sxs-lookup"><span data-stu-id="3c14b-119">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="3c14b-120">Em outras palavras, um método não resolvido é um método de classe que está marcado como `miForwardRef` mas que não está implementado no código não gerenciado (alcançado via PInvoke) nem implementado internamente pelo próprio tempo de execução</span><span class="sxs-lookup"><span data-stu-id="3c14b-120">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="3c14b-121">A enumeração exclui todos os métodos que são definidos no escopo do módulo (globais) ou em interfaces ou classes abstratas.</span><span class="sxs-lookup"><span data-stu-id="3c14b-121">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c14b-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3c14b-122">Requirements</span></span>  
 <span data-ttu-id="3c14b-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c14b-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c14b-124">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3c14b-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3c14b-125">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="3c14b-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3c14b-126">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c14b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c14b-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c14b-127">See Also</span></span>  
 [<span data-ttu-id="3c14b-128">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="3c14b-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="3c14b-129">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="3c14b-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
