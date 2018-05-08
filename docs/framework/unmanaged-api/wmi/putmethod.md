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
ms.openlocfilehash: 7f74b0d30a1a8899d3c8d0a2bf0f108ea11165cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
[in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.

`wszName`  
[in] O nome do método para criar. 

`lFlags`  
[in] Reservado. Esse parâmetro deve ser 0.

`pSignatureIn`  
[in] Um ponteiro para uma cópia do [classe de sistema de Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) que contém o `in` parâmetros do método. Esse parâmetro é ignorado se definido como `null`.  

`pSignatureOut`  
[in]  Um ponteiro para uma cópia do [classe de sistema de Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) que contém o `out` parâmetros do método. Esse parâmetro é ignorado se definido como `null`.
 

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um ou mais parâmetros não são válidos. |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | O `[in, out]` especificado no parâmetro do método de *pInSignature* e *pOutSignature* objetos têm diferentes qualificadores.
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | Um parâmetro de método não tem a especificação da **ID** qualificador. |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | A série de ID que é atribuída aos parâmetros de método não é consecutiva ou não começam com 0. |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | O valor de retorno de um método tem um **ID** qualificador. |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | Foi feita uma tentativa de reutilizar um nome de método existente de uma classe pai, e as assinaturas não correspondeu. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida. |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) método.

Esta chamada de método só terá suporte se `ptr` é uma definição de classe do CIM. Manipulação de método não está disponível no [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) ponteiros que apontam para instâncias CIM.

Os usuários não é possível criar métodos com nomes que podem começam ou terminam com um sublinhado. Isso é reservado para propriedades e classes do sistema.

Para um método, o `in` e `out` parâmetros são descritos como propriedades na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) objetos.

Um `[in/out]` parâmetro pode ser definido adicionando a mesma propriedade para os dois objetos apontados pelo `pInSignature` e `pOutSignature` parâmetros. Nesse caso, as propriedades compartilham o mesmo **ID** valor do qualificador.

Cada propriedade em uma [Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) diferente do objeto de classe `ReturnValue` deve ter uma **ID** qualificador, um valor numérico de base zero que identifica a ordem na qual os parâmetros aparecem. Não há dois parâmetros podem ter o mesmo **ID** valor e não **ID** valor pode ser ignorado. Se uma dessas condições ocorre, o `PutMethod` função retorna `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.

## <a name="example"></a>Exemplo

Para obter um exemplo, consulte o [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) método.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
