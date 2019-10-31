---
title: Função GetObjectText (referência de API não gerenciada)
description: A função GetObjectText retorna uma renderização textual de um objeto na sintaxe do MOF.
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 412e1ad503fa0e0b4f813298c0ac96ae80098c06
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102461"
---
# <a name="getobjecttext-function"></a>Função GetObjectText
Retorna uma renderização textual do objeto na sintaxe Managed Object Format (MOF).

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`  
no Este parâmetro não é usado.

`ptr`  
no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`lFlags`  
no Normalmente 0. Se `WBEM_FLAG_NO_FLAVORS` (ou 0x1) for especificado, os qualificadores serão incluídos sem informações de propagação ou de tipo.

`pstrObjectText`   
fora Um ponteiro para um `null` na entrada. No retorno, uma `BSTR` alocada recentemente que contém uma renderização de sintaxe do MOF do objeto.  

## <a name="return-value"></a>Valor retornado

Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Houve uma falha geral. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o método [IWbemClassObject:: GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) .

O texto MOF retornado não contém todas as informações sobre o objeto, mas apenas informações suficientes para o compilador MOF serem capazes de recriar o objeto original. Por exemplo, nenhum qualificador propagado ou propriedades de classe pai são incluídos.

O algoritmo a seguir é usado para reconstruir o texto dos parâmetros de um método:

1. Os parâmetros são resequenciados na ordem de seus valores de identificador.
1. Parâmetros que são especificados como `[in]` e `[out]` são combinados em um único parâmetro.
 
`pstrObjectText` deve ser um ponteiro para um `null` quando a função é chamada; Ele não deve apontar para uma cadeia de caracteres que seja válida antes da chamada do método, pois o ponteiro não será desalocado.

## <a name="requirements"></a>Requisitos  
**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils. idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
