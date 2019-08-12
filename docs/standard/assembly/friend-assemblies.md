---
title: Assemblies amigáveis (C#)
ms.date: 03/03/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
ms.openlocfilehash: 770eb70a5350d7d26e03cb4e605b442100da2a53
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68671191"
---
# <a name="friend-assemblies"></a><span data-ttu-id="ba982-102">Assemblies amigáveis</span><span class="sxs-lookup"><span data-stu-id="ba982-102">Friend assemblies</span></span>

<span data-ttu-id="ba982-103">Um *assembly amigável* é um assembly que pode acessar os membros e tipos [internos](../../csharp/language-reference/keywords/internal.md) de outro assembly (no C# ou [Amigável](../../visual-basic/language-reference/modifiers/friend.md) no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ba982-103">A *friend assembly* is an assembly that can access another assembly's [internal](../../csharp/language-reference/keywords/internal.md) (in C# or [Friend](../../visual-basic/language-reference/modifiers/friend.md) in Visual Basic) types and members.</span></span> <span data-ttu-id="ba982-104">Se você identificar um assembly como um assembly amigável, não precisará marcar os tipos e membros como públicos para que eles sejam acessados por outros assemblies.</span><span class="sxs-lookup"><span data-stu-id="ba982-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="ba982-105">Isso é especialmente conveniente nos seguintes cenários:</span><span class="sxs-lookup"><span data-stu-id="ba982-105">This is especially convenient in the following scenarios:</span></span>

- <span data-ttu-id="ba982-106">Durante os testes de unidade, quando o código de teste é executado em um assembly separado, mas exige acesso aos membros do assembly sendo testado que são marcados como `internal` no C# ou `Friend` no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ba982-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

- <span data-ttu-id="ba982-107">Quando você está desenvolvendo uma biblioteca de classes e as adições à biblioteca estão contidas em assemblies separados, mas exigem acesso a membros em assemblies existentes que são marcados como `internal` no C# ou `Friend` no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ba982-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

## <a name="remarks"></a><span data-ttu-id="ba982-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="ba982-108">Remarks</span></span>

<span data-ttu-id="ba982-109">Você pode usar o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para identificar um ou mais assemblies amigáveis para um determinado assembly.</span><span class="sxs-lookup"><span data-stu-id="ba982-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="ba982-110">O exemplo a seguir usa o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> no assembly A e especifica o assembly `AssemblyB` como um assembly amigável.</span><span class="sxs-lookup"><span data-stu-id="ba982-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in assembly A and specifies assembly `AssemblyB` as a friend assembly.</span></span> <span data-ttu-id="ba982-111">Isso fornece ao assembly `AssemblyB` acesso a todos os tipos e membros do assembly A que são marcados como `internal` no C# ou `Friend` no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ba982-111">This gives assembly `AssemblyB` access to all types and members in assembly A that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

> [!NOTE]
> <span data-ttu-id="ba982-112">Quando você compila um assembly (assembly `AssemblyB`) que acessará tipos internos ou membros internos de outro assembly (assembly *A*), deve especificar explicitamente o nome do arquivo de saída (.exe ou .dll) usando a opção do compilador **/out**.</span><span class="sxs-lookup"><span data-stu-id="ba982-112">When you compile an assembly (assembly `AssemblyB`) that will access internal types or internal members of another assembly (assembly *A*), you must explicitly specify the name of the output file (.exe or .dll) by using the **/out** compiler option.</span></span> <span data-ttu-id="ba982-113">Isso é necessário porque o compilador ainda não gerou o nome do assembly que está compilando no momento em que ele está se associando às referências externas.</span><span class="sxs-lookup"><span data-stu-id="ba982-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="ba982-114">Para obter mais informações, confira [/out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [/out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="ba982-114">For more information, see [/out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [/out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="ba982-115">C#</span><span class="sxs-lookup"><span data-stu-id="ba982-115">C#</span></span>](#tab/csharp)

```csharp
using System.Runtime.CompilerServices;
using System;

[assembly: InternalsVisibleTo("AssemblyB")]

// The class is internal by default.
class FriendClass
{
    public void Test()
    {
        Console.WriteLine("Sample Class");
    }
}

// Public class that has an internal method.
public class ClassWithFriendMethod
{
    internal void Test()
    {
        Console.WriteLine("Sample Method");
    }

}
```

# <a name="visual-basictabvb"></a>[<span data-ttu-id="ba982-116">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ba982-116">Visual Basic</span></span>](#tab/vb)

```vb
Imports System.Runtime.CompilerServices
Imports System
<Assembly: InternalsVisibleTo("AssemblyB")>

' Friend class.
Friend Class FriendClass
    Public Sub Test()
        Console.WriteLine("Sample Class")
    End Sub
End Class

' Public class with a Friend method.
Public Class ClassWithFriendMethod
    Friend Sub Test()
        Console.WriteLine("Sample Method")
    End Sub
End Class
```

---

<span data-ttu-id="ba982-117">Apenas os assemblies que você especificar explicitamente como amigáveis podem acessar os membros e os tipos `internal` (no C# ou `Friend` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ba982-117">Only assemblies that you explicitly specify as friends can access `internal` (in C# or `Friend` in Visual Basic) types and members.</span></span> <span data-ttu-id="ba982-118">Por exemplo, se o assembly B for amigável para o assembly A e o assembly C fizer referência ao assembly B, C não terá acesso aos tipos `internal` (no C# ou `Friend` no Visual Basic) de A.</span><span class="sxs-lookup"><span data-stu-id="ba982-118">For example, if assembly B is a friend of assembly A and assembly C references assembly B, C does not have access to `internal` (in C# or `Friend` in Visual Basic) types in A.</span></span>

<span data-ttu-id="ba982-119">O compilador executa algumas validações básicas do nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ba982-119">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="ba982-120">Se o assembly *A* declara o *B* como um assembly amigável, as regras de validação são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="ba982-120">If assembly *A* declares *B* as a friend assembly, the validation rules are as follows:</span></span>

- <span data-ttu-id="ba982-121">Se o assembly *A* for fortemente nomeado, o assembly *B* também deverá ser fortemente nomeado.</span><span class="sxs-lookup"><span data-stu-id="ba982-121">If assembly *A* is strong named, assembly *B* must also be strong named.</span></span> <span data-ttu-id="ba982-122">O nome do assembly amigável passado para o atributo deve consistir no nome do assembly e a chave pública da chave de nome forte usada para assinar o assembly *B*.</span><span class="sxs-lookup"><span data-stu-id="ba982-122">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign assembly *B*.</span></span>

     <span data-ttu-id="ba982-123">O nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> não pode ser o nome forte do assembly *B*: não inclua a versão, cultura, arquitetura ou token de chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="ba982-123">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of assembly *B*: do not include the assembly version, culture, architecture, or public key token.</span></span>

- <span data-ttu-id="ba982-124">Se o assembly *A* não tiver um nome forte, o nome do assembly amigável deverá consistir apenas no nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="ba982-124">If assembly *A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="ba982-125">Para obter mais informações, confira [Como: Como criar assemblies amigáveis sem sinal (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) ou [Como: Criar assemblies amigáveis sem sinal (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="ba982-125">For more information, see [How to: Create Unsigned Friend Assemblies (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) or [How to: Create Unsigned Friend Assemblies (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span></span>

- <span data-ttu-id="ba982-126">Se o assembly *B* tiver um nome forte, você deverá especificara a chave de nome forte do assembly *B* usando a configuração do projeto ou a opção do compilador `/keyfile` de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="ba982-126">If assembly *B* is strong named, you must specify the strong-name key for assembly *B* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="ba982-127">Para obter mais informações, confira [Como: Criar assemblies amigáveis com sinal (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) ou [Como: Criar assemblies amigáveis com sinal (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="ba982-127">For more information, see [How to: Create Signed Friend Assemblies (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) or [How to: Create Signed Friend Assemblies (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span></span>

 <span data-ttu-id="ba982-128">A classe <xref:System.Security.Permissions.StrongNameIdentityPermission> também fornece a capacidade de compartilhar tipos, com as seguintes diferenças:</span><span class="sxs-lookup"><span data-stu-id="ba982-128">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>

- <span data-ttu-id="ba982-129"><xref:System.Security.Permissions.StrongNameIdentityPermission> aplica-se a um tipo individual, enquanto um assembly amigável se aplica ao assembly inteiro.</span><span class="sxs-lookup"><span data-stu-id="ba982-129"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>

- <span data-ttu-id="ba982-130">Se há centenas de tipos no assembly *A* que você deseja compartilhar como o assembly *B*, é necessário adicionar <xref:System.Security.Permissions.StrongNameIdentityPermission> a todos eles.</span><span class="sxs-lookup"><span data-stu-id="ba982-130">If there are hundreds of types in assembly *A* that you want to share with assembly *B*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="ba982-131">Se usar um assembly amigável, você precisará declarar a relação de amigo uma vez.</span><span class="sxs-lookup"><span data-stu-id="ba982-131">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>

- <span data-ttu-id="ba982-132">Se você usar <xref:System.Security.Permissions.StrongNameIdentityPermission>, os tipos que você desejar compartilhar precisarão ser declarados como públicos.</span><span class="sxs-lookup"><span data-stu-id="ba982-132">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="ba982-133">Se você usar um assembly amigável, os tipos compartilhados serão declarados como `internal` (no C# ou `Friend` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ba982-133">If you use a friend assembly, the shared types are declared as `internal` (in C# or `Friend` in Visual Basic).</span></span>

<span data-ttu-id="ba982-134">Para obter informações sobre como acessar os métodos e os tipos `internal` (no C# ou `Friend` no Visual Basic) de um assembly em um arquivo de módulo (um arquivo com a extensão .netmodule), confira [/moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) ou [/moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span><span class="sxs-lookup"><span data-stu-id="ba982-134">For information about how to access an assembly's `internal` (in C# or `Friend` in Visual Basic) types and methods from a module file (a file with the .netmodule extension), see [/moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) or [/moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ba982-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba982-135">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [<span data-ttu-id="ba982-136">Como: Criar assemblies amigáveis sem sinal (C#)</span><span class="sxs-lookup"><span data-stu-id="ba982-136">How to: Create Unsigned Friend Assemblies (C#)</span></span>](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [<span data-ttu-id="ba982-137">Como: Criar assemblies amigáveis sem sinal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba982-137">How to: Create Unsigned Friend Assemblies (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [<span data-ttu-id="ba982-138">Como: Criar assemblies amigáveis com sinal (C#)</span><span class="sxs-lookup"><span data-stu-id="ba982-138">How to: Create Signed Friend Assemblies (C#)</span></span>](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [<span data-ttu-id="ba982-139">Como: Criar assemblies amigáveis com sinal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba982-139">How to: Create Signed Friend Assemblies (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [<span data-ttu-id="ba982-140">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="ba982-140">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="ba982-141">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="ba982-141">C# Programming Guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ba982-142">Conceitos de Programação</span><span class="sxs-lookup"><span data-stu-id="ba982-142">Programming Concepts</span></span>](../../visual-basic/programming-guide/concepts/index.md)
