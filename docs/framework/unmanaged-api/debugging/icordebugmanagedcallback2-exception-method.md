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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8952b34781045089945e7e72e179e88300b5fdd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942526"
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="1d392-102">Método ICorDebugManagedCallback2::Exception</span><span class="sxs-lookup"><span data-stu-id="1d392-102">ICorDebugManagedCallback2::Exception Method</span></span>
<span data-ttu-id="1d392-103">Notifica o depurador que uma pesquisa por um manipulador de exceção foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="1d392-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d392-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d392-104">Syntax</span></span>  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d392-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1d392-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="1d392-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém o segmento em que a exceção foi lançada.</span><span class="sxs-lookup"><span data-stu-id="1d392-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="1d392-107">[in] Um ponteiro para um objeto de ICorDebugThread que representa o thread no qual a exceção foi lançada.</span><span class="sxs-lookup"><span data-stu-id="1d392-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="1d392-108">[in] Um ponteiro para um objeto ICorDebugFrame que representa um quadro, conforme determinado pelo `dwEventType` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1d392-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="1d392-109">Para obter mais informações, consulte a tabela na seção comentários.</span><span class="sxs-lookup"><span data-stu-id="1d392-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="1d392-110">[in] Um inteiro que especifica um deslocamento, conforme determinado pelo `dwEventType` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1d392-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="1d392-111">Para obter mais informações, consulte a tabela na seção comentários.</span><span class="sxs-lookup"><span data-stu-id="1d392-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="1d392-112">[in] Um valor de enumeração CorDebugExceptionCallbackType que especifica o tipo de retorno de chamada essa exceção.</span><span class="sxs-lookup"><span data-stu-id="1d392-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="1d392-113">[in] Um valor igual a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeração que especifica informações adicionais sobre a exceção</span><span class="sxs-lookup"><span data-stu-id="1d392-113">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d392-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="1d392-114">Remarks</span></span>  
 <span data-ttu-id="1d392-115">O `Exception` retorno de chamada é chamado em vários pontos durante a fase de pesquisa do processo de manipulação de exceção.</span><span class="sxs-lookup"><span data-stu-id="1d392-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="1d392-116">Ou seja, ele pode ser chamado mais de uma vez durante o desenrolamento de uma exceção.</span><span class="sxs-lookup"><span data-stu-id="1d392-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="1d392-117">A exceção que está sendo processada pode ser recuperada do objeto ICorDebugThread referenciado pelo `pThread` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1d392-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="1d392-118">O quadro em particular e o deslocamento são determinados pelo `dwEventType` parâmetro da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="1d392-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="1d392-119">Valor de `dwEventType`</span><span class="sxs-lookup"><span data-stu-id="1d392-119">Value of `dwEventType`</span></span>|<span data-ttu-id="1d392-120">Valor de `pFrame`</span><span class="sxs-lookup"><span data-stu-id="1d392-120">Value of `pFrame`</span></span>|<span data-ttu-id="1d392-121">Valor de `nOffset`</span><span class="sxs-lookup"><span data-stu-id="1d392-121">Value of `nOffset`</span></span>|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="1d392-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="1d392-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="1d392-123">O quadro que gerou a exceção.</span><span class="sxs-lookup"><span data-stu-id="1d392-123">The frame that threw the exception.</span></span>|<span data-ttu-id="1d392-124">O ponteiro de instrução no quadro.</span><span class="sxs-lookup"><span data-stu-id="1d392-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="1d392-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="1d392-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="1d392-126">O quadro de código do usuário mais próximo ao ponto da exceção lançada.</span><span class="sxs-lookup"><span data-stu-id="1d392-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="1d392-127">O ponteiro de instrução no quadro.</span><span class="sxs-lookup"><span data-stu-id="1d392-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="1d392-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="1d392-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="1d392-129">O quadro que contém o manipulador catch.</span><span class="sxs-lookup"><span data-stu-id="1d392-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="1d392-130">O deslocamento de Microsoft intermediate language (MSIL) de início do manipulador catch.</span><span class="sxs-lookup"><span data-stu-id="1d392-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="1d392-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="1d392-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="1d392-132">NULL</span><span class="sxs-lookup"><span data-stu-id="1d392-132">NULL</span></span>|<span data-ttu-id="1d392-133">Indefinido.</span><span class="sxs-lookup"><span data-stu-id="1d392-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1d392-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1d392-134">Requirements</span></span>  
 <span data-ttu-id="1d392-135">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d392-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d392-136">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d392-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d392-137">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d392-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d392-138">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d392-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d392-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d392-139">See also</span></span>

- [<span data-ttu-id="1d392-140">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="1d392-140">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="1d392-141">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="1d392-141">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
