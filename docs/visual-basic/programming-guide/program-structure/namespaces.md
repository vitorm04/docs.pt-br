---
title: Namespaces no Visual Basic
ms.date: 07/20/2015
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
ms.openlocfilehash: dd7ac0487a5878122d9b1717a5e5fc8bf21a4ea7
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972036"
---
# <a name="namespaces-in-visual-basic"></a><span data-ttu-id="c8ab8-102">Namespaces no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c8ab8-102">Namespaces in Visual Basic</span></span>
<span data-ttu-id="c8ab8-103">Os namespaces organizam os objetos definidos em um assembly.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-103">Namespaces organize the objects defined in an assembly.</span></span> <span data-ttu-id="c8ab8-104">Os assemblies podem conter vários namespaces, que, por sua vez, podem conter outros namespaces.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-104">Assemblies can contain multiple namespaces, which can in turn contain other namespaces.</span></span> <span data-ttu-id="c8ab8-105">Os namespaces impedem ambigüidade e simplificam referências ao usar grandes grupos de objetos, como bibliotecas de classes.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-105">Namespaces prevent ambiguity and simplify references when using large groups of objects such as class libraries.</span></span>  
  
 <span data-ttu-id="c8ab8-106">Por exemplo, o .NET Framework define a <xref:System.Windows.Forms.ListBox> classe <xref:System.Windows.Forms?displayProperty=nameWithType> no namespace.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-106">For example, the .NET Framework defines the <xref:System.Windows.Forms.ListBox> class in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="c8ab8-107">O fragmento de código a seguir mostra como declarar uma variável usando o nome totalmente qualificado para esta classe:</span><span class="sxs-lookup"><span data-stu-id="c8ab8-107">The following code fragment shows how to declare a variable using the fully qualified name for this class:</span></span>  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a><span data-ttu-id="c8ab8-108">Evitando colisões de nome</span><span class="sxs-lookup"><span data-stu-id="c8ab8-108">Avoiding Name Collisions</span></span>  
 <span data-ttu-id="c8ab8-109">Os namespaces .NET Framework resolvem um problema às vezes chamado de *poluição de namespace*, em que o desenvolvedor de uma biblioteca de classes é dificultado pelo uso de nomes semelhantes em outra biblioteca.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-109">.NET Framework namespaces address a problem sometimes called *namespace pollution*, in which the developer of a class library is hampered by the use of similar names in another library.</span></span> <span data-ttu-id="c8ab8-110">Esses conflitos com os componentes existentes às vezes são chamados de *colisões de nome*.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-110">These conflicts with existing components are sometimes called *name collisions*.</span></span>  
  
 <span data-ttu-id="c8ab8-111">Por exemplo, se você criar uma nova classe chamada `ListBox`, poderá usá-la dentro de seu projeto sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-111">For example, if you create a new class named `ListBox`, you can use it inside your project without qualification.</span></span> <span data-ttu-id="c8ab8-112">No entanto, se você quiser usar a <xref:System.Windows.Forms.ListBox> classe .NET Framework no mesmo projeto, deverá usar uma referência totalmente qualificada para tornar a referência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-112">However, if you want to use the .NET Framework <xref:System.Windows.Forms.ListBox> class in the same project, you must use a fully qualified reference to make the reference unique.</span></span> <span data-ttu-id="c8ab8-113">Se a referência não for exclusiva, Visual Basic produzirá um erro informando que o nome é ambíguo.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-113">If the reference is not unique, Visual Basic produces an error stating that the name is ambiguous.</span></span> <span data-ttu-id="c8ab8-114">O exemplo de código a seguir demonstra como declarar esses objetos:</span><span class="sxs-lookup"><span data-stu-id="c8ab8-114">The following code example demonstrates how to declare these objects:</span></span>  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 <span data-ttu-id="c8ab8-115">A ilustração a seguir mostra duas hierarquias de namespace, ambas contendo um `ListBox`objeto chamado:</span><span class="sxs-lookup"><span data-stu-id="c8ab8-115">The following illustration shows two namespace hierarchies, both containing an object named `ListBox`:</span></span>  
  
 ![Captura de tela que mostra duas hierarquias de namespace.](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 <span data-ttu-id="c8ab8-117">Por padrão, cada arquivo executável que você cria com Visual Basic contém um namespace com o mesmo nome do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-117">By default, every executable file you create with Visual Basic contains a namespace with the same name as your project.</span></span> <span data-ttu-id="c8ab8-118">Por exemplo, se você definir um objeto em um projeto chamado `ListBoxProject`, o arquivo executável ListBoxProject. exe conterá um namespace `ListBoxProject`chamado.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-118">For example, if you define an object within a project named `ListBoxProject`, the executable file ListBoxProject.exe contains a namespace called `ListBoxProject`.</span></span>  
  
 <span data-ttu-id="c8ab8-119">Vários assemblies podem usar o mesmo namespace.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-119">Multiple assemblies can use the same namespace.</span></span> <span data-ttu-id="c8ab8-120">Visual Basic os trata como um único conjunto de nomes.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-120">Visual Basic treats them as a single set of names.</span></span> <span data-ttu-id="c8ab8-121">Por exemplo, você pode definir classes para um namespace chamado `SomeNameSpace` em um assembly chamado `Assemb1`e definir classes adicionais para o mesmo namespace de um assembly chamado `Assemb2`.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-121">For example, you can define classes for a namespace called `SomeNameSpace` in an assembly named `Assemb1`, and define additional classes for the same namespace from an assembly named `Assemb2`.</span></span>  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="c8ab8-122">Nomes totalmente qualificados</span><span class="sxs-lookup"><span data-stu-id="c8ab8-122">Fully Qualified Names</span></span>  
 <span data-ttu-id="c8ab8-123">Nomes totalmente qualificados são referências de objeto que são prefixadas com o nome do namespace no qual o objeto é definido.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-123">Fully qualified names are object references that are prefixed with the name of the namespace in which the object is defined.</span></span> <span data-ttu-id="c8ab8-124">Você pode usar objetos definidos em outros projetos se criar uma referência à classe (escolhendo **Adicionar referência** no menu **projeto** ) e, em seguida, usar o nome totalmente qualificado para o objeto em seu código.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-124">You can use objects defined in other projects if you create a reference to the class (by choosing **Add Reference** from the **Project** menu) and then use the fully qualified name for the object in your code.</span></span> <span data-ttu-id="c8ab8-125">O fragmento de código a seguir mostra como usar o nome totalmente qualificado para um objeto do namespace de outro projeto:</span><span class="sxs-lookup"><span data-stu-id="c8ab8-125">The following code fragment shows how to use the fully qualified name for an object from another project's namespace:</span></span>  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 <span data-ttu-id="c8ab8-126">Nomes totalmente qualificados impedem conflitos de nomenclatura porque possibilitam que o compilador determine qual objeto está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-126">Fully qualified names prevent naming conflicts because they make it possible for the compiler to determine which object is being used.</span></span> <span data-ttu-id="c8ab8-127">No entanto, os próprios nomes podem ser longos e complicados.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-127">However, the names themselves can get long and cumbersome.</span></span> <span data-ttu-id="c8ab8-128">Para contornar isso, você pode usar a `Imports` instrução para definir um *alias*— um nome abreviado que você pode usar no lugar de um nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-128">To get around this, you can use the `Imports` statement to define an *alias*—an abbreviated name you can use in place of a fully qualified name.</span></span> <span data-ttu-id="c8ab8-129">Por exemplo, o exemplo de código a seguir cria aliases para dois nomes totalmente qualificados e usa esses aliases para definir dois objetos.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-129">For example, the following code example creates aliases for two fully qualified names, and uses these aliases to define two objects.</span></span>  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 <span data-ttu-id="c8ab8-130">Se você usar a `Imports` instrução sem um alias, poderá usar todos os nomes nesse namespace sem qualificação, desde que eles sejam exclusivos ao projeto.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-130">If you use the `Imports` statement without an alias, you can use all the names in that namespace without qualification, provided they are unique to the project.</span></span> <span data-ttu-id="c8ab8-131">Se o seu projeto `Imports` contiver instruções para namespaces que contêm itens com o mesmo nome, você deverá qualificar totalmente esse nome ao usá-lo.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-131">If your project contains `Imports` statements for namespaces that contain items with the same name, you must fully qualify that name when you use it.</span></span> <span data-ttu-id="c8ab8-132">Suponha, por exemplo, que o projeto contivesse `Imports` as duas instruções a seguir:</span><span class="sxs-lookup"><span data-stu-id="c8ab8-132">Suppose, for example, your project contained the following two `Imports` statements:</span></span>  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 <span data-ttu-id="c8ab8-133">Se você tentar usar `Class1` o sem qualificá-lo totalmente, Visual Basic produzirá um erro informando que o nome `Class1` é ambíguo.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-133">If you attempt to use `Class1` without fully qualifying it, Visual Basic produces an error stating that the name `Class1` is ambiguous.</span></span>  
  
## <a name="namespace-level-statements"></a><span data-ttu-id="c8ab8-134">Instruções de nível de namespace</span><span class="sxs-lookup"><span data-stu-id="c8ab8-134">Namespace Level Statements</span></span>  
 <span data-ttu-id="c8ab8-135">Em um namespace, você pode definir itens como módulos, interfaces, classes, delegados, enumerações, estruturas e outros namespaces.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-135">Within a namespace, you can define items such as modules, interfaces, classes, delegates, enumerations, structures, and other namespaces.</span></span> <span data-ttu-id="c8ab8-136">Você não pode definir itens como propriedades, procedimentos, variáveis e eventos no nível de namespace.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-136">You cannot define items such as properties, procedures, variables and events at the namespace level.</span></span> <span data-ttu-id="c8ab8-137">Esses itens devem ser declarados em contêineres, como módulos, estruturas ou classes.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-137">These items must be declared within containers such as modules, structures, or classes.</span></span>  
  
## <a name="global-keyword-in-fully-qualified-names"></a><span data-ttu-id="c8ab8-138">Palavra-chave global em nomes totalmente qualificados</span><span class="sxs-lookup"><span data-stu-id="c8ab8-138">Global Keyword in Fully Qualified Names</span></span>  
 <span data-ttu-id="c8ab8-139">Se você tiver definido uma hierarquia aninhada de namespaces, o código dentro dessa hierarquia poderá ser impedido <xref:System?displayProperty=nameWithType> de acessar o namespace do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-139">If you have defined a nested hierarchy of namespaces, code inside that hierarchy might be blocked from accessing the <xref:System?displayProperty=nameWithType> namespace of the .NET Framework.</span></span> <span data-ttu-id="c8ab8-140">O exemplo a seguir ilustra uma hierarquia na qual `SpecialSpace.System` o namespace bloqueia o <xref:System?displayProperty=nameWithType>acesso ao.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-140">The following example illustrates a hierarchy in which the `SpecialSpace.System` namespace blocks access to <xref:System?displayProperty=nameWithType>.</span></span>  
  
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
  
 <span data-ttu-id="c8ab8-141">Como resultado, o compilador Visual Basic não consegue resolver com êxito a referência a <xref:System.Int32?displayProperty=nameWithType>, porque `SpecialSpace.System` não define `Int32`.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-141">As a result, the Visual Basic compiler cannot successfully resolve the reference to <xref:System.Int32?displayProperty=nameWithType>, because `SpecialSpace.System` does not define `Int32`.</span></span> <span data-ttu-id="c8ab8-142">Você pode usar a `Global` palavra-chave para iniciar a cadeia de qualificação no nível mais externo da biblioteca de classes de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-142">You can use the `Global` keyword to start the qualification chain at the outermost level of the .NET Framework class library.</span></span> <span data-ttu-id="c8ab8-143">Isso permite que você especifique o <xref:System?displayProperty=nameWithType> namespace ou qualquer outro namespace na biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-143">This allows you to specify the <xref:System?displayProperty=nameWithType> namespace or any other namespace in the class library.</span></span> <span data-ttu-id="c8ab8-144">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-144">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="c8ab8-145">Você pode usar `Global` o para acessar outros namespaces de nível raiz, <xref:Microsoft.VisualBasic?displayProperty=nameWithType>como e qualquer namespace associado ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-145">You can use `Global` to access other root-level namespaces, such as <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, and any namespace associated with your project.</span></span>  
  
## <a name="global-keyword-in-namespace-statements"></a><span data-ttu-id="c8ab8-146">Palavra-chave global em instruções de namespace</span><span class="sxs-lookup"><span data-stu-id="c8ab8-146">Global Keyword in Namespace Statements</span></span>  
 <span data-ttu-id="c8ab8-147">Você também pode usar a `Global` palavra-chave em uma [instrução de namespace](../../../visual-basic/language-reference/statements/namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c8ab8-147">You can also use the `Global` keyword in a [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span> <span data-ttu-id="c8ab8-148">Isso permite que você defina um namespace fora do namespace raiz do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-148">This lets you define a namespace out of the root namespace of your project.</span></span>  
  
 <span data-ttu-id="c8ab8-149">Todos os namespaces em seu projeto são baseados no namespace raiz do projeto.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-149">All namespaces in your project are based on the root namespace for the project.</span></span>  <span data-ttu-id="c8ab8-150">O Visual Studio atribui o nome do projeto como o namespace raiz padrão para todo o código em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-150">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="c8ab8-151">Por exemplo, se seu projeto for nomeado `ConsoleApplication1`, seus elementos de programação pertencerão `ConsoleApplication1`ao namespace.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-151">For example, if your project is named `ConsoleApplication1`, its programming elements belong to namespace `ConsoleApplication1`.</span></span> <span data-ttu-id="c8ab8-152">Se você declarar `Namespace Magnetosphere`, as referências `Magnetosphere` a no projeto serão acessadas `ConsoleApplication1.Magnetosphere`.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-152">If you declare `Namespace Magnetosphere`, references to `Magnetosphere` in the project will access `ConsoleApplication1.Magnetosphere`.</span></span>  
  
 <span data-ttu-id="c8ab8-153">Os exemplos a seguir usam `Global` a palavra-chave para declarar um namespace fora do namespace raiz do projeto.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-153">The following examples use the `Global` keyword to declare a namespace out of the root namespace for the project.</span></span>  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 <span data-ttu-id="c8ab8-154">Em uma declaração de namespace `Global` , não pode ser aninhada em outro namespace.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-154">In a namespace declaration, `Global` cannot be nested in another namespace.</span></span>  
  
 <span data-ttu-id="c8ab8-155">Você pode usar a [página do aplicativo, designer de projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) para exibir e modificar o **namespace raiz** do projeto.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-155">You can use the [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) to view and modify the **Root Namespace** of the project.</span></span>  <span data-ttu-id="c8ab8-156">Para novos projetos, o **namespace raiz** usa como padrão o nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-156">For new projects, the **Root Namespace** defaults to the project name.</span></span> <span data-ttu-id="c8ab8-157">Para fazer `Global` com que seja o namespace de nível superior, você pode limpar a entrada do **namespace raiz** para que a caixa esteja vazia.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-157">To cause `Global` to be the top-level namespace, you can clear the **Root Namespace** entry so that the box is empty.</span></span> <span data-ttu-id="c8ab8-158">Limpar o **namespace raiz** elimina a necessidade `Global` da palavra-chave nas declarações de namespace.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-158">Clearing **Root Namespace** removes the need for the `Global` keyword in namespace declarations.</span></span>  
  
 <span data-ttu-id="c8ab8-159">Se uma `Namespace` instrução declarar um nome que também seja um namespace no .NET Framework, o namespace .NET Framework ficará indisponível se a `Global` palavra-chave não for usada em um nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-159">If a `Namespace` statement declares a name that is also a namespace in the .NET Framework, the .NET Framework namespace becomes unavailable if the `Global` keyword is not used in a fully qualified name.</span></span> <span data-ttu-id="c8ab8-160">Para habilitar o acesso a esse .NET Framework namespace sem usar `Global` a palavra-chave, você `Global` pode incluir a `Namespace` palavra-chave na instrução.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-160">To enable access to that .NET Framework namespace without using the `Global` keyword, you can include the `Global` keyword in the `Namespace` statement.</span></span>  
  
 <span data-ttu-id="c8ab8-161">O exemplo a seguir tem `Global` a palavra- `System.Text` chave na declaração de namespace.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-161">The following example has the `Global` keyword in the `System.Text` namespace declaration.</span></span>  
  
 <span data-ttu-id="c8ab8-162">Se a `Global` palavra-chave não estiver presente na declaração de <xref:System.Text.StringBuilder> namespace, não poderá ser acessada sem especificar `Global.System.Text.StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-162">If the `Global` keyword was not present in the namespace declaration, <xref:System.Text.StringBuilder> could not be accessed without specifying `Global.System.Text.StringBuilder`.</span></span> <span data-ttu-id="c8ab8-163">Para um projeto chamado `ConsoleApplication1`, as referências `System.Text` a seriam `ConsoleApplication1.System.Text` acessadas se a `Global` palavra-chave não foi usada.</span><span class="sxs-lookup"><span data-stu-id="c8ab8-163">For a project named `ConsoleApplication1`, references to `System.Text` would access `ConsoleApplication1.System.Text` if the `Global` keyword was not used.</span></span>  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="c8ab8-164">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8ab8-164">See also</span></span>

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [<span data-ttu-id="c8ab8-165">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="c8ab8-165">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="c8ab8-166">Referências e a Instrução Imports</span><span class="sxs-lookup"><span data-stu-id="c8ab8-166">References and the Imports Statement</span></span>](references-and-the-imports-statement.md)
- [<span data-ttu-id="c8ab8-167">Instrução Imports (Tipo e Namespace .NET)</span><span class="sxs-lookup"><span data-stu-id="c8ab8-167">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="c8ab8-168">Escrevendo código em soluções do Office</span><span class="sxs-lookup"><span data-stu-id="c8ab8-168">Writing Code in Office Solutions</span></span>](/visualstudio/vsto/writing-code-in-office-solutions)
