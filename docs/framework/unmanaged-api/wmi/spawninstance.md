---
title: Função SpawnInstance (referência de API não gerenciada)
description: A função SpawnInstance cria uma nova instância de uma classe.
ms.date: 11/06/2017
api_name:
- SpawnInstance
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnInstance
helpviewer_keywords:
- SpawnInstance function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: a15eb8123c1ee807444bdb4c6fe71cdccc08f434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176715"
---
# <a name="spawninstance-function"></a>Função SpawnInstance
Cria uma nova instância de uma classe.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SpawnInstance (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance);
```  

## <a name="parameters"></a>parâmetros

`vFunc`  
[em] Este parâmetro não é usado.

`ptr`  
[em] Um ponteiro para uma instância [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`lFlags`  
[in] Reservado. Este parâmetro deve ser 0.

`ppNewInstance`  
[fora] Recebe o ponteiro para a nova instância da classe. Se ocorrer um erro, um novo objeto `ppNewInstance` não será devolvido e não será modificado.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | `ptr`não é uma definição de classe válida e não pode gerar novas instâncias. Ou ele está incompleto ou não foi registrado no Windows Management ligando para [PutClassWmi](putclasswmi.md). |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` é `null`. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem sucedida.  |
  
## <a name="remarks"></a>Comentários

Esta função envolve uma chamada para o método [IWbemClassObject::SpawnInstance.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance)

`ptr`deve ser uma definição de classe obtida do Windows Management. (Observe que a desova de uma instância de uma instância é suportada, mas a instância retornada está vazia.) Em seguida, use essa definição de classe para criar novas instâncias. Uma chamada para a função [PutInstanceWmi](putinstancewmi.md) é necessária se você pretende escrever a instância para o Gerenciamento do Windows.

O novo objeto `ppNewClass` retornado automaticamente torna-se uma subclasse do objeto atual. Esse comportamento não pode ser anulado. Não há outro método pelo qual subclasses (classes derivadas) possam ser criadas.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Confira também

- [WMI e Contadores de Desempenho (Referência de API Não Gerenciada)](index.md)
