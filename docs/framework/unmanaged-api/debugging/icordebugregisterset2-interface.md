---
title: Interface ICorDebugRegisterSet2
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2
helpviewer_keywords:
- ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type:
- apiref
ms.openlocfilehash: 161358fab9a4601e7b718321273d493bd84a3228
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792006"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="fcbc6-102">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="fcbc6-102">ICorDebugRegisterSet2 Interface</span></span>
<span data-ttu-id="fcbc6-103">Estende os recursos da interface [ICorDebugRegisterSet](icordebugregisterset-interface.md) para plataformas de hardware que têm mais de 64 registros.</span><span class="sxs-lookup"><span data-stu-id="fcbc6-103">Extends the capabilities of the [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fcbc6-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fcbc6-104">Methods</span></span>  
  
|<span data-ttu-id="fcbc6-105">Método</span><span class="sxs-lookup"><span data-stu-id="fcbc6-105">Method</span></span>|<span data-ttu-id="fcbc6-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="fcbc6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fcbc6-107">Método GetRegisters</span><span class="sxs-lookup"><span data-stu-id="fcbc6-107">GetRegisters Method</span></span>](icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="fcbc6-108">Obtém o valor de cada registro (no computador que está executando o código) que é especificado pela máscara de bits.</span><span class="sxs-lookup"><span data-stu-id="fcbc6-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="fcbc6-109">Método GetRegistersAvailable</span><span class="sxs-lookup"><span data-stu-id="fcbc6-109">GetRegistersAvailable Method</span></span>](icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="fcbc6-110">Obtém uma matriz de bytes que fornece um bitmap dos registros disponíveis.</span><span class="sxs-lookup"><span data-stu-id="fcbc6-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="fcbc6-111">Método SetRegisters</span><span class="sxs-lookup"><span data-stu-id="fcbc6-111">SetRegisters Method</span></span>](icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="fcbc6-112">Não implementado na versão .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="fcbc6-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcbc6-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="fcbc6-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fcbc6-114">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="fcbc6-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcbc6-115">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="fcbc6-115">Requirements</span></span>  
 <span data-ttu-id="fcbc6-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcbc6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcbc6-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fcbc6-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fcbc6-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fcbc6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcbc6-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcbc6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcbc6-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="fcbc6-120">See also</span></span>

- [<span data-ttu-id="fcbc6-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="fcbc6-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="fcbc6-122">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="fcbc6-122">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
