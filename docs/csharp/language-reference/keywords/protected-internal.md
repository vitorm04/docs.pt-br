---
title: "protegidos internos (referência de c#)"
ms.date: 11/15/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
author: sputier
ms.author: wiwagn
ms.openlocfilehash: f9004a5e8d65179c9ff2e30688e63c14c95ab431
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="68e3b-102">protegidos internos (referência de c#)</span><span class="sxs-lookup"><span data-stu-id="68e3b-102">protected internal (C# Reference)</span></span>
<span data-ttu-id="68e3b-103">O `protected internal` combinação de palavra-chave é um modificador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="68e3b-103">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="68e3b-104">Um membro interno protegido é acessível a partir do assembly atual ou de tipos que derivam da classe que contém.</span><span class="sxs-lookup"><span data-stu-id="68e3b-104">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="68e3b-105">Para obter uma comparação de `protected internal` com os outros modificadores de acesso, consulte [Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="68e3b-105">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
   
## <a name="example"></a><span data-ttu-id="68e3b-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68e3b-106">Example</span></span>  
 <span data-ttu-id="68e3b-107">Um membro interno protegido de uma classe base é acessível de qualquer tipo em seu assembly que contém.</span><span class="sxs-lookup"><span data-stu-id="68e3b-107">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="68e3b-108">Ela também é acessível em uma classe derivada, localizada em outro assembly somente se o acesso ocorre por meio de uma variável do tipo de classe derivada.</span><span class="sxs-lookup"><span data-stu-id="68e3b-108">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="68e3b-109">Por exemplo, considere o seguinte segmento de código:</span><span class="sxs-lookup"><span data-stu-id="68e3b-109">For example, consider the following code segment:</span></span>  

```
// Assembly1.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   protected internal int myValue = 0;  
}

class TestAccess 
{
    void Access()
    {
        BaseClass baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}  
```  
  
```  
// Assembly2.cs  
// Compile with: /reference:Assembly1.dll  
class DerivedClass : BaseClass   
{  
    static void Main()
    {
        BaseClass baseObject = new BaseClass();
        DerivedClass derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10; 

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
} 
```  
 <span data-ttu-id="68e3b-110">Este exemplo contém dois arquivos, `Assembly1.cs` e `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="68e3b-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span> <span data-ttu-id="68e3b-111">O primeiro arquivo contém uma classe base pública `BaseClass`e outra classe, `TestAccess`.</span><span class="sxs-lookup"><span data-stu-id="68e3b-111">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="68e3b-112">`BaseClass`possui um membro interno protegido, `myValue`, que é acessado pelo `TestAccess` tipo.</span><span class="sxs-lookup"><span data-stu-id="68e3b-112">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span> <span data-ttu-id="68e3b-113">No segundo arquivo, uma tentativa de acessar `myValue` por meio de uma instância de `BaseClass` produzirá um erro, enquanto um acesso a esse membro por meio de uma instância de uma classe derivada, `DerivedClass` será bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="68e3b-113">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span> 

 <span data-ttu-id="68e3b-114">Membros de estrutura não podem ser `protected internal` porque a estrutura não pode ser herdada.</span><span class="sxs-lookup"><span data-stu-id="68e3b-114">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="68e3b-115">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="68e3b-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="68e3b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68e3b-116">See Also</span></span>  
 <span data-ttu-id="68e3b-117">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="68e3b-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="68e3b-118">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="68e3b-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="68e3b-119">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="68e3b-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="68e3b-120">[Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="68e3b-120">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="68e3b-121">[Níveis de Acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="68e3b-121">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="68e3b-122">[Modificadores](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="68e3b-122">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="68e3b-123">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="68e3b-123">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="68e3b-124">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="68e3b-124">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="68e3b-125">[internal](../../../csharp/language-reference/keywords/internal.md) </span><span class="sxs-lookup"><span data-stu-id="68e3b-125">[internal](../../../csharp/language-reference/keywords/internal.md) </span></span>  
 <span data-ttu-id="68e3b-126">[Questões de segurança para palavras-chave virtual internas](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="68e3b-126">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>
