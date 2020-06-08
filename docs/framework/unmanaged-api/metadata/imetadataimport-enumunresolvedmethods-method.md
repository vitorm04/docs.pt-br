---
title: Método IMetaDataImport::EnumUnresolvedMethods
ms.date: 03/30/2017
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
ms.openlocfilehash: c991c0af845bc6825db6b3bf258fe0809d5db804
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503686"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="7e5e9-102">Método IMetaDataImport::EnumUnresolvedMethods</span><span class="sxs-lookup"><span data-stu-id="7e5e9-102">IMetaDataImport::EnumUnresolvedMethods Method</span></span>
<span data-ttu-id="7e5e9-103">Enumera os tokens MemberDef que representam os métodos não resolvidos no escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="7e5e9-103">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e5e9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e5e9-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e5e9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7e5e9-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="7e5e9-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="7e5e9-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="7e5e9-107">Isso deve ser nulo para a primeira chamada deste método.</span><span class="sxs-lookup"><span data-stu-id="7e5e9-107">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="7e5e9-108">fora A matriz usada para armazenar os tokens MemberDef.</span><span class="sxs-lookup"><span data-stu-id="7e5e9-108">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7e5e9-109">no O tamanho máximo da `rMethods` matriz.</span><span class="sxs-lookup"><span data-stu-id="7e5e9-109">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="7e5e9-110">fora O número de tokens MemberDef retornados em `rMethods` .</span><span class="sxs-lookup"><span data-stu-id="7e5e9-110">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e5e9-111">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="7e5e9-111">Return Value</span></span>  
  
|<span data-ttu-id="7e5e9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7e5e9-112">HRESULT</span></span>|<span data-ttu-id="7e5e9-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e5e9-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7e5e9-114">`EnumUnresolvedMethods`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="7e5e9-114">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="7e5e9-115">Não há tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="7e5e9-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="7e5e9-116">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="7e5e9-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e5e9-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="7e5e9-117">Remarks</span></span>  
 <span data-ttu-id="7e5e9-118">Um método não resolvido é aquele que foi declarado mas não implementado.</span><span class="sxs-lookup"><span data-stu-id="7e5e9-118">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="7e5e9-119">Um método será incluído na enumeração se o método estiver marcado `miForwardRef` e `mdPinvokeImpl` ou `miRuntime` estiver definido como zero.</span><span class="sxs-lookup"><span data-stu-id="7e5e9-119">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="7e5e9-120">Em outras palavras, um método não resolvido é um método de classe marcado `miForwardRef` , mas que não é implementado em código não gerenciado (alcançado via PInvoke) nem implementado internamente pelo próprio tempo de execução</span><span class="sxs-lookup"><span data-stu-id="7e5e9-120">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="7e5e9-121">A enumeração exclui todos os métodos que são definidos no escopo do módulo (Globals) ou em interfaces ou classes abstratas.</span><span class="sxs-lookup"><span data-stu-id="7e5e9-121">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e5e9-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7e5e9-122">Requirements</span></span>  
 <span data-ttu-id="7e5e9-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e5e9-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e5e9-124">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7e5e9-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7e5e9-125">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7e5e9-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7e5e9-126">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e5e9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e5e9-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="7e5e9-127">See also</span></span>

- [<span data-ttu-id="7e5e9-128">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="7e5e9-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="7e5e9-129">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="7e5e9-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
