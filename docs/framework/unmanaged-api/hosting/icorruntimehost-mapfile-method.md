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
ms.openlocfilehash: bcf1b49f0576f5dbd73c001f8edff7a9ab29af22
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139511"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="eb91f-102">Método ICorRuntimeHost::MapFile</span><span class="sxs-lookup"><span data-stu-id="eb91f-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="eb91f-103">Mapeia o arquivo especificado na memória.</span><span class="sxs-lookup"><span data-stu-id="eb91f-103">Maps the specified file into memory.</span></span> <span data-ttu-id="eb91f-104">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="eb91f-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb91f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb91f-105">Syntax</span></span>  
  
```cpp  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb91f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eb91f-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="eb91f-107">no O identificador do arquivo a ser mapeado.</span><span class="sxs-lookup"><span data-stu-id="eb91f-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="eb91f-108">fora O endereço de memória inicial no qual começar a mapear o arquivo.</span><span class="sxs-lookup"><span data-stu-id="eb91f-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb91f-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eb91f-109">Requirements</span></span>  
 <span data-ttu-id="eb91f-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb91f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb91f-111">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="eb91f-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eb91f-112">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="eb91f-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eb91f-113">**Versão do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="eb91f-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb91f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb91f-114">See also</span></span>

- [<span data-ttu-id="eb91f-115">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="eb91f-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
