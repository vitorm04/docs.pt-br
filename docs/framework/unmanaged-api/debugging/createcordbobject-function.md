---
title: Função CreateCordbObject
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
ms.openlocfilehash: 2716adcc8c79c8003202561ea2011c2469a6bc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179230"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="00649-102">Função CreateCordbObject</span><span class="sxs-lookup"><span data-stu-id="00649-102">CreateCordbObject Function</span></span>
<span data-ttu-id="00649-103">Cria uma interface de depurador[(ICorDebug)](icordebug-interface.md)que fornece funcionalidade para instanciar uma sessão de depuração gerenciada em um processo remoto.</span><span class="sxs-lookup"><span data-stu-id="00649-103">Creates a debugger interface ([ICorDebug](icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00649-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00649-104">Syntax</span></span>  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00649-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="00649-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="00649-106">[em] Versão dedepurador do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="00649-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="00649-107">Este parâmetro deve ser CorDebugVersion_2_0 para depuração remota.</span><span class="sxs-lookup"><span data-stu-id="00649-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="00649-108">[fora] Ponteiro para um ponteiro para um objeto que será lançado para uma interface [ICorDebug](icordebug-interface.md) e retornado.</span><span class="sxs-lookup"><span data-stu-id="00649-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00649-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="00649-109">Return Value</span></span>  
 <span data-ttu-id="00649-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="00649-110">S_OK</span></span>  
 <span data-ttu-id="00649-111">O número de CLRs no processo foi determinado com sucesso, e as matrizes de cabo e caminho correspondentes foram devidamente preenchidas.</span><span class="sxs-lookup"><span data-stu-id="00649-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="00649-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="00649-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="00649-113">`ppCordb`é nulo, ou `iDebuggerVersion` não é CorDebugVersion_2_0.</span><span class="sxs-lookup"><span data-stu-id="00649-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="00649-114">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="00649-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="00649-115">Incapaz de alocar memória suficiente para`ppCordb`</span><span class="sxs-lookup"><span data-stu-id="00649-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="00649-116">E_FAIL (ou outros códigos de retorno E_)</span><span class="sxs-lookup"><span data-stu-id="00649-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="00649-117">Outras falhas.</span><span class="sxs-lookup"><span data-stu-id="00649-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00649-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="00649-118">Remarks</span></span>  
 <span data-ttu-id="00649-119">A interface [ICorDebug](icordebug-interface.md) que `ppCordb` é retornada é a interface de depuração de nível superior para todos os serviços gerenciados de depuração.</span><span class="sxs-lookup"><span data-stu-id="00649-119">The [ICorDebug](icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00649-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="00649-120">Requirements</span></span>  
 <span data-ttu-id="00649-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00649-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00649-122">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="00649-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="00649-123">**Biblioteca:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="00649-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="00649-124">**.NET Framework Versões:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="00649-124">**.NET Framework Versions:** 3.5 SP1</span></span>
