---
title: Método ICorDebugThread::GetCurrentException
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4baa4eb4da48b923ab0137ca25d9d819c94e33d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994026"
---
# <a name="icordebugthreadgetcurrentexception-method"></a><span data-ttu-id="b82c2-102">Método ICorDebugThread::GetCurrentException</span><span class="sxs-lookup"><span data-stu-id="b82c2-102">ICorDebugThread::GetCurrentException Method</span></span>
<span data-ttu-id="b82c2-103">Obtém um ponteiro de interface para um objeto de ICorDebugValue que representa uma exceção que está sendo atualmente gerada pelo código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b82c2-103">Gets an interface pointer to an ICorDebugValue object that represents an exception that is currently being thrown by managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b82c2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b82c2-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b82c2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b82c2-105">Parameters</span></span>  
 `ppExceptionObject`  
 <span data-ttu-id="b82c2-106">[out] Um ponteiro para o endereço de um `ICorDebugValue` que representa a exceção que está sendo atualmente gerada pelo objeto de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b82c2-106">[out] A pointer to the address of an `ICorDebugValue` object that represents the exception that is currently being thrown by managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b82c2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b82c2-107">Remarks</span></span>  
 <span data-ttu-id="b82c2-108">O objeto de exceção continuará a existir desde o momento em que a exceção é lançada até o final do `catch` bloco.</span><span class="sxs-lookup"><span data-stu-id="b82c2-108">The exception object will exist from the time the exception is thrown until the end of the `catch` block.</span></span> <span data-ttu-id="b82c2-109">Uma avaliação de função, que é executada pelos métodos ICorDebugEval, limpará horizontalmente o objeto de exceção na instalação e restaurá-lo após a conclusão.</span><span class="sxs-lookup"><span data-stu-id="b82c2-109">A function evaluation, which is performed by the ICorDebugEval methods, will clear out the exception object on setup and restore it on completion.</span></span>  
  
 <span data-ttu-id="b82c2-110">Exceções podem ser aninhadas (por exemplo, se uma exceção é gerada em um filtro ou em uma avaliação de função), portanto, pode haver várias exceções pendentes em um único thread.</span><span class="sxs-lookup"><span data-stu-id="b82c2-110">Exceptions can be nested (for example, if an exception is thrown in a filter or in a function evaluation), so there may be multiple outstanding exceptions on a single thread.</span></span> <span data-ttu-id="b82c2-111">`GetCurrentException` Retorna a exceção mais atual.</span><span class="sxs-lookup"><span data-stu-id="b82c2-111">`GetCurrentException` returns the most current exception.</span></span>  
  
 <span data-ttu-id="b82c2-112">O objeto de exceção e o tipo podem mudar durante a vida útil da exceção.</span><span class="sxs-lookup"><span data-stu-id="b82c2-112">The exception object and type may change throughout the life of the exception.</span></span> <span data-ttu-id="b82c2-113">Por exemplo, depois que uma exceção do tipo x é gerada, o common language runtime (CLR) pode ficar sem memória e promovê-lo para uma exceção de falta de memória.</span><span class="sxs-lookup"><span data-stu-id="b82c2-113">For example, after an exception of type x is thrown, the common language runtime (CLR) may run out of memory and promote it to an out-of-memory exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b82c2-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b82c2-114">Requirements</span></span>  
 <span data-ttu-id="b82c2-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b82c2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b82c2-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b82c2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b82c2-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b82c2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b82c2-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b82c2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
