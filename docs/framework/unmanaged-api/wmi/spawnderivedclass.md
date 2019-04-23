---
title: Função SpawnDerivedClass (referência de API não gerenciada)
description: A função SpawnDerivedClass cria um novo objeto que deriva de um objeto.
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81f4d5219865bf7f7c9e6d284d74d0c249729dfc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59194416"
---
# <a name="spawnderivedclass-function"></a>Função SpawnDerivedClass
Cria um objeto de classe derivada recentemente por meio de um objeto especificado.    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`  
[in] Esse parâmetro é usado.

`ptr`  
[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.

`lFlags`  
[in] Reservado. Esse parâmetro deve ser 0.

`ppNewClass`  
[out] Recebe o ponteiro para o novo objeto de definição de classe. Se ocorrer um erro, um novo objeto não é retornado, e `ppNewClass` é esquerda sem modificações. Seu valor não pode ser `null`.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Houve uma falha geral. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Uma operação inválida, como a geração de uma classe de uma instância, foi solicitada. |
| `WBEM_E_INCOMPLETE_CLASS` | A classe de origem não completamente foi definida ou está registrada com o gerenciamento do Windows, portanto, uma nova classe derivada não é permitida. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` é `null`. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) método.

`ptr` deve ser uma definição de classe que se torna a classe pai do objeto gerado. O objeto retornado se torna uma subclasse do objeto atual.

O novo objeto retornado no `ppNewClass` automaticamente se torna uma subclasse do objeto atual. Esse comportamento não pode ser substituído. Não há nenhum outro método pelo qual as subclasses (classes derivadas) podem ser criadas.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
