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
ms.openlocfilehash: b0644258eb1622f388f55d0657c8922079fe4dc1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407217"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a>Método ICLRDebuggingLibraryProvider::ProvideLibrary
Obtém um provedor de biblioteca de interface de retorno de chamada que permite common language runtime (CLR) específicos da versão depuração bibliotecas de ser localizada e carregada na demanda.  
  
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
 [in] O carimbo de hora de data armazenado no cabeçalho do arquivo COFF dos arquivos PE.  
  
 `pLibraryProvider`  
 [in] O `SizeOfImage` campo armazenado no cabeçalho COFF opcional de arquivo dos arquivos PE.  
  
 `hModule`  
 [out] O identificador para o módulo solicitado.  
  
## <a name="return-value"></a>Valor de retorno  
 Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 `ProvideLibrary` permite que o depurador fornecer os módulos que são necessários para a depuração de arquivos específicos do CLR como mscordbi.dll e qual mscordacwks.dll. Os identificadores de módulo precisam permanecer válida até uma chamada para o [: Canunloadnow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) método indica que eles podem ser liberados, no ponto em que é de responsabilidade do chamador para liberar os identificadores.  
  
 O depurador pode usar qualquer meio disponível para localizar ou adquirir o módulo de depuração.  
  
> [!IMPORTANT]
>  Esse recurso permite que o chamador de API fornecer os módulos que contêm código executável e possivelmente mal-intencionados. Como uma precaução de segurança, o chamador não deve usar `ProvideLibrary` para distribuir qualquer código que não está disposto a execute em si.  
>   
>  Se for detectado um problema sério de segurança em uma biblioteca já lançada, como mscordbi.dll ou qual mscordacwks.dll, a correção poderá ser corrigida para reconhecer as versões incorretas dos arquivos. O shim pode emitir solicitações para as versões com patch dos arquivos e rejeitar as versões incorretas se eles são fornecidos em resposta a qualquer solicitação. Isso pode ocorrer somente se o usuário tem o patch para uma nova versão do shim. Versões sem patch permanecerá vulneráveis.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
