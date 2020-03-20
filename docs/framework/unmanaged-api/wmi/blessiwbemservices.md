---
title: Função BlessIWbemServices (referência de API não gerenciada)
description: A função BlessIWbemServices indica se as credenciais do usuário permitem acesso a uma classe IWbemServices.
ms.date: 11/06/2017
api_name:
- BlessIWbemServices
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServices
helpviewer_keywords:
- BlessIWbemServices function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 4b15af840cc00b3ec261604db4f3625c6b975d3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176858"
---
# <a name="blessiwbemservices-function"></a>Função BlessIWbemServices
Indica se as credenciais do usuário permitem acesso à classe [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) especificada.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT BlessIWbemServices (
   [in] IWbemServices* pIWbemServices,
   [in] BSTR strUser,
   [in] BSTR strPassword,
   [in] BSTR strAuthority,
   [in] DWORD impLevel,
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a>parâmetros

`pIWbemServices`\
[em] Um ponteiro para o objeto [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) para o qual as permissões são necessárias.

`strUser`\
[em] O nome do usuário.

`strPassword`\
[em] A senha `strUser`associada a .

`strAuthority`\
[em] O nome de domínio do usuário. Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.

`impLevel`\
[em] O nível de representação.

`authnLevel`\
[em] O nível de autorização.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WinError.h,* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | Um ou mais argumentos são inválidos. |
| `E_POINTER` | 0x80004003 | `pIWbemServices` é `null`. |
| `E_FAIL` | 0x80000008 | Ocorreu um erro não especificado. |
| `E_OUTOFMEMORY` | 0x80000002 | A memória insuficiente está disponível para realizar a operação. |
| `S_OK` | 0 | A chamada de função foi bem sucedida. |

## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Confira também

- [WMI e Contadores de Desempenho (Referência de API Não Gerenciada)](index.md)
