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
ms.openlocfilehash: 4a950beef2e9bf8c0230d6a38008d75f89373410
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174830"
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

## <a name="parameters"></a>parâmetros

`vFunc`  
[em] Este parâmetro não é usado.

`ptr`  
[em] Um ponteiro para uma instância [IWbemObjectAccess.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess)

`lHandle`  
[em] Um inteiro que contém a alça que identifica esta propriedade. A alça pode ser recuperada chamando a função [GetPropertyHandle.](getpropertyhandle.md)

`lNumBytes`  
[em] O número de bytes sendo escritos para a propriedade. Consulte a seção [Observações](#remarks) para obter mais informações.

`pHandle`[fora] Um ponteiro para a matriz de bytes que contém os dados.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | Ocorreu uma incompatibilidade de tipo. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem sucedida.  |
  
## <a name="remarks"></a>Comentários

Esta função envolve uma chamada para o método [IWbemClassObject::WritePropertyValue.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue)

Use esta função para definir string`DWORD` e`QWORD` todos os outros dados não ou não.

Para valores de `lNumBytes` propriedade não string, deve ser o tamanho correto dos dados do tipo de propriedade especificado. Para valores `lNumBytes` de propriedade de seqüência, deve ser o comprimento da seqüência especificada em bytes, e a seqüência em si deve ser de um comprimento uniforme em bytes e ser seguida com um caractere de rescisão nula.

## <a name="requirements"></a>Requisitos  
**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Confira também

- [WMI e Contadores de Desempenho (Referência de API Não Gerenciada)](index.md)
