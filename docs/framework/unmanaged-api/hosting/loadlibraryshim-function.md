---
title: "Função LoadLibraryShim"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5b8fe8413d0eff332e60508a083f03574e58d7bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="loadlibraryshim-function"></a>Função LoadLibraryShim
Carrega uma versão especificada de uma DLL que está incluída no pacote redistribuível do .NET Framework.  
  
 Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Use o [Iclrruntimeinfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) método em vez disso.  
  
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
 [in] Uma cadeia terminada em zero que representa o nome da DLL seja carregado da biblioteca do .NET Framework.  
  
 `szVersion`  
 [in] Uma cadeia terminada em zero que representa a versão da DLL a ser carregado. Se `szVersion` for null, a versão selecionada para carregamento é a versão mais recente da DLL especificado que é inferior à versão 4. Ou seja, todas as versões iguais ou maiores que a versão 4 são ignoradas se `szVersion` for null, e se nenhuma versão inferior a versão 4 está instalado, a DLL Falha ao carregar. Isso é para garantir a instalação do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] não afeta os aplicativos já existentes ou componentes. Consulte a entrada [SxS em processo e o início rápido da migração](http://go.microsoft.com/fwlink/?LinkId=200329) no blog da equipe do CLR.  
  
 `pvReserved`  
 Reservado para uso futuro.  
  
 `phModDll`  
 [out] Um ponteiro para o identificador do módulo.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna códigos de erro do modelo de objeto de componente (COM) padrão, conforme definido no Winerror. H, além dos valores a seguir.  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|CLR_E_SHIM_RUNTIMELOAD|Carregando `szDllName` requer o carregamento não não possível carregar o common language runtime (CLR) e a versão necessária do CLR.|  
  
## <a name="remarks"></a>Comentários  
 Essa função é usada para carregar DLLs que são incluídos no pacote redistribuível do .NET Framework. Ele não carregar DLLs geradas pelo usuário.  
  
> [!NOTE]
>  Começando com o .NET Framework versão 2.0, carregar Fusion faz com que o CLR a ser carregado. Isso ocorre porque as funções em Fusion agora são wrappers cujas implementações são fornecidas pelo tempo de execução.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
