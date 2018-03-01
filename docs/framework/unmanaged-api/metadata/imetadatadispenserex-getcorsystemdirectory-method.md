---
title: "Método IMetaDataDispenserEx::GetCORSystemDirectory"
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
- IMetaDataDispenserEx.GetCORSystemDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory
helpviewer_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory method [.NET Framework metadata]
- GetCORSystemDirectory method [.NET Framework metadata]
ms.assetid: d9e0f3b6-e106-4820-bada-5bfba34ce360
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e93f544e504949b496881369c15905ef43a0d2f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="d27ee-102">Método IMetaDataDispenserEx::GetCORSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="d27ee-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="d27ee-103">Obtém o diretório que contém o atual common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="d27ee-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="d27ee-104">Esse método tem suporte apenas para uso por depuradores fora do processo.</span><span class="sxs-lookup"><span data-stu-id="d27ee-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="d27ee-105">Se a chamada de outro componente, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="d27ee-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d27ee-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d27ee-106">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,   
    [in]  DWORD       cchBuffer,   
    [out] DWORD*      pchBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d27ee-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d27ee-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="d27ee-108">[out] O buffer para receber o nome do diretório.</span><span class="sxs-lookup"><span data-stu-id="d27ee-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="d27ee-109">[in] O tamanho, em bytes, de `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="d27ee-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="d27ee-110">[out] O número de bytes realmente retornados em `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="d27ee-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d27ee-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d27ee-111">Requirements</span></span>  
 <span data-ttu-id="d27ee-112">**Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d27ee-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d27ee-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d27ee-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d27ee-114">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d27ee-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d27ee-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d27ee-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d27ee-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d27ee-116">See Also</span></span>  
 [<span data-ttu-id="d27ee-117">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="d27ee-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="d27ee-118">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="d27ee-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
