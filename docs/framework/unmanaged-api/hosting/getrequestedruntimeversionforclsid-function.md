---
title: Função GetRequestedRuntimeVersionForCLSID
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersionForCLSID
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersionForCLSID
helpviewer_keywords:
- GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4b4ac1a37c2b3506216499ed0c9f8194949b768
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985641"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>Função GetRequestedRuntimeVersionForCLSID
Obtém o common language runtime (CLR) versão informações apropriadas para a classe com especificado `CLSID`.  
  
 Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `rclsid`  
 [in]  O `CLSID` do componente.  
  
 `pVersion`  
 [out]  Um buffer que contém a cadeia de caracteres de número de versão após a conclusão bem-sucedida.  
  
 `cchBuffer`  
 [in]  O tamanho, em caracteres largos, da `pVersion` buffer.  
  
 `dwLength`  
 [out] O comprimento, em bytes, do buffer retornado.  
  
 `dwResolutionFlags`  
 [in]  Um dos valores CLSID_RESOLUTION_FLAGS. Há suporte para os seguintes valores:  
  
- CLSID_RESOLUTION_DEFAULT: (0x0) Especifica que o comportamento de interoperabilidade padrão deve ser usado.  
  
- CLSID_RESOLUTION_REGISTERED: (0x1) Especifica que o registro deve ser pesquisado e política de correção deve ser aplicada.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|A função retornou com êxito.|  
|E_INVALIDARG|Um dos parâmetros tem um tipo ou formato inválido.|  
|ERROR_INSUFFICIENT_BUFFER|O `pVersion` buffer não é grande o suficiente para manter a cadeia de caracteres de versão inteira.|  
|REGDB_E_CLASSNOTREG|Não há nenhuma classe registrada com o especificado `CLSID`.|  
|E_POINTER|`dwLength` é nulo, ou `cchBuffer` é grande o suficiente para manter a cadeia de caracteres de versão, mas `pVersion` é nulo.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
