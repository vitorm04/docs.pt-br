---
title: Função PutClassWmi (referência de API não gerenciada)
description: A função PutClassWmi cria uma nova classe ou atualiza uma existente.
ms.date: 11/06/2017
api_name:
- PutClassWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutClassWmi
helpviewer_keywords:
- PutClassWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 995c697497876969edc1021350b7bfe28e4018bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614504"
---
# <a name="putclasswmi-function"></a>Função PutClassWmi
Cria uma nova classe ou atualiza uma existente.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a>Parâmetros

`pObject`    
[in] Um ponteiro para uma definição de classe válido. Ele deve ser inicializado corretamente com todos os valores de propriedade necessária.

`lFlags`   
[in] Uma combinação de sinalizadores que afetam o comportamento dessa função. Os seguintes valores são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código: 

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Se definido, o WMI não armazena qualquer qualificador com o tipo corrigido. </br> Se não for definido, supõe-se que esse objeto não está localizado, e todos os qualificadores são storedwith dessa instância. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Crie a classe se ele não existir ou substituí-lo se ele já existir. |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | Atualize a classe. A classe deve existir para a chamada seja bem-sucedida. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Crie a classe. A chamada falhará se a classe já existe. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | O sinalizador faz com que uma chamada semissíncrona. |
| `WBEM_FLAG_OWNER_UPDATE` | 0x10000 | Provedores de envio devem especificar esse sinalizador ao chamar `PutClassWmi` para indicar que essa classe foi alterado. |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | 0 | Permite que uma classe a ser atualizado se não houver nenhuma classe derivada e não há instâncias dessa classe. Ele também permite atualizações em todos os casos se a alteração é apenas para os qualificadores sem importância, como o qualificador de descrição. Se a classe tem instâncias ou alterações são para qualificadores importantes, a atualização falhará. |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | 0x20 | Permite atualizações de classes, mesmo que haja classes filhas, desde que a alteração não faz com que todos os conflitos com classes filho. Por exemplo, esse sinalizador permite que uma nova propriedade a ser adicionado à classe base que não foi mencionado anteriormente em qualquer uma das classes filhas. Se a classe tiver instâncias, a atualização falhará. |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | 0x40 | força as atualizações das classes quando as classes filhas conflitantes. Por exemplo, esse sinalizador de força uma atualização se um qualificador de classe é definido em uma classe filha e a classe base tenta adicionar o mesmo qualificador que está em conflito com thte existente a um. No modo force, o conflito de tis é resolvido pela exclusão do qualificador conflitante na classe filho. |

`pCtx`  
[in] Normalmente, esse valor é `null`. Caso contrário, ele é um ponteiro para um [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instância que pode ser usada pelo provedor que está fornecendo as classes solicitadas. 

`ppCallResult`  
[out] Se `null`, esse parâmetro é usado. Se `lFlags` contém `WBEM_FLAG_RETURN_IMMEDIATELY`, a função retornará imediatamente com `WBEM_S_NO_ERROR`. O `ppCallResult` parâmetro recebe um ponteiro para um novo [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) objeto.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | O usuário não tem permissão para criar ou modificar classes. |
| `WBEM_E_FAILED` | 0x80041001 | Ocorreu um erro não especificado. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | A classe especificada é inválida. Normalmente, isso indica que `pObject` Especifica um objeto de instância. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
| `WBEM_E_INVALID OPERATION` | 0x80041016 | O nome da classe especificada não é válido. |
| `WBEM_E_CLASS_HAS_CHILDREN` | 0x80041025 | Foi feita uma tentativa de fazer uma alteração que invalidaria uma subclasse. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | O `WBEM_FLAG_CREATE_ONLY` sinalizador foi especificado, mas a classe já existe. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY` foi especificado no `lFlags`, e a classe não foi encontrada. |
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | As propriedades necessárias para classes nem todos foram definidas. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI foi provavelmente interrompido e reiniciar. Chame [ConnectServerWmi](connectserverwmi.md) novamente. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | O link RPC (chamada) de procedimento remoto entre o processo atual e a WMI falhou. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemServices::PutClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) método.

O usuário não pode criar classes com nomes que começam ou terminam com um sublinhado chacater

Se a chamada de função falhar, você pode obter informações adicionais sobre erros chamando o [GetErrorInfo](geterrorinfo.md) função.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também
- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
