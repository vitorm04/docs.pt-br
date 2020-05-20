---
title: Enumeração ECustomDumpFlavor
ms.date: 03/30/2017
api_name:
- ECustomDumpFlavor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECustomDumpFlavor
helpviewer_keywords:
- ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type:
- apiref
ms.openlocfilehash: 9b4c1187945b4c243375a3096c3a8a3b22599aef
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616275"
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="8dc1a-102">Enumeração ECustomDumpFlavor</span><span class="sxs-lookup"><span data-stu-id="8dc1a-102">ECustomDumpFlavor Enumeration</span></span>
<span data-ttu-id="8dc1a-103">Contém valores que indicam quais itens incluir em um subconjunto personalizado de um despejo de heap ao relatar erros.</span><span class="sxs-lookup"><span data-stu-id="8dc1a-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dc1a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8dc1a-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="8dc1a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="8dc1a-105">Members</span></span>  
  
|<span data-ttu-id="8dc1a-106">Membro</span><span class="sxs-lookup"><span data-stu-id="8dc1a-106">Member</span></span>|<span data-ttu-id="8dc1a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8dc1a-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="8dc1a-108">Especifica que o despejo de heap personalizado deve iniciar como um minidespejo e incluir dados adicionais especificados por quaisquer instâncias de [CustomDumpItem](customdumpitem-structure.md) passadas para o mesmo método.</span><span class="sxs-lookup"><span data-stu-id="8dc1a-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="8dc1a-109">Especifica que o despejo de heap personalizado deve coletar todos os dados de estado de tempo de execução que não foram alocados dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="8dc1a-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8dc1a-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="8dc1a-110">Remarks</span></span>  
 <span data-ttu-id="8dc1a-111">Um parâmetro do tipo `ECustomDumpFlavor` é passado para o método [ICLRErrorReportingManager:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8dc1a-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dc1a-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8dc1a-112">Requirements</span></span>  
 <span data-ttu-id="8dc1a-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8dc1a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8dc1a-114">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8dc1a-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8dc1a-115">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8dc1a-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8dc1a-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8dc1a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dc1a-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="8dc1a-117">See also</span></span>

- [<span data-ttu-id="8dc1a-118">Enumeração ECustomDumpItemKind</span><span class="sxs-lookup"><span data-stu-id="8dc1a-118">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="8dc1a-119">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="8dc1a-119">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="8dc1a-120">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="8dc1a-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
