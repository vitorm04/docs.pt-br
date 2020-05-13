---
title: Interface ICorDebugILFrame2
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2
helpviewer_keywords:
- ICorDebugILFrame2 interface [.NET Framework debugging]
ms.assetid: f94b9d53-d8f8-4424-a95e-53a1bfd26e4a
topic_type:
- apiref
ms.openlocfilehash: 2e0f284625e99215900c6aaab94e4eae611787ed
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212094"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="cfae7-102">Interface ICorDebugILFrame2</span><span class="sxs-lookup"><span data-stu-id="cfae7-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="cfae7-103">Uma extensão lógica da interface ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="cfae7-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cfae7-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="cfae7-104">Methods</span></span>  
  
|<span data-ttu-id="cfae7-105">Método</span><span class="sxs-lookup"><span data-stu-id="cfae7-105">Method</span></span>|<span data-ttu-id="cfae7-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="cfae7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cfae7-107">Método EnumerateTypeParameters</span><span class="sxs-lookup"><span data-stu-id="cfae7-107">EnumerateTypeParameters Method</span></span>](icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="cfae7-108">Obtém um objeto ICorDebugTypeEnum que contém os <xref:System.Type> parâmetros neste quadro.</span><span class="sxs-lookup"><span data-stu-id="cfae7-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="cfae7-109">Método RemapFunction</span><span class="sxs-lookup"><span data-stu-id="cfae7-109">RemapFunction Method</span></span>](icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="cfae7-110">Remapeia uma função editada especificando o novo deslocamento MSIL.</span><span class="sxs-lookup"><span data-stu-id="cfae7-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfae7-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="cfae7-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cfae7-112">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="cfae7-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfae7-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cfae7-113">Requirements</span></span>  
 <span data-ttu-id="cfae7-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfae7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfae7-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cfae7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cfae7-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfae7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfae7-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfae7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfae7-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="cfae7-118">See also</span></span>

- [<span data-ttu-id="cfae7-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="cfae7-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
