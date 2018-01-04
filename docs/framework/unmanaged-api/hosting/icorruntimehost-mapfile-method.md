---
title: "Método ICorRuntimeHost::MapFile"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.MapFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::MapFile
helpviewer_keywords:
- ICorRuntimeHost::MapFile method [.NET Framework hosting]
- MapFile method [.NET Framework hosting]
ms.assetid: 45ae0502-0a31-4342-b7e3-f36e1cf738f3
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b3047a473f36762ec57ae4ea87067e941ac568c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="2bec6-102">Método ICorRuntimeHost::MapFile</span><span class="sxs-lookup"><span data-stu-id="2bec6-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="2bec6-103">Mapeia o arquivo especificado na memória.</span><span class="sxs-lookup"><span data-stu-id="2bec6-103">Maps the specified file into memory.</span></span> <span data-ttu-id="2bec6-104">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="2bec6-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bec6-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2bec6-105">Syntax</span></span>  
  
```  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2bec6-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2bec6-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="2bec6-107">[in] O identificador do arquivo a ser mapeada.</span><span class="sxs-lookup"><span data-stu-id="2bec6-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="2bec6-108">[out] O endereço de memória inicial no qual começar o arquivo de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="2bec6-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bec6-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2bec6-109">Requirements</span></span>  
 <span data-ttu-id="2bec6-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bec6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bec6-111">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2bec6-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2bec6-112">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="2bec6-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2bec6-113">**Versão do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="2bec6-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bec6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2bec6-114">See Also</span></span>  
 [<span data-ttu-id="2bec6-115">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="2bec6-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
