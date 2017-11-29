---
title: "Método ICLRStrongName::StrongNameHashSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameHashSize
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameHashSize
helpviewer_keywords:
- ICLRStrongName::StrongNameHashSize method [.NET Framework hosting]
- StrongNameHashSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 4a05ee56-08e4-4f3a-86a9-9b52083d5c0f
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3edcc3f6a80476e1c665d0606c05fb53e801227a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="41f64-102">Método ICLRStrongName::StrongNameHashSize</span><span class="sxs-lookup"><span data-stu-id="41f64-102">ICLRStrongName::StrongNameHashSize Method</span></span>
<span data-ttu-id="41f64-103">Obtém o tamanho do buffer necessário para um hash, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="41f64-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41f64-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41f64-104">Syntax</span></span>  
  
```  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41f64-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41f64-105">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="41f64-106">[in] O algoritmo de hash usado para calcular o tamanho do buffer.</span><span class="sxs-lookup"><span data-stu-id="41f64-106">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="41f64-107">[out] O tamanho do buffer retornado, em bytes.</span><span class="sxs-lookup"><span data-stu-id="41f64-107">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41f64-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="41f64-108">Return Value</span></span>  
 <span data-ttu-id="41f64-109">`S_OK`Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="41f64-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41f64-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="41f64-110">Requirements</span></span>  
 <span data-ttu-id="41f64-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41f64-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41f64-112">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="41f64-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="41f64-113">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="41f64-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41f64-114">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41f64-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41f64-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41f64-115">See Also</span></span>  
 [<span data-ttu-id="41f64-116">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="41f64-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
