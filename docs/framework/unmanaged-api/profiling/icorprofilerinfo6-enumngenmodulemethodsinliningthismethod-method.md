---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67ae413ae8944757fc90bcde752b9a5fe53cc68f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365315"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a>ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method

Retorna um enumerador para todos os métodos que são definidos em um determinado módulo do NGen e embutida de um determinado método.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a>Parâmetros

`inlinersModuleId`\
[in] O identificador de um módulo do NGen.

`inlineeModuleId`\
[in] O identificador de um módulo que define `inlineeMethodId`. Consulte a seção Comentários para obter mais informações.

`inlineeMethodId`\
[in] O identificador de um método embutido. Consulte a seção Comentários para obter mais informações.

`incompleteData`\
[out] Um sinalizador que indica se `ppEnum` contém todos os métodos de embutidos um determinado método.  Consulte a seção Comentários para obter mais informações.

`ppEnum`\
[out] Um ponteiro para o endereço de um enumerador

## <a name="remarks"></a>Comentários

`inlineeModuleId` e `inlineeMethodId` juntos, formam o identificador completo para o método que pode ser embutido. Por exemplo, suponha que o módulo `A` define um método `Simple.Add`:

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

e o módulo B define `Fancy.AddTwice`:

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

Vamos supor também que `Fancy.AddTwice` inlines a chamada para `SimpleAdd`. Um criador de perfil pode usar este enumerador para localizar todos os métodos definidos no módulo B qual embutido `Simple.Add`, e o resultado seria enumerar `AddTwice`.  `inlineeModuleId` é o identificador do módulo `A`, e `inlineeMethodId` é o identificador do `Simple.Add(int a, int b)`.

Se `incompleteData` é verdadeiro após a função retornar, o enumerador não contém todos os métodos de embutidos um determinado método. Isso pode acontecer quando um ou mais dependências diretas ou indiretas do módulo inliners ainda não foi carregadas ainda. Se um criador de perfil precisa dados precisos, ele deve novamente mais tarde quando mais módulos são carregados, preferencialmente na carga de cada módulo.

O `EnumNgenModuleMethodsInliningThisMethod` método pode ser usado para contornar limitações em inlining para ReJIT. Permite que um criador de perfil do ReJIT alterar a implementação de um método e, em seguida, crie o novo código para ele em tempo real. Por exemplo, podemos pode alterar `Simple.Add` da seguinte maneira:

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

No entanto porque `Fancy.AddTwice` tem já embutida `Simple.Add`, ele continua a ter o mesmo comportamento como antes. Para contornar essa limitação, o chamador tenha que pesquisar todos os métodos em todos os módulos isso de forma embutida `Simple.Add` e use `ICorProfilerInfo5::RequestRejit` em cada um desses métodos. Quando os métodos são compilados novamente, eles terão o novo comportamento da `Simple.Add` em vez do comportamento antigo.

## <a name="requirements"></a>Requisitos

**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).

**Cabeçalho:** CorProf.idl, CorProf.h

**Biblioteca:** CorGuids.lib

**Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]

## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo6](icorprofilerinfo6-interface.md)