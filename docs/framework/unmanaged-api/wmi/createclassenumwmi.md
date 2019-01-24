---
title: Função CreateClassEnumWmi (referência de API não gerenciada)
description: A função CreateClassEnumWmi retorna um enumerador para todas as classes que atendem aos critérios especificados.
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
ms.openlocfilehash: 2fc8b25465657ba41220d4a19e10aa06b0e30e86
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733032"
---
# <a name="createclassenumwmi-function"></a>CreateClassEnumWmi function
Retorna um enumerador para todas as classes que satisfaçam os critérios de seleção especificados.  

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
[in] Se não for `null` ou em branco, especifica o nome de uma classe pai; o enumerador os retorna apenas as subclasses dessa classe. Se ele estiver `null` ou deixe em branco e `lFlags` é WBEM_FLAG_SHALLOW, retorna apenas classes de nível superior (classes sem classe pai). Se ele estiver `null` ou deixe em branco e `lFlags` é `WBEM_FLAG_DEEP`, retorna todas as classes no namespace.

`lFlags`   
[in] Uma combinação de sinalizadores que afetam o comportamento dessa função. Os seguintes valores são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código: 

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Se definido, a função recupera os qualificadores corrigidos armazenados no namespace localizado da localidade da conexão atual. <br/> Se não for definido, a função recupera somente os qualificadores armazenados no namespace de imediato. |
| `WBEM_FLAG_DEEP` | 0 | A enumeração inclui todas as subclasses na hierarquia, mas não essa classe. |
| `WBEM_FLAG_SHALLOW` | 1 | A enumeração inclui apenas puras instâncias dessa classe e exclui todas as instâncias de subclasses que fornecem propriedades não encontradas nessa classe. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | O sinalizador faz com que uma chamada semissíncrona. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | A função retorna um enumerador de somente avanço. Normalmente, os enumeradores de somente avanço são mais rápidos e usam menos memória do que os enumeradores convencionais, mas eles não permitem chamadas para [Clone](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | WMI mantém ponteiros para objetos no enumration até que eles sejam liberados. | 

Os sinalizadores recomendados são `WBEM_FLAG_RETURN_IMMEDIATELY` e `WBEM_FLAG_FORWARD_ONLY` para melhor desempenho.

`pCtx`  
[in] Normalmente, esse valor é `null`. Caso contrário, ele é um ponteiro para um [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instância que pode ser usada pelo provedor que está fornecendo as classes solicitadas. 

`ppEnum`  
[out] Recebe o ponteiro para o enumerador.

`authLevel`  
[in] O nível de autorização.

`impLevel` [in] O nível de representação.

`pCurrentNamespace`   
[in] Um ponteiro para um [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objeto que representa o namespace atual.

`strUser`   
[in] O nome de usuário. Consulte a [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.

`strPassword`   
[in] A senha. Consulte a [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.

`strAuthority`   
[in] O nome de domínio do usuário. Consulte a [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | O usuário não tem permissão para exibir um ou mais das classes que a função pode retornar. |
| `WBEM_E_FAILED` | 0x80041001 | Ocorreu um erro não especificado. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | `strSuperClass` não existe. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI foi provavelmente interrompido e reiniciar. Chame [ConnectServerWmi](connectserverwmi.md) novamente. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | O link RPC (chamada) de procedimento remoto entre o processo atual e a WMI falhou. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemServices:: Createclassenum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) método.

Se a chamada de função falhar, você pode obter informações adicionais sobre erros chamando o [GetErrorInfo](geterrorinfo.md) função.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também
- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
