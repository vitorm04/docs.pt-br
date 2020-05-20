---
title: Interface ICorPublishProcess
ms.date: 03/30/2017
api_name:
- ICorPublishProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess
helpviewer_keywords:
- ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type:
- apiref
ms.openlocfilehash: 8d958e949612b502ab218f5c6b75779174d34e19
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421079"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="ca677-102">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="ca677-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="ca677-103">Fornece métodos que acessam informações a serem exibidas sobre um processo.</span><span class="sxs-lookup"><span data-stu-id="ca677-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ca677-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ca677-104">Methods</span></span>  
  
|<span data-ttu-id="ca677-105">Método</span><span class="sxs-lookup"><span data-stu-id="ca677-105">Method</span></span>|<span data-ttu-id="ca677-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca677-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ca677-107">Método EnumAppDomains</span><span class="sxs-lookup"><span data-stu-id="ca677-107">EnumAppDomains Method</span></span>](icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="ca677-108">Obtém uma instância de [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) que contém os domínios de aplicativo no processo referenciado por isso `ICorPublishProcess` .</span><span class="sxs-lookup"><span data-stu-id="ca677-108">Gets an [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="ca677-109">Método GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="ca677-109">GetDisplayName Method</span></span>](icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="ca677-110">Obtém o caminho completo do executável para o processo referenciado por isso `ICorPublishProcess` .</span><span class="sxs-lookup"><span data-stu-id="ca677-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="ca677-111">Método GetProcessID</span><span class="sxs-lookup"><span data-stu-id="ca677-111">GetProcessID Method</span></span>](icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="ca677-112">Obtém o identificador do sistema operacional para o processo referenciado por isso `ICorPublishProcess` .</span><span class="sxs-lookup"><span data-stu-id="ca677-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="ca677-113">Método IsManaged</span><span class="sxs-lookup"><span data-stu-id="ca677-113">IsManaged Method</span></span>](icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="ca677-114">Obtém um valor que indica se o processo referenciado por isso `ICorPublishProcess` é conhecido por estar executando código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ca677-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ca677-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ca677-115">Requirements</span></span>  
 <span data-ttu-id="ca677-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca677-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca677-117">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="ca677-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ca677-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca677-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca677-119">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca677-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca677-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="ca677-120">See also</span></span>

- [<span data-ttu-id="ca677-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ca677-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ca677-122">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="ca677-122">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
