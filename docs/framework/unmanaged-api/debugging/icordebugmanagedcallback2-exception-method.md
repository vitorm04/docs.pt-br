---
title: Método ICorDebugManagedCallback2::Exception
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type:
- apiref
ms.openlocfilehash: f40030a2034057e83de51a21655a686f30b9ee88
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137451"
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="20cee-102">Método ICorDebugManagedCallback2::Exception</span><span class="sxs-lookup"><span data-stu-id="20cee-102">ICorDebugManagedCallback2::Exception Method</span></span>
<span data-ttu-id="20cee-103">Notifica o depurador de que uma pesquisa de um manipulador de exceção foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="20cee-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20cee-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="20cee-104">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20cee-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="20cee-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="20cee-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que contém o thread no qual a exceção foi gerada.</span><span class="sxs-lookup"><span data-stu-id="20cee-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="20cee-107">no Um ponteiro para um objeto ICorDebugThread que representa o thread no qual a exceção foi gerada.</span><span class="sxs-lookup"><span data-stu-id="20cee-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="20cee-108">no Um ponteiro para um objeto ICorDebugFrame que representa um quadro, conforme determinado pelo parâmetro `dwEventType`.</span><span class="sxs-lookup"><span data-stu-id="20cee-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="20cee-109">Para obter mais informações, consulte a tabela na seção comentários.</span><span class="sxs-lookup"><span data-stu-id="20cee-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="20cee-110">no Um inteiro que especifica um deslocamento, conforme determinado pelo parâmetro `dwEventType`.</span><span class="sxs-lookup"><span data-stu-id="20cee-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="20cee-111">Para obter mais informações, consulte a tabela na seção comentários.</span><span class="sxs-lookup"><span data-stu-id="20cee-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="20cee-112">no Um valor da enumeração CorDebugExceptionCallbackType que especifica o tipo deste retorno de chamada de exceção.</span><span class="sxs-lookup"><span data-stu-id="20cee-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="20cee-113">no Um valor da enumeração [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) que especifica informações adicionais sobre a exceção</span><span class="sxs-lookup"><span data-stu-id="20cee-113">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20cee-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="20cee-114">Remarks</span></span>  
 <span data-ttu-id="20cee-115">O retorno de chamada `Exception` é chamado em vários pontos durante a fase de pesquisa do processo de tratamento de exceção.</span><span class="sxs-lookup"><span data-stu-id="20cee-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="20cee-116">Ou seja, ele pode ser chamado mais de uma vez ao desenrolar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="20cee-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="20cee-117">A exceção que está sendo processada pode ser recuperada do objeto ICorDebugThread referenciado pelo parâmetro `pThread`.</span><span class="sxs-lookup"><span data-stu-id="20cee-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="20cee-118">O quadro e o deslocamento específicos são determinados pelo parâmetro `dwEventType` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="20cee-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="20cee-119">Valor de `dwEventType`</span><span class="sxs-lookup"><span data-stu-id="20cee-119">Value of `dwEventType`</span></span>|<span data-ttu-id="20cee-120">Valor de `pFrame`</span><span class="sxs-lookup"><span data-stu-id="20cee-120">Value of `pFrame`</span></span>|<span data-ttu-id="20cee-121">Valor de `nOffset`</span><span class="sxs-lookup"><span data-stu-id="20cee-121">Value of `nOffset`</span></span>|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="20cee-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="20cee-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="20cee-123">O quadro que gerou a exceção.</span><span class="sxs-lookup"><span data-stu-id="20cee-123">The frame that threw the exception.</span></span>|<span data-ttu-id="20cee-124">O ponteiro de instrução no quadro.</span><span class="sxs-lookup"><span data-stu-id="20cee-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="20cee-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="20cee-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="20cee-126">O quadro de código do usuário mais próximo do ponto da exceção gerada.</span><span class="sxs-lookup"><span data-stu-id="20cee-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="20cee-127">O ponteiro de instrução no quadro.</span><span class="sxs-lookup"><span data-stu-id="20cee-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="20cee-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="20cee-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="20cee-129">O quadro que contém o manipulador catch.</span><span class="sxs-lookup"><span data-stu-id="20cee-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="20cee-130">O deslocamento da MSIL (Microsoft Intermediate Language) do início do manipulador catch.</span><span class="sxs-lookup"><span data-stu-id="20cee-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="20cee-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="20cee-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="20cee-132">NULL</span><span class="sxs-lookup"><span data-stu-id="20cee-132">NULL</span></span>|<span data-ttu-id="20cee-133">Indefinido.</span><span class="sxs-lookup"><span data-stu-id="20cee-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="20cee-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="20cee-134">Requirements</span></span>  
 <span data-ttu-id="20cee-135">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20cee-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20cee-136">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20cee-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20cee-137">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20cee-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20cee-138">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20cee-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20cee-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20cee-139">See also</span></span>

- [<span data-ttu-id="20cee-140">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="20cee-140">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="20cee-141">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="20cee-141">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
