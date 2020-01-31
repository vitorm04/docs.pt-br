---
title: Interface ICorPublish
ms.date: 03/30/2017
api_name:
- ICorPublish
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish
helpviewer_keywords:
- ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type:
- apiref
ms.openlocfilehash: c4a24d879ebd9e8813ea0ac4597818569f4ae6fa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790722"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="c56ed-102">Interface ICorPublish</span><span class="sxs-lookup"><span data-stu-id="c56ed-102">ICorPublish Interface</span></span>
<span data-ttu-id="c56ed-103">O serve como interface geral para publicar informações sobre processos e informações sobre os domínios de aplicativo nesses processos.</span><span class="sxs-lookup"><span data-stu-id="c56ed-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c56ed-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c56ed-104">Methods</span></span>  
  
|<span data-ttu-id="c56ed-105">Método</span><span class="sxs-lookup"><span data-stu-id="c56ed-105">Method</span></span>|<span data-ttu-id="c56ed-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c56ed-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c56ed-107">Método EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="c56ed-107">EnumProcesses Method</span></span>](icorpublish-enumprocesses-method.md)|<span data-ttu-id="c56ed-108">Obtém uma instância de [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) que contém os processos gerenciados em execução neste computador.</span><span class="sxs-lookup"><span data-stu-id="c56ed-108">Gets an [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="c56ed-109">Método GetProcess</span><span class="sxs-lookup"><span data-stu-id="c56ed-109">GetProcess Method</span></span>](icorpublish-getprocess-method.md)|<span data-ttu-id="c56ed-110">Obtém uma instância de [ICorPublishProcess](icorpublishprocess-interface.md) que representa o processo com o identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="c56ed-110">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c56ed-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="c56ed-111">Requirements</span></span>  
 <span data-ttu-id="c56ed-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c56ed-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c56ed-113">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="c56ed-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c56ed-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c56ed-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c56ed-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c56ed-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c56ed-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="c56ed-116">See also</span></span>

- [<span data-ttu-id="c56ed-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c56ed-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c56ed-118">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="c56ed-118">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
