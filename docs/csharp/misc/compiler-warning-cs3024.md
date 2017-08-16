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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 92c533d2fc5b5d9f6add118013a68918a7ad9ef1
ms.lasthandoff: 03/13/2017

---
# <a name="compiler-warning-cs3024"></a>CS3024 de aviso do compilador
Tipo de restrição 'type' não é compatível com CLS.  
  
 O compilador emite esse aviso porque o uso de um tipo não compatível com CLS como uma restrição de tipo genérico pode tornar impossível para código escrito em alguns idiomas para consumir sua classe genérica.  
  
### <a name="to-eliminate-this-warning"></a>Para eliminar esse aviso  
  
1.  Use um tipo compatível com CLS para a restrição de tipo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir gera CS3024 em vários locais:  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Restrições a parâmetros de tipo](../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
