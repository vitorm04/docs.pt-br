---
title: Método ICorConfiguration::AddDebuggerSpecialThread
ms.date: 03/30/2017
api_name:
- ICorConfiguration.AddDebuggerSpecialThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AddDebuggerSpecialThread
helpviewer_keywords:
- AddDebuggerSpecialThread method [.NET Framework hosting]
- ICorConfiguration::AddDebuggerSpecialThread method [.NET Framework hosting]
ms.assetid: 1f1e3239-438e-4be9-a3bb-7d0722d3a76d
topic_type:
- apiref
ms.openlocfilehash: 8b6593ad995872f0e0014b1e8bcd8a4b576bbeaf
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762416"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="4d302-102">Método ICorConfiguration::AddDebuggerSpecialThread</span><span class="sxs-lookup"><span data-stu-id="4d302-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>
<span data-ttu-id="4d302-103">Indica aos serviços de depuração que um thread específico deve ter permissão para continuar a execução enquanto o depurador tem um aplicativo interrompido durante cenários de depuração gerenciados ou não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="4d302-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d302-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4d302-104">Syntax</span></span>  
  
```cpp  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d302-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4d302-105">Parameters</span></span>  
 `dwSpecialThreadId`  
 <span data-ttu-id="4d302-106">no A ID do thread que deve ter permissão para continuar a execução.</span><span class="sxs-lookup"><span data-stu-id="4d302-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d302-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="4d302-107">Remarks</span></span>  
 <span data-ttu-id="4d302-108">O thread especificado não terá permissão para executar código gerenciado ou inserir o tempo de execução de qualquer forma.</span><span class="sxs-lookup"><span data-stu-id="4d302-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="4d302-109">Um exemplo desse thread seria um thread em processo para dar suporte a depuradores de script herdados.</span><span class="sxs-lookup"><span data-stu-id="4d302-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d302-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4d302-110">Requirements</span></span>  
 <span data-ttu-id="4d302-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d302-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d302-112">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4d302-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4d302-113">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4d302-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d302-114">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d302-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d302-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="4d302-115">See also</span></span>

- [<span data-ttu-id="4d302-116">Interface ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="4d302-116">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
