---
title: Aviso do compilador CS3024
ms.date: 07/20/2015
f1_keywords:
- CS3024
helpviewer_keywords:
- CS3024
ms.assetid: fef9db31-9a7f-42d5-ad37-3e7faf661f95
ms.openlocfilehash: 7515fdd7bc8f57890e3f1aac6303ed4607cc2249
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297287"
---
# <a name="compiler-warning-cs3024"></a>Aviso do compilador CS3024
Tipo de restrição 'type' não é compatível com CLS.  
  
 O compilador emite esse aviso, pois o uso de um tipo não compatível com CLS como uma restrição de tipo genérico pode tornar impossível para o código escrito em alguns idiomas para consumir a classe genérica.  
  
### <a name="to-eliminate-this-warning"></a>Para eliminar esse aviso  
  
1. Use um tipo compatível com CLS para a restrição de tipo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir gera CS3024 em vários locais:  
  
```csharp  
// cs3024.cs  
// Compile with: /target:library  
 [assembly: System.CLSCompliant(true)]  
  
[type: System.CLSCompliant(false)]  
public class TestClass // CS3024  
{  
    public ushort us;  
}  
[type: System.CLSCompliant(false)]  
public interface ITest // CS3024  
{}  
public interface I<T> where T : TestClass  
{}  
public class TestClass_2<T> where T : ITest  
{}  
public class TestClass_3<T> : I<T> where T : TestClass  
{}  
public class TestClass_4<T> : TestClass_2<T> where T : ITest  
{}  
public class Test  
{  
    public static int Main()  
    {  
        return 0;  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também

- [Restrições a parâmetros de tipo](../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
