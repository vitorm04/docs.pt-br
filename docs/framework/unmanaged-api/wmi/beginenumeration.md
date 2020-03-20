---
title: Função startEnumeration (referência de API não gerenciada)
description: A função StartEnumeration redefine um enumerador para o início da enumeração
ms.date: 11/06/2017
api_name:
- BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginEnumeration
helpviewer_keywords:
- BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: eac23916bd78ec3970a87566e2d2f4d79b379824
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176871"
---
# <a name="beginenumeration-function"></a>Função BeginEnumeration
Redefine um enumerador de volta ao início da enumeração.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a>parâmetros

`vFunc`\
[em] Este parâmetro não é usado.

`ptr`\
[em] Um ponteiro para uma instância [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`lEnumFlags`\
[em] Uma combinação bitwise dos sinalizadores ou valores descritos na seção Observações que [controla](#remarks) as propriedades incluídas na enumeração.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | A combinação de `lEnumFlags` sinalizadores em é inválida, ou um argumento inválido foi especificado. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Uma segunda `BeginEnumeration` chamada foi feita sem [`EndEnumeration`](endenumeration.md)uma chamada intervindo para . |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória suficiente disponível para começar uma nova enumeração. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem sucedida.  |
  
## <a name="remarks"></a>Comentários

Esta função envolve uma chamada para o [método IWbemClassObject::BeginEnumeration.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

As bandeiras que podem `lEnumFlags` ser passadas à medida que o argumento são definidas no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-las como constantes em seu código.  Você pode combinar uma bandeira de cada grupo com qualquer bandeira de qualquer outro grupo. No entanto, bandeiras do mesmo grupo são mutuamente exclusivas.

**Grupo 1**

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Inclua propriedades que constituem apenas a chave. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Inclua propriedades que são apenas referências de objeto. |

**Grupo 2**

Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Limitar a enumeração apenas às propriedades do sistema. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Inclua propriedades locais e propagadas, mas exclua propriedades do sistema da enumeração. |

Para aulas:

Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | Limitar a enumeração a propriedades substituídas na definição da classe. |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | Limitar a enumeração a propriedades substituídas na definição de classe atual e a novas propriedades definidas na classe. |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | Uma máscara (em vez de um `lEnumFlags` sinalizador) para `WBEM_FLAG_CLASS_OVERRIDES_ONLY` `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` aplicar contra um valor para verificar se está ou está definido. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Limitar a enumeração a propriedades definidas ou modificadas na própria classe. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Limitar a enumeração a propriedades herdadas das classes básicas. |

Para exemplos:

Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Limitar a enumeração a propriedades definidas ou modificadas na própria classe. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Limitar a enumeração a propriedades herdadas das classes básicas. |

## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Confira também

- [WMI e Contadores de Desempenho (Referência de API Não Gerenciada)](index.md)
