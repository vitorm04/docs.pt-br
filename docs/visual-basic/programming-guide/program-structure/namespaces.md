---
title: Namespaces no Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.global
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- name collisions
- Global keyword [Visual Basic]
- namespace pollution
- names [Visual Basic], avoiding conflicts
- naming conflicts [Visual Basic], namespaces
- namespaces [Visual Basic], assemblies
- Visual Basic code, namespaces
- fully qualified names [Visual Basic]
- naming conventions [Visual Basic], naming conflicts
- namespaces
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0ec038a17b4a6b10dbe339fe33969c4ade57e2a7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="namespaces-in-visual-basic"></a><span data-ttu-id="7d520-102">Namespaces no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d520-102">Namespaces in Visual Basic</span></span>
<span data-ttu-id="7d520-103">Namespaces organizar os objetos definidos em um assembly.</span><span class="sxs-lookup"><span data-stu-id="7d520-103">Namespaces organize the objects defined in an assembly.</span></span> <span data-ttu-id="7d520-104">Os assemblies podem conter vários namespaces, que por sua vez pode conter outros namespaces.</span><span class="sxs-lookup"><span data-stu-id="7d520-104">Assemblies can contain multiple namespaces, which can in turn contain other namespaces.</span></span> <span data-ttu-id="7d520-105">Namespaces evitar a ambiguidade e simplificar as referências ao usar grandes grupos de objetos, como bibliotecas de classe.</span><span class="sxs-lookup"><span data-stu-id="7d520-105">Namespaces prevent ambiguity and simplify references when using large groups of objects such as class libraries.</span></span>  
  
 <span data-ttu-id="7d520-106">Por exemplo, o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] define o <xref:System.Windows.Forms.ListBox> classe no <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="7d520-106">For example, the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] defines the <xref:System.Windows.Forms.ListBox> class in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="7d520-107">O fragmento de código a seguir mostra como declarar uma variável usando o nome totalmente qualificado para esta classe:</span><span class="sxs-lookup"><span data-stu-id="7d520-107">The following code fragment shows how to declare a variable using the fully qualified name for this class:</span></span>  
  
 [!code-vb[VbVbalrApplication#6](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]  
  
## <a name="avoiding-name-collisions"></a><span data-ttu-id="7d520-108">Evitando conflitos de nome</span><span class="sxs-lookup"><span data-stu-id="7d520-108">Avoiding Name Collisions</span></span>  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]<span data-ttu-id="7d520-109"> namespaces solucionar um problema que às vezes chamado de *poluição de namespace*, em que o desenvolvedor de uma biblioteca de classe é reduzido pelo uso de nomes semelhantes em outra biblioteca.</span><span class="sxs-lookup"><span data-stu-id="7d520-109"> namespaces address a problem sometimes called *namespace pollution*, in which the developer of a class library is hampered by the use of similar names in another library.</span></span> <span data-ttu-id="7d520-110">Esses conflitos com os componentes existentes são chamados de *nome colisões*.</span><span class="sxs-lookup"><span data-stu-id="7d520-110">These conflicts with existing components are sometimes called *name collisions*.</span></span>  
  
 <span data-ttu-id="7d520-111">Por exemplo, se você criar uma nova classe chamada `ListBox`, você pode usá-lo em seu projeto sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="7d520-111">For example, if you create a new class named `ListBox`, you can use it inside your project without qualification.</span></span> <span data-ttu-id="7d520-112">No entanto, se você quiser usar o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Windows.Forms.ListBox> classe no mesmo projeto, você deve usar uma referência totalmente qualificada para tornar a referência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="7d520-112">However, if you want to use the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Windows.Forms.ListBox> class in the same project, you must use a fully qualified reference to make the reference unique.</span></span> <span data-ttu-id="7d520-113">Se a referência não for exclusiva, Visual Basic gera um erro informando que o nome é ambíguo.</span><span class="sxs-lookup"><span data-stu-id="7d520-113">If the reference is not unique, Visual Basic produces an error stating that the name is ambiguous.</span></span> <span data-ttu-id="7d520-114">O exemplo de código a seguir demonstra como declarar esses objetos:</span><span class="sxs-lookup"><span data-stu-id="7d520-114">The following code example demonstrates how to declare these objects:</span></span>  
  
 [!code-vb[VbVbalrApplication#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]  
  
 <span data-ttu-id="7d520-115">A ilustração a seguir mostra duas hierarquias de namespace, ambos os que contém um objeto chamado `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="7d520-115">The following illustration shows two namespace hierarchies, both containing an object named `ListBox`.</span></span>  
  
 <span data-ttu-id="7d520-116">![Hierarquia de Namespace](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")</span><span class="sxs-lookup"><span data-stu-id="7d520-116">![Namespace Hierarchy](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")</span></span>  
  
 <span data-ttu-id="7d520-117">Por padrão, cada arquivo executável que você criar com o Visual Basic contém um namespace com o mesmo nome de seu projeto.</span><span class="sxs-lookup"><span data-stu-id="7d520-117">By default, every executable file you create with Visual Basic contains a namespace with the same name as your project.</span></span> <span data-ttu-id="7d520-118">Por exemplo, se você definir um objeto em um projeto chamado `ListBoxProject`, o arquivo executável ListBoxProject.exe contém um namespace chamado `ListBoxProject`.</span><span class="sxs-lookup"><span data-stu-id="7d520-118">For example, if you define an object within a project named `ListBoxProject`, the executable file ListBoxProject.exe contains a namespace called `ListBoxProject`.</span></span>  
  
 <span data-ttu-id="7d520-119">Vários assemblies podem usar o mesmo namespace.</span><span class="sxs-lookup"><span data-stu-id="7d520-119">Multiple assemblies can use the same namespace.</span></span> <span data-ttu-id="7d520-120">Visual Basic trata como um único conjunto de nomes.</span><span class="sxs-lookup"><span data-stu-id="7d520-120">Visual Basic treats them as a single set of names.</span></span> <span data-ttu-id="7d520-121">Por exemplo, você pode definir classes para um namespace chamado `SomeNameSpace` em um assembly nomeado `Assemb1`e definir classes adicionais para o mesmo namespace de um assembly chamado `Assemb2`.</span><span class="sxs-lookup"><span data-stu-id="7d520-121">For example, you can define classes for a namespace called `SomeNameSpace` in an assembly named `Assemb1`, and define additional classes for the same namespace from an assembly named `Assemb2`.</span></span>  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="7d520-122">Nomes totalmente qualificados</span><span class="sxs-lookup"><span data-stu-id="7d520-122">Fully Qualified Names</span></span>  
 <span data-ttu-id="7d520-123">Nomes totalmente qualificados são referências a objetos que são prefixadas com o nome do namespace no qual o objeto é definido.</span><span class="sxs-lookup"><span data-stu-id="7d520-123">Fully qualified names are object references that are prefixed with the name of the namespace in which the object is defined.</span></span> <span data-ttu-id="7d520-124">Você pode usar objetos definidos em outros projetos, se você criar uma referência à classe (escolhendo **adicionar referência** do **projeto** menu) e, em seguida, usar o nome totalmente qualificado para o objeto em seu código.</span><span class="sxs-lookup"><span data-stu-id="7d520-124">You can use objects defined in other projects if you create a reference to the class (by choosing **Add Reference** from the **Project** menu) and then use the fully qualified name for the object in your code.</span></span> <span data-ttu-id="7d520-125">O fragmento de código a seguir mostra como usar o nome totalmente qualificado de um objeto de namespace outro projeto do:</span><span class="sxs-lookup"><span data-stu-id="7d520-125">The following code fragment shows how to use the fully qualified name for an object from another project's namespace:</span></span>  
  
 [!code-vb[VbVbalrApplication#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]  
  
 <span data-ttu-id="7d520-126">Nomes totalmente qualificados impedem a nomeação entra em conflito porque eles tornam possível para o compilador determinar qual objeto está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="7d520-126">Fully qualified names prevent naming conflicts because they make it possible for the compiler to determine which object is being used.</span></span> <span data-ttu-id="7d520-127">No entanto, os nomes podem obter longas e complicadas.</span><span class="sxs-lookup"><span data-stu-id="7d520-127">However, the names themselves can get long and cumbersome.</span></span> <span data-ttu-id="7d520-128">Para contornar esse problema, você pode usar o `Imports` instrução para definir um *alias*— um nome abreviado, você pode usar no lugar do nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="7d520-128">To get around this, you can use the `Imports` statement to define an *alias*—an abbreviated name you can use in place of a fully qualified name.</span></span> <span data-ttu-id="7d520-129">Por exemplo, o exemplo de código a seguir cria aliases para dois nomes totalmente qualificados e usa esses aliases para definir dois objetos.</span><span class="sxs-lookup"><span data-stu-id="7d520-129">For example, the following code example creates aliases for two fully qualified names, and uses these aliases to define two objects.</span></span>  
  
 [!code-vb[VbVbalrApplication#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]  
  
 [!code-vb[VbVbalrApplication#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]  
  
 <span data-ttu-id="7d520-130">Se você usar o `Imports` instrução sem um alias, você pode usar todos os nomes em que o namespace sem qualificação, fornecidas sejam exclusivas para o projeto.</span><span class="sxs-lookup"><span data-stu-id="7d520-130">If you use the `Imports` statement without an alias, you can use all the names in that namespace without qualification, provided they are unique to the project.</span></span> <span data-ttu-id="7d520-131">Se o seu projeto contém `Imports` instruções para os namespaces que contêm itens com o mesmo nome, você deve qualificar totalmente esse nome quando você usá-lo.</span><span class="sxs-lookup"><span data-stu-id="7d520-131">If your project contains `Imports` statements for namespaces that contain items with the same name, you must fully qualify that name when you use it.</span></span> <span data-ttu-id="7d520-132">Suponha que, por exemplo, seu projeto continha os dois seguintes `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="7d520-132">Suppose, for example, your project contained the following two `Imports` statements:</span></span>  
  
 [!code-vb[VbVbalrApplication#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]  
  
 <span data-ttu-id="7d520-133">Se você tentar usar `Class1` sem qualificar totalmente-lo, Visual Basic gera um erro informando que o nome `Class1` é ambíguo.</span><span class="sxs-lookup"><span data-stu-id="7d520-133">If you attempt to use `Class1` without fully qualifying it, Visual Basic produces an error stating that the name `Class1` is ambiguous.</span></span>  
  
## <a name="namespace-level-statements"></a><span data-ttu-id="7d520-134">Instruções de nível de Namespace</span><span class="sxs-lookup"><span data-stu-id="7d520-134">Namespace Level Statements</span></span>  
 <span data-ttu-id="7d520-135">Dentro de um namespace, você pode definir itens como módulos, interfaces, classes, delegados, enumerações, estruturas e outros namespaces.</span><span class="sxs-lookup"><span data-stu-id="7d520-135">Within a namespace, you can define items such as modules, interfaces, classes, delegates, enumerations, structures, and other namespaces.</span></span> <span data-ttu-id="7d520-136">Não é possível definir itens como propriedades, procedimentos, variáveis e eventos em nível de namespace.</span><span class="sxs-lookup"><span data-stu-id="7d520-136">You cannot define items such as properties, procedures, variables and events at the namespace level.</span></span> <span data-ttu-id="7d520-137">Esses itens devem ser declarados em contêineres, como classes, estruturas ou módulos.</span><span class="sxs-lookup"><span data-stu-id="7d520-137">These items must be declared within containers such as modules, structures, or classes.</span></span>  
  
## <a name="global-keyword-in-fully-qualified-names"></a><span data-ttu-id="7d520-138">Palavra-chave global em nomes totalmente qualificados</span><span class="sxs-lookup"><span data-stu-id="7d520-138">Global Keyword in Fully Qualified Names</span></span>  
 <span data-ttu-id="7d520-139">Se você tiver definido uma hierarquia aninhada de namespaces, o código dentro dessa hierarquia poderão ser impedido de acessar o <xref:System?displayProperty=nameWithType> namespace do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7d520-139">If you have defined a nested hierarchy of namespaces, code inside that hierarchy might be blocked from accessing the <xref:System?displayProperty=nameWithType> namespace of the .NET Framework.</span></span> <span data-ttu-id="7d520-140">O exemplo a seguir ilustra uma hierarquia na qual o `SpecialSpace.System` namespace bloqueia o acesso à <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7d520-140">The following example illustrates a hierarchy in which the `SpecialSpace.System` namespace blocks access to <xref:System?displayProperty=nameWithType>.</span></span>  
  
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
  
 <span data-ttu-id="7d520-141">Como resultado, o compilador do Visual Basic com êxito não é possível resolver a referência ao <xref:System.Int32?displayProperty=nameWithType>, pois `SpecialSpace.System` não define `Int32`.</span><span class="sxs-lookup"><span data-stu-id="7d520-141">As a result, the Visual Basic compiler cannot successfully resolve the reference to <xref:System.Int32?displayProperty=nameWithType>, because `SpecialSpace.System` does not define `Int32`.</span></span> <span data-ttu-id="7d520-142">Você pode usar o `Global` palavra-chave para iniciar a cadeia de qualificação no nível mais externo da biblioteca de classes do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7d520-142">You can use the `Global` keyword to start the qualification chain at the outermost level of the .NET Framework class library.</span></span> <span data-ttu-id="7d520-143">Isso permite que você especifique o <xref:System?displayProperty=nameWithType> namespace ou qualquer outro namespace na biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="7d520-143">This allows you to specify the <xref:System?displayProperty=nameWithType> namespace or any other namespace in the class library.</span></span> <span data-ttu-id="7d520-144">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="7d520-144">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="7d520-145">Você pode usar `Global` para acessar outros namespaces no nível raiz, como <xref:Microsoft.VisualBasic?displayProperty=nameWithType>e qualquer namespace associado ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="7d520-145">You can use `Global` to access other root-level namespaces, such as <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, and any namespace associated with your project.</span></span>  
  
## <a name="global-keyword-in-namespace-statements"></a><span data-ttu-id="7d520-146">Palavra-chave em instruções de Namespace global</span><span class="sxs-lookup"><span data-stu-id="7d520-146">Global Keyword in Namespace Statements</span></span>  
 <span data-ttu-id="7d520-147">Você também pode usar o `Global` palavra-chave em um [declaração de Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7d520-147">You can also use the `Global` keyword in a [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span> <span data-ttu-id="7d520-148">Isso permite definir um namespace do namespace raiz do projeto.</span><span class="sxs-lookup"><span data-stu-id="7d520-148">This lets you define a namespace out of the root namespace of your project.</span></span>  
  
 <span data-ttu-id="7d520-149">Todos os namespaces no seu projeto baseiam-se no namespace raiz do projeto.</span><span class="sxs-lookup"><span data-stu-id="7d520-149">All namespaces in your project are based on the root namespace for the project.</span></span>  <span data-ttu-id="7d520-150">Visual Studio atribui o nome do projeto como o namespace de raiz padrão para todo o código em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="7d520-150">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="7d520-151">Por exemplo, se seu projeto for chamado `ConsoleApplication1`, seus elementos de programação pertencem ao namespace `ConsoleApplication1`.</span><span class="sxs-lookup"><span data-stu-id="7d520-151">For example, if your project is named `ConsoleApplication1`, its programming elements belong to namespace `ConsoleApplication1`.</span></span> <span data-ttu-id="7d520-152">Se você declarar `Namespace Magnetosphere`, as referências a `Magnetosphere` no projeto terão acesso `ConsoleApplication1.Magnetosphere`.</span><span class="sxs-lookup"><span data-stu-id="7d520-152">If you declare `Namespace Magnetosphere`, references to `Magnetosphere` in the project will access `ConsoleApplication1.Magnetosphere`.</span></span>  
  
 <span data-ttu-id="7d520-153">Os exemplos a seguir usam o `Global` palavra-chave para declarar um namespace do namespace raiz do projeto.</span><span class="sxs-lookup"><span data-stu-id="7d520-153">The following examples use the `Global` keyword to declare a namespace out of the root namespace for the project.</span></span>  
  
 [!code-vb[VbVbalrApplication#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]  
  
 <span data-ttu-id="7d520-154">Em uma declaração de namespace, `Global` não pode ser aninhado em outro namespace.</span><span class="sxs-lookup"><span data-stu-id="7d520-154">In a namespace declaration, `Global` cannot be nested in another namespace.</span></span>  
  
 <span data-ttu-id="7d520-155">Você pode usar o [página de aplicativo, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) para exibir e modificar o **Namespace raiz** do projeto.</span><span class="sxs-lookup"><span data-stu-id="7d520-155">You can use the [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) to view and modify the **Root Namespace** of the project.</span></span>  <span data-ttu-id="7d520-156">Para novos projetos, o **Namespace raiz** padrão é o nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="7d520-156">For new projects, the **Root Namespace** defaults to the project name.</span></span> <span data-ttu-id="7d520-157">Para fazer com que `Global` para ser o namespace de nível superior, você pode limpar o **Namespace raiz** entrada para que a caixa estiver vazia.</span><span class="sxs-lookup"><span data-stu-id="7d520-157">To cause `Global` to be the top-level namespace, you can clear the **Root Namespace** entry so that the box is empty.</span></span> <span data-ttu-id="7d520-158">Limpando **Namespace raiz** elimina a necessidade do `Global` palavra-chave em declarações de namespace.</span><span class="sxs-lookup"><span data-stu-id="7d520-158">Clearing **Root Namespace** removes the need for the `Global` keyword in namespace declarations.</span></span>  
  
 <span data-ttu-id="7d520-159">Se um `Namespace` instrução declara um nome que também é um namespace do .NET Framework, o namespace do .NET Framework se torna indisponível se o `Global` palavra-chave não é usado em um nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="7d520-159">If a `Namespace` statement declares a name that is also a namespace in the .NET Framework, the .NET Framework namespace becomes unavailable if the `Global` keyword is not used in a fully qualified name.</span></span> <span data-ttu-id="7d520-160">Para habilitar o acesso a esse namespace do .NET Framework sem usar o `Global` palavra-chave, você pode incluir o `Global` palavra-chave no `Namespace` instrução.</span><span class="sxs-lookup"><span data-stu-id="7d520-160">To enable access to that .NET Framework namespace without using the `Global` keyword, you can include the `Global` keyword in the `Namespace` statement.</span></span>  
  
 <span data-ttu-id="7d520-161">O exemplo a seguir tem o `Global` palavra-chave no `System.Text` declaração de namespace.</span><span class="sxs-lookup"><span data-stu-id="7d520-161">The following example has the `Global` keyword in the `System.Text` namespace declaration.</span></span>  
  
 <span data-ttu-id="7d520-162">Se o `Global` palavra-chave não estava presente na declaração de namespace, <xref:System.Text.StringBuilder> não pôde ser acessado sem especificar `Global.System.Text.StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="7d520-162">If the `Global` keyword was not present in the namespace declaration, <xref:System.Text.StringBuilder> could not be accessed without specifying `Global.System.Text.StringBuilder`.</span></span> <span data-ttu-id="7d520-163">Para um projeto chamado `ConsoleApplication1`, as referências a `System.Text` acessaria `ConsoleApplication1.System.Text` se o `Global` palavra-chave não foi usado.</span><span class="sxs-lookup"><span data-stu-id="7d520-163">For a project named `ConsoleApplication1`, references to `System.Text` would access `ConsoleApplication1.System.Text` if the `Global` keyword was not used.</span></span>  
  
 [!code-vb[VbVbalrApplication#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7d520-164">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7d520-164">See Also</span></span>  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
 [<span data-ttu-id="7d520-165">Assemblies e o Cache de Assembly Global</span><span class="sxs-lookup"><span data-stu-id="7d520-165">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="7d520-166">Como criar e usar assemblies usando a linha de comando</span><span class="sxs-lookup"><span data-stu-id="7d520-166">How to: Create and Use Assemblies Using the Command Line</span></span>](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)  
 [<span data-ttu-id="7d520-167">Referências e a Instrução Imports</span><span class="sxs-lookup"><span data-stu-id="7d520-167">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="7d520-168">Instrução Imports (Tipo e Namespace .NET)</span><span class="sxs-lookup"><span data-stu-id="7d520-168">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="7d520-169">Escrevendo código em soluções do Office</span><span class="sxs-lookup"><span data-stu-id="7d520-169">Writing Code in Office Solutions</span></span>](https://msdn.microsoft.com/library/bb608596)
