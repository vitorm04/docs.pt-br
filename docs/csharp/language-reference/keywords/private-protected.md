---
title: private protected – Referência de C#
ms.date: 11/15/2017
f1_keywords:
- privateprotected_CSharpKeyword
author: sputier
ms.openlocfilehash: 94ef55d7e13841f81b036f52659b215e22a3a0d7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301795"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="2502c-102">private protected (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="2502c-102">private protected (C# Reference)</span></span>

<span data-ttu-id="2502c-103">A combinação de palavras-chave `private protected` é um modificador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="2502c-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="2502c-104">Um membro particular protegido é acessível por tipos derivados da classe recipiente, mas apenas dentro de seu assembly recipiente.</span><span class="sxs-lookup"><span data-stu-id="2502c-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="2502c-105">Para obter uma comparação de `private protected` com os outros modificadores de acesso, consulte [Níveis de acessibilidade](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2502c-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

> [!NOTE]
> <span data-ttu-id="2502c-106">O modificador de acesso `private protected` é válido no C# versão 7.2 e posterior.</span><span class="sxs-lookup"><span data-stu-id="2502c-106">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>

## <a name="example"></a><span data-ttu-id="2502c-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2502c-107">Example</span></span>

<span data-ttu-id="2502c-108">Um membro particular protegido de uma classe base é acessível de tipos derivados em seu assembly recipiente apenas se o tipo estático da variável é o tipo da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="2502c-108">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="2502c-109">Por exemplo, considere o seguinte segmento de código:</span><span class="sxs-lookup"><span data-stu-id="2502c-109">For example, consider the following code segment:</span></span>

```csharp
public class BaseClass
{
    private protected int myValue = 0;
}

public class DerivedClass1 : BaseClass
{
    void Access()
    {
        var baseObject = new BaseClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 5;

        // OK, accessed through the current derived class instance
        myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass2 : BaseClass
{
    void Access()
    {
        // Error CS0122, because myValue can only be
        // accessed by types in Assembly1
        // myValue = 10;
    }
}
```

<span data-ttu-id="2502c-110">Este exemplo contém dois arquivos, `Assembly1.cs` e `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="2502c-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="2502c-111">O primeiro arquivo contém uma classe base pública, `BaseClass`, e um tipo derivado dela, `DerivedClass1`.</span><span class="sxs-lookup"><span data-stu-id="2502c-111">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="2502c-112">`BaseClass` tem um membro particular protegido, `myValue`, que `DerivedClass1` tenta acessar de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="2502c-112">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="2502c-113">A primeira tentativa de acessar `myValue` por meio de uma instância de `BaseClass` produzirá um erro.</span><span class="sxs-lookup"><span data-stu-id="2502c-113">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="2502c-114">No entanto, a tentativa de usá-lo como um membro herdado em `DerivedClass1` terá êxito.</span><span class="sxs-lookup"><span data-stu-id="2502c-114">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>

<span data-ttu-id="2502c-115">No segundo arquivo, uma tentativa de acessar `myValue` como um membro herdado de `DerivedClass2` produzirá um erro, pois ele é acessível apenas por tipos derivados em Assembly1.</span><span class="sxs-lookup"><span data-stu-id="2502c-115">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span>

<span data-ttu-id="2502c-116">Se `Assembly1.cs` contiver um <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> nome que `Assembly2` , a classe derivada terá `DerivedClass1` acesso aos `private protected` membros declarados em `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="2502c-116">If `Assembly1.cs` contains an <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> that names `Assembly2`, the derived class `DerivedClass1` will have access to `private protected` members declared in `BaseClass`.</span></span> <span data-ttu-id="2502c-117">`InternalsVisibleTo`torna `private protected` os membros visíveis para classes derivadas em outros assemblies.</span><span class="sxs-lookup"><span data-stu-id="2502c-117">`InternalsVisibleTo` makes `private protected` members visible to derived classes in other assemblies.</span></span>

<span data-ttu-id="2502c-118">Membros de struct não podem ser `private protected` porque o struct não pode ser herdado.</span><span class="sxs-lookup"><span data-stu-id="2502c-118">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2502c-119">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="2502c-119">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="2502c-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="2502c-120">See also</span></span>

- [<span data-ttu-id="2502c-121">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="2502c-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2502c-122">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="2502c-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2502c-123">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="2502c-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2502c-124">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="2502c-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="2502c-125">Níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="2502c-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="2502c-126">Modificadores</span><span class="sxs-lookup"><span data-stu-id="2502c-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="2502c-127">público</span><span class="sxs-lookup"><span data-stu-id="2502c-127">public</span></span>](public.md)
- [<span data-ttu-id="2502c-128">pessoal</span><span class="sxs-lookup"><span data-stu-id="2502c-128">private</span></span>](private.md)
- [<span data-ttu-id="2502c-129">internal</span><span class="sxs-lookup"><span data-stu-id="2502c-129">internal</span></span>](internal.md)
- <span data-ttu-id="2502c-130">[Questões de segurança de palavras-chave virtuais internas](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2502c-130">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
