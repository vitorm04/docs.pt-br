---
title: Método ICorRuntimeHost::MapFile
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.MapFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::MapFile
helpviewer_keywords:
- ICorRuntimeHost::MapFile method [.NET Framework hosting]
- MapFile method [.NET Framework hosting]
ms.assetid: 45ae0502-0a31-4342-b7e3-f36e1cf738f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 956de98fca1caec0ac1b94afc7251f9741246f94
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494773"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="a68c0-102">Método ICorRuntimeHost::MapFile</span><span class="sxs-lookup"><span data-stu-id="a68c0-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="a68c0-103">Mapeia o arquivo especificado na memória.</span><span class="sxs-lookup"><span data-stu-id="a68c0-103">Maps the specified file into memory.</span></span> <span data-ttu-id="a68c0-104">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="a68c0-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a68c0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a68c0-105">Syntax</span></span>  
  
```  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a68c0-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a68c0-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="a68c0-107">[in] O identificador do arquivo a ser mapeado.</span><span class="sxs-lookup"><span data-stu-id="a68c0-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="a68c0-108">[out] O endereço de memória inicial no qual iniciar o arquivo de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="a68c0-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a68c0-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a68c0-109">Requirements</span></span>  
 <span data-ttu-id="a68c0-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a68c0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a68c0-111">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a68c0-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a68c0-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a68c0-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a68c0-113">**Versão do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="a68c0-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a68c0-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a68c0-114">See also</span></span>
- [<span data-ttu-id="a68c0-115">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="a68c0-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
