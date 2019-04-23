---
title: Método IMetaDataDispenserEx::GetCORSystemDirectory
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3dbfca942d61cd5667293d11f358f06bd000fa2e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117995"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="23fab-102">Método IMetaDataDispenserEx::GetCORSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="23fab-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="23fab-103">Obtém o diretório que mantém o atual common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="23fab-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="23fab-104">Esse método tem suporte apenas para uso por depuradores out-of-process.</span><span class="sxs-lookup"><span data-stu-id="23fab-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="23fab-105">Se chamado de outro componente, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="23fab-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23fab-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23fab-106">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,   
    [in]  DWORD       cchBuffer,   
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23fab-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="23fab-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="23fab-108">[out] O buffer para receber o nome do diretório.</span><span class="sxs-lookup"><span data-stu-id="23fab-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="23fab-109">[in] O tamanho, em bytes, do `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="23fab-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="23fab-110">[out] O número de bytes realmente retornados em `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="23fab-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23fab-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="23fab-111">Requirements</span></span>  
 <span data-ttu-id="23fab-112">**Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23fab-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23fab-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="23fab-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="23fab-114">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="23fab-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="23fab-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23fab-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23fab-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23fab-116">See also</span></span>

- [<span data-ttu-id="23fab-117">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="23fab-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="23fab-118">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="23fab-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
