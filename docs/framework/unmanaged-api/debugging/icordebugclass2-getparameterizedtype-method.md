---
title: Método ICorDebugClass2::GetParameterizedType
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.GetParameterizedType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::GetParameterizedType
helpviewer_keywords:
- GetParameterizedType method [.NET Framework debugging]
- ICorDebugClass2::GetParameterizedType method [.NET Framework debugging]
ms.assetid: 94b591c4-9302-4af2-a510-089496afb036
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a5b3a28c7250a16e78e199bceff7c9e64517319
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408207"
---
# <a name="icordebugclass2getparameterizedtype-method"></a>Método ICorDebugClass2::GetParameterizedType
Obtém o tipo de declaração para essa classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `elementType`  
 [in] Um valor da enumeração CorElementType que especifica o tipo de elemento para esta classe: Defina esse valor como ELEMENT_TYPE_VALUETYPE se este ICorDebugClass2 representa um tipo de valor. Defina esse valor como ELEMENT_TYPE_CLASS se este `ICorDebugClass2` representa um tipo complexo.  
  
 `nTypeArgs`  
 [in] O número de parâmetros de tipo, se o tipo é genérico. O número de parâmetros de tipo (se houver) deve corresponder ao número exigido pela classe.  
  
 `ppTypeArgs`  
 [in] Uma matriz de ponteiros, cada um deles aponta para um objeto ICorDebugType que representa um parâmetro de tipo. Se a classe não-genérica, esse valor é nulo.  
  
 `ppType`  
 [out] Um ponteiro para o endereço de uma `ICorDebugType` objeto que representa o tipo de declaração. Esse objeto é equivalente a um <xref:System.Type> objeto no código gerenciado.  
  
## <a name="remarks"></a>Comentários  
 Se a classe for não genérico, ou seja, se nenhum parâmetro de tipo, `GetParameterizedType` simplesmente obtém o objeto de tipo de tempo de execução correspondente à classe. O `elementType` parâmetro deve ser definido para o tipo de elemento correto para a classe: ELEMENT_TYPE_VALUETYPE se a classe for um tipo de valor; caso contrário, ELEMENT_TYPE_CLASS.  
  
 Se a classe aceita parâmetros de tipo (por exemplo, `ArrayList<T>`), você pode usar `GetParameterizedType` para construir um objeto de tipo para um tipo instanciado como `ArrayList<int>`.  
  
## <a name="background-information"></a>Informações gerais  
 Nas versões do .NET Framework 1.0 e 1.1, todos os tipos nos metadados do podem ser mapeado diretamente para um tipo no processo de execução. Portanto, um tipo de metadados e um tipo de tempo de execução tinham uma única representação do processo em execução. No entanto, um tipo genérico nos metadados pode ser mapeado para muitas instâncias diferentes do tipo do processo em execução. Por exemplo, o tipo de metadados `SortedList<K,V>` pode ser mapeado para `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`e assim por diante. Assim, você precisa de uma maneira de lidar com uma instância de tipo.  
  
 O .NET Framework versão 2.0 introduz o `ICorDebugType` interface. Para um tipo genérico, um `ICorDebugClass` ou `ICorDebugClass2` objeto representa o tipo instanciado (`SortedList<K,V>`) e um `ICorDebugType` objeto representa os vários tipos de instâncias. Dado um `ICorDebugClass` ou `ICorDebugClass2` do objeto, você pode criar um `ICorDebugType` objeto para qualquer instanciação chamando o `ICorDebugClass2::GetParameterizedType` método. Você também pode criar um `ICorDebugType` objeto para um tipo simple, como Int32, ou para um tipo não genérico.  
  
 A introdução do `ICorDebugType` objeto para representar a noção de tempo de execução de um tipo tem um efeito de ondulação em toda a API. Funções que levaram anteriormente um `ICorDebugClass` ou `ICorDebugClass2` do objeto ou até mesmo um `CorElementType` valor estão generalizados para tirar uma `ICorDebugType` objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
