---
title: Aviso do compilador CS3024
ms.date: 07/20/2015
f1_keywords:
- CS3024
helpviewer_keywords:
- CS3024
ms.assetid: fef9db31-9a7f-42d5-ad37-3e7faf661f95
ms.openlocfilehash: 7515fdd7bc8f57890e3f1aac6303ed4607cc2249
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59297287"
---
# <a name="compiler-warning-cs3024"></a><span data-ttu-id="707f2-102">Aviso do compilador CS3024</span><span class="sxs-lookup"><span data-stu-id="707f2-102">Compiler Warning CS3024</span></span>
<span data-ttu-id="707f2-103">Tipo de restrição 'type' não é compatível com CLS.</span><span class="sxs-lookup"><span data-stu-id="707f2-103">Constraint type 'type' is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="707f2-104">O compilador emite esse aviso, pois o uso de um tipo não compatível com CLS como uma restrição de tipo genérico pode tornar impossível para o código escrito em alguns idiomas para consumir a classe genérica.</span><span class="sxs-lookup"><span data-stu-id="707f2-104">The compiler issues this warning because the use of a non-CLS-compliant type as a generic type constraint could make it impossible for code written in some languages to consume your generic class.</span></span>  
  
### <a name="to-eliminate-this-warning"></a><span data-ttu-id="707f2-105">Para eliminar esse aviso</span><span class="sxs-lookup"><span data-stu-id="707f2-105">To eliminate this warning</span></span>  
  
1. <span data-ttu-id="707f2-106">Use um tipo compatível com CLS para a restrição de tipo.</span><span class="sxs-lookup"><span data-stu-id="707f2-106">Use a CLS-compliant type for the type constraint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="707f2-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="707f2-107">Example</span></span>  
 <span data-ttu-id="707f2-108">O exemplo a seguir gera CS3024 em vários locais:</span><span class="sxs-lookup"><span data-stu-id="707f2-108">The following example generates CS3024 in several locations:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="707f2-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="707f2-109">See also</span></span>

- [<span data-ttu-id="707f2-110">Restrições a parâmetros de tipo</span><span class="sxs-lookup"><span data-stu-id="707f2-110">Constraints on Type Parameters</span></span>](../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
