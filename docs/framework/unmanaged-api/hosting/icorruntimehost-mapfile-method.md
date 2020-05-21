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
ms.openlocfilehash: 3b1a0cd9a1dfba6f33a20416f2a10c967f871a06
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762663"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="0e19f-102">Método ICorRuntimeHost::MapFile</span><span class="sxs-lookup"><span data-stu-id="0e19f-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="0e19f-103">Mapeia o arquivo especificado na memória.</span><span class="sxs-lookup"><span data-stu-id="0e19f-103">Maps the specified file into memory.</span></span> <span data-ttu-id="0e19f-104">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="0e19f-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e19f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0e19f-105">Syntax</span></span>  
  
```cpp  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e19f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0e19f-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="0e19f-107">no O identificador do arquivo a ser mapeado.</span><span class="sxs-lookup"><span data-stu-id="0e19f-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="0e19f-108">fora O endereço de memória inicial no qual começar a mapear o arquivo.</span><span class="sxs-lookup"><span data-stu-id="0e19f-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e19f-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0e19f-109">Requirements</span></span>  
 <span data-ttu-id="0e19f-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e19f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e19f-111">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0e19f-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e19f-112">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0e19f-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e19f-113">**Versão do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="0e19f-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e19f-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="0e19f-114">See also</span></span>

- [<span data-ttu-id="0e19f-115">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="0e19f-115">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
