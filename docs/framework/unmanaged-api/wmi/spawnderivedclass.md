---
title: Função SpawnDerivedClass (referência de API não gerenciada)
description: A função SpawnDerivedClass cria um novo objeto que deriva de um objeto.
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: e9784f8a024c788823dc702794b2b86eea1827bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174843"
---
# <a name="spawnderivedclass-function"></a>Função SpawnDerivedClass
Cria um objeto de classe derivada recentemente por meio de um objeto especificado.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass);
```  

## <a name="parameters"></a>parâmetros

`vFunc`  
[em] Este parâmetro não é usado.

`ptr`  
[em] Um ponteiro para uma instância [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`lFlags`  
[in] Reservado. Este parâmetro deve ser 0.

`ppNewClass`  
[fora] Recebe o ponteiro para o novo objeto de definição de classe. Se ocorrer um erro, um novo objeto `ppNewClass` não será devolvido e não será modificado. Seu valor `null`não pode ser.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Houve um fracasso geral. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Uma operação inválida, como a desova de uma classe de uma instância, foi solicitada. |
| `WBEM_E_INCOMPLETE_CLASS` | A classe de origem não foi completamente definida ou registrada no Windows Management, portanto, uma nova classe derivada não é permitida. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` é `null`. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem sucedida.  |
  
## <a name="remarks"></a>Comentários

Esta função envolve uma chamada para o método [IWbemClassObject::SpawnDerivedClass.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone)

`ptr`deve ser uma definição de classe que se torna a classe pai do objeto gerado. O objeto retornado torna-se uma subclasse do objeto atual.

O novo objeto `ppNewClass` retornado automaticamente torna-se uma subclasse do objeto atual. Esse comportamento não pode ser anulado. Não há outro método pelo qual subclasses (classes derivadas) possam ser criadas.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Confira também

- [WMI e Contadores de Desempenho (Referência de API Não Gerenciada)](index.md)
