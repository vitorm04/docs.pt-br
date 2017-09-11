---
title: "Assemblies amigáveis (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 9b3d5716-e6e4-47a7-a3e9-084d7fba5c28
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 23c9167bf6a632b53202bdc56aebb2248065e967
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="friend-assemblies-visual-basic"></a><span data-ttu-id="a9af3-102">Assemblies amigáveis (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9af3-102">Friend Assemblies (Visual Basic)</span></span>
<span data-ttu-id="a9af3-103">A *assembly autorizado* é um assembly que pode acessar outro assembly [amigo](../../../../visual-basic/language-reference/modifiers/friend.md) tipos e membros.</span><span class="sxs-lookup"><span data-stu-id="a9af3-103">A *friend assembly* is an assembly that can access another assembly's [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) types and members.</span></span> <span data-ttu-id="a9af3-104">Se você identificar um assembly como um assembly autorizado, você não precisa marcar tipos e membros como público na ordem para que eles sejam acessados por outros assemblies.</span><span class="sxs-lookup"><span data-stu-id="a9af3-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="a9af3-105">Isso é especialmente conveniente nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="a9af3-105">This is especially convenient in the following scenarios:</span></span>  
  
-   <span data-ttu-id="a9af3-106">Durante testes de unidade, quando o código de teste é executado em um assembly separado mas requer acesso a membros no assembly que está sendo testado que são marcados como `Friend`.</span><span class="sxs-lookup"><span data-stu-id="a9af3-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `Friend`.</span></span>  
  
-   <span data-ttu-id="a9af3-107">Quando você estiver desenvolvendo uma biblioteca de classes e adições à biblioteca estão contidas em conjuntos separados, mas precisam acessar os membros existentes conjuntos de assemblies que são marcados como `Friend`.</span><span class="sxs-lookup"><span data-stu-id="a9af3-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `Friend`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9af3-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a9af3-108">Remarks</span></span>  
 <span data-ttu-id="a9af3-109">Você pode usar o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>atributo para identificar um ou mais assemblies amigáveis para um determinado assembly.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="a9af3-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="a9af3-110">O exemplo a seguir usa o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>de atributo em um assembly e especifica o assembly `AssemblyB` como um assembly autorizado.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="a9af3-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in assembly A and specifies assembly `AssemblyB` as a friend assembly.</span></span> <span data-ttu-id="a9af3-111">Isso permite que o assembly `AssemblyB` acesso a todos os tipos e membros no assembly um que são marcados como `Friend`.</span><span class="sxs-lookup"><span data-stu-id="a9af3-111">This gives assembly `AssemblyB` access to all types and members in assembly A that are marked as `Friend`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9af3-112">Quando você compila um assembly (assembly `AssemblyB`) que irá acessar tipos internos ou membros internos de outro assembly (assembly *um*), você deve especificar explicitamente o nome do arquivo de saída (.exe ou. dll) usando o **/out** opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="a9af3-112">When you compile an assembly (assembly `AssemblyB`) that will access internal types or internal members of another assembly (assembly *A*), you must explicitly specify the name of the output file (.exe or .dll) by using the **/out** compiler option.</span></span> <span data-ttu-id="a9af3-113">Isso é necessário porque o compilador ainda não gerou o nome do assembly que está construindo no momento em que ele está se ligando referências externas.</span><span class="sxs-lookup"><span data-stu-id="a9af3-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="a9af3-114">Para obter mais informações, consulte [entrada/saída (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="a9af3-114">For more information, see [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span></span>  
  
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
  
 <span data-ttu-id="a9af3-115">Apenas os assemblies que você especificar explicitamente como autorizados podem acessar `Friend` tipos e membros.</span><span class="sxs-lookup"><span data-stu-id="a9af3-115">Only assemblies that you explicitly specify as friends can access `Friend` types and members.</span></span> <span data-ttu-id="a9af3-116">Por exemplo, se o assembly B é um amigo do assembly A e C assembly faz referência ao assembly B, C não tem acesso a `Friend` tipos na.</span><span class="sxs-lookup"><span data-stu-id="a9af3-116">For example, if assembly B is a friend of assembly A and assembly C references assembly B, C does not have access to `Friend` types in A.</span></span>  
  
 <span data-ttu-id="a9af3-117">O compilador executa algumas validações básicas do nome do assembly autorizado passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>atributo.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="a9af3-117">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="a9af3-118">Se assembly *um* declara *B* como um assembly autorizado, as regras de validação são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="a9af3-118">If assembly *A* declares *B* as a friend assembly, the validation rules are as follows:</span></span>  
  
-   <span data-ttu-id="a9af3-119">Se assembly *um* for nomeado, assembly forte *B* também deve ser nomeado forte.</span><span class="sxs-lookup"><span data-stu-id="a9af3-119">If assembly *A* is strong named, assembly *B* must also be strong named.</span></span> <span data-ttu-id="a9af3-120">O nome do assembly autorizado que é passado para o atributo deve conter o nome do assembly e a chave pública da chave de nome forte que é usada para assinar o assembly *B*.</span><span class="sxs-lookup"><span data-stu-id="a9af3-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign assembly *B*.</span></span>  
  
     <span data-ttu-id="a9af3-121">O nome do assembly autorizado que é passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>atributo não pode ser o nome forte do assembly *B*: não incluem a versão do assembly, cultura, arquitetura ou símbolo de chave pública.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="a9af3-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of assembly *B*: do not include the assembly version, culture, architecture, or public key token.</span></span>  
  
-   <span data-ttu-id="a9af3-122">Se assembly *um* não for nomeado forte, o nome do assembly autorizado deve consistir apenas o nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="a9af3-122">If assembly *A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="a9af3-123">Para obter mais informações, consulte [como: Criar Assemblies não assinados Friend (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="a9af3-123">For more information, see [How to: Create Unsigned Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span></span>  
  
-   <span data-ttu-id="a9af3-124">Se assembly *B* for nomeado forte, especifique a chave de nome forte para o assembly *B* usando a configuração do projeto ou da linha de comando `/keyfile` opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="a9af3-124">If assembly *B* is strong named, you must specify the strong-name key for assembly *B* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="a9af3-125">Para obter mais informações, consulte [como: Criar Assemblies assinados do amigo (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="a9af3-125">For more information, see [How to: Create Signed Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span></span>  
  
 <span data-ttu-id="a9af3-126">O <xref:System.Security.Permissions.StrongNameIdentityPermission>classe também fornece a capacidade de compartilhar tipos, com as seguintes diferenças:</xref:System.Security.Permissions.StrongNameIdentityPermission></span><span class="sxs-lookup"><span data-stu-id="a9af3-126">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>  
  
-   <span data-ttu-id="a9af3-127"><xref:System.Security.Permissions.StrongNameIdentityPermission>aplica-se a um tipo individual, enquanto um assembly autorizado se aplica a todo o assembly.</xref:System.Security.Permissions.StrongNameIdentityPermission></span><span class="sxs-lookup"><span data-stu-id="a9af3-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>  
  
-   <span data-ttu-id="a9af3-128">Se há centenas de tipos no assembly *um* que você deseja compartilhar com assembly *B*, você precisa adicionar <xref:System.Security.Permissions.StrongNameIdentityPermission>a todos eles.</xref:System.Security.Permissions.StrongNameIdentityPermission></span><span class="sxs-lookup"><span data-stu-id="a9af3-128">If there are hundreds of types in assembly *A* that you want to share with assembly *B*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="a9af3-129">Se você usar um assembly autorizado, você precisa declarar a relação de amigo uma vez.</span><span class="sxs-lookup"><span data-stu-id="a9af3-129">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>  
  
-   <span data-ttu-id="a9af3-130">Se você usar <xref:System.Security.Permissions.StrongNameIdentityPermission>, os tipos que você deseja compartilhar tem que ser declarado como público.</xref:System.Security.Permissions.StrongNameIdentityPermission></span><span class="sxs-lookup"><span data-stu-id="a9af3-130">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="a9af3-131">Se você usar um assembly autorizado, os tipos compartilhados são declarados como `Friend`.</span><span class="sxs-lookup"><span data-stu-id="a9af3-131">If you use a friend assembly, the shared types are declared as `Friend`.</span></span>  
  
 <span data-ttu-id="a9af3-132">Para obter informações sobre como acessar um assembly `Friend` tipos e métodos de um arquivo de módulo (um arquivo com a extensão. netmodule), consulte [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span><span class="sxs-lookup"><span data-stu-id="a9af3-132">For information about how to access an assembly's `Friend` types and methods from a module file (a file with the .netmodule extension), see [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9af3-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9af3-133">See Also</span></span>  
 <span data-ttu-id="a9af3-134"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="a9af3-134"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span></span>   
 <span data-ttu-id="a9af3-135"><xref:System.Security.Permissions.StrongNameIdentityPermission></xref:System.Security.Permissions.StrongNameIdentityPermission></span><span class="sxs-lookup"><span data-stu-id="a9af3-135"><xref:System.Security.Permissions.StrongNameIdentityPermission></span></span>   
<span data-ttu-id="a9af3-136"> [Como: Criar Assemblies amigáveis não assinados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="a9af3-136"> [How to: Create Unsigned Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) </span></span>  
<span data-ttu-id="a9af3-137"> [Como: Criar Assemblies amigáveis assinados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="a9af3-137"> [How to: Create Signed Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) </span></span>  
<span data-ttu-id="a9af3-138"> [Assemblies e o Cache de Assembly Global (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="a9af3-138"> [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="a9af3-139"> [Conceitos de Programação](../../../../visual-basic/programming-guide/concepts/index.md)</span><span class="sxs-lookup"><span data-stu-id="a9af3-139"> [Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md)</span></span>
