---
title: Função ExecQueryWmi (referência de API não gerenciada)
description: A função ExecQueryWmi executa uma consulta para recuperar objetos.
ms.date: 11/06/2017
api_name:
- ExecQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecQueryWmi
helpviewer_keywords:
- ExecQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cd8992fc37c570b5ea20f8751bef729311bfb7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718189"
---
# <a name="execquerywmi-function"></a>Função ExecQueryWmi
Executa uma consulta para recuperar objetos.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ExecQueryWmi (
   [in] BSTR                    strQueryLanguage,
   [in] BSTR                    strQuery,
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

`strQueryLanguage`    
[in] Uma cadeia de caracteres com a linguagem de consulta válida com suporte pelo gerenciamento do Windows. Ele deve ser "WQL", o acrônimo de linguagem de consulta WMI.

`strQuery`  
[in] O texto da consulta. O parâmetro não pode ser `null`.

`lFlags`   
[in] Uma combinação de sinalizadores que afetam o comportamento dessa função. Os seguintes valores são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código: 

| Constante | Valor  | Descrição  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Se definido, a função recupera os qualificadores corrigidos armazenados no namespace localizado da localidade da conexão atual. <br/> Se não for definido, a função recupera somente os qualificadores armazenados no namespace de imediato. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | O sinalizador faz com que uma chamada semissíncrona. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | A função retorna um enumerador de somente avanço. Normalmente, os enumeradores de somente avanço são mais rápidos e usam menos memória do que os enumeradores convencionais, mas eles não permitem chamadas para [Clone](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | WMI mantém ponteiros para objetos no enumration até que eles sejam liberados. | 
| `WBEM_FLAG_ENSURE_LOCATABLE` | 0x100 | Garante que quaisquer objetos retornados tenham informações suficientes neles até que as propriedades do sistema, como **Path**, **RelPath**, e **Server**, não são `null`. |
| `WBEM_FLAG_PROTOTYPE` | 2 | Este sinalizador é usado para criação de protótipos. Ele não executa a consulta e, em vez disso, retorna um objeto que se parece com um objeto de resultado típico. |
| `WBEM_FLAG_DIRECT_READ` | 0x200 | Causas acesso direcionam ao provedor para a classe especificada sem levar em consideração as subclasses ou de sua classe pai. |

Os sinalizadores recomendados são `WBEM_FLAG_RETURN_IMMEDIATELY` e `WBEM_FLAG_FORWARD_ONLY` para melhor desempenho.

`pCtx`  
[in] Normalmente, esse valor é `null`. Caso contrário, ele é um ponteiro para um [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instância que pode ser usada pelo provedor que está fornecendo as classes solicitadas. 

`ppEnum`  
[out] Se nenhum erro ocorrer, recebe o ponteiro para o enumerador que permite que o chamador recuperar as instâncias no conjunto de resultados da consulta. A consulta pode ter um conjunto de resultados com instâncias de zero. Consulte a [comentários](#remarks) seção para obter mais informações.

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
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | A consulta teve um erro de sintaxe. |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | O idioma de consulta solicitado não tem suporte. |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | A consulta é muito complexa. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI foi provavelmente interrompido e reiniciar. Chame [ConnectServerWmi](connectserverwmi.md) novamente. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | O link RPC (chamada) de procedimento remoto entre o processo atual e a WMI falhou. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | A consulta especifica uma classe que não existe. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemServices::ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) método.

Essa função processa a consulta especificada no `strQuery` parâmetro e cria um enumerador por meio do qual o chamador pode acessar os resultados da consulta. O enumerador é um ponteiro para um [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) interface; a consulta os resultados são instâncias de objetos de classe disponibilizados por meio de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) interface.

Há limites para o número de `AND` e `OR` palavras-chave que podem ser usadas em consultas WQL. Grande número de palavras-chave WQL usadas em uma consulta complexa pode fazer com que o WMI retornar os `WBEM_E_QUOTA_VIOLATION` (ou 0x8004106c) código de erro como um `HRESULT` valor. O limite de palavras-chave WQL depende complexas como a consulta é.

Se a chamada de função falhar, você pode obter informações adicionais sobre erros chamando o [GetErrorInfo](geterrorinfo.md) função.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também
- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
