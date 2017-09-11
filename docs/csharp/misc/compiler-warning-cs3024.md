---
title: CS3024 de aviso do compilador | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- CS3024
dev_langs:
- CSharp
helpviewer_keywords:
- CS3024
ms.assetid: fef9db31-9a7f-42d5-ad37-3e7faf661f95
caps.latest.revision: 7
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 92c533d2fc5b5d9f6add118013a68918a7ad9ef1
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="compiler-warning-cs3024"></a><span data-ttu-id="6fa3a-102">CS3024 de aviso do compilador</span><span class="sxs-lookup"><span data-stu-id="6fa3a-102">Compiler Warning CS3024</span></span>
<span data-ttu-id="6fa3a-103">Tipo de restrição 'type' não é compatível com CLS.</span><span class="sxs-lookup"><span data-stu-id="6fa3a-103">Constraint type 'type' is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="6fa3a-104">O compilador emite esse aviso porque o uso de um tipo não compatível com CLS como uma restrição de tipo genérico pode tornar impossível para código escrito em alguns idiomas para consumir sua classe genérica.</span><span class="sxs-lookup"><span data-stu-id="6fa3a-104">The compiler issues this warning because the use of a non-CLS-compliant type as a generic type constraint could make it impossible for code written in some languages to consume your generic class.</span></span>  
  
### <a name="to-eliminate-this-warning"></a><span data-ttu-id="6fa3a-105">Para eliminar esse aviso</span><span class="sxs-lookup"><span data-stu-id="6fa3a-105">To eliminate this warning</span></span>  
  
1.  <span data-ttu-id="6fa3a-106">Use um tipo compatível com CLS para a restrição de tipo.</span><span class="sxs-lookup"><span data-stu-id="6fa3a-106">Use a CLS-compliant type for the type constraint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fa3a-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6fa3a-107">Example</span></span>  
 <span data-ttu-id="6fa3a-108">O exemplo a seguir gera CS3024 em vários locais:</span><span class="sxs-lookup"><span data-stu-id="6fa3a-108">The following example generates CS3024 in several locations:</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="6fa3a-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6fa3a-109">See Also</span></span>  
 [<span data-ttu-id="6fa3a-110">Restrições a parâmetros de tipo</span><span class="sxs-lookup"><span data-stu-id="6fa3a-110">Constraints on Type Parameters</span></span>](../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
