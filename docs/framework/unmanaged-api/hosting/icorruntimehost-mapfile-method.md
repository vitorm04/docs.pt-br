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
ms.openlocfilehash: a8a979e86dbe52577d0b58089015338e4a87750d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193870"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="f8fca-102">Método ICorRuntimeHost::MapFile</span><span class="sxs-lookup"><span data-stu-id="f8fca-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="f8fca-103">Mapeia o arquivo especificado na memória.</span><span class="sxs-lookup"><span data-stu-id="f8fca-103">Maps the specified file into memory.</span></span> <span data-ttu-id="f8fca-104">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="f8fca-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8fca-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f8fca-105">Syntax</span></span>  
  
```  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8fca-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8fca-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="f8fca-107">[in] O identificador do arquivo a ser mapeado.</span><span class="sxs-lookup"><span data-stu-id="f8fca-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="f8fca-108">[out] O endereço de memória inicial no qual iniciar o arquivo de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="f8fca-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8fca-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f8fca-109">Requirements</span></span>  
 <span data-ttu-id="f8fca-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8fca-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8fca-111">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f8fca-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8fca-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f8fca-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8fca-113">**Versão do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="f8fca-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8fca-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8fca-114">See also</span></span>

- [<span data-ttu-id="f8fca-115">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="f8fca-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
