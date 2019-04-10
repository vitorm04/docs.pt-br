---
title: Método ICLRStrongName::StrongNameHashSize
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameHashSize
helpviewer_keywords:
- ICLRStrongName::StrongNameHashSize method [.NET Framework hosting]
- StrongNameHashSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 4a05ee56-08e4-4f3a-86a9-9b52083d5c0f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91b84a980e8a670b8e8b2970cfc96ddd6f4c33b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218479"
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="54bb7-102">Método ICLRStrongName::StrongNameHashSize</span><span class="sxs-lookup"><span data-stu-id="54bb7-102">ICLRStrongName::StrongNameHashSize Method</span></span>
<span data-ttu-id="54bb7-103">Obtém o tamanho do buffer necessário para um hash, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="54bb7-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54bb7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="54bb7-104">Syntax</span></span>  
  
```  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54bb7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="54bb7-105">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="54bb7-106">[in] O algoritmo de hash usado para calcular o tamanho do buffer.</span><span class="sxs-lookup"><span data-stu-id="54bb7-106">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="54bb7-107">[out] O tamanho do buffer retornado, em bytes.</span><span class="sxs-lookup"><span data-stu-id="54bb7-107">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54bb7-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="54bb7-108">Return Value</span></span>  
 `S_OK` <span data-ttu-id="54bb7-109">Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="54bb7-109">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54bb7-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="54bb7-110">Requirements</span></span>  
 <span data-ttu-id="54bb7-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54bb7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54bb7-112">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="54bb7-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="54bb7-113">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="54bb7-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="54bb7-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="54bb7-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="54bb7-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54bb7-115">See also</span></span>

- [<span data-ttu-id="54bb7-116">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="54bb7-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
