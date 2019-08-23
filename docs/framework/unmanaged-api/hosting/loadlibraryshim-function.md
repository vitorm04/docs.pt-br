---
title: Função LoadLibraryShim
ms.date: 03/30/2017
api_name:
- LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LoadLibraryShim
helpviewer_keywords:
- LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ab44ce8f51620d83084d1dd16e98b2b310feb76
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968931"
---
# <a name="loadlibraryshim-function"></a>Função LoadLibraryShim
Carrega uma versão especificada de uma DLL que está incluída no pacote redistribuível .NET Framework.  
  
 Essa função foi preterida no .NET Framework 4. Em vez disso, use o método [ICLRRuntimeInfo:: LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `szDllName`  
 no Uma cadeia de caracteres terminada em zero que representa o nome da DLL a ser carregada a partir da biblioteca de .NET Framework.  
  
 `szVersion`  
 no Uma cadeia de caracteres terminada em zero que representa a versão da DLL a ser carregada. Se `szVersion` for NULL, a versão selecionada para carregamento será a versão mais recente da DLL especificada menor que a versão 4. Ou seja, todas as versões iguais ou maiores que a versão 4 são ignoradas se `szVersion` for NULL e, se nenhuma versão anterior à versão 4 estiver instalada, a dll não será carregada. Isso é para garantir que a instalação do .NET Framework 4 não afete aplicativos ou componentes pré-existentes. Consulte a entrada [SxS e início rápido de migração](https://go.microsoft.com/fwlink/?LinkId=200329) no blog da equipe do CLR.  
  
 `pvReserved`  
 Reservado para uso futuro.  
  
 `phModDll`  
 fora Um ponteiro para o identificador do módulo.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna códigos de erro padrão de Component Object Model (COM), conforme definido no WinError. h, além dos valores a seguir.  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|CLR_E_SHIM_RUNTIMELOAD|O `szDllName` carregamento requer o carregamento do Common Language Runtime (CLR) e a versão necessária do CLR não pode ser carregada.|  
  
## <a name="remarks"></a>Comentários  
 Essa função é usada para carregar DLLs incluídas no pacote redistribuível .NET Framework. Ele não carrega DLLs geradas pelo usuário.  
  
> [!NOTE]
> A partir do .NET Framework versão 2,0, o carregamento de Fusion. dll faz com que o CLR seja carregado. Isso ocorre porque as funções em Fusion. dll agora são wrappers cujas implementações são fornecidas pelo tempo de execução.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
