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
ms.openlocfilehash: 9d4ea16a212ac5f0120d63510f07eaee69af739e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431479"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="a8556-102">Método IMetaDataEmit::DefinePinvokeMap</span><span class="sxs-lookup"><span data-stu-id="a8556-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="a8556-103">Define os recursos da assinatura PInvoke do método referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="a8556-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8556-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8556-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePinvokeMap (   
    [in]  mdToken            tk,   
    [in]  DWORD              dwMappingFlags,   
    [in]  LPCWSTR            szImportName,   
    [in]  mdModuleRef        mrImportDLL   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8556-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a8556-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a8556-106">no O token para o método de destino.</span><span class="sxs-lookup"><span data-stu-id="a8556-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="a8556-107">no Sinalizadores usados pelo PInvoke para fazer o mapeamento.</span><span class="sxs-lookup"><span data-stu-id="a8556-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="a8556-108">no O nome do método de exportação de destino em uma DLL não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="a8556-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="a8556-109">no O token para a DLL nativa de destino.</span><span class="sxs-lookup"><span data-stu-id="a8556-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8556-110">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a8556-110">Requirements</span></span>  
 <span data-ttu-id="a8556-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8556-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8556-112">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a8556-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a8556-113">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a8556-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a8556-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8556-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8556-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8556-115">See also</span></span>

- [<span data-ttu-id="a8556-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="a8556-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a8556-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="a8556-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
