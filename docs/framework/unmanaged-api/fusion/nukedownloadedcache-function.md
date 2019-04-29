---
title: Função NukeDownloadedCache
ms.date: 03/30/2017
api_name:
- NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- NukeDownloadedCache
helpviewer_keywords:
- NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e549e13c0d51e4aa708a674a2224168ab66f8ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774524"
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="3590c-102">Função NukeDownloadedCache</span><span class="sxs-lookup"><span data-stu-id="3590c-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="3590c-103">Exclui o cache de download do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="3590c-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3590c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3590c-104">Syntax</span></span>  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3590c-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3590c-105">Return Value</span></span>  
 <span data-ttu-id="3590c-106">Esse método retorna códigos de erro COM padrão, conforme definido em Winerror. H.</span><span class="sxs-lookup"><span data-stu-id="3590c-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3590c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="3590c-107">Remarks</span></span>  
 <span data-ttu-id="3590c-108">O cache de download do CLR é a área em que os assemblies de nome forte que são baixados de uma URL são armazenados para possível reutilização.</span><span class="sxs-lookup"><span data-stu-id="3590c-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3590c-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3590c-109">Requirements</span></span>  
 <span data-ttu-id="3590c-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3590c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3590c-111">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="3590c-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="3590c-112">**Biblioteca:** Fusion e mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="3590c-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="3590c-113">Use Fusion em vez de mscorwks. dll para garantir que você direcione a versão correta do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3590c-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="3590c-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3590c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3590c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3590c-115">See also</span></span>

- [<span data-ttu-id="3590c-116">Função CreateHistoryReader</span><span class="sxs-lookup"><span data-stu-id="3590c-116">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [<span data-ttu-id="3590c-117">Função GetHistoryFileDirectory</span><span class="sxs-lookup"><span data-stu-id="3590c-117">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)
- [<span data-ttu-id="3590c-118">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="3590c-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
