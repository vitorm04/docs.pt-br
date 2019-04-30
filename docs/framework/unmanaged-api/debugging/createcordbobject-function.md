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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f546d7707c40f7f26a46177ae972a988e54e1e45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965822"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="cfa23-102">Função CreateCordbObject</span><span class="sxs-lookup"><span data-stu-id="cfa23-102">CreateCordbObject Function</span></span>
<span data-ttu-id="cfa23-103">Cria uma interface do depurador ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) que fornece funcionalidade para instanciar uma sessão de depuração gerenciada em um processo remoto.</span><span class="sxs-lookup"><span data-stu-id="cfa23-103">Creates a debugger interface ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfa23-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cfa23-104">Syntax</span></span>  
  
```  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfa23-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cfa23-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="cfa23-106">[in] Versão do depurador do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="cfa23-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="cfa23-107">Esse parâmetro deve ser CorDebugVersion_2_0 para depuração remota.</span><span class="sxs-lookup"><span data-stu-id="cfa23-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="cfa23-108">[out] Ponteiro para um ponteiro para um objeto que será convertido em um [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) de interface e retornado.</span><span class="sxs-lookup"><span data-stu-id="cfa23-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cfa23-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="cfa23-109">Return Value</span></span>  
 <span data-ttu-id="cfa23-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="cfa23-110">S_OK</span></span>  
 <span data-ttu-id="cfa23-111">O número de CLRs no processo com êxito foi determinado e o identificador correspondente e matrizes de caminho foram preenchidos corretamente.</span><span class="sxs-lookup"><span data-stu-id="cfa23-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="cfa23-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="cfa23-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="cfa23-113">`ppCordb` é nulo, ou `iDebuggerVersion` não é CorDebugVersion_2_0.</span><span class="sxs-lookup"><span data-stu-id="cfa23-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="cfa23-114">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="cfa23-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="cfa23-115">Não é possível alocar memória suficiente para `ppCordb`</span><span class="sxs-lookup"><span data-stu-id="cfa23-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="cfa23-116">E_FAIL (ou outros códigos de retorno e _)</span><span class="sxs-lookup"><span data-stu-id="cfa23-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="cfa23-117">Outras falhas.</span><span class="sxs-lookup"><span data-stu-id="cfa23-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfa23-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="cfa23-118">Remarks</span></span>  
 <span data-ttu-id="cfa23-119">O [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface que é retornado no `ppCordb` é a interface de depuração de nível superior para todos os gerenciados serviços de depuração.</span><span class="sxs-lookup"><span data-stu-id="cfa23-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfa23-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cfa23-120">Requirements</span></span>  
 <span data-ttu-id="cfa23-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfa23-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfa23-122">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="cfa23-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="cfa23-123">**Biblioteca:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="cfa23-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="cfa23-124">**Versões do .NET framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="cfa23-124">**.NET Framework Versions:** 3.5 SP1</span></span>
