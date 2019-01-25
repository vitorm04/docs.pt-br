---
title: Função BlessIWbemServicesObject (referência de API não gerenciada)
description: A função BlessIWbemServicesObject indica se as credenciais de usuário permitirem o acesso a um objeto IWbemServices
ms.date: 11/06/2017
api_name:
- BlessIWbemServicesObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServicesObject
helpviewer_keywords:
- BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a561c5af868968624ee9ee81050d87b17c4591be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624412"
---
# <a name="blessiwbemservicesobject-function"></a>Função BlessIWbemServicesObject
Indica se as credenciais de usuário permitirem o acesso a determinado [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objeto.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a>Parâmetros

`pIWbemServices`  
[in] Um ponteiro para um objeto de serviço do WMI.

`strUser`  
[in] O nome de usuário.

`strPassword`  
[in] A senha associada `strUser`.

`strAuthority` [in] O nome de domínio do usuário. Consulte a [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.

`impLevel` [in] O nível de representação.

`authnLevel` [in] O nível de autorização.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos na *Winerror. H* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | Um ou mais argumentos são inválidos. |
| `E_POINTER` | 0x80004003 | `pIWbemServices` é `null`. | 
| `E_FAIL` | 0x80000008 | Ocorreu um erro não especificado. |
| `E_OUTOFMEMORY` | 0x80000002 | Memória disponível é insuficiente para executar a operação. | 
| `S_OK` | 0 | A chamada de função foi bem-sucedida. | 

## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também
- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
