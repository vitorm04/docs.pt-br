---
title: Função PutMethod (referência de API não gerenciada)
description: A função PutMethod cria um método.
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74654cf18d87fed8ad5ce9a4cd4249d56fdb4343
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693445"
---
# <a name="putmethod-function"></a>Função PutMethod
Cria um método.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`  
[in] Esse parâmetro é usado.

`ptr`  
[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.

`wszName`  
[in] O nome do método para criar. 

`lFlags`  
[in] Reservado. Esse parâmetro deve ser 0.

`pSignatureIn`  
[in] Um ponteiro para uma cópia do [classe de sistema de Parameters](/windows/desktop/WmiSdk/--parameters) que contém o `in` parâmetros para o método. Esse parâmetro será ignorado se definido como `null`.  

`pSignatureOut`  
[in]  Um ponteiro para uma cópia do [classe de sistema de Parameters](/windows/desktop/WmiSdk/--parameters) que contém o `out` parâmetros para o método. Esse parâmetro será ignorado se definido como `null`.
 

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um ou mais parâmetros não são válidos. |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | O `[in, out]` parâmetro de método especificado em ambos os *pInSignature* e *pOutSignature* objetos têm qualificadores diferentes.
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | Um parâmetro de método não tem a especificação do **ID** qualificador. |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | A série de ID que é atribuída aos parâmetros de método não é consecutiva ou não inicia em 0. |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | O valor de retorno para um método tem um **ID** qualificador. |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | Foi feita uma tentativa de reutilizar um nome de método existente de uma classe pai, e as assinaturas não correspondem. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida. |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) método.

Esta chamada de método só tem suporte se `ptr` é uma definição de classe do CIM. Manipulação de método não está disponível no [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponteiros que apontam para instâncias CIM.

Os usuários não é possível criar métodos com nomes que começam ou terminam com um sublinhado. Isso é reservado para as propriedades e classes do sistema.

Para um método, o `in` e `out` parâmetros são descritos como propriedades nas [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) objetos.

Uma `[in/out]` parâmetro pode ser definido, adicionando a mesma propriedade para ambos os objetos apontados pela `pInSignature` e `pOutSignature` parâmetros. Nesse caso, as propriedades compartilham o mesmo **ID** valor do qualificador.

Cada propriedade em uma [Parameters](/windows/desktop/WmiSdk/--parameters) diferente de objeto de classe `ReturnValue` deve ter um **ID** qualificador, um valor numérico de base zero que identifica a ordem na qual os parâmetros aparecem. Não há dois parâmetros podem ter o mesmo **identificação** valor e não **ID** valor pode ser ignorado. Se uma dessas condições ocorre, o `PutMethod` retornos de função `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.

## <a name="example"></a>Exemplo

Por exemplo, consulte o [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) método.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também
- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
