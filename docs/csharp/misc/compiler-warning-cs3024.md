---
title: Aviso do compilador CS3024
ms.date: 07/20/2015
f1_keywords:
- CS3024
helpviewer_keywords:
- CS3024
ms.assetid: fef9db31-9a7f-42d5-ad37-3e7faf661f95
ms.openlocfilehash: 6147fc1aafc06d7c844cfc39eafebbd737d89610
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69601967"
---
# <a name="compiler-warning-cs3024"></a>Aviso do compilador CS3024
O tipo de restrição ' type ' não é compatível com CLS.  
  
 O compilador emite esse aviso porque o uso de um tipo não compatível com CLS como uma restrição de tipo genérico pode tornar impossível para o código escrito em algumas linguagens consumirem sua classe genérica.  
  
### <a name="to-eliminate-this-warning"></a>Para eliminar este aviso  
  
1. Use um tipo em conformidade com CLS para a restrição de tipo.  
  
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

- [Restrições a parâmetros de tipo](../programming-guide/generics/constraints-on-type-parameters.md)
