---
title: Função GetPropertyQualifierSet (referência de API não gerenciada)
description: A função GetPropertyQualifierSet recupera o qualificador definido para uma propriedade.
ms.date: 11/06/2017
api_name:
- GetPropertyQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyQualifierSet
helpviewer_keywords:
- GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fcddca2e435a3f5bf4b8d083784613254d9801a4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481189"
---
# <a name="getpropertyqualifierset-function"></a>Função GetPropertyQualifierSet
Recupera o qualificador definido para uma determinada propriedade.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`  
[in] Esse parâmetro é usado.

`ptr`  
[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.

`wszMethod`  
[in] O nome da propriedade. `wszProperty` deve apontar para um válido `LPCWSTR`. 

`ppQualSet`  
[out] Recebe o ponteiro de interface que permite o acesso para os qualificadores de propriedade. `ppQualSet` não pode ser `null`. Se ocorrer um erro, um novo objeto não é retornado e o ponteiro é definido para apontar para `null`. 

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Houve uma falha geral. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | O método especificado não existe. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro é `null`. |
| `WBEM_E_SYSTEM_PROPERTY` | 0x80041030 | A função tenta obter qualificadores de uma propriedade do sistema. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemClassObject::GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) método. 

Uma chamada para essa função tem suporte apenas se o objeto atual é uma definição de classe do CIM. Manipulação de método não está disponível para [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponters que apontam para instâncias CIM.

Porque cada método pode ter seus próprio qualificadores, o [IWbemQualifierSet ponteiro](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) permite que o chamador adicionar, editar ou excluir esses qualificadores.

Como as propriedades do sistema não têm nenhum qualificador, a função retornará `WBEM_E_SYSTEM_PROPERTY` se você tentar obter uma [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) ponteiro para uma propriedade do sistema.

## <a name="requirements"></a>Requisitos  
**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
