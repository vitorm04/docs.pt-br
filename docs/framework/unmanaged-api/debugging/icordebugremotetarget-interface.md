---
title: Interface ICorDebugRemoteTarget
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugRemoteTarget
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget
helpviewer_keywords:
- ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fcfdab2857745dee7c40823ad25592de5dc833ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="1a92c-102">Interface ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="1a92c-102">ICorDebugRemoteTarget Interface</span></span>
<span data-ttu-id="1a92c-103">Fornece métodos que permitem aos desenvolvedores depurar aplicativos baseados no Silverlight no ambiente do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="1a92c-103">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a92c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1a92c-104">Syntax</span></span>  
  
```  
interface ICorDebugRemoteTarget  : IUnknown  
{  
    HRESULT GetHostName (  
        [in]  ULONG32                    cchHostName,  
        [out] ULONG32*                   pcchHostName,  
        [out, size_is(cchHostName),  
              length_is(*pcchHostName)]  
                  WCHAR szHostName[]  
        );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1a92c-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="1a92c-105">Methods</span></span>  
  
|<span data-ttu-id="1a92c-106">Método</span><span class="sxs-lookup"><span data-stu-id="1a92c-106">Method</span></span>|<span data-ttu-id="1a92c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1a92c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1a92c-108">Método ICorDebugRemoteTarget::GetHostName</span><span class="sxs-lookup"><span data-stu-id="1a92c-108">ICorDebugRemoteTarget::GetHostName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="1a92c-109">Retorna o nome do host ou o endereço IP de um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="1a92c-109">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a92c-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="1a92c-110">Remarks</span></span>  
 <span data-ttu-id="1a92c-111">Não há suporte para a depuração (ou seja, código gerenciado e nativo) de modo misto no Windows 95, Windows 98 ou Windows ME ou em plataformas x86 não (como IA-64 e AMD64).</span><span class="sxs-lookup"><span data-stu-id="1a92c-111">Mixed-mode (that is, managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a92c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1a92c-112">Requirements</span></span>  
 <span data-ttu-id="1a92c-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a92c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a92c-114">**Cabeçalho:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="1a92c-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="1a92c-115">**Biblioteca:** : CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a92c-115">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a92c-116">**Versões do .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="1a92c-116">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a92c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a92c-117">See Also</span></span>  
 [<span data-ttu-id="1a92c-118">Interface ICorDebugRemote</span><span class="sxs-lookup"><span data-stu-id="1a92c-118">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [<span data-ttu-id="1a92c-119">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="1a92c-119">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="1a92c-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1a92c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
