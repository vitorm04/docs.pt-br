---
title: Método IMetaDataEmit::DefinePinvokeMap
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePinvokeMap
helpviewer_keywords:
- DefinePinvokeMap method [.NET Framework metadata]
- IMetaDataEmit::DefinePinvokeMap method [.NET Framework metadata]
ms.assetid: 03abf921-5154-4070-88fa-10b7092901fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15fd75ae807ee5cd7f94f6e650639c3be0628429
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043895"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="781af-102">Método IMetaDataEmit::DefinePinvokeMap</span><span class="sxs-lookup"><span data-stu-id="781af-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="781af-103">Define os recursos da assinatura do método referenciada pelo token especificado PInvoke.</span><span class="sxs-lookup"><span data-stu-id="781af-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="781af-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="781af-104">Syntax</span></span>  
  
```  
HRESULT DefinePinvokeMap (   
    [in]  mdToken            tk,   
    [in]  DWORD              dwMappingFlags,   
    [in]  LPCWSTR            szImportName,   
    [in]  mdModuleRef        mrImportDLL   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="781af-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="781af-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="781af-106">[in] O token para o método de destino.</span><span class="sxs-lookup"><span data-stu-id="781af-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="781af-107">[in] Sinalizadores usados por PInvoke para fazer o mapeamento.</span><span class="sxs-lookup"><span data-stu-id="781af-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="781af-108">[in] O nome do destino de exportação de método em uma DLL não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="781af-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="781af-109">[in] O token para o destino de DLL nativa.</span><span class="sxs-lookup"><span data-stu-id="781af-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="781af-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="781af-110">Requirements</span></span>  
 <span data-ttu-id="781af-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="781af-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="781af-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="781af-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="781af-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="781af-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="781af-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="781af-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="781af-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="781af-115">See also</span></span>

- [<span data-ttu-id="781af-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="781af-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="781af-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="781af-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
