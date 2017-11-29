---
title: "Enumeração ESymbolReadingPolicy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ESymbolReadingPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ESymbolReadingPolicy
helpviewer_keywords: ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ce56486453e88a18ebd9dbb42f30bcfdafcf328e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="7265d-102">Enumeração ESymbolReadingPolicy</span><span class="sxs-lookup"><span data-stu-id="7265d-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="7265d-103">Contém valores que defina a política para ler os arquivos do programa (PDB) de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="7265d-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7265d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7265d-104">Syntax</span></span>  
  
```  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="7265d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="7265d-105">Members</span></span>  
  
|<span data-ttu-id="7265d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="7265d-106">Member</span></span>|<span data-ttu-id="7265d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7265d-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="7265d-108">Especifica que o depurador sempre deve ler arquivos PDB.</span><span class="sxs-lookup"><span data-stu-id="7265d-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="7265d-109">Especifica que o depurador deve ler apenas os arquivos PDB que estão associados a assemblies de confiança total.</span><span class="sxs-lookup"><span data-stu-id="7265d-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="7265d-110">Especifica que o depurador nunca deve ler arquivos PDB.</span><span class="sxs-lookup"><span data-stu-id="7265d-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7265d-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="7265d-111">Remarks</span></span>  
 <span data-ttu-id="7265d-112">O `ESymbolReadingPolicy` enumeração é usada com a [: Setsymbolreadingpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="7265d-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7265d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7265d-113">Requirements</span></span>  
 <span data-ttu-id="7265d-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7265d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7265d-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7265d-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7265d-116">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7265d-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7265d-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7265d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7265d-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7265d-118">See Also</span></span>  
 [<span data-ttu-id="7265d-119">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="7265d-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
