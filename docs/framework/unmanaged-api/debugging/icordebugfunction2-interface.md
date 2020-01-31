---
title: Interface ICorDebugFunction2
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2
helpviewer_keywords:
- ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type:
- apiref
ms.openlocfilehash: 5364e39f7e0a9b6c9cd10cd8f17bab4a03a4b7af
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794477"
---
# <a name="icordebugfunction2-interface"></a><span data-ttu-id="a34c0-102">Interface ICorDebugFunction2</span><span class="sxs-lookup"><span data-stu-id="a34c0-102">ICorDebugFunction2 Interface</span></span>

<span data-ttu-id="a34c0-103">Estende logicamente a interface ICorDebugFunction para fornecer suporte para depuração passo a Apenas Meu Código, que ignora o código que não é do usuário.</span><span class="sxs-lookup"><span data-stu-id="a34c0-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a34c0-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a34c0-104">Methods</span></span>  
  
|<span data-ttu-id="a34c0-105">Método</span><span class="sxs-lookup"><span data-stu-id="a34c0-105">Method</span></span>|<span data-ttu-id="a34c0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a34c0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a34c0-107">Método EnumerateNativeCode</span><span class="sxs-lookup"><span data-stu-id="a34c0-107">EnumerateNativeCode Method</span></span>](icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="a34c0-108">(Ainda não implementado.) Obtém um ponteiro de interface para um ICorDebugCodeEnum que contém as instruções de código nativo na função referenciada por este objeto ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="a34c0-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="a34c0-109">Método GetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="a34c0-109">GetJMCStatus Method</span></span>](icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="a34c0-110">Obtém um valor que indica se esta função está marcada como código de usuário.</span><span class="sxs-lookup"><span data-stu-id="a34c0-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="a34c0-111">Método GetVersionNumber</span><span class="sxs-lookup"><span data-stu-id="a34c0-111">GetVersionNumber Method</span></span>](icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="a34c0-112">Obtém a versão editar e continuar desta função.</span><span class="sxs-lookup"><span data-stu-id="a34c0-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="a34c0-113">Método SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="a34c0-113">SetJMCStatus Method</span></span>](icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="a34c0-114">Marca essa função para Apenas Meu Código stepping.</span><span class="sxs-lookup"><span data-stu-id="a34c0-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a34c0-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="a34c0-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a34c0-116">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="a34c0-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a34c0-117">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="a34c0-117">Requirements</span></span>  
 <span data-ttu-id="a34c0-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a34c0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a34c0-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a34c0-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a34c0-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a34c0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a34c0-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a34c0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a34c0-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="a34c0-122">See also</span></span>

- [<span data-ttu-id="a34c0-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a34c0-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
