---
title: Colocar a função (referência de API não gerenciada)
description: A função Put atribui um novo valor para uma propriedade nomeada.
ms.date: 11/06/2017
api_name:
- Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Put
helpviewer_keywords:
- Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f3ffe27bef6583b733fc04f2f25903d545daa74
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460373"
---
# <a name="put-function"></a>Colocar a função
Define uma propriedade nomeada para um novo valor.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Put (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`  
[in] Esse parâmetro é usado.

`ptr`  
[in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.

`wszName`  
[in] O nome da propriedade. O parâmetro não pode ser `null`.

`lFlags`  
[in] Reservado. Esse parâmetro deve ser 0.

`pVal`   
[in] Um ponteiro para um válida `VARIANT` que se torna o novo valor da propriedade. Se `pVal` é `null` ou aponta para um `VARIANT` do tipo `VT_NULL`, a propriedade é definida como `null`. 

`vtType`  
[in] O tipo de `VARIANT` apontada pelo `pVal`. Consulte o [comentários](#remarks) para obter mais informações.
 

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Houve uma falha geral. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um ou mais parâmetros não são válidos. |
|`WBEM_E_INVALID_PROPERTY_TYPE` | 0x8004102a | O tipo de propriedade não é reconhecido. Esse valor é retornado ao criar instâncias de classe, se a classe já existe. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
| `WBEM_E_TYPE_MISMATCH` | 0x80041005 | Para instâncias: indica que `pVal` aponta para um `VARIANT` de um tipo incorreto para a propriedade. <br/> Para obter definições de classe: A propriedade já existe na classe pai e o novo tipo de COM é diferente do tipo de COM antigo. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida. |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) método.

Essa função sempre substitui o valor da propriedade atual com um novo. Se o [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) aponta para uma definição de classe `Put` cria ou atualiza o valor da propriedade. Quando [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) aponta para uma instância CIM, `Put` atualiza o valor da propriedade. `Put` não é possível criar um valor de propriedade.

O `__CLASS` sistema propriedade só é gravável durante a criação de classe quando ele não pode ser deixado em branco. Todas as outras propriedades de sistema são somente leitura.

Um usuário não é possível criar propriedades com nomes que podem começam ou terminam com um sublinhado ("_"). Isso é reservado para propriedades e classes do sistema.

Se a propriedade definida `Put` função existe na classe pai, o valor padrão da propriedade é alterado, a menos que o tipo de propriedade não coincide com o tipo de classe pai. Se a propriedade não existe e não é uma incompatibilidade de tipo, a propriedade é ceated.

Use o `vtType` parâmetro somente durante a criação de novas propriedades em uma definição de classe do CIM e `pVal` é `null` ou aponta para um `VARIANT` do tipo `VT_NULL`. Nesse caso, o `vType` parâmetro especifica o tipo CIM da propriedade. Em todos os outros casos, `vtType` deve ser 0. `vtType` também deve ser 0 se o objeto subjacente é uma instância (mesmo se `Val` é `null`) porque o tipo da propriedade é fixo e não pode ser alterado.   

## <a name="example"></a>Exemplo

Para obter um exemplo, consulte o [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) método.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
