---
title: Função CreateClassEnumWmi (referência de API não gerenciada)
description: A função CreateClassEnumWmi retorna um enumerador para todas as classes que atendem a critérios especificados.
ms.date: 11/06/2017
api_name:
- CreateClassEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateClassEnumWmi
helpviewer_keywords:
- CreateClassEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f84902586a2b940d52eb6365a141af61af802dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="createclassenumwmi-function"></a>Função CreateClassEnumWmi
Retorna um enumerador para todas as classes que atendem aos critérios de seleção especificada.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateClassEnumWmi (
   [in] BSTR                    strSuperclass,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
); 
```  

## <a name="parameters"></a>Parâmetros

`strSuperclass`    
[in] Se não `null` ou em branco, especifica o nome de uma classe pai; o enumerador retorna apenas as subclasses dessa classe. Se for `null` ou em branco e `lFlags` é WBEM_FLAG_SHALLOW, retorna apenas classes de nível superior (classes com nenhuma classe pai). Se for `null` ou em branco e `lFlags` é `WBEM_FLAG_DEEP`, retorna todas as classes no namespace.

`lFlags`   
[in] Uma combinação de sinalizadores que afetam o comportamento dessa função. Os seguintes valores são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código: 

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Se o conjunto, a função recupera os qualificadores aperfeiçoados armazenados no namespace localizado da localidade da conexão atual. <br/> Se não for definido, a função recupera somente os qualificadores armazenados no namespace de imediato. |
| `WBEM_FLAG_DEEP` | 0 | A enumeração inclui todas as subclasses da hierarquia, mas não essa classe. |
| `WBEM_FLAG_SHALLOW` | 1 | A enumeração inclui somente puras instâncias dessa classe e exclui todas as instâncias das subclasses que fornecem a propriedade não foi encontrada nesta classe. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | O sinalizador faz com que uma chamada semi-síncrona. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | A função retorna um enumerador de somente avanço. Normalmente, os enumeradores de somente avanço são mais rápidos e usam menos memória do que os enumeradores convencionais, mas não permitem chamadas para [Clone](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | WMI retém ponteiros para objetos de enumration até que eles sejam liberados. | 

Os sinalizadores recomendados são `WBEM_FLAG_RETURN_IMMEDIATELY` e `WBEM_FLAG_FORWARD_ONLY` para melhor desempenho.

`pCtx`  
[in] Normalmente, esse valor é `null`. Caso contrário, é um ponteiro para um [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instância pode ser usada pelo provedor que fornece as classes solicitadas. 

`ppEnum`  
[out] Recebe o ponteiro para o enumerador.

`authLevel`  
[in] O nível de autorização.

`impLevel` [in] O nível de representação.

`pCurrentNamespace`   
[in] Um ponteiro para um [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) objeto que representa o namespace atual.

`strUser`   
[in] O nome de usuário. Consulte o [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.

`strPassword`   
[in] A senha. Consulte o [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.

`strAuthority`   
[in] O nome de domínio do usuário. Consulte o [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | O usuário não tem permissão para exibir um ou mais das classes que a função pode retornar. |
| `WBEM_E_FAILED` | 0x80041001 | Ocorreu um erro não especificado. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | `strSuperClass` não existe. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI foi provavelmente interrompido e reiniciar. Chamar [ConnectServerWmi](connectserverwmi.md) novamente. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | O link RPC (chamada) de procedimento remoto entre o processo atual e a WMI falhou. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [Createclassenum](https://msdn.microsoft.com/library/aa392095(v=vs.85).aspx) método.

Se a chamada de função falhar, você pode obter informações adicionais sobre erros chamando o [GetErrorInfo](geterrorinfo.md) função.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
