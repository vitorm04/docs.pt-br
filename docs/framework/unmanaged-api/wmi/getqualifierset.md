---
title: Função GetQualifierSet (referência de API não gerenciada)
description: A função GetQualifierSet recupera o conjunto de qualificação para uma classe ou instância.
ms.date: 11/06/2017
api_name:
- GetQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetQualifierSet
helpviewer_keywords:
- GetQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 368f0a13871bd48780fa30b370d37157d2724bb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176767"
---
# <a name="getqualifierset-function"></a>Função GetQualifierSet
Recupera o qualificador definido para uma instância da classe ou uma definição de classe.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [out] IWbemQualifierSet  **ppQualSet
);
```  

## <a name="parameters"></a>parâmetros

`vFunc`  
[em] Este parâmetro não é usado.

`ptr`  
[em] Um ponteiro para uma instância [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`ppQualSet`  
[fora] Recebe o ponteiro de interface que permite o acesso aos qualificadores do objeto de classe. `ppQualSet` não pode ser `null`. Se ocorrer um erro, um novo objeto não será devolvido e o ponteiro não será modificado.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Houve um fracasso geral. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | O método especificado não existe. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro `null`é. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem sucedida.  |
  
## <a name="remarks"></a>Comentários

Esta função envolve uma chamada para o método [IWbemClassObject::GetQualifierSet.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset)

O [ponteiro IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) permite que o chamador adicione, edite ou exclua esses qualificadores. Tais qualificações adicionadas, editadas ou excluídas aplicam-se a toda a instância ou definição de classe.

## <a name="requirements"></a>Requisitos  
**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Confira também

- [WMI e Contadores de Desempenho (Referência de API Não Gerenciada)](index.md)
