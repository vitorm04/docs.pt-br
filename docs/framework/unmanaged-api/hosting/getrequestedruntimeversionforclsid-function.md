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
ms.openlocfilehash: 6132e94544b30486b70ecfec49c1ddd5e3c0f50b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178110"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>Função GetRequestedRuntimeVersionForCLSID
Obtém as informações apropriadas da versão de tempo de `CLSID`execução do idioma comum (CLR) para a classe com a especificada .  
  
 Esta função foi depreciada no Quadro .NET 4.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,
    [out]  LPWSTR     pVersion,
    [in]  DWORD      cchBuffer,
    [out] DWORD*     dwLength,
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `rclsid`  
 [em]  O `CLSID` do componente.  
  
 `pVersion`  
 [fora]  Um buffer que contém a seqüência de números da versão após a conclusão bem sucedida.  
  
 `cchBuffer`  
 [em]  O tamanho, em caracteres `pVersion` largos, do buffer.  
  
 `dwLength`  
 [fora] O comprimento, em bytes, do tampão devolvido.  
  
 `dwResolutionFlags`  
 [em]  Um dos valores CLSID_RESOLUTION_FLAGS. Os valores a seguir têm suporte:  
  
- CLSID_RESOLUTION_DEFAULT: (0x0) Especifica que o comportamento de interop padrão deve ser usado.  
  
- CLSID_RESOLUTION_REGISTERED: (0x1) Especifica que o registro deve ser pesquisado e a política de shim deve ser aplicada.  
  
## <a name="return-value"></a>Valor retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|A função retornou com sucesso.|  
|E_INVALIDARG|Um dos parâmetros tem um tipo ou formato inválido.|  
|Error_insufficient_buffer|O `pVersion` buffer não é grande o suficiente para segurar toda a seqüência de versão.|  
|REGDB_E_CLASSNOTREG|Não há classe registrada com `CLSID`o especificado .|  
|E_POINTER|`dwLength`é nulo, ou `cchBuffer` é grande o `pVersion` suficiente para segurar a seqüência de versão, mas é nulo.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Funções de hospedagem CLR reprovadas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
