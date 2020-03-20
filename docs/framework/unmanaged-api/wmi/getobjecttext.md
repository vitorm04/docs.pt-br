---
title: Função GetObjectText (referência a API não gerenciada)
description: A função GetObjectText retorna uma renderização textual de um objeto na sintaxe MOF.
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
ms.openlocfilehash: 6881125760e0f1dc38e6b01917d5829edc95e3ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176780"
---
# <a name="getobjecttext-function"></a>Função GetObjectText
Retorna uma renderização textual do objeto na sintaxe MOF (Managed Object Format, formato de objeto gerenciado).

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

## <a name="parameters"></a>parâmetros

`vFunc`  
[em] Este parâmetro não é usado.

`ptr`  
[em] Um ponteiro para uma instância [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`lFlags`  
[em] Normalmente 0. Se `WBEM_FLAG_NO_FLAVORS` (ou 0x1) for especificado, as qualificações serão incluídas sem informações de propagação ou sabor.

`pstrObjectText`[fora] Um ponteiro `null` para uma entrada. No retorno, um `BSTR` recém-alocado que contém uma renderização de sintaxe MOF do objeto.  

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Houve um fracasso geral. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem sucedida.  |
  
## <a name="remarks"></a>Comentários

Esta função envolve uma chamada para o método [IWbemClassObject::GetObjectText.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext)

O texto mof retornado não contém todas as informações sobre o objeto, mas apenas informações suficientes para que o compilador MOF possa recriar o objeto original. Por exemplo, não estão incluídas qualificações propagadas ou propriedades de classe pai.

O seguinte algoritmo é usado para reconstruir o texto dos parâmetros de um método:

1. Os parâmetros são reseqüenciados na ordem de seus valores identificadores.
1. Parâmetros especificados `[in]` como `[out]` e combinados em um único parâmetro.

`pstrObjectText`deve ser um `null` ponteiro para um quando a função é chamada; ele não deve apontar para uma seqüência que é válida antes da chamada do método, porque o ponteiro não será desalocado.

## <a name="requirements"></a>Requisitos  
**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Confira também

- [WMI e Contadores de Desempenho (Referência de API Não Gerenciada)](index.md)
