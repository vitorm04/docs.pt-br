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
ms.openlocfilehash: 5fe1ba15f8a9f8ee79582158209049c1e502a61d
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44270823"
---
# <a name="loadlibraryshim-function"></a>Função LoadLibraryShim
Carrega uma versão especificada de uma DLL que está incluída no pacote redistribuível do .NET Framework.  
  
 Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Use o [iclrruntimeinfo:: LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) método em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `szDllName`  
 [in] Uma cadeia terminada em zero que representa o nome da DLL a ser carregado na biblioteca do .NET Framework.  
  
 `szVersion`  
 [in] Uma cadeia terminada em zero que representa a versão da DLL a ser carregado. Se `szVersion` for nula, a versão selecionada para o carregamento é a versão mais recente da DLL especificado que é inferior à versão 4. Ou seja, todas as versões iguais ou maiores que a versão 4 são ignoradas se `szVersion` for nulo, e se nenhuma versão menor do que a versão 4 está instalado, a DLL não será carregada. Isso é para garantir a instalação do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] não afeta componentes ou aplicativos já existentes. Consulte a entrada [in-proc SxS e o início rápido da migração](https://go.microsoft.com/fwlink/?LinkId=200329) no blog da equipe do CLR.  
  
 `pvReserved`  
 Reservado para uso futuro.  
  
 `phModDll`  
 [out] Um ponteiro para a alça do módulo.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna códigos de erro padrão (COM Component Object Model), conforme definido em Winerror. H, além dos valores a seguir.  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|CLR_E_SHIM_RUNTIMELOAD|Carregando `szDllName` requer o carregamento, o common language runtime (CLR) e a versão necessária do CLR não podem ser carregado.|  
  
## <a name="remarks"></a>Comentários  
 Essa função é usada para carregar as DLLs que são incluídas no pacote redistribuível do .NET Framework. Ele não carrega DLLs gerados pelo usuário.  
  
> [!NOTE]
>  Começando com o .NET Framework versão 2.0, carregar Fusion faz com que o CLR a ser carregado. Isso ocorre porque as funções em Fusion agora são wrappers cujas implementações são fornecidas pelo tempo de execução.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** mscoree. H  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
