---
title: Método IMetaDataImport::EnumInterfaceImpls
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
ms.openlocfilehash: 910c40413075131765a37e00703ac892e3f39641
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492181"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="ec2a0-102">Método IMetaDataImport::EnumInterfaceImpls</span><span class="sxs-lookup"><span data-stu-id="ec2a0-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="ec2a0-103">Enumera todas as interfaces implementadas pelo especificado `TypeDef` .</span><span class="sxs-lookup"><span data-stu-id="ec2a0-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="ec2a0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec2a0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec2a0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ec2a0-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ec2a0-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="ec2a0-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="ec2a0-107">no O token do TypeDef cujos tokens MethodDef que representam implementações de interface devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="ec2a0-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="ec2a0-108">fora A matriz usada para armazenar os tokens MethodDef.</span><span class="sxs-lookup"><span data-stu-id="ec2a0-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ec2a0-109">no O comprimento máximo da `rImpls` matriz.</span><span class="sxs-lookup"><span data-stu-id="ec2a0-109">[in] The maximum length of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="ec2a0-110">fora O número real de tokens retornados em `rImpls` .</span><span class="sxs-lookup"><span data-stu-id="ec2a0-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec2a0-111">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="ec2a0-111">Return Value</span></span>  
  
|<span data-ttu-id="ec2a0-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ec2a0-112">HRESULT</span></span>|<span data-ttu-id="ec2a0-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec2a0-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ec2a0-114">`EnumInterfaceImpls`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="ec2a0-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ec2a0-115">Não há tokens MethodDef para enumerar.</span><span class="sxs-lookup"><span data-stu-id="ec2a0-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="ec2a0-116">Nesse caso, `pcImpls` é definido como zero.</span><span class="sxs-lookup"><span data-stu-id="ec2a0-116">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="ec2a0-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="ec2a0-117">Remarks</span></span>

<span data-ttu-id="ec2a0-118">A enumeração retorna uma coleção de `mdInterfaceImpl` tokens para cada interface implementada pelo especificado `TypeDef` .</span><span class="sxs-lookup"><span data-stu-id="ec2a0-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="ec2a0-119">Os tokens de interface são retornados na ordem em que as interfaces foram especificadas (por meio `DefineTypeDef` de ou `SetTypeDefProps` ).</span><span class="sxs-lookup"><span data-stu-id="ec2a0-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="ec2a0-120">As propriedades dos `mdInterfaceImpl` tokens retornados podem ser consultadas usando [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span><span class="sxs-lookup"><span data-stu-id="ec2a0-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="ec2a0-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ec2a0-121">Requirements</span></span>  
 <span data-ttu-id="ec2a0-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec2a0-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec2a0-123">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ec2a0-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ec2a0-124">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ec2a0-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ec2a0-125">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec2a0-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec2a0-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="ec2a0-126">See also</span></span>

- [<span data-ttu-id="ec2a0-127">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="ec2a0-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="ec2a0-128">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="ec2a0-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
