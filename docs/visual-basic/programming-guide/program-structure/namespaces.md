---
title: Namespaces no Visual Basic | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.global
dev_langs:
- VB
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- name collisions
- Global keyword [Visual Basic]
- namespace pollution
- names, avoiding conflicts
- naming conflicts, namespaces
- namespaces, assemblies
- Visual Basic code, namespaces
- fully qualified names
- naming conventions, naming conflicts
- namespaces
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: bfc9f8f71b5ce5e05b6509ad490354663f894651
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="namespaces-in-visual-basic"></a><span data-ttu-id="88055-102">Namespaces no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="88055-102">Namespaces in Visual Basic</span></span>
<span data-ttu-id="88055-103">Os namespaces organizam os objetos definidos em um assembly.</span><span class="sxs-lookup"><span data-stu-id="88055-103">Namespaces organize the objects defined in an assembly.</span></span> <span data-ttu-id="88055-104">Os assemblies podem conter vários namespaces, que por sua vez pode conter outros namespaces.</span><span class="sxs-lookup"><span data-stu-id="88055-104">Assemblies can contain multiple namespaces, which can in turn contain other namespaces.</span></span> <span data-ttu-id="88055-105">Namespaces evitar a ambiguidade e simplificar as referências ao usar grupos grandes de objetos, como bibliotecas de classes.</span><span class="sxs-lookup"><span data-stu-id="88055-105">Namespaces prevent ambiguity and simplify references when using large groups of objects such as class libraries.</span></span>  
  
 <span data-ttu-id="88055-106">Por exemplo, o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] define o <xref:System.Windows.Forms.ListBox>classe o <xref:System.Windows.Forms?displayProperty=fullName>namespace.</xref:System.Windows.Forms?displayProperty=fullName> </xref:System.Windows.Forms.ListBox></span><span class="sxs-lookup"><span data-stu-id="88055-106">For example, the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] defines the <xref:System.Windows.Forms.ListBox> class in the <xref:System.Windows.Forms?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="88055-107">O fragmento de código a seguir mostra como declarar uma variável usando o nome totalmente qualificado para esta classe:</span><span class="sxs-lookup"><span data-stu-id="88055-107">The following code fragment shows how to declare a variable using the fully qualified name for this class:</span></span>  
  
 <span data-ttu-id="88055-108">[!code-vb[VbVbalrApplication n º&6;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="88055-108">[!code-vb[VbVbalrApplication#6](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]</span></span>  
  
## <a name="avoiding-name-collisions"></a><span data-ttu-id="88055-109">Evitando conflitos de nome</span><span class="sxs-lookup"><span data-stu-id="88055-109">Avoiding Name Collisions</span></span>  
 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]<span data-ttu-id="88055-110">namespaces resolver um problema que às vezes chamado de *poluição de namespace*, no qual o desenvolvedor de uma biblioteca de classe é violado pelo uso de nomes semelhantes em outra biblioteca.</span><span class="sxs-lookup"><span data-stu-id="88055-110"> namespaces address a problem sometimes called *namespace pollution*, in which the developer of a class library is hampered by the use of similar names in another library.</span></span> <span data-ttu-id="88055-111">Esses conflitos com os componentes existentes são chamados *conflitos de nome*.</span><span class="sxs-lookup"><span data-stu-id="88055-111">These conflicts with existing components are sometimes called *name collisions*.</span></span>  
  
 <span data-ttu-id="88055-112">Por exemplo, se você criar uma nova classe chamada `ListBox`, você pode usá-lo em seu projeto sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="88055-112">For example, if you create a new class named `ListBox`, you can use it inside your project without qualification.</span></span> <span data-ttu-id="88055-113">No entanto, se você quiser usar o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.Windows.Forms.ListBox>classe no mesmo projeto, você deve usar uma referência totalmente qualificada para fazer a referência exclusiva.</xref:System.Windows.Forms.ListBox></span><span class="sxs-lookup"><span data-stu-id="88055-113">However, if you want to use the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.Windows.Forms.ListBox> class in the same project, you must use a fully qualified reference to make the reference unique.</span></span> <span data-ttu-id="88055-114">Se a referência não for exclusiva, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] produz um erro informando que o nome é ambíguo.</span><span class="sxs-lookup"><span data-stu-id="88055-114">If the reference is not unique, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] produces an error stating that the name is ambiguous.</span></span> <span data-ttu-id="88055-115">O exemplo de código a seguir demonstra como declarar esses objetos:</span><span class="sxs-lookup"><span data-stu-id="88055-115">The following code example demonstrates how to declare these objects:</span></span>  
  
 <span data-ttu-id="88055-116">[!code-vb[VbVbalrApplication&#7;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="88055-116">[!code-vb[VbVbalrApplication#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]</span></span>  
  
 <span data-ttu-id="88055-117">A ilustração a seguir mostra duas hierarquias de namespace, ambos os que contém um objeto chamado `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="88055-117">The following illustration shows two namespace hierarchies, both containing an object named `ListBox`.</span></span>  
  
 <span data-ttu-id="88055-118">![Hierarquia de Namespace](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")</span><span class="sxs-lookup"><span data-stu-id="88055-118">![Namespace Hierarchy](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")</span></span>  
  
 <span data-ttu-id="88055-119">Por padrão, cada arquivo executável que você criar com [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] contém um namespace com o mesmo nome do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="88055-119">By default, every executable file you create with [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] contains a namespace with the same name as your project.</span></span> <span data-ttu-id="88055-120">Por exemplo, se você definir um objeto em um projeto chamado `ListBoxProject`, o arquivo executável ListBoxProject.exe contém um namespace chamado `ListBoxProject`.</span><span class="sxs-lookup"><span data-stu-id="88055-120">For example, if you define an object within a project named `ListBoxProject`, the executable file ListBoxProject.exe contains a namespace called `ListBoxProject`.</span></span>  
  
 <span data-ttu-id="88055-121">Vários assemblies podem usar o mesmo namespace.</span><span class="sxs-lookup"><span data-stu-id="88055-121">Multiple assemblies can use the same namespace.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="88055-122">trata-os como um único conjunto de nomes.</span><span class="sxs-lookup"><span data-stu-id="88055-122"> treats them as a single set of names.</span></span> <span data-ttu-id="88055-123">Por exemplo, você pode definir classes para um namespace chamado `SomeNameSpace` em um assembly denominado `Assemb1`e definir classes adicionais para o mesmo namespace de um assembly denominado `Assemb2`.</span><span class="sxs-lookup"><span data-stu-id="88055-123">For example, you can define classes for a namespace called `SomeNameSpace` in an assembly named `Assemb1`, and define additional classes for the same namespace from an assembly named `Assemb2`.</span></span>  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="88055-124">Nomes totalmente qualificados</span><span class="sxs-lookup"><span data-stu-id="88055-124">Fully Qualified Names</span></span>  
 <span data-ttu-id="88055-125">Nomes totalmente qualificados são referências de objeto que são prefixadas com o nome do namespace no qual o objeto é definido.</span><span class="sxs-lookup"><span data-stu-id="88055-125">Fully qualified names are object references that are prefixed with the name of the namespace in which the object is defined.</span></span> <span data-ttu-id="88055-126">Você pode usar objetos definidos em outros projetos, se você criar uma referência à classe (escolhendo **adicionar referência** do **projeto** menu) e, em seguida, usar o nome totalmente qualificado para o objeto em seu código.</span><span class="sxs-lookup"><span data-stu-id="88055-126">You can use objects defined in other projects if you create a reference to the class (by choosing **Add Reference** from the **Project** menu) and then use the fully qualified name for the object in your code.</span></span> <span data-ttu-id="88055-127">O fragmento de código a seguir mostra como usar o nome totalmente qualificado de um objeto de namespace outro projeto do:</span><span class="sxs-lookup"><span data-stu-id="88055-127">The following code fragment shows how to use the fully qualified name for an object from another project's namespace:</span></span>  
  
 <span data-ttu-id="88055-128">[!code-vb[VbVbalrApplication n º&8;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="88055-128">[!code-vb[VbVbalrApplication#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]</span></span>  
  
 <span data-ttu-id="88055-129">Nomes totalmente qualificados impedem a nomeação entra em conflito porque eles possibilitam que o compilador determinar qual objeto está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="88055-129">Fully qualified names prevent naming conflicts because they make it possible for the compiler to determine which object is being used.</span></span> <span data-ttu-id="88055-130">No entanto, os nomes podem obter longo e complicado.</span><span class="sxs-lookup"><span data-stu-id="88055-130">However, the names themselves can get long and cumbersome.</span></span> <span data-ttu-id="88055-131">Para contornar esse problema, você pode usar o `Imports` instrução para definir um *alias*— um nome abreviado que você pode usar no lugar de um nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="88055-131">To get around this, you can use the `Imports` statement to define an *alias*—an abbreviated name you can use in place of a fully qualified name.</span></span> <span data-ttu-id="88055-132">Por exemplo, o exemplo de código a seguir cria aliases para dois nomes totalmente qualificados e usa esses aliases para definir dois objetos.</span><span class="sxs-lookup"><span data-stu-id="88055-132">For example, the following code example creates aliases for two fully qualified names, and uses these aliases to define two objects.</span></span>  
  
 <span data-ttu-id="88055-133">[!code-vb[VbVbalrApplication n º&9;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="88055-133">[!code-vb[VbVbalrApplication#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]</span></span>  
  
 <span data-ttu-id="88055-134">[!code-vb[VbVbalrApplication n º&10;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="88055-134">[!code-vb[VbVbalrApplication#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]</span></span>  
  
 <span data-ttu-id="88055-135">Se você usar o `Imports` instrução sem um alias, você pode usar todos os nomes que namespace sem qualificação, fornecidas sejam exclusivas para o projeto.</span><span class="sxs-lookup"><span data-stu-id="88055-135">If you use the `Imports` statement without an alias, you can use all the names in that namespace without qualification, provided they are unique to the project.</span></span> <span data-ttu-id="88055-136">Se seu projeto contém `Imports` instruções para os namespaces que contêm itens com o mesmo nome, você deve qualificar totalmente esse nome quando você usá-lo.</span><span class="sxs-lookup"><span data-stu-id="88055-136">If your project contains `Imports` statements for namespaces that contain items with the same name, you must fully qualify that name when you use it.</span></span> <span data-ttu-id="88055-137">Suponha, por exemplo, seu projeto contidos nas próximas duas `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="88055-137">Suppose, for example, your project contained the following two `Imports` statements:</span></span>  
  
 <span data-ttu-id="88055-138">[!code-vb[VbVbalrApplication n º&11;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="88055-138">[!code-vb[VbVbalrApplication#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]</span></span>  
  
 <span data-ttu-id="88055-139">Se você tentar usar `Class1` sem qualificar totalmente, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] produz um erro informando que o nome `Class1` é ambíguo.</span><span class="sxs-lookup"><span data-stu-id="88055-139">If you attempt to use `Class1` without fully qualifying it, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] produces an error stating that the name `Class1` is ambiguous.</span></span>  
  
## <a name="namespace-level-statements"></a><span data-ttu-id="88055-140">Declarações de nível de Namespace</span><span class="sxs-lookup"><span data-stu-id="88055-140">Namespace Level Statements</span></span>  
 <span data-ttu-id="88055-141">Dentro de um namespace, você pode definir itens como módulos, interfaces, classes, delegados, enumerações, estruturas e outros namespaces.</span><span class="sxs-lookup"><span data-stu-id="88055-141">Within a namespace, you can define items such as modules, interfaces, classes, delegates, enumerations, structures, and other namespaces.</span></span> <span data-ttu-id="88055-142">Não é possível definir itens como propriedades, procedimentos, variáveis e eventos no nível de namespace.</span><span class="sxs-lookup"><span data-stu-id="88055-142">You cannot define items such as properties, procedures, variables and events at the namespace level.</span></span> <span data-ttu-id="88055-143">Esses itens devem ser declarados dentro de contêineres, como módulos, classes ou estruturas.</span><span class="sxs-lookup"><span data-stu-id="88055-143">These items must be declared within containers such as modules, structures, or classes.</span></span>  
  
## <a name="global-keyword-in-fully-qualified-names"></a><span data-ttu-id="88055-144">Palavra-chave global em nomes totalmente qualificados</span><span class="sxs-lookup"><span data-stu-id="88055-144">Global Keyword in Fully Qualified Names</span></span>  
 <span data-ttu-id="88055-145">Se você tiver definido uma hierarquia aninhada de namespaces, o código dentro dessa hierarquia pode ser impedido de acessar o <xref:System?displayProperty=fullName>namespace do .NET Framework.</xref:System?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="88055-145">If you have defined a nested hierarchy of namespaces, code inside that hierarchy might be blocked from accessing the <xref:System?displayProperty=fullName> namespace of the .NET Framework.</span></span> <span data-ttu-id="88055-146">O exemplo a seguir ilustra uma hierarquia na qual o `SpecialSpace.System` namespace bloqueia o acesso à <xref:System?displayProperty=fullName>.</xref:System?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="88055-146">The following example illustrates a hierarchy in which the `SpecialSpace.System` namespace blocks access to <xref:System?displayProperty=fullName>.</span></span>  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As System.Int32  
                Dim n As System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 <span data-ttu-id="88055-147">Como resultado, o compilador do Visual Basic não pode resolver com êxito a referência à <xref:System.Int32?displayProperty=fullName>, pois `SpecialSpace.System` não define `Int32`.</xref:System.Int32?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="88055-147">As a result, the Visual Basic compiler cannot successfully resolve the reference to <xref:System.Int32?displayProperty=fullName>, because `SpecialSpace.System` does not define `Int32`.</span></span> <span data-ttu-id="88055-148">Você pode usar o `Global` palavra-chave para iniciar a cadeia de qualificação no nível mais externo de biblioteca de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="88055-148">You can use the `Global` keyword to start the qualification chain at the outermost level of the .NET Framework class library.</span></span> <span data-ttu-id="88055-149">Isso permite que você especifique o <xref:System?displayProperty=fullName>namespace ou qualquer outro namespace na biblioteca de classes.</xref:System?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="88055-149">This allows you to specify the <xref:System?displayProperty=fullName> namespace or any other namespace in the class library.</span></span> <span data-ttu-id="88055-150">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="88055-150">The following example illustrates this.</span></span>  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As Global.System.Int32  
                Dim n As Global.System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 <span data-ttu-id="88055-151">Você pode usar `Global` para acessar outros namespaces no nível da raiz, como <xref:Microsoft.VisualBasic?displayProperty=fullName>e qualquer namespace associado ao projeto.</xref:Microsoft.VisualBasic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="88055-151">You can use `Global` to access other root-level namespaces, such as <xref:Microsoft.VisualBasic?displayProperty=fullName>, and any namespace associated with your project.</span></span>  
  
## <a name="global-keyword-in-namespace-statements"></a><span data-ttu-id="88055-152">Palavra-chave nas declarações de Namespace global</span><span class="sxs-lookup"><span data-stu-id="88055-152">Global Keyword in Namespace Statements</span></span>  
 <span data-ttu-id="88055-153">Você também pode usar o `Global` palavra-chave em uma [declaração de Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="88055-153">You can also use the `Global` keyword in a [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span> <span data-ttu-id="88055-154">Isso permite definir um namespace fora do namespace raiz do projeto.</span><span class="sxs-lookup"><span data-stu-id="88055-154">This lets you define a namespace out of the root namespace of your project.</span></span>  
  
 <span data-ttu-id="88055-155">Todos os namespaces em seu projeto são baseados no namespace raiz do projeto.</span><span class="sxs-lookup"><span data-stu-id="88055-155">All namespaces in your project are based on the root namespace for the project.</span></span>  <span data-ttu-id="88055-156">Visual Studio atribui o nome do projeto como o namespace de raiz padrão para todo o código em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="88055-156">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="88055-157">Por exemplo, se seu projeto for chamado `ConsoleApplication1`, seus elementos de programação pertencem ao namespace `ConsoleApplication1`.</span><span class="sxs-lookup"><span data-stu-id="88055-157">For example, if your project is named `ConsoleApplication1`, its programming elements belong to namespace `ConsoleApplication1`.</span></span> <span data-ttu-id="88055-158">Se você declarar `Namespace Magnetosphere`, as referências a `Magnetosphere` no projeto irá acessar `ConsoleApplication1.Magnetosphere`.</span><span class="sxs-lookup"><span data-stu-id="88055-158">If you declare `Namespace Magnetosphere`, references to `Magnetosphere` in the project will access `ConsoleApplication1.Magnetosphere`.</span></span>  
  
 <span data-ttu-id="88055-159">Os exemplos a seguir usam o `Global` palavra-chave para declarar um namespace fora do namespace raiz do projeto.</span><span class="sxs-lookup"><span data-stu-id="88055-159">The following examples use the `Global` keyword to declare a namespace out of the root namespace for the project.</span></span>  
  
 <span data-ttu-id="88055-160">[!code-vb[VbVbalrApplication&#22;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="88055-160">[!code-vb[VbVbalrApplication#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]</span></span>  
  
 <span data-ttu-id="88055-161">Em uma declaração de namespace, `Global` não pode ser aninhado em outro namespace.</span><span class="sxs-lookup"><span data-stu-id="88055-161">In a namespace declaration, `Global` cannot be nested in another namespace.</span></span>  
  
 <span data-ttu-id="88055-162">Você pode usar o [página de aplicativo, Designer de projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic) para exibir e modificar o **Namespace raiz** do projeto.</span><span class="sxs-lookup"><span data-stu-id="88055-162">You can use the [Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic) to view and modify the **Root Namespace** of the project.</span></span>  <span data-ttu-id="88055-163">Para novos projetos, o **Namespace raiz** assume como padrão o nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="88055-163">For new projects, the **Root Namespace** defaults to the project name.</span></span> <span data-ttu-id="88055-164">Para fazer com que `Global` para ser o namespace de nível superior, você pode limpar o **Namespace raiz** entrada para que a caixa estiver vazia.</span><span class="sxs-lookup"><span data-stu-id="88055-164">To cause `Global` to be the top-level namespace, you can clear the **Root Namespace** entry so that the box is empty.</span></span> <span data-ttu-id="88055-165">Limpando **Namespace raiz** elimina a necessidade do `Global` palavra-chave em declarações de namespace.</span><span class="sxs-lookup"><span data-stu-id="88055-165">Clearing **Root Namespace** removes the need for the `Global` keyword in namespace declarations.</span></span>  
  
 <span data-ttu-id="88055-166">Se um `Namespace` instrução declara um nome que também é um namespace do .NET Framework, o namespace do .NET Framework se torna indisponível se o `Global` palavra-chave não é usada em um nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="88055-166">If a `Namespace` statement declares a name that is also a namespace in the .NET Framework, the .NET Framework namespace becomes unavailable if the `Global` keyword is not used in a fully qualified name.</span></span> <span data-ttu-id="88055-167">Para habilitar o acesso a esse namespace do .NET Framework sem usar o `Global` palavra-chave, você pode incluir o `Global` palavra-chave no `Namespace` instrução.</span><span class="sxs-lookup"><span data-stu-id="88055-167">To enable access to that .NET Framework namespace without using the `Global` keyword, you can include the `Global` keyword in the `Namespace` statement.</span></span>  
  
 <span data-ttu-id="88055-168">O exemplo a seguir tem o `Global` palavra-chave no `System.Text` declaração de namespace.</span><span class="sxs-lookup"><span data-stu-id="88055-168">The following example has the `Global` keyword in the `System.Text` namespace declaration.</span></span>  
  
 <span data-ttu-id="88055-169">Se o `Global` palavra-chave não estava presente na declaração de namespace, <xref:System.Text.StringBuilder>não pôde ser acessado sem especificar `Global.System.Text.StringBuilder`.</xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="88055-169">If the `Global` keyword was not present in the namespace declaration, <xref:System.Text.StringBuilder> could not be accessed without specifying `Global.System.Text.StringBuilder`.</span></span> <span data-ttu-id="88055-170">Para um projeto chamado `ConsoleApplication1`, as referências a `System.Text` acessaria `ConsoleApplication1.System.Text` se o `Global` palavra-chave não foi usado.</span><span class="sxs-lookup"><span data-stu-id="88055-170">For a project named `ConsoleApplication1`, references to `System.Text` would access `ConsoleApplication1.System.Text` if the `Global` keyword was not used.</span></span>  
  
 <span data-ttu-id="88055-171">[!code-vb[VbVbalrApplication&#21;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="88055-171">[!code-vb[VbVbalrApplication#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88055-172">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88055-172">See Also</span></span>  
 <span data-ttu-id="88055-173"><xref:System.Windows.Forms.ListBox></xref:System.Windows.Forms.ListBox></span><span class="sxs-lookup"><span data-stu-id="88055-173"><xref:System.Windows.Forms.ListBox></span></span>   
 <span data-ttu-id="88055-174"><xref:System.Windows.Forms?displayProperty=fullName></xref:System.Windows.Forms?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="88055-174"><xref:System.Windows.Forms?displayProperty=fullName></span></span>   
<span data-ttu-id="88055-175"> [Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="88055-175"> [Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="88055-176"> [Como: criar e usar Assemblies usando a linha de comando](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4) </span><span class="sxs-lookup"><span data-stu-id="88055-176"> [How to: Create and Use Assemblies Using the Command Line](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4) </span></span>  
<span data-ttu-id="88055-177"> [Referências e a instrução Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span><span class="sxs-lookup"><span data-stu-id="88055-177"> [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span></span>  
<span data-ttu-id="88055-178"> [Instrução Imports (tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span><span class="sxs-lookup"><span data-stu-id="88055-178"> [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span></span>  
<span data-ttu-id="88055-179"> [Escrevendo código em soluções do Office](https://msdn.microsoft.com/library/bb608596)</span><span class="sxs-lookup"><span data-stu-id="88055-179"> [Writing Code in Office Solutions](https://msdn.microsoft.com/library/bb608596)</span></span>
