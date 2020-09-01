---
description: protected internal (referência do C#)
title: protected internal (referência do C#)
ms.date: 11/15/2017
f1_keywords:
- protectedinternal_CSharpKeyword
author: sputier
ms.openlocfilehash: a7537fba93c0d7145f04c6236d15c11b70f8bf98
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139431"
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="d90bc-103">protected internal (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="d90bc-103">protected internal (C# Reference)</span></span>

<span data-ttu-id="d90bc-104">A combinação de palavras-chave `protected internal` é um modificador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="d90bc-104">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="d90bc-105">Um membro protegido interno é acessível no assembly atual ou nos tipos que derivam da classe recipiente.</span><span class="sxs-lookup"><span data-stu-id="d90bc-105">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="d90bc-106">Para obter uma comparação de `protected internal` com os outros modificadores de acesso, consulte [Níveis de acessibilidade](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="d90bc-106">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="d90bc-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d90bc-107">Example</span></span>

<span data-ttu-id="d90bc-108">Um membro protegido interno de uma classe base é acessível em qualquer tipo em seu assembly recipiente.</span><span class="sxs-lookup"><span data-stu-id="d90bc-108">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="d90bc-109">Ele também é acessível em uma classe derivada localizada em outro assembly somente se o acesso ocorre por meio de uma variável do tipo de classe derivada.</span><span class="sxs-lookup"><span data-stu-id="d90bc-109">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="d90bc-110">Por exemplo, considere o seguinte segmento de código:</span><span class="sxs-lookup"><span data-stu-id="d90bc-110">For example, consider the following code segment:</span></span>

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

<span data-ttu-id="d90bc-111">Este exemplo contém dois arquivos, `Assembly1.cs` e `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="d90bc-111">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="d90bc-112">O primeiro arquivo contém uma classe base pública, `BaseClass`, e outra classe, `TestAccess`.</span><span class="sxs-lookup"><span data-stu-id="d90bc-112">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="d90bc-113">`BaseClass` tem um membro interno protegido, `myValue`, que é acessado pelo tipo `TestAccess`.</span><span class="sxs-lookup"><span data-stu-id="d90bc-113">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span>
<span data-ttu-id="d90bc-114">No segundo arquivo, uma tentativa de acessar `myValue` por meio de uma instância de `BaseClass` produzirá um erro, enquanto um acesso a esse membro por meio de uma instância de uma classe derivada, `DerivedClass`, terá êxito.</span><span class="sxs-lookup"><span data-stu-id="d90bc-114">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span>

<span data-ttu-id="d90bc-115">Membros de struct não podem ser `protected internal` porque o struct não pode ser herdado.</span><span class="sxs-lookup"><span data-stu-id="d90bc-115">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d90bc-116">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d90bc-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d90bc-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="d90bc-117">See also</span></span>

- [<span data-ttu-id="d90bc-118">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="d90bc-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d90bc-119">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="d90bc-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d90bc-120">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="d90bc-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d90bc-121">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="d90bc-121">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="d90bc-122">Níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="d90bc-122">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="d90bc-123">Modificadores</span><span class="sxs-lookup"><span data-stu-id="d90bc-123">Modifiers</span></span>](index.md)
- [<span data-ttu-id="d90bc-124">public</span><span class="sxs-lookup"><span data-stu-id="d90bc-124">public</span></span>](public.md)
- [<span data-ttu-id="d90bc-125">particulares</span><span class="sxs-lookup"><span data-stu-id="d90bc-125">private</span></span>](private.md)
- [<span data-ttu-id="d90bc-126">interno</span><span class="sxs-lookup"><span data-stu-id="d90bc-126">internal</span></span>](internal.md)
- <span data-ttu-id="d90bc-127">[Questões de segurança de palavras-chave virtuais internas](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d90bc-127">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
