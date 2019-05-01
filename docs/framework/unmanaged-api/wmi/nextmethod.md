---
title: Função NextMethod (referência de API não gerenciada)
description: A função NextMethod recupera o próximo método em uma enumeração.
ms.date: 11/06/2017
api_name:
- NextMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- NextMethod
helpviewer_keywords:
- NextMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b3667f7371131a4c1394ba5ca619d1f605c89ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000175"
---
# <a name="nextmethod-function"></a>Função NextMethod
Recupera o próximo método em uma enumeração que começa com uma chamada para [BeginMethodEnumeration](beginmethodenumeration.md).  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT NextMethod (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature   
); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`  
[in] Esse parâmetro é usado.

`ptr`  
[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.

`lFlags`  
[in] Reservado. Esse parâmetro deve ser 0.

`pName`  
[out] Um ponteiro que aponta para `null` antes da chamada. Quando a função retornar, o endereço de um novo `BSTR` que contém o nome do método. 

`ppSignatureIn`  
[out] Um ponteiro que recebe um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) que contém o `in` parâmetros para o método. 

`ppSignatureOut`  
[out] Um ponteiro que recebe um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) que contém o `out` parâmetros para o método. 

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101d | Não houve nenhuma chamada para o [ `BeginEnumeration` ](beginenumeration.md) função. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Não há nenhum mais propriedades na enumeração. |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) método.

O chamador inicia a sequência de enumeração por meio da chamada a [BeginMethodEnumeration](beginmethodenumeration.md) de função e, em seguida, chama a função [NextMethod] até que a função retorna `WBEM_S_NO_MORE_DATA`. Opcionalmente, o chamador conclui a sequência chamando [EndMethodEnumeration](endmethodenumeration.md). O chamador pode encerrar a enumeração no início, chamando [EndMethodEnumeration](endmethodenumeration.md) a qualquer momento.

## <a name="example"></a>Exemplo

Para obter um exemplo de C++, consulte a [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) método.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
