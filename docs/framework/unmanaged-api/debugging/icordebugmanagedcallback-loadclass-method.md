---
title: Método ICorDebugManagedCallback::LoadClass
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
ms.openlocfilehash: 5d35ab4610ffa04d15dd2404fdf8010308bcb42a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212719"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="a1f9c-102">Método ICorDebugManagedCallback::LoadClass</span><span class="sxs-lookup"><span data-stu-id="a1f9c-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="a1f9c-103">Notifica o depurador de que uma classe foi carregada.</span><span class="sxs-lookup"><span data-stu-id="a1f9c-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1f9c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1f9c-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1f9c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a1f9c-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="a1f9c-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo no qual a classe foi carregada.</span><span class="sxs-lookup"><span data-stu-id="a1f9c-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="a1f9c-107">no Um ponteiro para um objeto ICorDebugClass que representa a classe.</span><span class="sxs-lookup"><span data-stu-id="a1f9c-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1f9c-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a1f9c-108">Remarks</span></span>  
 <span data-ttu-id="a1f9c-109">Esse retorno de chamada ocorrerá somente se o carregamento da classe tiver sido habilitado para o módulo que contém a classe.</span><span class="sxs-lookup"><span data-stu-id="a1f9c-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="a1f9c-110">O carregamento de classe é sempre habilitado para módulos dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="a1f9c-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="a1f9c-111">O `LoadClass` retorno de chamada fornece um tempo apropriado para associar pontos de interrupção a classes recém-gerado em módulos dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="a1f9c-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1f9c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a1f9c-112">Requirements</span></span>  
 <span data-ttu-id="a1f9c-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1f9c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1f9c-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1f9c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1f9c-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1f9c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1f9c-116">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1f9c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1f9c-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="a1f9c-117">See also</span></span>

- [<span data-ttu-id="a1f9c-118">Método UnloadClass</span><span class="sxs-lookup"><span data-stu-id="a1f9c-118">UnloadClass Method</span></span>](icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="a1f9c-119">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="a1f9c-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
