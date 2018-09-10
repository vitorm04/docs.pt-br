---
title: private protected (referência do C#)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 4a4ee999fe932674e854b1428ab33b33bc71d2ad
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518445"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="a89a2-102">private protected (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="a89a2-102">private protected (C# Reference)</span></span>

<span data-ttu-id="a89a2-103">A combinação de palavras-chave `private protected` é um modificador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="a89a2-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="a89a2-104">Um membro particular protegido é acessível por tipos derivados da classe recipiente, mas apenas dentro de seu assembly recipiente.</span><span class="sxs-lookup"><span data-stu-id="a89a2-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="a89a2-105">Para obter uma comparação de `private protected` com os outros modificadores de acesso, consulte [Níveis de acessibilidade](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a89a2-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a89a2-106">O modificador de acesso `private protected` é válido no C# versão 7.2 e posterior.</span><span class="sxs-lookup"><span data-stu-id="a89a2-106">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>

## <a name="example"></a><span data-ttu-id="a89a2-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a89a2-107">Example</span></span>

<span data-ttu-id="a89a2-108">Um membro particular protegido de uma classe base é acessível de tipos derivados em seu assembly recipiente apenas se o tipo estático da variável é o tipo da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="a89a2-108">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="a89a2-109">Por exemplo, considere o seguinte segmento de código:</span><span class="sxs-lookup"><span data-stu-id="a89a2-109">For example, consider the following code segment:</span></span>  

```csharp
// Assembly1.cs  
// Compile with: /target:library  
public class BaseClass
{
    private protected int myValue = 0;
}

public class DerivedClass1 : BaseClass
{
    void Access()
    {
        BaseClass baseObject = new BaseClass();

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

<span data-ttu-id="a89a2-110">Este exemplo contém dois arquivos, `Assembly1.cs` e `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="a89a2-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="a89a2-111">O primeiro arquivo contém uma classe base pública, `BaseClass`, e um tipo derivado dela, `DerivedClass1`.</span><span class="sxs-lookup"><span data-stu-id="a89a2-111">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="a89a2-112">`BaseClass` tem um membro particular protegido, `myValue`, que `DerivedClass1` tenta acessar de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="a89a2-112">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="a89a2-113">A primeira tentativa de acessar `myValue` por meio de uma instância de `BaseClass` produzirá um erro.</span><span class="sxs-lookup"><span data-stu-id="a89a2-113">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="a89a2-114">No entanto, a tentativa de usá-lo como um membro herdado em `DerivedClass1` terá êxito.</span><span class="sxs-lookup"><span data-stu-id="a89a2-114">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>
<span data-ttu-id="a89a2-115">No segundo arquivo, uma tentativa de acessar `myValue` como um membro herdado de `DerivedClass2` produzirá um erro, pois ele é acessível apenas por tipos derivados em Assembly1.</span><span class="sxs-lookup"><span data-stu-id="a89a2-115">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span>

<span data-ttu-id="a89a2-116">Membros de struct não podem ser `private protected` porque o struct não pode ser herdado.</span><span class="sxs-lookup"><span data-stu-id="a89a2-116">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="a89a2-117">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="a89a2-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a><span data-ttu-id="a89a2-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a89a2-118">See also</span></span>

- [<span data-ttu-id="a89a2-119">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a89a2-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a89a2-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a89a2-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a89a2-121">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="a89a2-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a89a2-122">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="a89a2-122">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="a89a2-123">Níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="a89a2-123">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="a89a2-124">Modificadores</span><span class="sxs-lookup"><span data-stu-id="a89a2-124">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="a89a2-125">public</span><span class="sxs-lookup"><span data-stu-id="a89a2-125">public</span></span>](public.md)
- [<span data-ttu-id="a89a2-126">private</span><span class="sxs-lookup"><span data-stu-id="a89a2-126">private</span></span>](private.md)
- [<span data-ttu-id="a89a2-127">internal</span><span class="sxs-lookup"><span data-stu-id="a89a2-127">internal</span></span>](internal.md)
- <span data-ttu-id="a89a2-128">[Questões de segurança de palavras-chave virtuais internas](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a89a2-128">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>