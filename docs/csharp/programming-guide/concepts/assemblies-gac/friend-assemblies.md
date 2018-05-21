---
title: Assemblies amigáveis (C#)
ms.date: 07/20/2015
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
ms.openlocfilehash: c9265a6ce53d97f1d0b8aaeb0f1aae3b7b75f2cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="friend-assemblies-c"></a><span data-ttu-id="76cca-102">Assemblies amigáveis (C#)</span><span class="sxs-lookup"><span data-stu-id="76cca-102">Friend Assemblies (C#)</span></span>
<span data-ttu-id="76cca-103">Um *assembly amigável* é um assembly que pode acessar os membros e tipos [internos](../../../../csharp/language-reference/keywords/internal.md) de outro assembly.</span><span class="sxs-lookup"><span data-stu-id="76cca-103">A *friend assembly* is an assembly that can access another assembly's [internal](../../../../csharp/language-reference/keywords/internal.md) types and members.</span></span> <span data-ttu-id="76cca-104">Se você identificar um assembly como um assembly amigável, não precisará marcar os tipos e membros como públicos para que eles sejam acessados por outros assemblies.</span><span class="sxs-lookup"><span data-stu-id="76cca-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="76cca-105">Isso é especialmente conveniente nos seguintes cenários:</span><span class="sxs-lookup"><span data-stu-id="76cca-105">This is especially convenient in the following scenarios:</span></span>  
  
-   <span data-ttu-id="76cca-106">Durante os testes de unidade, quando o código de teste é executado em um assembly separado, mas requer acesso a membros no assembly sendo testado que são marcados como `internal`.</span><span class="sxs-lookup"><span data-stu-id="76cca-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` .</span></span>  
  
-   <span data-ttu-id="76cca-107">Quando você está desenvolvendo uma biblioteca de classes e as adições à biblioteca estão contidas em assemblies separados, mas exigem acesso a membros em assemblies existentes que são marcados como `internal`.</span><span class="sxs-lookup"><span data-stu-id="76cca-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` .</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76cca-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="76cca-108">Remarks</span></span>  
 <span data-ttu-id="76cca-109">Você pode usar o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para identificar um ou mais assemblies amigáveis para um determinado assembly.</span><span class="sxs-lookup"><span data-stu-id="76cca-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="76cca-110">O exemplo a seguir usa o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> no assembly A e especifica o assembly `AssemblyB` como um assembly amigável.</span><span class="sxs-lookup"><span data-stu-id="76cca-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in assembly A and specifies assembly `AssemblyB` as a friend assembly.</span></span> <span data-ttu-id="76cca-111">Isso fornece ao assembly `AssemblyB` acesso a todos os tipos e membros no assembly A que são marcados como `internal`.</span><span class="sxs-lookup"><span data-stu-id="76cca-111">This gives assembly `AssemblyB` access to all types and members in assembly A that are marked as `internal`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76cca-112">Quando você compila um assembly (assembly `AssemblyB`) que acessará tipos internos ou membros internos de outro assembly (assembly *A*), deve especificar explicitamente o nome do arquivo de saída (.exe ou .dll) usando a opção do compilador **/out**.</span><span class="sxs-lookup"><span data-stu-id="76cca-112">When you compile an assembly (assembly `AssemblyB`) that will access internal types or internal members of another assembly (assembly *A*), you must explicitly specify the name of the output file (.exe or .dll) by using the **/out** compiler option.</span></span> <span data-ttu-id="76cca-113">Isso é necessário porque o compilador ainda não gerou o nome do assembly que está compilando no momento em que ele está se associando às referências externas.</span><span class="sxs-lookup"><span data-stu-id="76cca-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="76cca-114">Para obter mais informações, consulte [/out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="76cca-114">For more information, see [/out (C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) .</span></span>  
  
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
  
 <span data-ttu-id="76cca-115">Apenas os assemblies que você especificar explicitamente como amigáveis podem acessar os membros e tipos `internal`.</span><span class="sxs-lookup"><span data-stu-id="76cca-115">Only assemblies that you explicitly specify as friends can access `internal` types and members.</span></span> <span data-ttu-id="76cca-116">Por exemplo, se o assembly B é um amigo do assembly A e o assembly C faz referência ao assembly B, C não tem acesso aos tipos `internal` em A.</span><span class="sxs-lookup"><span data-stu-id="76cca-116">For example, if assembly B is a friend of assembly A and assembly C references assembly B, C does not have access to `internal` types in A.</span></span>  
  
 <span data-ttu-id="76cca-117">O compilador executa algumas validações básicas do nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="76cca-117">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="76cca-118">Se o assembly *A* declara o *B* como um assembly amigável, as regras de validação são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="76cca-118">If assembly *A* declares *B* as a friend assembly, the validation rules are as follows:</span></span>  
  
-   <span data-ttu-id="76cca-119">Se o assembly *A* for fortemente nomeado, o assembly *B* também deverá ser fortemente nomeado.</span><span class="sxs-lookup"><span data-stu-id="76cca-119">If assembly *A* is strong named, assembly *B* must also be strong named.</span></span> <span data-ttu-id="76cca-120">O nome do assembly amigável passado para o atributo deve consistir no nome do assembly e a chave pública da chave de nome forte usada para assinar o assembly *B*.</span><span class="sxs-lookup"><span data-stu-id="76cca-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign assembly *B*.</span></span>  
  
     <span data-ttu-id="76cca-121">O nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> não pode ser o nome forte do assembly *B*: não inclua a versão, cultura, arquitetura ou token de chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="76cca-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of assembly *B*: do not include the assembly version, culture, architecture, or public key token.</span></span>  
  
-   <span data-ttu-id="76cca-122">Se o assembly *A* não tiver um nome forte, o nome do assembly amigável deverá consistir apenas no nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="76cca-122">If assembly *A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="76cca-123">Para obter mais informações, consulte [Como criar assemblies amigáveis não assinados (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="76cca-123">For more information, see [How to: Create Unsigned Friend Assemblies (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span></span>  
  
-   <span data-ttu-id="76cca-124">Se o assembly *B* tiver um nome forte, você deverá especificara a chave de nome forte do assembly *B* usando a configuração do projeto ou a opção do compilador `/keyfile` de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="76cca-124">If assembly *B* is strong named, you must specify the strong-name key for assembly *B* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="76cca-125">Para obter mais informações, consulte [Como criar assemblies amigáveis assinados (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="76cca-125">For more information, see [How to: Create Signed Friend Assemblies (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span></span>  
  
 <span data-ttu-id="76cca-126">A classe <xref:System.Security.Permissions.StrongNameIdentityPermission> também fornece a capacidade de compartilhar tipos, com as seguintes diferenças:</span><span class="sxs-lookup"><span data-stu-id="76cca-126">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>  
  
-   <span data-ttu-id="76cca-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> aplica-se a um tipo individual, enquanto um assembly amigável se aplica ao assembly inteiro.</span><span class="sxs-lookup"><span data-stu-id="76cca-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>  
  
-   <span data-ttu-id="76cca-128">Se há centenas de tipos no assembly *A* que você deseja compartilhar como o assembly *B*, é necessário adicionar <xref:System.Security.Permissions.StrongNameIdentityPermission> a todos eles.</span><span class="sxs-lookup"><span data-stu-id="76cca-128">If there are hundreds of types in assembly *A* that you want to share with assembly *B*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="76cca-129">Se usar um assembly amigável, você precisará declarar a relação de amigo uma vez.</span><span class="sxs-lookup"><span data-stu-id="76cca-129">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>  
  
-   <span data-ttu-id="76cca-130">Se você usar <xref:System.Security.Permissions.StrongNameIdentityPermission>, os tipos que você desejar compartilhar precisarão ser declarados como públicos.</span><span class="sxs-lookup"><span data-stu-id="76cca-130">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="76cca-131">Se você usar um assembly amigável, os tipos compartilhados serão declarados como `internal`.</span><span class="sxs-lookup"><span data-stu-id="76cca-131">If you use a friend assembly, the shared types are declared as `internal`.</span></span>  
  
 <span data-ttu-id="76cca-132">Para obter informações sobre como acessar os métodos e tipos `internal` de um assembly de um arquivo de módulo (um arquivo com a extensão .netmodule), consulte [/moduleassemblyname (C#)](../../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="76cca-132">For information about how to access an assembly's `internal` types and methods from a module file (a file with the .netmodule extension), see [/moduleassemblyname (C#)](../../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76cca-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76cca-133">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 <xref:System.Security.Permissions.StrongNameIdentityPermission>  
 [<span data-ttu-id="76cca-134">Como criar assemblies amigáveis não assinados (C#)</span><span class="sxs-lookup"><span data-stu-id="76cca-134">How to: Create Unsigned Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [<span data-ttu-id="76cca-135">Como criar assemblies amigáveis assinados (C#)</span><span class="sxs-lookup"><span data-stu-id="76cca-135">How to: Create Signed Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [<span data-ttu-id="76cca-136">Assemblies e o Cache de Assembly Global (C#)</span><span class="sxs-lookup"><span data-stu-id="76cca-136">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="76cca-137">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="76cca-137">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
