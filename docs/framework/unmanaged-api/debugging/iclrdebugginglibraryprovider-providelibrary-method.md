---
title: Método ICLRDebuggingLibraryProvider::ProvideLibrary
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9cac9e00c8cb6a13e2acc62b5f314b7bc0cf9e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629106"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a>Método ICLRDebuggingLibraryProvider::ProvideLibrary
Obtém um provedor de biblioteca de interface de retorno de chamada que permite que o common language runtime (CLR) específicos da versão bibliotecas de depuração ser localizada e carregada sob demanda.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ProvideLibrary(  
     [in] const WCHAR* pwszFileName,  
     [in] DWORD dwTimestamp,  
     [in] DWORD dwSizeOfImage,  
     [out] HMODULE* hModule);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pwszFilename`  
 [in] O nome do módulo que está sendo solicitado.  
  
 `dwTimestamp`  
 [in] O carimbo de data armazenado no cabeçalho COFF arquivo dos arquivos PE.  
  
 `pLibraryProvider`  
 [in] O `SizeOfImage` campo armazenado no cabeçalho COFF opcional de arquivo dos arquivos PE.  
  
 `hModule`  
 [out] O identificador para o módulo solicitado.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 `ProvideLibrary` permite que o depurador fornece módulos que são necessários para a depuração de arquivos específicos do CLR como mscordbi e Mscordacwks. Os identificadores de módulo precisam permanecer válida até uma chamada para o [iclrdebugging:: Canunloadnow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) método indica que eles podem ser liberados, ponto em que é responsabilidade do chamador liberar os identificadores.  
  
 O depurador pode usar qualquer meio disponível para localizar ou adquirir o módulo de depuração.  
  
> [!IMPORTANT]
>  Esse recurso permite que o chamador de API fornecer os módulos que contêm código executável e possivelmente mal-intencionado. Como uma precaução de segurança, o chamador não deve usar `ProvideLibrary` para distribuir qualquer código que não está disposto a executar em si.  
>   
>  Se um problema de segurança grave for detectado em uma biblioteca já lançada, como mscordbi ou Mscordacwks, o shim pode ser corrigido para reconhecer as versões incorretas dos arquivos. O shim pode emitir solicitações para as versões com aplicações de patches dos arquivos e rejeitar as versões ruins se eles são fornecidos em resposta a qualquer solicitação. Isso pode ocorrer somente se o usuário foi corrigida para uma nova versão do shim. Versões sem patch permanecerá vulneráveis.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
