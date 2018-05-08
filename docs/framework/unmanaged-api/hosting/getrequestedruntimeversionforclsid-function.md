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
ms.openlocfilehash: e8d3a7168ce0ee3484384ae0e2d10ca00367fc9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="getrequestedruntimeversionforclsid-function"></a>Função GetRequestedRuntimeVersionForCLSID
Obtém as comuns language runtime (CLR) versão informações apropriadas para a classe com especificado `CLSID`.  
  
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
  
#### <a name="parameters"></a>Parâmetros  
 `rclsid`  
 [in]  O `CLSID` do componente.  
  
 `pVersion`  
 [out]  Um buffer que contém a cadeia de caracteres de número de versão após a conclusão bem-sucedida.  
  
 `cchBuffer`  
 [in]  O tamanho, em caracteres largos, do `pVersion` buffer.  
  
 `dwLength`  
 [out] O comprimento, em bytes, do buffer retornado.  
  
 `dwResolutionFlags`  
 [in]  Um dos valores CLSID_RESOLUTION_FLAGS. Há suporte para os seguintes valores:  
  
-   CLSID_RESOLUTION_DEFAULT: (0x0) Especifica o comportamento padrão interoperabilidade deve ser usado.  
  
-   CLSID_RESOLUTION_REGISTERED: (0x1) Especifica que o registro deve ser pesquisado e corrigir a política deve ser aplicada.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|A função retornou com êxito.|  
|E_INVALIDARG|Um dos parâmetros tem um formato ou tipo inválido.|  
|ERROR_INSUFFICIENT_BUFFER|O `pVersion` buffer não é grande o suficiente para manter a cadeia de caracteres de versão.|  
|REGDB_E_CLASSNOTREG|Não há nenhuma classe registrada com o `CLSID`.|  
|E_POINTER|`dwLength` é nulo, ou `cchBuffer` é grande o suficiente para manter a cadeia de caracteres de versão, mas `pVersion` é nulo.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
