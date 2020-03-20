---
title: Função PutMethod (referência a PiPI não gerenciada)
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
ms.openlocfilehash: 93347b7290211b5d62829604678261fdf4da1ec3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174908"
---
# <a name="putmethod-function"></a>Função PutMethod
Cria um método.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT PutMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*  ptr,
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
);
```  

## <a name="parameters"></a>parâmetros

`vFunc`  
[em] Este parâmetro não é usado.

`ptr`  
[em] Um ponteiro para uma instância [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`wszName`  
[em] O nome do método para criar.

`lFlags`  
[in] Reservado. Este parâmetro deve ser 0.

`pSignatureIn`  
[em] Um ponteiro para uma cópia da classe `in` do sistema [__Parameters](/windows/desktop/WmiSdk/--parameters) que contém os parâmetros para o método. Este parâmetro é ignorado se `null`definido como .  

`pSignatureOut`  
[em]  Um ponteiro para uma cópia da classe `out` do sistema [__Parameters](/windows/desktop/WmiSdk/--parameters) que contém os parâmetros para o método. Este parâmetro é ignorado se `null`definido como .

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um ou mais parâmetros não são válidos. |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | O `[in, out]` parâmetro de método especificado nos objetos *pInSignature* e *pOutSignature* tem qualificações diferentes.
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | Um parâmetro de método está faltando a especificação do qualificador de **ID.** |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | A série ID atribuída aos parâmetros do método não é consecutiva ou não começa em 0. |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | O valor de retorno para um método tem um qualificador **de ID.** |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | Uma tentativa foi feita para reutilizar um nome de método existente de uma classe pai, e as assinaturas não coincidiram. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem sucedida. |
  
## <a name="remarks"></a>Comentários

Esta função envolve uma chamada para o método [IWbemClassObject::PutMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)

Esta chamada de método `ptr` só é suportada se for uma definição de classe CIM. A manipulação do método não está disponível a partir de ponteiros [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) que apontam para instâncias CIM.

Os usuários não podem criar métodos com nomes que começam ou terminam com um sublinhado. Isso é reservado para classes e propriedades do sistema.

Para um método, os `in` parâmetros e `out` parâmetros são descritos como propriedades em objetos [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

Um `[in/out]` parâmetro pode ser definido adicionando a mesma propriedade `pInSignature` `pOutSignature` a ambos os objetos apontados pelos parâmetros e parâmetros. Neste caso, as propriedades compartilham o mesmo valor de qualificação **de ID.**

Cada propriedade em um objeto `ReturnValue` de classe [__Parameters](/windows/desktop/WmiSdk/--parameters) que não seja deve ter um qualificador de **identificação,** um valor numérico baseado em zero que identifica a ordem em que os parâmetros aparecem. Nenhum dos dois parâmetros pode ter o mesmo valor **de ID,** e nenhum valor **de ID** pode ser ignorado. Se ocorrer qualquer `PutMethod` condição, `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`a função retorna .

## <a name="example"></a>Exemplo

Por exemplo, consulte o método [IWbemClassObject::PutMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)

## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Confira também

- [WMI e Contadores de Desempenho (Referência de API Não Gerenciada)](index.md)
