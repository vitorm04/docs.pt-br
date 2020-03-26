---
title: private protected – Referência de C#
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 01a8b716ce87a63a50a92a25b2842f7bb12d4c9f
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134361"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="2be91-102">private protected (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="2be91-102">private protected (C# Reference)</span></span>

<span data-ttu-id="2be91-103">A combinação de palavras-chave `private protected` é um modificador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="2be91-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="2be91-104">Um membro particular protegido é acessível por tipos derivados da classe recipiente, mas apenas dentro de seu assembly recipiente.</span><span class="sxs-lookup"><span data-stu-id="2be91-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="2be91-105">Para obter uma comparação de `private protected` com os outros modificadores de acesso, consulte [Níveis de acessibilidade](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2be91-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

> [!NOTE]
> <span data-ttu-id="2be91-106">O modificador de acesso `private protected` é válido no C# versão 7.2 e posterior.</span><span class="sxs-lookup"><span data-stu-id="2be91-106">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>

## <a name="example"></a><span data-ttu-id="2be91-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2be91-107">Example</span></span>

<span data-ttu-id="2be91-108">Um membro particular protegido de uma classe base é acessível de tipos derivados em seu assembly recipiente apenas se o tipo estático da variável é o tipo da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="2be91-108">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="2be91-109">Por exemplo, considere o seguinte segmento de código:</span><span class="sxs-lookup"><span data-stu-id="2be91-109">For example, consider the following code segment:</span></span>  

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

<span data-ttu-id="2be91-110">Este exemplo contém dois arquivos, `Assembly1.cs` e `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="2be91-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="2be91-111">O primeiro arquivo contém uma classe base pública, `BaseClass`, e um tipo derivado dela, `DerivedClass1`.</span><span class="sxs-lookup"><span data-stu-id="2be91-111">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="2be91-112">`BaseClass` tem um membro particular protegido, `myValue`, que `DerivedClass1` tenta acessar de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="2be91-112">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="2be91-113">A primeira tentativa de acessar `myValue` por meio de uma instância de `BaseClass` produzirá um erro.</span><span class="sxs-lookup"><span data-stu-id="2be91-113">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="2be91-114">No entanto, a tentativa de usá-lo como um membro herdado em `DerivedClass1` terá êxito.</span><span class="sxs-lookup"><span data-stu-id="2be91-114">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>
<span data-ttu-id="2be91-115">No segundo arquivo, uma tentativa de acessar `myValue` como um membro herdado de `DerivedClass2` produzirá um erro, pois ele é acessível apenas por tipos derivados em Assembly1.</span><span class="sxs-lookup"><span data-stu-id="2be91-115">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span>

<span data-ttu-id="2be91-116">Membros de struct não podem ser `private protected` porque o struct não pode ser herdado.</span><span class="sxs-lookup"><span data-stu-id="2be91-116">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="2be91-117">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="2be91-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a><span data-ttu-id="2be91-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="2be91-118">See also</span></span>

- [<span data-ttu-id="2be91-119">C# Referência</span><span class="sxs-lookup"><span data-stu-id="2be91-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2be91-120">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="2be91-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2be91-121">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="2be91-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2be91-122">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="2be91-122">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="2be91-123">Níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="2be91-123">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="2be91-124">Modificadores</span><span class="sxs-lookup"><span data-stu-id="2be91-124">Modifiers</span></span>](index.md)
- [<span data-ttu-id="2be91-125">público</span><span class="sxs-lookup"><span data-stu-id="2be91-125">public</span></span>](public.md)
- [<span data-ttu-id="2be91-126">Privada</span><span class="sxs-lookup"><span data-stu-id="2be91-126">private</span></span>](private.md)
- [<span data-ttu-id="2be91-127">Interno</span><span class="sxs-lookup"><span data-stu-id="2be91-127">internal</span></span>](internal.md)
- <span data-ttu-id="2be91-128">[Questões de segurança de palavras-chave virtuais internas](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2be91-128">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
