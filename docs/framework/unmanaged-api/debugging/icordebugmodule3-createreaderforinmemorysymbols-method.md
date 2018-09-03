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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 342739f6c71e9c576e557433dc6abd0adbf38c8c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468346"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="85b7e-102">Método ICorDebugModule3::CreateReaderForInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="85b7e-102">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>
<span data-ttu-id="85b7e-103">Cria um leitor de símbolo de depuração para um módulo dinâmico.</span><span class="sxs-lookup"><span data-stu-id="85b7e-103">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85b7e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="85b7e-104">Syntax</span></span>  
  
```  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
#### <a name="parameters"></a><span data-ttu-id="85b7e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="85b7e-105">Parameters</span></span>  
 <span data-ttu-id="85b7e-106">riid</span><span class="sxs-lookup"><span data-stu-id="85b7e-106">riid</span></span>  
 <span data-ttu-id="85b7e-107">[in] O IID da interface COM para retornar.</span><span class="sxs-lookup"><span data-stu-id="85b7e-107">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="85b7e-108">Normalmente, esse é um [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span><span class="sxs-lookup"><span data-stu-id="85b7e-108">Typically, this is an [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="85b7e-109">ppObj</span><span class="sxs-lookup"><span data-stu-id="85b7e-109">ppObj</span></span>  
 <span data-ttu-id="85b7e-110">[out] Ponteiro para um ponteiro para a interface retornada.</span><span class="sxs-lookup"><span data-stu-id="85b7e-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85b7e-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="85b7e-111">Return Value</span></span>  
 <span data-ttu-id="85b7e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="85b7e-112">S_OK</span></span>  
 <span data-ttu-id="85b7e-113">O leitor foi criado com êxito.</span><span class="sxs-lookup"><span data-stu-id="85b7e-113">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="85b7e-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="85b7e-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="85b7e-115">O módulo não é um módulo na memória ou dinâmico.</span><span class="sxs-lookup"><span data-stu-id="85b7e-115">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="85b7e-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="85b7e-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="85b7e-117">Símbolos não foram fornecidos pelo aplicativo, ou ainda não estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="85b7e-117">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="85b7e-118">E_FAIL (ou outros códigos de retorno e _)</span><span class="sxs-lookup"><span data-stu-id="85b7e-118">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="85b7e-119">Não é possível criar o leitor.</span><span class="sxs-lookup"><span data-stu-id="85b7e-119">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85b7e-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="85b7e-120">Remarks</span></span>  
 <span data-ttu-id="85b7e-121">Esse método também pode ser usado para criar um objeto de leitor de símbolo para módulos de memória (não dinâmicos), mas somente depois que os símbolos primeiro estão disponíveis (indicado pelo [método UpdateModuleSymbols](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) retorno de chamada).</span><span class="sxs-lookup"><span data-stu-id="85b7e-121">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="85b7e-122">Esse método retorna uma nova instância de leitor toda vez que ele é chamado (como [CComPtrBase::CoCreateInstance](https://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6)).</span><span class="sxs-lookup"><span data-stu-id="85b7e-122">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](https://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6)).</span></span> <span data-ttu-id="85b7e-123">Portanto, o depurador deve armazenar em cache o resultado e solicitar uma nova instância somente quando os dados subjacentes podem ter sido alterado (ou seja, quando um [método LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) retorno de chamada é recebido).</span><span class="sxs-lookup"><span data-stu-id="85b7e-123">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="85b7e-124">Módulos dinâmicos não têm qualquer símbolos disponíveis até que o primeiro tipo foi carregado (conforme indicado pelo [método LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) retorno de chamada).</span><span class="sxs-lookup"><span data-stu-id="85b7e-124">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85b7e-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="85b7e-125">Requirements</span></span>  
 <span data-ttu-id="85b7e-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85b7e-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85b7e-127">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85b7e-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85b7e-128">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85b7e-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85b7e-129">**Versões do .NET framework:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="85b7e-129">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85b7e-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85b7e-130">See Also</span></span>  
 [<span data-ttu-id="85b7e-131">Interface ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="85b7e-131">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="85b7e-132">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="85b7e-132">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="85b7e-133">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="85b7e-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
