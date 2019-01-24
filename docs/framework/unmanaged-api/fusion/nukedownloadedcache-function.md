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
ms.openlocfilehash: 80891da7d61aa5114d5cc4d8aff4c7ce82020237
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720087"
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="669e4-102">Função NukeDownloadedCache</span><span class="sxs-lookup"><span data-stu-id="669e4-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="669e4-103">Exclui o cache de download do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="669e4-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="669e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="669e4-104">Syntax</span></span>  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="669e4-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="669e4-105">Return Value</span></span>  
 <span data-ttu-id="669e4-106">Esse método retorna códigos de erro COM padrão, conforme definido em Winerror. H.</span><span class="sxs-lookup"><span data-stu-id="669e4-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="669e4-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="669e4-107">Remarks</span></span>  
 <span data-ttu-id="669e4-108">O cache de download do CLR é a área em que os assemblies de nome forte que são baixados de uma URL são armazenados para possível reutilização.</span><span class="sxs-lookup"><span data-stu-id="669e4-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="669e4-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="669e4-109">Requirements</span></span>  
 <span data-ttu-id="669e4-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="669e4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="669e4-111">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="669e4-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="669e4-112">**Biblioteca:** Fusion e mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="669e4-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="669e4-113">Use Fusion em vez de mscorwks. dll para garantir que você direcione a versão correta do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="669e4-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="669e4-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="669e4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="669e4-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669e4-115">See also</span></span>
- [<span data-ttu-id="669e4-116">Função CreateHistoryReader</span><span class="sxs-lookup"><span data-stu-id="669e4-116">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [<span data-ttu-id="669e4-117">Função GetHistoryFileDirectory</span><span class="sxs-lookup"><span data-stu-id="669e4-117">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)
- [<span data-ttu-id="669e4-118">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="669e4-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
