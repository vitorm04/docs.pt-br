---
title: Interface ICorDebugRemoteTarget
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemoteTarget
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget
helpviewer_keywords: ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 38357072b3a6e8e8a326a16600b2d7ed56cdcb2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="a5163-102">Interface ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="a5163-102">ICorDebugRemoteTarget Interface</span></span>
<span data-ttu-id="a5163-103">Fornece métodos que permitem aos desenvolvedores depurar aplicativos baseados no Silverlight no ambiente do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="a5163-103">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5163-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a5163-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="a5163-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="a5163-105">Methods</span></span>  
  
|<span data-ttu-id="a5163-106">Método</span><span class="sxs-lookup"><span data-stu-id="a5163-106">Method</span></span>|<span data-ttu-id="a5163-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5163-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a5163-108">Método Icordebugremotetarget::</span><span class="sxs-lookup"><span data-stu-id="a5163-108">ICorDebugRemoteTarget::GetHostName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="a5163-109">Retorna o nome do host ou o endereço IP de um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="a5163-109">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5163-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a5163-110">Remarks</span></span>  
 <span data-ttu-id="a5163-111">Não há suporte para a depuração (ou seja, código gerenciado e nativo) de modo misto no Windows 95, Windows 98 ou Windows ME ou em plataformas x86 não (como IA-64 e AMD64).</span><span class="sxs-lookup"><span data-stu-id="a5163-111">Mixed-mode (that is, managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5163-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a5163-112">Requirements</span></span>  
 <span data-ttu-id="a5163-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5163-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5163-114">**Cabeçalho:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="a5163-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="a5163-115">**Biblioteca:** : CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5163-115">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5163-116">**Versões do .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="a5163-116">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5163-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5163-117">See Also</span></span>  
 [<span data-ttu-id="a5163-118">Interface ICorDebugRemote</span><span class="sxs-lookup"><span data-stu-id="a5163-118">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [<span data-ttu-id="a5163-119">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="a5163-119">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="a5163-120">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="a5163-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
