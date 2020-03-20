---
title: QualifierSet_Next função (referência de API não gerenciada)
description: A função QualifierSet_Next recupera o próximo qualificador em uma enumeração.
ms.date: 11/06/2017
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: d3702426bc409d601ccfc6b7a8e93e8d9729c64e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174869"
---
# <a name="qualifierset_next-function"></a>Função QualifierSet_Next
Recupera o próximo qualificador em uma enumeração que começou com uma chamada para a função [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT QualifierSet_Next (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor
);
```  

## <a name="parameters"></a>parâmetros

`vFunc`[em] Este parâmetro não é usado.

`ptr`[em] Um ponteiro para uma instância [IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)

`lFlags`[em] Reservados. Este parâmetro deve ser 0.

`pstrName`[fora] O nome da qualificatória. Se `null`, este parâmetro é ignorado; caso contrário, `pstrName` não deve `BSTR` apontar para um vazamento válido ou de memória. Se não for nula, a `BSTR` função `WBEM_S_NO_ERROR`sempre aloca um novo quando retorna .

`pVal`[fora] Quando bem sucedido, o valor para o qualificador. Se a função `VARIANT` falhar, `pVal` o apontado por não é modificado. Se este parâmetro `null`for, o parâmetro é ignorado.

`plFlavor`[fora] Um ponteiro para um LONG que recebe o sabor qualificado. Se a informação do sabor não for `null`desejada, este parâmetro pode ser .

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | O interlocutor não [ligou para QualifierSet_BeginEnumeration.](qualifierset-beginenumeration.md) |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória suficiente disponível para começar uma nova enumeração. |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Não restam mais qualificações na enumeração. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem sucedida.  |
  
## <a name="remarks"></a>Comentários

Esta função envolve uma chamada para o [método IWbemQualifierSet:::Next.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next)

Você chama `QualifierSet_Next` a função repetidamente para enumerar todas `WBEM_S_NO_MORE_DATA`as qualificações até que a função retorne . Para encerrar a enumeração mais cedo, chame a função [QualifierSet_EndEnumeration.](qualifierset-endenumeration.md)

A ordem das qualificatórias devolvidas durante a enumeração é indefinida.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Confira também

- [WMI e Contadores de Desempenho (Referência de API Não Gerenciada)](index.md)
