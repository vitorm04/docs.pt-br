---
title: "Função BlessIWbemServices (referência de API não gerenciada)"
description: "A função BlessIWbemServices indica se as credenciais do usuário permitirem o acesso a uma classe IWbemServices."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
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
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f384e8d045dd7a6f2f864f0991f8caf4a674408b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="blessiwbemservices-function"></a>Função BlessIWbemServices
Indica se as credenciais do usuário permitirem o acesso a especificado [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) classe.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT BlessIWbemServices (
   [in] IWbemServices* pIWbemServices,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a>Parâmetros

`pIWbemServices`  
[in] Um ponteiro para o [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) para o qual são necessárias permissões de objeto.

`strUser`  
[in] O nome de usuário.

`strPassword`  
[in] A senha associada com `strUser`.

`strAuthority`[in] O nome de domínio do usuário. Consulte o [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.

`impLevel`[in] O nível de representação.

`authnLevel`[in] O nível de autorização.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos no *Winerror. H* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | Um ou mais argumentos são inválidos. |
| `E_POINTER` | 0x80004003 | `pIWbemServices` é `null`. | 
| `E_FAIL` | 0x80000008 | Ocorreu um erro não especificado. |
| `E_OUTOFMEMORY` | 0x80000002 | Memória disponível é insuficiente para executar a operação. | 
| `S_OK` | 0 | A chamada de função foi bem-sucedida. | 

## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
