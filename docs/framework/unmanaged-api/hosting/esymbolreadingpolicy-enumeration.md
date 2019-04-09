---
title: Enumeração ESymbolReadingPolicy
ms.date: 03/30/2017
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ba29952fe4a6edfc6e9e80ec02f82de65ef0064
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208417"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="a3fdf-102">Enumeração ESymbolReadingPolicy</span><span class="sxs-lookup"><span data-stu-id="a3fdf-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="a3fdf-103">Contém valores que definir a política para a leitura de arquivos de banco de dados (PDB) do programa.</span><span class="sxs-lookup"><span data-stu-id="a3fdf-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3fdf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3fdf-104">Syntax</span></span>  
  
```  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="a3fdf-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a3fdf-105">Members</span></span>  
  
|<span data-ttu-id="a3fdf-106">Membro</span><span class="sxs-lookup"><span data-stu-id="a3fdf-106">Member</span></span>|<span data-ttu-id="a3fdf-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3fdf-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="a3fdf-108">Especifica que o depurador sempre deve ler arquivos PDB.</span><span class="sxs-lookup"><span data-stu-id="a3fdf-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="a3fdf-109">Especifica que o depurador deve ler apenas os arquivos PDB que estão associados a assemblies de confiança total.</span><span class="sxs-lookup"><span data-stu-id="a3fdf-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="a3fdf-110">Especifica que o depurador nunca deve ler arquivos PDB.</span><span class="sxs-lookup"><span data-stu-id="a3fdf-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3fdf-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="a3fdf-111">Remarks</span></span>  
 <span data-ttu-id="a3fdf-112">O `ESymbolReadingPolicy` enumeração é usada com o [iclrdebugmanager:: Setsymbolreadingpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="a3fdf-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3fdf-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a3fdf-113">Requirements</span></span>  
 <span data-ttu-id="a3fdf-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3fdf-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3fdf-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a3fdf-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a3fdf-116">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a3fdf-116">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="a3fdf-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="a3fdf-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a3fdf-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3fdf-118">See also</span></span>

- [<span data-ttu-id="a3fdf-119">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="a3fdf-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
