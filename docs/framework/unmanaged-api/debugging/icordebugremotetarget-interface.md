---
title: Interface ICorDebugRemoteTarget
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae31506d4ba34bf262f49bc2321c6cfcd30f1b60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782688"
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="5eee9-102">Interface ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="5eee9-102">ICorDebugRemoteTarget Interface</span></span>
<span data-ttu-id="5eee9-103">Fornece métodos que permitem que desenvolvedores depurem aplicativos baseados no Silverlight no ambiente do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="5eee9-103">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5eee9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5eee9-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="5eee9-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="5eee9-105">Methods</span></span>  
  
|<span data-ttu-id="5eee9-106">Método</span><span class="sxs-lookup"><span data-stu-id="5eee9-106">Method</span></span>|<span data-ttu-id="5eee9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5eee9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5eee9-108">Método ICorDebugRemoteTarget::GetHostName</span><span class="sxs-lookup"><span data-stu-id="5eee9-108">ICorDebugRemoteTarget::GetHostName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="5eee9-109">Retorna o nome do host ou o endereço IP de um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="5eee9-109">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5eee9-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="5eee9-110">Remarks</span></span>  
 <span data-ttu-id="5eee9-111">Não há suporte para a depuração mista (ou seja, código gerenciado e nativo) no Windows 95, Windows 98 ou Windows ME ou em plataformas não x86 (como IA-64 e AMD64).</span><span class="sxs-lookup"><span data-stu-id="5eee9-111">Mixed-mode (that is, managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5eee9-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5eee9-112">Requirements</span></span>  
 <span data-ttu-id="5eee9-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5eee9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5eee9-114">**Cabeçalho:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="5eee9-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="5eee9-115">**Biblioteca:** : CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5eee9-115">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="5eee9-116">**Versões do .NET framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="5eee9-116">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5eee9-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5eee9-117">See also</span></span>

- [<span data-ttu-id="5eee9-118">Interface ICorDebugRemote</span><span class="sxs-lookup"><span data-stu-id="5eee9-118">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="5eee9-119">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="5eee9-119">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="5eee9-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5eee9-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
