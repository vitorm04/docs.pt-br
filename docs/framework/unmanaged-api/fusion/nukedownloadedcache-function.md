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
ms.openlocfilehash: 29f492173a7fd22ab497d6e0096798e164fccf26
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796310"
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="a061c-102">Função NukeDownloadedCache</span><span class="sxs-lookup"><span data-stu-id="a061c-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="a061c-103">Exclui o cache de download do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="a061c-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a061c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a061c-104">Syntax</span></span>  
  
```cpp  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a061c-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a061c-105">Return Value</span></span>  
 <span data-ttu-id="a061c-106">Esse método retorna códigos de erro COM padrão, conforme definido em WinError. h.</span><span class="sxs-lookup"><span data-stu-id="a061c-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a061c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a061c-107">Remarks</span></span>  
 <span data-ttu-id="a061c-108">O cache de download do CLR é a área em que os assemblies de nome forte baixados de uma URL são armazenados para possível reutilização.</span><span class="sxs-lookup"><span data-stu-id="a061c-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a061c-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a061c-109">Requirements</span></span>  
 <span data-ttu-id="a061c-110">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a061c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a061c-111">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="a061c-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a061c-112">**Biblioteca** Fusion. dll e mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="a061c-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="a061c-113">Use Fusion. dll em vez de mscorwks. dll para garantir que você direcione a versão correta do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a061c-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="a061c-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a061c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a061c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a061c-115">See also</span></span>

- [<span data-ttu-id="a061c-116">Função CreateHistoryReader</span><span class="sxs-lookup"><span data-stu-id="a061c-116">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="a061c-117">Função GetHistoryFileDirectory</span><span class="sxs-lookup"><span data-stu-id="a061c-117">GetHistoryFileDirectory Function</span></span>](gethistoryfiledirectory-function.md)
- [<span data-ttu-id="a061c-118">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="a061c-118">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
