---
title: Método IMetaDataAssemblyImport::EnumFiles
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumFiles
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type:
- apiref
ms.openlocfilehash: ed8bafd67b5d55a5116111b7721fbdc31c52aca6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009087"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="cba39-102">Método IMetaDataAssemblyImport::EnumFiles</span><span class="sxs-lookup"><span data-stu-id="cba39-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="cba39-103">Enumera os arquivos referenciados no manifesto do assembly atual.</span><span class="sxs-lookup"><span data-stu-id="cba39-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cba39-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cba39-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,
    [out] mdFile          rFiles[],
    [in]  ULONG           cMax,
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cba39-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cba39-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="cba39-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="cba39-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="cba39-107">Deve ser um valor nulo para a primeira chamada deste método.</span><span class="sxs-lookup"><span data-stu-id="cba39-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="cba39-108">fora A matriz usada para armazenar os `mdFile` tokens de metadados.</span><span class="sxs-lookup"><span data-stu-id="cba39-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="cba39-109">no O número máximo de `mdFile` tokens que podem ser colocados `rFiles` .</span><span class="sxs-lookup"><span data-stu-id="cba39-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="cba39-110">fora O número de `mdFile` tokens realmente colocados no `rFiles` .</span><span class="sxs-lookup"><span data-stu-id="cba39-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cba39-111">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="cba39-111">Return Value</span></span>  
  
|<span data-ttu-id="cba39-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cba39-112">HRESULT</span></span>|<span data-ttu-id="cba39-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="cba39-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="cba39-114">`EnumFiles`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="cba39-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="cba39-115">Não há tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="cba39-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="cba39-116">Nesse caso, `pcTokens` é definido como zero.</span><span class="sxs-lookup"><span data-stu-id="cba39-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cba39-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cba39-117">Requirements</span></span>  
 <span data-ttu-id="cba39-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cba39-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cba39-119">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cba39-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cba39-120">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cba39-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cba39-121">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cba39-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cba39-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="cba39-122">See also</span></span>

- [<span data-ttu-id="cba39-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="cba39-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
