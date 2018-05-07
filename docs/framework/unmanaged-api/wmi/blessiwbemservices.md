---
title: Função BlessIWbemServices (referência de API não gerenciada)
description: A função BlessIWbemServices indica se as credenciais do usuário permitirem o acesso a uma classe IWbemServices.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59cb20f7ccfbd0b8f9d6026c9805468613818130
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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

`strAuthority` [in] O nome de domínio do usuário. Consulte o [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.

`impLevel` [in] O nível de representação.

`authnLevel` [in] O nível de autorização.

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
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
