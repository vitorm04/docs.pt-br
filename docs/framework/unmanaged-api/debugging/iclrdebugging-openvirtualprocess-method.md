---
title: "Método ICLRDebugging::OpenVirtualProcess"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRDebugging.OpenVirtualProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::OpenVirtualProcess
helpviewer_keywords:
- OpenVirtualProcess method [.NET Framework debugging]
- ICLRDebugging::OpenVirtualProcess method [.NET Framework debugging]
ms.assetid: e8ab7c41-d508-4ed9-8a31-ead072b5a314
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f1f71f42f10c3d25714998d1697b20a5ee13e055
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a>Método ICLRDebugging::OpenVirtualProcess
Obtém a interface ICorDebugProcess que corresponde a um módulo de runtime (CLR) de linguagem comum carregado no processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT OpenVirtualProcess(  
    [in] ULONG64 moduleBaseAddress,  
    [in] IUnknown * pDataTarget,  
    [in] ICLRDebuggingLibraryProvider * pLibraryProvider,  
    [in] CLR_DEBUGGING_VERSION * pMaxDebuggerSupportedVersion,  
    [in] REFIID riidProcess,  
    [out, iid_is(riidProcess)] IUnknown ** ppProcess,  
    [in, out] CLR_DEBUGGING_VERSION * pVersion,  
    [out] CLR_DEBUGGING_PROCESS_FLAGS * pdwFlags);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `moduleBaseAddress`  
 [in] O endereço base de um módulo no processo de destino. COR_E_NOT_CLR será retornado se o módulo especificado não é um módulo CLR.  
  
 `pDataTarget`  
 [in] Uma abstração de destino de dados que permite que o depurador gerenciado inspecionar o estado do processo. O depurador deve implementar o [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface. Você deve implementar o [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface para oferecer suporte a cenários em que o CLR que está sendo depurado não está instalado localmente no computador.  
  
 `pLibraryProvider`  
 [in] Uma interface de retorno de chamada de provedor de biblioteca que permite bibliotecas de depuração específicos da versão a ser localizada e carregada na demanda. Esse parâmetro é necessário somente se `ppProcess` ou `pFlags` não é `null`.  
  
 `pMaxDebuggerSupportedVersion`  
 [in] A versão mais recente do CLR que este depurador pode depurar. Você deve especificar major, minor e criar versões da mais recente versão do CLR este depurador dá suporte a e definir o número de revisão a 65535 para acomodar futuras CLR in-loco versões de manutenção.  
  
 `riidProcess`  
 [in] A ID da interface ICorDebugProcess para recuperar. Atualmente, os únicos valores aceitos são IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2 e IID_CORDEBUGPROCESS.  
  
 `ppProcess`  
 [out] Um ponteiro para a interface COM que é identificado pelo `riidProcess`.  
  
 `pVersion`  
 [out no] A versão do CLR. Na entrada, esse valor pode ser `null`. Ele também pode apontar para um [CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) estrutura, caso em que a estrutura `wStructVersion` campo deve ser inicializado como 0 (zero).  
  
 Na saída, retornada `CLR_DEBUGGING_VERSION` estrutura será preenchida com as informações de versão para o CLR.  
  
 `pdwFlags`  
 [out] Sinalizadores de informação sobre o tempo de execução especificado. Consulte o [CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) tópico para obter uma descrição dos sinalizadores.  
  
## <a name="return-value"></a>Valor de retorno  
 Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|E_POINTER|`pDataTarget` é `null`.|  
|CORDBG_E_LIBRARY_PROVIDER_ERROR|O [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) retorno de chamada retornará um erro ou não fornecer um identificador válido.|  
|CORDBG_E_MISSING_DATA_TARGET_INTERFACE|`pDataTarget`não implementa as interfaces de destino de dados necessários para esta versão do tempo de execução.|  
|CORDBG_E_NOT_CLR|O módulo indicado não é um módulo CLR. Esse HRESULT também é retornado quando um módulo CLR não pode ser detectado porque a memória está corrompida, o módulo não está disponível ou a versão CLR é posterior à versão de correção.|  
|CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL|Esta versão de tempo de execução não dá suporte a este modelo de depuração. Atualmente, o modelo de depuração não é suportado por versões CLR antes do [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. O `pwszVersion` parâmetro de saída ainda está definido para o valor correto depois deste erro.|  
|CORDBG_E_UNSUPPORTED_FORWARD_COMPAT|A versão do CLR é maior que a versão que esse depurador declarações para dar suporte. O `pwszVersion` parâmetro de saída ainda está definido para o valor correto depois deste erro.|  
|E_NO_INTERFACE|O `riidProcess` interface não está disponível.|  
|CORDBG_E_UNSUPPORTED_VERSION_STRUCT|O `CLR_DEBUGGING_VERSION` estrutura não tem um valor reconhecido para `wStructVersion`. O único valor aceito no momento é 0.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
