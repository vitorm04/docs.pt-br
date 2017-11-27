---
title: "Método IMetaDataDispenserEx::GetCORSystemDirectory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.GetCORSystemDirectory
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::GetCORSystemDirectory
helpviewer_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory method [.NET Framework metadata]
- GetCORSystemDirectory method [.NET Framework metadata]
ms.assetid: d9e0f3b6-e106-4820-bada-5bfba34ce360
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a876d6ffb8331ee52789d5c146db7615d352dc1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="7f7d3-102">Método IMetaDataDispenserEx::GetCORSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="7f7d3-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="7f7d3-103">Obtém o diretório que contém o atual common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="7f7d3-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="7f7d3-104">Esse método tem suporte apenas para uso por depuradores fora do processo.</span><span class="sxs-lookup"><span data-stu-id="7f7d3-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="7f7d3-105">Se a chamada de outro componente, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="7f7d3-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f7d3-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f7d3-106">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,   
    [in]  DWORD       cchBuffer,   
    [out] DWORD*      pchBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f7d3-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7f7d3-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="7f7d3-108">[out] O buffer para receber o nome do diretório.</span><span class="sxs-lookup"><span data-stu-id="7f7d3-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="7f7d3-109">[in] O tamanho, em bytes, de `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="7f7d3-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="7f7d3-110">[out] O número de bytes realmente retornados em `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="7f7d3-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f7d3-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7f7d3-111">Requirements</span></span>  
 <span data-ttu-id="7f7d3-112">**Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f7d3-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f7d3-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7f7d3-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f7d3-114">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="7f7d3-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7f7d3-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f7d3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f7d3-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f7d3-116">See Also</span></span>  
 [<span data-ttu-id="7f7d3-117">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="7f7d3-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="7f7d3-118">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="7f7d3-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
