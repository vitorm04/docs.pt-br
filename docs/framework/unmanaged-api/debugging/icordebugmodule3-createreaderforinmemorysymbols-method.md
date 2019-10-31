---
title: Método ICorDebugModule3::CreateReaderForInMemorySymbols
ms.date: 03/30/2017
api_name:
- ICorDebugModule3.CreateReaderForInMemorySymbols
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type:
- apiref
ms.openlocfilehash: 2655151d34275b1b0fdc5d0903dd57fcea646014
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137314"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="85902-102">Método ICorDebugModule3::CreateReaderForInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="85902-102">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>
<span data-ttu-id="85902-103">Cria um leitor de símbolo de depuração para um módulo dinâmico.</span><span class="sxs-lookup"><span data-stu-id="85902-103">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85902-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="85902-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a><span data-ttu-id="85902-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="85902-105">Parameters</span></span>  
 <span data-ttu-id="85902-106">riid</span><span class="sxs-lookup"><span data-stu-id="85902-106">riid</span></span>  
 <span data-ttu-id="85902-107">no O IID da interface COM a ser retornada.</span><span class="sxs-lookup"><span data-stu-id="85902-107">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="85902-108">Normalmente, essa é uma [interface ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span><span class="sxs-lookup"><span data-stu-id="85902-108">Typically, this is an [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="85902-109">ppObj</span><span class="sxs-lookup"><span data-stu-id="85902-109">ppObj</span></span>  
 <span data-ttu-id="85902-110">fora Ponteiro para um ponteiro para a interface retornada.</span><span class="sxs-lookup"><span data-stu-id="85902-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85902-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="85902-111">Return Value</span></span>  
 <span data-ttu-id="85902-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="85902-112">S_OK</span></span>  
 <span data-ttu-id="85902-113">Leitor criado com êxito.</span><span class="sxs-lookup"><span data-stu-id="85902-113">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="85902-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="85902-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="85902-115">O módulo não é um módulo na memória ou dinâmico.</span><span class="sxs-lookup"><span data-stu-id="85902-115">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="85902-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="85902-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="85902-117">Os símbolos não foram fornecidos pelo aplicativo ou ainda não estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="85902-117">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="85902-118">E_FAIL (ou outros códigos de retorno de E_)</span><span class="sxs-lookup"><span data-stu-id="85902-118">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="85902-119">Não é possível criar o leitor.</span><span class="sxs-lookup"><span data-stu-id="85902-119">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85902-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="85902-120">Remarks</span></span>  
 <span data-ttu-id="85902-121">Esse método também pode ser usado para criar um objeto de leitor de símbolo para módulos na memória (não dinâmicos), mas somente depois que os símbolos são disponibilizados pela primeira vez (indicado pelo retorno de chamada do [método UpdateModuleSymbols](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="85902-121">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="85902-122">Esse método retorna uma nova instância de leitor toda vez que é chamado (como [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span><span class="sxs-lookup"><span data-stu-id="85902-122">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span></span> <span data-ttu-id="85902-123">Portanto, o depurador deve armazenar em cache o resultado e solicitar uma nova instância somente quando os dados subjacentes podem ter mudado (ou seja, quando um retorno de chamada de [método LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) é recebido).</span><span class="sxs-lookup"><span data-stu-id="85902-123">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="85902-124">Módulos dinâmicos não têm nenhum símbolo disponível até que o primeiro tipo seja carregado (conforme indicado pelo retorno de chamada do [método LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="85902-124">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85902-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="85902-125">Requirements</span></span>  
 <span data-ttu-id="85902-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85902-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85902-127">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85902-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85902-128">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85902-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85902-129">**Versões do .NET Framework:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="85902-129">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85902-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85902-130">See also</span></span>

- [<span data-ttu-id="85902-131">Interface ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="85902-131">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="85902-132">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="85902-132">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="85902-133">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="85902-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
