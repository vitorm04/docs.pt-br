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
ms.openlocfilehash: 4883c208468db0096bed3ff8cf4a8ed50a5d7cc6
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379225"
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="cd081-102">Interface ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="cd081-102">ICorDebugRemoteTarget Interface</span></span>
<span data-ttu-id="cd081-103">Fornece métodos que permitem aos desenvolvedores depurar aplicativos baseados no Silverlight no ambiente Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="cd081-103">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd081-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd081-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="methods"></a><span data-ttu-id="cd081-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="cd081-105">Methods</span></span>  
  
|<span data-ttu-id="cd081-106">Método</span><span class="sxs-lookup"><span data-stu-id="cd081-106">Method</span></span>|<span data-ttu-id="cd081-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="cd081-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cd081-108">Método ICorDebugRemoteTarget::GetHostName</span><span class="sxs-lookup"><span data-stu-id="cd081-108">ICorDebugRemoteTarget::GetHostName Method</span></span>](icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="cd081-109">Retorna o nome do host ou o endereço IP de um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="cd081-109">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd081-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="cd081-110">Remarks</span></span>  
 <span data-ttu-id="cd081-111">A depuração de modo misto (ou seja, código gerenciado e nativo) não tem suporte no Windows 95, Windows 98 ou Windows ME, ou em plataformas não x86 (como IA-64 e AMD64).</span><span class="sxs-lookup"><span data-stu-id="cd081-111">Mixed-mode (that is, managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd081-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cd081-112">Requirements</span></span>  
 <span data-ttu-id="cd081-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd081-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd081-114">**Cabeçalho:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="cd081-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="cd081-115">**Biblioteca:** : CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cd081-115">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd081-116">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="cd081-116">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd081-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="cd081-117">See also</span></span>

- [<span data-ttu-id="cd081-118">Interface ICorDebugRemote</span><span class="sxs-lookup"><span data-stu-id="cd081-118">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="cd081-119">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="cd081-119">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="cd081-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="cd081-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
