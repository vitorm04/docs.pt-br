---
title: Interface ICLRDebugging
ms.date: 03/30/2017
api_name:
- ICLRDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging
helpviewer_keywords:
- ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type:
- apiref
ms.openlocfilehash: a3d4297e3b16dd1637e6293dbf7f04d4fbeda50f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860388"
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="5c4f2-102">Interface ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="5c4f2-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="5c4f2-103">Fornece métodos que manipulam os módulos de carregamento e descarregamento para depuração.</span><span class="sxs-lookup"><span data-stu-id="5c4f2-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5c4f2-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="5c4f2-104">Methods</span></span>  
  
|<span data-ttu-id="5c4f2-105">Método</span><span class="sxs-lookup"><span data-stu-id="5c4f2-105">Method</span></span>|<span data-ttu-id="5c4f2-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c4f2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5c4f2-107">Método OpenVirtualProcess</span><span class="sxs-lookup"><span data-stu-id="5c4f2-107">OpenVirtualProcess Method</span></span>](iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="5c4f2-108">Obtém a interface "ICorDebugProcess" que corresponde a um módulo Common Language Runtime (CLR) carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="5c4f2-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="5c4f2-109">Método CanUnloadNow</span><span class="sxs-lookup"><span data-stu-id="5c4f2-109">CanUnloadNow Method</span></span>](iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="5c4f2-110">Determina se uma biblioteca fornecida por uma interface [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) ainda está em uso ou pode ser descarregada.</span><span class="sxs-lookup"><span data-stu-id="5c4f2-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c4f2-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="5c4f2-111">Remarks</span></span>  
 <span data-ttu-id="5c4f2-112">Você pode obter uma instância da `ICLRDebugging` interface usando a função [CLRCreateInstance](../hosting/clrcreateinstance-function.md) .</span><span class="sxs-lookup"><span data-stu-id="5c4f2-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c4f2-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5c4f2-113">Requirements</span></span>  
 <span data-ttu-id="5c4f2-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c4f2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c4f2-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c4f2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c4f2-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c4f2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c4f2-117">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c4f2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c4f2-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="5c4f2-118">See also</span></span>

- [<span data-ttu-id="5c4f2-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5c4f2-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5c4f2-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="5c4f2-120">Debugging</span></span>](index.md)
