---
title: protected internal (referência do C#)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 877df74b51fb859043171619f5687ecddb8409d1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713190"
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="abfad-102">protected internal (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="abfad-102">protected internal (C# Reference)</span></span>

<span data-ttu-id="abfad-103">A combinação de palavras-chave `protected internal` é um modificador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="abfad-103">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="abfad-104">Um membro protegido interno é acessível no assembly atual ou nos tipos que derivam da classe recipiente.</span><span class="sxs-lookup"><span data-stu-id="abfad-104">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="abfad-105">Para obter uma comparação de `protected internal` com os outros modificadores de acesso, consulte [Níveis de acessibilidade](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="abfad-105">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="abfad-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="abfad-106">Example</span></span>

<span data-ttu-id="abfad-107">Um membro protegido interno de uma classe base é acessível em qualquer tipo em seu assembly recipiente.</span><span class="sxs-lookup"><span data-stu-id="abfad-107">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="abfad-108">Ele também é acessível em uma classe derivada localizada em outro assembly somente se o acesso ocorre por meio de uma variável do tipo de classe derivada.</span><span class="sxs-lookup"><span data-stu-id="abfad-108">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="abfad-109">Por exemplo, considere o seguinte segmento de código:</span><span class="sxs-lookup"><span data-stu-id="abfad-109">For example, consider the following code segment:</span></span>

```csharp
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
        var baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass : BaseClass
{
    static void Main()
    {
        var baseObject = new BaseClass();
        var derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10;

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
}
```

<span data-ttu-id="abfad-110">Este exemplo contém dois arquivos, `Assembly1.cs` e `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="abfad-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="abfad-111">O primeiro arquivo contém uma classe base pública, `BaseClass`, e outra classe, `TestAccess`.</span><span class="sxs-lookup"><span data-stu-id="abfad-111">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="abfad-112">`BaseClass` tem um membro interno protegido, `myValue`, que é acessado pelo tipo `TestAccess`.</span><span class="sxs-lookup"><span data-stu-id="abfad-112">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span>
<span data-ttu-id="abfad-113">No segundo arquivo, uma tentativa de acessar `myValue` por meio de uma instância de `BaseClass` produzirá um erro, enquanto um acesso a esse membro por meio de uma instância de uma classe derivada, `DerivedClass`, terá êxito.</span><span class="sxs-lookup"><span data-stu-id="abfad-113">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span>

<span data-ttu-id="abfad-114">Membros de struct não podem ser `protected internal` porque o struct não pode ser herdado.</span><span class="sxs-lookup"><span data-stu-id="abfad-114">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="abfad-115">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="abfad-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="abfad-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="abfad-116">See also</span></span>

- [<span data-ttu-id="abfad-117">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="abfad-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="abfad-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="abfad-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="abfad-119">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="abfad-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="abfad-120">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="abfad-120">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="abfad-121">Níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="abfad-121">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="abfad-122">Modificadores</span><span class="sxs-lookup"><span data-stu-id="abfad-122">Modifiers</span></span>](index.md)
- [<span data-ttu-id="abfad-123">public</span><span class="sxs-lookup"><span data-stu-id="abfad-123">public</span></span>](public.md)
- [<span data-ttu-id="abfad-124">private</span><span class="sxs-lookup"><span data-stu-id="abfad-124">private</span></span>](private.md)
- [<span data-ttu-id="abfad-125">internal</span><span class="sxs-lookup"><span data-stu-id="abfad-125">internal</span></span>](internal.md)
- <span data-ttu-id="abfad-126">[Questões de segurança de palavras-chave virtuais internas](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="abfad-126">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
