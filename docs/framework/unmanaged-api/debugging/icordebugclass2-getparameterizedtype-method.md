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
ms.openlocfilehash: 5e1734ca91fd48cc15b8dbf25f11518ed0455b6f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475626"
---
# <a name="icordebugclass2getparameterizedtype-method"></a>Método ICorDebugClass2::GetParameterizedType
Obtém a declaração de tipo para esta classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `elementType`  
 [in] Um valor de enumeração CorElementType que especifica o tipo de elemento para esta classe: Defina esse valor como ELEMENT_TYPE_VALUETYPE se este ICorDebugClass2 representa um tipo de valor. Defina esse valor como ELEMENT_TYPE_CLASS se este `ICorDebugClass2` representa um tipo complexo.  
  
 `nTypeArgs`  
 [in] O número de parâmetros de tipo, se o tipo for genérico. O número de parâmetros de tipo (se houver) deve corresponder ao número exigido pela classe.  
  
 `ppTypeArgs`  
 [in] Uma matriz de ponteiros, cada um deles aponta para um objeto de ICorDebugType que representa um parâmetro de tipo. Se a classe não genérica, esse valor é nulo.  
  
 `ppType`  
 [out] Um ponteiro para o endereço de um `ICorDebugType` objeto que representa o tipo de declaração. Esse objeto é equivalente a um <xref:System.Type> objeto em código gerenciado.  
  
## <a name="remarks"></a>Comentários  
 Se a classe não genérica, ou seja, se ele tiver nenhum parâmetro de tipo `GetParameterizedType` simplesmente obtém o objeto de tipo de tempo de execução correspondente à classe. O `elementType` parâmetro deve ser definido como o tipo de elemento correto para a classe: ELEMENT_TYPE_VALUETYPE se a classe é um tipo de valor; Caso contrário, ELEMENT_TYPE_CLASS.  
  
 Se a classe aceita parâmetros de tipo (por exemplo, `ArrayList<T>`), você pode usar `GetParameterizedType` para construir um objeto de tipo para um tipo instanciado como `ArrayList<int>`.  
  
## <a name="background-information"></a>Informações gerais  
 Nas versões do .NET Framework 1.0 e 1.1, todos os tipos nos metadados podem ser mapeado diretamente para um tipo de processo em execução. Portanto, um tipo de metadados e um tipo de tempo de execução tinham uma representação única no processo em execução. No entanto, um tipo genérico nos metadados pode ser mapeado para muitas instâncias diferentes do tipo no processo em execução. Por exemplo, o tipo de metadados `SortedList<K,V>` pode ser mapeado para `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`e assim por diante. Portanto, você precisa de uma maneira de lidar com uma instância de tipo.  
  
 O .NET Framework versão 2.0 introduz o `ICorDebugType` interface. Para um tipo genérico, um `ICorDebugClass` ou `ICorDebugClass2` objeto representa o tipo não instanciado (`SortedList<K,V>`) e um `ICorDebugType` objeto representa os vários tipos de instanciados. Considerando um `ICorDebugClass` ou `ICorDebugClass2` do objeto, você pode criar um `ICorDebugType` objeto para qualquer instanciação chamando o `ICorDebugClass2::GetParameterizedType` método. Você também pode criar um `ICorDebugType` objeto para um tipo simple, como Int32, ou para um tipo não genérico.  
  
 A introdução do `ICorDebugType` objeto para representar a noção de tempo de execução de um tipo tem um efeito dominó por toda a API. Funções que anteriormente exigiam um `ICorDebugClass` ou `ICorDebugClass2` do objeto ou até mesmo um `CorElementType` valor são generalizado para tirar uma `ICorDebugType` objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
