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
ms.openlocfilehash: ccfe83707b6354c42a4c3c81e911918b2ea79ec4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942448"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a>Método ICorDebugModule3::CreateReaderForInMemorySymbols
Cria um leitor de símbolo de depuração para um módulo dinâmico.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a>Parâmetros  
 riid  
 [in] O IID da interface COM para retornar. Normalmente, esse é um [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).  
  
 ppObj  
 [out] Ponteiro para um ponteiro para a interface retornada.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 O leitor foi criado com êxito.  
  
 CORDBG_E_MODULE_LOADED_FROM_DISK  
 O módulo não é um módulo na memória ou dinâmico.  
  
 CORDBG_E_SYMBOLS_NOT_AVAILABLE  
 Símbolos não foram fornecidos pelo aplicativo, ou ainda não estão disponíveis.  
  
 E_FAIL (ou outros códigos de retorno e _)  
 Não é possível criar o leitor.  
  
## <a name="remarks"></a>Comentários  
 Esse método também pode ser usado para criar um objeto de leitor de símbolo para módulos de memória (não dinâmicos), mas somente depois que os símbolos primeiro estão disponíveis (indicado pelo [método UpdateModuleSymbols](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) retorno de chamada).  
  
 Esse método retorna uma nova instância de leitor toda vez que ele é chamado (como [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)). Portanto, o depurador deve armazenar em cache o resultado e solicitar uma nova instância somente quando os dados subjacentes podem ter sido alterado (ou seja, quando um [método LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) retorno de chamada é recebido).  
  
 Módulos dinâmicos não têm qualquer símbolos disponíveis até que o primeiro tipo foi carregado (conforme indicado pelo [método LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) retorno de chamada).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** 4.5, 4, 3.5 SP1  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugRemoteTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [Interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
