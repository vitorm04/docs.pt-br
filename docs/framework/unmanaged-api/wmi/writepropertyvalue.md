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
ms.openlocfilehash: f02fb3877d55e9f47384b281573202712c29c606
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107296"
---
# <a name="writepropertyvalue-function"></a>Função WritePropertyValue
Grava um número especificado de bytes em uma propriedade identificada por um identificador de propriedade.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
no Este parâmetro não é usado.

`ptr`  
no Um ponteiro para uma instância de [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) .

`lHandle`  
no Um inteiro que contém o identificador que identifica essa propriedade. O identificador pode ser recuperado chamando a função [GetPropertyHandle](getpropertyhandle.md) .   

`lNumBytes`  
no O número de bytes que estão sendo gravados na propriedade. Consulte a seção [comentários](#remarks) para obter mais informações.

`pHandle`   
fora Um ponteiro para a matriz de bytes que contém os dados.

## <a name="return-value"></a>Valor retornado

Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | Ocorreu uma incompatibilidade de tipo. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o método [IWbemClassObject:: WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) .

Use essa função para definir cadeia de caracteres e todos os outros dados não`DWORD` ou não`QWORD`.

Para valores de propriedade que não são de cadeia de caracteres, `lNumBytes` deve ser o tamanho de dados correto do tipo de propriedade especificado. Para valores de propriedade de cadeia de caracteres, `lNumBytes` deve ser o comprimento da cadeia de caracteres especificada em bytes, e a cadeia de caracteres deve ser de um comprimento par em bytes e ser seguida de um caractere de terminação nula.

## <a name="requirements"></a>Requisitos  
**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils. idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
