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
ms.openlocfilehash: fb673666543bea3df44005ee3b20d311524f51d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175909"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="154e1-102">Método IMetaDataDispenserEx::GetCORSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="154e1-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="154e1-103">Obtém o diretório que detém o tempo de execução da linguagem comum atual (CLR).</span><span class="sxs-lookup"><span data-stu-id="154e1-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="154e1-104">Este método é suportado apenas para uso por depuradores fora de processo.</span><span class="sxs-lookup"><span data-stu-id="154e1-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="154e1-105">Se for chamado de outro componente, ele voltará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="154e1-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="154e1-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="154e1-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,
    [in]  DWORD       cchBuffer,
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="154e1-107">parâmetros</span><span class="sxs-lookup"><span data-stu-id="154e1-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="154e1-108">[fora] O buffer para receber o nome do diretório.</span><span class="sxs-lookup"><span data-stu-id="154e1-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="154e1-109">[em] O tamanho, em bytes, de `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="154e1-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="154e1-110">[fora] O número de bytes `szBuffer`realmente retornou em .</span><span class="sxs-lookup"><span data-stu-id="154e1-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="154e1-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="154e1-111">Requirements</span></span>  
 <span data-ttu-id="154e1-112">**Plataforma:** Consulte [os requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="154e1-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="154e1-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="154e1-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="154e1-114">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="154e1-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="154e1-115">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="154e1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="154e1-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="154e1-116">See also</span></span>

- [<span data-ttu-id="154e1-117">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="154e1-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="154e1-118">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="154e1-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
