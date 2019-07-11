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
ms.openlocfilehash: b58da58897edbf3ec9492c1f9f1b2f3d7b83e07a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780079"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="63191-102">Método ICorRuntimeHost::MapFile</span><span class="sxs-lookup"><span data-stu-id="63191-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="63191-103">Mapeia o arquivo especificado na memória.</span><span class="sxs-lookup"><span data-stu-id="63191-103">Maps the specified file into memory.</span></span> <span data-ttu-id="63191-104">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="63191-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63191-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="63191-105">Syntax</span></span>  
  
```cpp  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63191-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="63191-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="63191-107">[in] O identificador do arquivo a ser mapeado.</span><span class="sxs-lookup"><span data-stu-id="63191-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="63191-108">[out] O endereço de memória inicial no qual iniciar o arquivo de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="63191-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63191-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="63191-109">Requirements</span></span>  
 <span data-ttu-id="63191-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63191-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63191-111">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="63191-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63191-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="63191-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63191-113">**Versão do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="63191-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63191-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63191-114">See also</span></span>

- [<span data-ttu-id="63191-115">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="63191-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
