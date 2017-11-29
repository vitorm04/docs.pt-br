---
title: "Função GetPropertyQualifierSet (referência de API não gerenciada)"
description: "A função GetPropertyQualifierSet recupera o qualificador definido para uma propriedade."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetPropertyQualifierSet
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetPropertyQualifierSet
helpviewer_keywords: GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bd8abdb34f37273e469bdf5fc659b261bb2b9304
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
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
[in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.

`wszMethod`  
[in] O nome da propriedade. `wszProperty`deve apontar para um válida `LPCWSTR`. 

`ppQualSet`  
[out] Recebe o ponteiro de interface que permite acessar os qualificadores da propriedade. `ppQualSet` não pode ser `null`. Se ocorrer um erro, um novo objeto não é retornado e o ponteiro é definido para apontar para `null`. 

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Houve uma falha geral. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | O método especificado não existe. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória suficiente está disponível para concluir a operação. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro é `null`. |
| `WBEM_E_SYSTEM_PROPERTY` | 0x80041030 | A função tenta obter qualificadores de uma propriedade de sistema. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemClassObject::GetPropertyQualifierSet](https://msdn.microsoft.com/library/aa391450(v=vs.85).aspx) método. 

Uma chamada para essa função tem suporte apenas se o objeto atual é uma definição de classe do CIM. Manipulação de método não está disponível para [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters que apontam para instâncias CIM.

Como cada método pode ter seus próprio qualificadores de [IWbemQualifierSet ponteiro](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) permite que o chamador adicionar, editar ou excluir esses qualificadores.

Como as propriedades de sistema não ter nenhum qualificador, a função retorna `WBEM_E_SYSTEM_PROPERTY` se você tentar obter um [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) ponteiro para uma propriedade do sistema.

## <a name="requirements"></a>Requisitos  
**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
