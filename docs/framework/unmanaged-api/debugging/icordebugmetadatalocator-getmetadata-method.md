---
title: Método ICorDebugMetaDataLocator::GetMetaData
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator.GetMetaData
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator::GetMetaData
helpviewer_keywords:
- ICorDebugMetaDataLocator::GetMetaData method [.NET Framework debugging]
- GetMetaData method, ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: f9b0ff22-54db-45eb-9cc3-508000a3141d
topic_type:
- apiref
ms.openlocfilehash: 6e4f11de423d1ab6b66aca40e671607a383a4413
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136628"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a>Método ICorDebugMetaDataLocator::GetMetaData
Solicita que o depurador retorne o caminho completo para um módulo cujos metadados são necessários para concluir uma operação solicitada pelo depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMetaData(  
      [in] LPCWSTR wszImagePath,  
      [in] DWORD   dwImageTimeStamp,  
      [in] DWORD   dwImageSize,  
      [in] ULONG32 cchPathBuffer,  
      [out] ULONG32 * pcchPathBuffer,  
      [out, size_is(cchPathBuffer), length_is(*pcchPathBuffer)]  
               WCHAR wszPathBuffer[]  
      );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `wszImagePath`  
 no Uma cadeia de caracteres terminada em nulo que representa o caminho completo para o arquivo. Se o caminho completo não estiver disponível, o nome e a extensão do arquivo (*filename*. *extensão*).  
  
 `dwImageTimeStamp`  
 no O carimbo de data/hora dos cabeçalhos de arquivo PE da imagem. Esse parâmetro pode potencialmente ser usado para uma pesquisa de servidor de símbolo ([symsrv](/windows/desktop/debug/using-symsrv)).  
  
 `dwImageSize`  
 no O tamanho da imagem dos cabeçalhos de arquivo PE. Esse parâmetro pode potencialmente ser usado para uma pesquisa SymSrv.  
  
 `cchPathBuffer`  
 no A contagem de caracteres em `wszPathBuffer`.  
  
 `pcchPathBuffer`  
 fora A contagem de `WCHAR`s gravados em `wszPathBuffer`.  
  
 Se o método retornar E_NOT_SUFFICIENT_BUFFER, conterá a contagem de `WCHAR`s necessários para armazenar o caminho.  
  
 `wszPathBuffer`  
 fora Ponteiro para um buffer no qual o depurador irá copiar o caminho completo do arquivo que contém os metadados solicitados.  
  
 O sinalizador de `ofReadOnly` da enumeração [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) é usado para solicitar acesso somente leitura aos metadados nesse arquivo.  
  
## <a name="return-value"></a>Valor retornado  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método. Todos os outros HRESULTs de falha indicam que o arquivo não é recuperável.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito. `wszPathBuffer` contém o caminho completo para o arquivo e é encerrado em nulo.|  
|E_NOT_SUFFICIENT_BUFFER|O tamanho atual de `wszPathBuffer` não é suficiente para manter o caminho completo. Nesse caso, `pcchPathBuffer` contém a contagem necessária de `WCHAR`s, incluindo o caractere nulo de terminação e `GetMetaData` é chamado uma segunda vez com o tamanho do buffer solicitado.|  
  
## <a name="remarks"></a>Comentários  
 Se `wszImagePath` contiver um caminho completo para um módulo de um despejo, ele especificará o caminho do computador em que o despejo foi coletado. O arquivo pode não existir neste local ou um arquivo incorreto com o mesmo nome pode ser armazenado no caminho.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugThread4](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
