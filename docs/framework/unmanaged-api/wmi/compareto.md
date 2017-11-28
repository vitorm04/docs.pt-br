---
title: "Função CompareTo (referência de API não gerenciada)"
description: "A função CompareTo compara um objeto com outro objeto WMI."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: CompareTo
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: CompareTo
helpviewer_keywords: CompareTo function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dacb1516bebfc73ae9e16b03f3755ab49382e571
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="compareto-function"></a>Função CompareTo
Compara a um objeto para outro objeto de gerenciamento do Windows.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sintaxe  
  
```
HRESULT CompareTo (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo 
); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`  
[in] Esse parâmetro é usado.

`ptr`  
[in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.

`flags`  
[in] Uma combinação bit a bit dos sinalizadores que especificam as características de objeto a serem considerados para a comparação. Consulte o [comentários](#remarks) para obter mais informações.

`pCompareTo`  

[in] O objeto para comparação. `pcompareTo`deve ser um válido [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância; ele não pode ser `null`.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Ocorreu um erro não especificado. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro é inválido. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | Uma segunda chamada para `BeginEnumeration` foi feita sem uma chamada intermediária para [ `EndEnumeration` ](endenumeration.md). |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
| `WBEM_S_DIFFERENT` | 0x40003 | Os objetos são diferentes. |
| `WBEM_S_SAME` | 0 | Os objetos são os mesmos, com base nos sinalizadores de comparação. |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemClassObject::CompareTo](https://msdn.microsoft.com/library/aa391437(v=vs.85).aspx) método.

Os sinalizadores que podem ser passados como o `lEnumFlags` argumento são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código. Você pode especificar as características individuais envolvido na comparação com a especificação de uma combinação bit a bit dos sinalizadores a seguir:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | 2 | Ignore o origem (o servidor e o namespace que de onde vieram). |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | 1 | Ignorar todos os qualificadores (incluindo **chave** e **dinâmico**) |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | 4 | Ignore valores padrão das propriedades. Esse sinalizador só se aplica a comparação de classes. |
| `WBEM_FLAG_IGNORE_FLAVOR` | 0x20 | Ignore tipos de qualificadores. Este sinalizador ainda considera qualificadores, mas ignora diferenças de tipo, como regras de propagação e substituir as restrições. |
| `WBEM_FLAG_IGNORE_CASE` | 0x10 | Ignore maiusculas e minúsculas na comparação de valores de cadeia de caracteres. Isso se aplica a cadeias de caracteres e valores de qualificador. A comparação de nomes de propriedade e qualificador sempre diferencia maiusculas de minúsculas, independentemente de se esse sinalizador é definido. |
| `WBEM_FLAG_IGNORE_CLASS` | 0x8 | Suponha que os objetos que estão sendo comparados são instâncias da mesma classe. Consequentemente, esse sinalizador compara somente informações relacionadas à instância. Use este sinalizadores para otimizar o desempenho. Se os objetos não são da mesma classe, os resultados serão indefinidos. |

Ou você pode especificar um único sinalizador composto da seguinte maneira:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | 0 | Considere a possibilidade de todos os recursos na comparação. |

## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
