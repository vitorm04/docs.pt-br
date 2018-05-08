---
title: Método ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 564f3b1cdfab2a3020b6bb5ac8d9af03c6532c8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a>Método ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod
[Com suporte no .NET Framework 4.6 e versões posteriores]  
  
 Retorna um enumerador para todos os métodos que são definidos em um módulo especificado do NGen e embutido um determinado método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumNgenModuleMethodsInliningThisMethod(  
        [in] ModuleID inlinersModuleId,  
        [in] ModuleID inlineeModuleId,  
        [in] mdMethodDef inlineeMethodId,  
        [out] BOOL *incompleteData,  
        [out] ICorProfilerMethodEnum** ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `inlinersModuleId`  
 [in] O identificador de um módulo do NGen.  
  
 `inlineeModuleId`  
 [in] O identificador de um módulo que define `inlineeMethodId`. Consulte a seção Comentários para obter mais informações.  
  
 `inlineeMethodId`  
 [in] O identificador de um método embutido. Consulte a seção Comentários para obter mais informações.  
  
 `incompleteData`  
 [out] Um sinalizador que indica se `ppEnum` contém todos os métodos de inlining um método específico.  Consulte a seção Comentários para obter mais informações.  
  
 `ppEnum`  
 [out] Um ponteiro para o endereço de um enumerador  
  
## <a name="remarks"></a>Comentários  
 `inlineeModuleId` e `inlineeMethodId` juntos, formam o identificador completo para o método que pode ser embutido. Por exemplo, suponha que o módulo `A` define um método `Simple.Add`:  
  
```csharp  
Simple.Add(int a, int b)   
{ return a + b; }  
```  
  
 módulo Bdefines e `Fancy.AddTwice`:  
  
```csharp  
Fancy.AddTwice(int a, int b)   
{ return Simple.Add(a,b) + Simple.Add(a,b); }  
```  
  
 Suponha também que `Fancy.AddTwice` linhas internas a chamada para `SimpleAdd`. Um criador de perfil pode usar esse enumerador para localizar todos os métodos definidos no módulo B quais embutido `Simple.Add`, e o resultado seria enumerar `AddTwice`.  `inlineeModuleId` é o identificador de módulo `A`, e `inlineeeMethodId` é o identificador de `Simple.Add(int a, int b)`.  
  
 Se `incompleteData` ocorre após a função retornar, o enumerador não contém todos os métodos de inlining um determinado método. Isso pode acontecer quando um ou mais diretas ou indiretas dependências do módulo inliners ainda não foi carregadas ainda. Se precisar de um criador de perfil dados precisos, ele deve novamente mais tarde quando mais de módulos são carregados, preferencialmente em cada carga de módulo.  
  
 O `EnumNgenModuleMethodsInliningThisMethod` método pode ser usado para contornar limitações em inlining para ReJIT. ReJIT permite um criador de perfil, altere a implementação de um método e, em seguida, criar o novo código para ele em tempo real. Por exemplo, podemos pode alterar `Simple.Add` da seguinte maneira:  
  
```csharp  
Simple.Add(int a, int b)   
{ return 42; }  
```  
  
 No entanto porque `Fancy.AddTwice` tem embutida já `Simple.Add`, ele continuará a ter o mesmo comportamento como antes. Para contornar essa limitação, o chamador tem que procurar todos os métodos em todos os módulos que embutido `Simple.Add` e usar `ICorProfilerInfo5::RequestRejit` em cada um desses métodos. Quando os métodos são compilados novamente, eles terão o novo comportamento de `Simple.Add` em vez do comportamento antigo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)
