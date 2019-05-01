---
title: Método IMetaDataEmit::SetPinvokeMap
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b838a83a160707e546b05ef334eb17d0c6e6cc27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049988"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="32544-102">Método IMetaDataEmit::SetPinvokeMap</span><span class="sxs-lookup"><span data-stu-id="32544-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="32544-103">Define ou altera os recursos de assinatura de PInvoke de um método, conforme definido por uma chamada anterior a [imetadataemit:: Definepinvokemap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span><span class="sxs-lookup"><span data-stu-id="32544-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32544-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32544-104">Syntax</span></span>  
  
```  
HRESULT SetPinvokeMap (   
    [in]  mdToken      tk,   
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,   
    [in]  mdModuleRef  mrImportDLL   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32544-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="32544-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="32544-106">[in] O `mdToken` para mapeamento de quais informações se aplicam.</span><span class="sxs-lookup"><span data-stu-id="32544-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="32544-107">[in] Sinalizadores usados por PInvoke para fazer o mapeamento.</span><span class="sxs-lookup"><span data-stu-id="32544-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="32544-108">Esse é um bitmask de `CorPinvokeMap` valores.</span><span class="sxs-lookup"><span data-stu-id="32544-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="32544-109">[in] O nome do destino de exportação na DLL nativa.</span><span class="sxs-lookup"><span data-stu-id="32544-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="32544-110">[in] O `mdModuleRef` token para o destino não gerenciado a DLL.</span><span class="sxs-lookup"><span data-stu-id="32544-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32544-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="32544-111">Requirements</span></span>  
 <span data-ttu-id="32544-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32544-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32544-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="32544-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="32544-114">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="32544-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="32544-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32544-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32544-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32544-116">See also</span></span>

- [<span data-ttu-id="32544-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="32544-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="32544-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="32544-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
