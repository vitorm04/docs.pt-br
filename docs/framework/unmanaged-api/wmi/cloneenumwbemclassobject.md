---
title: Função CloneEnumWbemClassObject (referência de API não gerenciada)
description: A função CloneEnumWbemClassObject faz uma cópia lógica de um enumerador.
ms.date: 11/06/2017
api_name:
- CloneEnumWbemClassObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CloneEnumWbemClassObject
helpviewer_keywords:
- CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: f2a3a7e848108e50c04f0ec70cf42586755a0a88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175012"
---
# <a name="cloneenumwbemclassobject-function"></a>Função CloneEnumWbemClassObject
Faz uma cópia lógica de um enumerador, mantendo sua posição atual em uma enumeração.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum,
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject,
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority
);
```

## <a name="parameters"></a>parâmetros

`ppEnum`\
[fora] Recebe um ponteiro para um novo [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).

`authLevel`\
[em] O nível de autorização.

`impLevel`\
[em] O nível de representação.

`pCurrentEnumWbemClassObject`\
[fora] Um ponteiro para a ocorrência [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) a ser clonado.

`strUser`\
[em] O nome do usuário. Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.

`strPassword`\
[em] A senha. Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.

`strAuthority`\
[em] O nome de domínio do usuário. Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Houve um fracasso geral. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro é inválido. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória suficiente para completar a operação. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | O link de chamada de procedimento remoto (RPC) entre o processo atual e o WMI falhou. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem sucedida.  |

## <a name="remarks"></a>Comentários

Esta função envolve uma chamada para o [método IEnumWbemClassObject::Clone.](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone)

Este método faz apenas uma cópia de "melhor esforço". Devido à natureza dinâmica de muitos objetos CIM, é possível que o novo enumerador não enumera o mesmo conjunto de objetos que o enumerador de origem.

Se a chamada de função falhar, você pode obter informações adicionais de erro ligando para a função [GetErrorInfo.](geterrorinfo.md)

## <a name="example"></a>Exemplo

Por exemplo, consulte o método [IEnumWbemClassObject::Clone.](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone)

## <a name="requirements"></a>Requisitos
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

 **Cabeçalho:** WMINet_Utils.idl

 **.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Confira também

- [WMI e Contadores de Desempenho (Referência de API Não Gerenciada)](index.md)
