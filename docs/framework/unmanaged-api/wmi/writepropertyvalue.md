---
title: Função WritePropertyValue (referência de API não gerenciada)
description: A função WritePropertyValue grava bytes em uma propriedade.
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a98103367f497b18f9b8fbd61a37abf9816b8356
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107933"
---
# <a name="writepropertyvalue-function"></a>Função WritePropertyValue
Grava um número especificado de bytes em uma propriedade identificada por um identificador de propriedade.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`  
[in] Esse parâmetro é usado.

`ptr`  
[in] Um ponteiro para um [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instância.

`lHandle`  
[in] Um inteiro que contém o identificador que identifica esta propriedade. O identificador pode ser recuperado chamando o [GetPropertyHandle](getpropertyhandle.md) função.   

`lNumBytes`  
[in] O número de bytes que está sendo gravado na propriedade. Consulte a [comentários](#remarks) seção para obter mais informações.

`pHandle`   
[out] Um ponteiro para a matriz de bytes que contém os dados.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | Ocorreu uma incompatibilidade de tipo. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) método.

Use essa função para definir a cadeia de caracteres e todos os outros não -`DWORD` ou não-`QWORD` dados.

Para valores de propriedade não cadeia de caracteres, `lNumBytes` deve ser o tamanho dos dados corretos do tipo de propriedade especificado. Para valores de propriedade de cadeia de caracteres, `lNumBytes` deve ser o comprimento da cadeia de caracteres especificada em bytes e a cadeia de caracteres em si deve ser de um mesmo comprimento em bytes e ser seguida por um caractere nulo de terminação.

## <a name="requirements"></a>Requisitos  
**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
