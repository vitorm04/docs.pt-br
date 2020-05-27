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
ms.openlocfilehash: 447ec44ed3efc4eec84d1e4acd6f2ec1a730bf74
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008021"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="49284-102">Método IMetaDataEmit::DefinePinvokeMap</span><span class="sxs-lookup"><span data-stu-id="49284-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="49284-103">Define os recursos da assinatura PInvoke do método referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="49284-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49284-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="49284-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePinvokeMap (
    [in]  mdToken            tk,
    [in]  DWORD              dwMappingFlags,
    [in]  LPCWSTR            szImportName,
    [in]  mdModuleRef        mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49284-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="49284-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="49284-106">no O token para o método de destino.</span><span class="sxs-lookup"><span data-stu-id="49284-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="49284-107">no Sinalizadores usados pelo PInvoke para fazer o mapeamento.</span><span class="sxs-lookup"><span data-stu-id="49284-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="49284-108">no O nome do método de exportação de destino em uma DLL não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="49284-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="49284-109">no O token para a DLL nativa de destino.</span><span class="sxs-lookup"><span data-stu-id="49284-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49284-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="49284-110">Requirements</span></span>  
 <span data-ttu-id="49284-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49284-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49284-112">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="49284-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="49284-113">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="49284-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49284-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49284-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49284-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="49284-115">See also</span></span>

- [<span data-ttu-id="49284-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="49284-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="49284-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="49284-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
