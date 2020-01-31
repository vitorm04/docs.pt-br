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
ms.openlocfilehash: 1d190c5b558c7c523be09267e59eab7c5611563a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793852"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="9f4ca-102">Função CreateCordbObject</span><span class="sxs-lookup"><span data-stu-id="9f4ca-102">CreateCordbObject Function</span></span>
<span data-ttu-id="9f4ca-103">Cria uma interface do depurador ([ICorDebug](icordebug-interface.md)) que fornece funcionalidade para instanciar uma sessão de depuração gerenciada em um processo remoto.</span><span class="sxs-lookup"><span data-stu-id="9f4ca-103">Creates a debugger interface ([ICorDebug](icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f4ca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f4ca-104">Syntax</span></span>  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f4ca-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9f4ca-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="9f4ca-106">no Versão do depurador do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="9f4ca-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="9f4ca-107">Esse parâmetro deve ser CorDebugVersion_2_0 para depuração remota.</span><span class="sxs-lookup"><span data-stu-id="9f4ca-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="9f4ca-108">fora Ponteiro para um ponteiro para um objeto que será convertido em uma interface [ICorDebug](icordebug-interface.md) e retornado.</span><span class="sxs-lookup"><span data-stu-id="9f4ca-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f4ca-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9f4ca-109">Return Value</span></span>  
 <span data-ttu-id="9f4ca-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9f4ca-110">S_OK</span></span>  
 <span data-ttu-id="9f4ca-111">O número de CLRs no processo foi determinado com êxito e as matrizes de identificador e caminho correspondentes foram preenchidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="9f4ca-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="9f4ca-112">{1&gt;E_INVALIDARG&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9f4ca-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="9f4ca-113">`ppCordb` é nulo ou `iDebuggerVersion` não está CorDebugVersion_2_0.</span><span class="sxs-lookup"><span data-stu-id="9f4ca-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="9f4ca-114">{1&gt;E_OUTOFMEMORY&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9f4ca-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="9f4ca-115">Não é possível alocar memória suficiente para `ppCordb`</span><span class="sxs-lookup"><span data-stu-id="9f4ca-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="9f4ca-116">E_FAIL (ou outros códigos de retorno de E_)</span><span class="sxs-lookup"><span data-stu-id="9f4ca-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="9f4ca-117">Outras falhas.</span><span class="sxs-lookup"><span data-stu-id="9f4ca-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f4ca-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="9f4ca-118">Remarks</span></span>  
 <span data-ttu-id="9f4ca-119">A interface [ICorDebug](icordebug-interface.md) retornada em `ppCordb` é a interface de depuração de nível superior para todos os serviços de depuração gerenciados.</span><span class="sxs-lookup"><span data-stu-id="9f4ca-119">The [ICorDebug](icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f4ca-120">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="9f4ca-120">Requirements</span></span>  
 <span data-ttu-id="9f4ca-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f4ca-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f4ca-122">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="9f4ca-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="9f4ca-123">**Biblioteca:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="9f4ca-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="9f4ca-124">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="9f4ca-124">**.NET Framework Versions:** 3.5 SP1</span></span>
