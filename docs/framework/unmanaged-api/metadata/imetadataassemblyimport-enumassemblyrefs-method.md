---
title: Método IMetaDataAssemblyImport::EnumAssemblyRefs
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumAssemblyRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type:
- apiref
ms.openlocfilehash: 1b9700455da82fc7f4a39d4c208ac0b18ef79722
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009113"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="d0d23-102">Método IMetaDataAssemblyImport::EnumAssemblyRefs</span><span class="sxs-lookup"><span data-stu-id="d0d23-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="d0d23-103">Enumera as `mdAssemblyRef` instâncias que são definidas no manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="d0d23-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0d23-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0d23-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,
    [out]     mdAssemblyRef   rAssemblyRefs[],
    [in]      ULONG           cMax,
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0d23-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d0d23-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d0d23-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="d0d23-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="d0d23-107">Esse deve ser um valor nulo quando o `EnumAssemblyRefs` método é chamado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="d0d23-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="d0d23-108">fora A enumeração de `mdAssemblyRef` tokens de metadados.</span><span class="sxs-lookup"><span data-stu-id="d0d23-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d0d23-109">no O número máximo de tokens que podem ser colocados na `rAssemblyRefs` matriz.</span><span class="sxs-lookup"><span data-stu-id="d0d23-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d0d23-110">fora O número de tokens realmente colocados no `rAssemblyRefs` .</span><span class="sxs-lookup"><span data-stu-id="d0d23-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0d23-111">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="d0d23-111">Return Value</span></span>  
  
|<span data-ttu-id="d0d23-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d0d23-112">HRESULT</span></span>|<span data-ttu-id="d0d23-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0d23-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d0d23-114">`EnumAssemblyRefs`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="d0d23-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d0d23-115">Não há tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="d0d23-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="d0d23-116">Nesse caso, `pcTokens` é definido como zero.</span><span class="sxs-lookup"><span data-stu-id="d0d23-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d0d23-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d0d23-117">Requirements</span></span>  
 <span data-ttu-id="d0d23-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0d23-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0d23-119">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d0d23-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d0d23-120">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d0d23-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d0d23-121">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0d23-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0d23-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="d0d23-122">See also</span></span>

- [<span data-ttu-id="d0d23-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="d0d23-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
