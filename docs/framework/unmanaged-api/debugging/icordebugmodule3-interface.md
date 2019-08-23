---
title: Interface ICorDebugModule3
ms.date: 03/30/2017
api_name:
- ICorDebugModule3
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3
helpviewer_keywords:
- ICorDebugModule3 interface [.NET Framework debugging]
ms.assetid: 0b69f945-263a-4e11-8512-89d27f6ea296
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e51ff64115ce3417087eee6845aa802ad64f2a72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960999"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="85cd7-102">Interface ICorDebugModule3</span><span class="sxs-lookup"><span data-stu-id="85cd7-102">ICorDebugModule3 Interface</span></span>
<span data-ttu-id="85cd7-103">Cria um leitor de símbolos para um módulo dinâmico.</span><span class="sxs-lookup"><span data-stu-id="85cd7-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85cd7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="85cd7-104">Syntax</span></span>  
  
```cpp  
interface ICorDebugModule3 : IUnknown  
{  
    HRESULT CreateReaderForInMemorySymbols  
      (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **  ppObj  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="85cd7-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="85cd7-105">Methods</span></span>  
  
|<span data-ttu-id="85cd7-106">Método</span><span class="sxs-lookup"><span data-stu-id="85cd7-106">Method</span></span>|<span data-ttu-id="85cd7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="85cd7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85cd7-108">Método ICorDebugModule3::CreateReaderForInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="85cd7-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="85cd7-109">Cria um leitor de símbolo (normalmente [interface ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) para um módulo dinâmico.</span><span class="sxs-lookup"><span data-stu-id="85cd7-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85cd7-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="85cd7-110">Remarks</span></span>  
 <span data-ttu-id="85cd7-111">Essa interface estende logicamente as interfaces "ICorDebugModule" e "ICorDebugModule2".</span><span class="sxs-lookup"><span data-stu-id="85cd7-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85cd7-112">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="85cd7-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85cd7-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="85cd7-113">Requirements</span></span>  
 <span data-ttu-id="85cd7-114">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85cd7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85cd7-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85cd7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85cd7-116">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85cd7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85cd7-117">**.NET Framework versões:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="85cd7-117">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="85cd7-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85cd7-118">See also</span></span>

- [<span data-ttu-id="85cd7-119">Interface ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="85cd7-119">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="85cd7-120">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="85cd7-120">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="85cd7-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="85cd7-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
