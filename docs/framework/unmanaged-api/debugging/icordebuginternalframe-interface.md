---
title: Interface ICorDebugInternalFrame
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame
helpviewer_keywords:
- ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type:
- apiref
ms.openlocfilehash: 332bc99795c0a4c896b60c61941a5a24b3f4accc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209931"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="0e97c-102">Interface ICorDebugInternalFrame</span><span class="sxs-lookup"><span data-stu-id="0e97c-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="0e97c-103">Representa um quadro interno de tempo de execução na pilha.</span><span class="sxs-lookup"><span data-stu-id="0e97c-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="0e97c-104">Essa interface é uma subclasse da interface ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="0e97c-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0e97c-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="0e97c-105">Methods</span></span>  
  
|<span data-ttu-id="0e97c-106">Método</span><span class="sxs-lookup"><span data-stu-id="0e97c-106">Method</span></span>|<span data-ttu-id="0e97c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0e97c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0e97c-108">Método GetFrameType</span><span class="sxs-lookup"><span data-stu-id="0e97c-108">GetFrameType Method</span></span>](icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="0e97c-109">Obtém o tipo deste quadro interno.</span><span class="sxs-lookup"><span data-stu-id="0e97c-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e97c-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="0e97c-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e97c-111">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="0e97c-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e97c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0e97c-112">Requirements</span></span>  
 <span data-ttu-id="0e97c-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e97c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e97c-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e97c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e97c-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e97c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e97c-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e97c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e97c-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="0e97c-117">See also</span></span>

- [<span data-ttu-id="0e97c-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="0e97c-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
