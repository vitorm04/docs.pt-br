---
title: Referências a elementos declarados (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: 18f9920891e35517efe7adcfd4c03e03ac771478
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="references-to-declared-elements-visual-basic"></a><span data-ttu-id="0445e-102">Referências a elementos declarados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0445e-102">References to Declared Elements (Visual Basic)</span></span>
<span data-ttu-id="0445e-103">Quando seu código se refere a um elemento declarado, o compilador do Visual Basic corresponde ao nome na sua referência com a declaração adequada daquele nome.</span><span class="sxs-lookup"><span data-stu-id="0445e-103">When your code refers to a declared element, the Visual Basic compiler matches the name in your reference to the appropriate declaration of that name.</span></span> <span data-ttu-id="0445e-104">Se mais de um elemento é declarado com o mesmo nome, você pode controlar qual desses elementos para ser referenciado por *qualificação* seu nome.</span><span class="sxs-lookup"><span data-stu-id="0445e-104">If more than one element is declared with the same name, you can control which of those elements is to be referenced by *qualifying* its name.</span></span>  
  
 <span data-ttu-id="0445e-105">O compilador tenta fazer a correspondência de uma referência de nome a uma declaração de nome com o *escopo mais restrito*.</span><span class="sxs-lookup"><span data-stu-id="0445e-105">The compiler attempts to match a name reference to a name declaration with the *narrowest scope*.</span></span> <span data-ttu-id="0445e-106">Isso significa que ela começa com o código fazendo a referência e trabalha externamente através de níveis sucessivos do que contém elementos.</span><span class="sxs-lookup"><span data-stu-id="0445e-106">This means it starts with the code making the reference and works outward through successive levels of containing elements.</span></span>  
  
 <span data-ttu-id="0445e-107">O exemplo a seguir mostra as referências a duas variáveis com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="0445e-107">The following example shows references to two variables with the same name.</span></span> <span data-ttu-id="0445e-108">O exemplo declara duas variáveis, cada uma nomeada `totalCount`, em diferentes níveis de escopo no módulo `container`.</span><span class="sxs-lookup"><span data-stu-id="0445e-108">The example declares two variables, each named `totalCount`, at different levels of scope in module `container`.</span></span> <span data-ttu-id="0445e-109">Quando o procedimento `showCount` exibe `totalCount` sem qualificação, o compilador do Visual Basic resolve a referência para a declaração com o escopo mais restrito, ou seja, a declaração dentro de `showCount`.</span><span class="sxs-lookup"><span data-stu-id="0445e-109">When the procedure `showCount` displays `totalCount` without qualification, the Visual Basic compiler resolves the reference to the declaration with the narrowest scope, namely the local declaration inside `showCount`.</span></span> <span data-ttu-id="0445e-110">Quando ela se qualificar `totalCount` com o módulo contendo `container`, o compilador resolve a referência para a declaração com o escopo mais amplo.</span><span class="sxs-lookup"><span data-stu-id="0445e-110">When it qualifies `totalCount` with the containing module `container`, the compiler resolves the reference to the declaration with the broader scope.</span></span>  
  
```vb  
' Assume these two modules are both in the same assembly.  
Module container  
    Public totalCount As Integer = 1  
    Public Sub showCount()  
        Dim totalCount As Integer = 6000  
        ' The following statement displays the local totalCount (6000).  
        MsgBox("Unqualified totalCount is " & CStr(totalCount))  
        ' The following statement displays the module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
Module callingModule  
    Public Sub displayCount()  
        container.showCount()  
        ' The following statement displays the containing module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
```  
  
## <a name="qualifying-an-element-name"></a><span data-ttu-id="0445e-111">Um nome de elemento de qualificação</span><span class="sxs-lookup"><span data-stu-id="0445e-111">Qualifying an Element Name</span></span>  
 <span data-ttu-id="0445e-112">Se você quiser substituir esse processo de pesquisa e especificar um nome declarado em um escopo mais amplo, você deve *qualificar* o nome com o elemento que contém o escopo mais amplo.</span><span class="sxs-lookup"><span data-stu-id="0445e-112">If you want to override this search process and specify a name declared in a broader scope, you must *qualify* the name with the containing element of the broader scope.</span></span> <span data-ttu-id="0445e-113">Em alguns casos, talvez você também precise qualificar o elemento que contém.</span><span class="sxs-lookup"><span data-stu-id="0445e-113">In some cases, you might also have to qualify the containing element.</span></span>  
  
 <span data-ttu-id="0445e-114">Classificar um nome significa precedê-lo na sua instrução de fonte com informações que identificam onde o elemento de destino é definido.</span><span class="sxs-lookup"><span data-stu-id="0445e-114">Qualifying a name means preceding it in your source statement with information that identifies where the target element is defined.</span></span> <span data-ttu-id="0445e-115">Esta informação é chamada uma *cadeia de caracteres de qualificação*.</span><span class="sxs-lookup"><span data-stu-id="0445e-115">This information is called a *qualification string*.</span></span> <span data-ttu-id="0445e-116">Ele pode incluir um ou mais namespaces e um módulo, classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="0445e-116">It can include one or more namespaces and a module, class, or structure.</span></span>  
  
 <span data-ttu-id="0445e-117">A cadeia de caracteres de qualificação inequivocamente deve especificar o módulo, classe ou estrutura que contém o elemento de destino.</span><span class="sxs-lookup"><span data-stu-id="0445e-117">The qualification string should unambiguously specify the module, class, or structure containing the target element.</span></span> <span data-ttu-id="0445e-118">O contêiner por sua vez pode estar localizado em outro contendo elemento, normalmente um namespace.</span><span class="sxs-lookup"><span data-stu-id="0445e-118">The container might in turn be located in another containing element, usually a namespace.</span></span> <span data-ttu-id="0445e-119">Você precisará incluir vários elementos continentes na cadeia de caracteres de qualificação.</span><span class="sxs-lookup"><span data-stu-id="0445e-119">You might need to include several containing elements in the qualification string.</span></span>  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a><span data-ttu-id="0445e-120">Para acessar um elemento declarado classificando seu nome</span><span class="sxs-lookup"><span data-stu-id="0445e-120">To access a declared element by qualifying its name</span></span>  
  
1.  <span data-ttu-id="0445e-121">Determine o local no qual o elemento foi definido.</span><span class="sxs-lookup"><span data-stu-id="0445e-121">Determine the location in which the element has been defined.</span></span> <span data-ttu-id="0445e-122">Isso pode incluir um namespace, ou mesmo uma hierarquia de namespaces.</span><span class="sxs-lookup"><span data-stu-id="0445e-122">This might include a namespace, or even a hierarchy of namespaces.</span></span> <span data-ttu-id="0445e-123">Dentro do namespace de nível mais baixo, o elemento deve estar contido em um módulo, classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="0445e-123">Within the lowest-level namespace, the element must be contained in a module, class, or structure.</span></span>  
  
    ```vb  
    ' Assume the following hierarchy exists outside your code.  
    Namespace outerSpace  
        Namespace innerSpace  
            Module holdsTotals  
                Public Structure totals  
                    Public thisTotal As Integer  
                    Public Shared grandTotal As Long  
                End Structure  
            End Module  
        End Namespace  
    End Namespace  
    ```  
  
2.  <span data-ttu-id="0445e-124">Determine um caminho de qualificação com base na localização do elemento de destino.</span><span class="sxs-lookup"><span data-stu-id="0445e-124">Determine a qualification path based on the target element's location.</span></span> <span data-ttu-id="0445e-125">Iniciar com o namespace de nível mais alto, vá para o namespace de nível mais baixo e terminar com o módulo, classe ou estrutura que contém o elemento de destino.</span><span class="sxs-lookup"><span data-stu-id="0445e-125">Start with the highest-level namespace, proceed to the lowest-level namespace, and end with the module, class, or structure containing the target element.</span></span> <span data-ttu-id="0445e-126">Cada elemento no caminho deve conter o elemento que o segue.</span><span class="sxs-lookup"><span data-stu-id="0445e-126">Each element in the path must contain the element that follows it.</span></span>  
  
     <span data-ttu-id="0445e-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span><span class="sxs-lookup"><span data-stu-id="0445e-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span></span>  
  
3.  <span data-ttu-id="0445e-128">Prepare a cadeia de caracteres de qualificação para o elemento de destino.</span><span class="sxs-lookup"><span data-stu-id="0445e-128">Prepare the qualification string for the target element.</span></span> <span data-ttu-id="0445e-129">Colocar um período (`.`) após cada elemento no caminho.</span><span class="sxs-lookup"><span data-stu-id="0445e-129">Place a period (`.`) after every element in the path.</span></span> <span data-ttu-id="0445e-130">Seu aplicativo deve ter acesso a todos os elementos em sua cadeia de caracteres de qualificação.</span><span class="sxs-lookup"><span data-stu-id="0445e-130">Your application must have access to every element in your qualification string.</span></span>  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4.  <span data-ttu-id="0445e-131">Escreva a expressão ou instrução de atribuição que faz referência ao elemento de destino da maneira normal.</span><span class="sxs-lookup"><span data-stu-id="0445e-131">Write the expression or assignment statement referring to the target element in the normal way.</span></span>  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5.  <span data-ttu-id="0445e-132">Preceda o nome do elemento de destino com a cadeia de caracteres de qualificação.</span><span class="sxs-lookup"><span data-stu-id="0445e-132">Precede the target element name with the qualification string.</span></span> <span data-ttu-id="0445e-133">O nome deve seguir imediatamente o período (`.`) que segue o módulo, classe ou estrutura que contém o elemento.</span><span class="sxs-lookup"><span data-stu-id="0445e-133">The name should immediately follow the period (`.`) that follows the module, class, or structure that contains the element.</span></span>  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6.  <span data-ttu-id="0445e-134">O compilador usa a cadeia de caracteres de qualificação para localizar uma declaração clara e não ambígua, para que ela pode corresponder a referência de elemento de destino.</span><span class="sxs-lookup"><span data-stu-id="0445e-134">The compiler uses the qualification string to find a clear, unambiguous declaration to which it can match the target element reference.</span></span>  
  
 <span data-ttu-id="0445e-135">Você também pode precisar qualificar uma referência de nome se seu aplicativo tem acesso a mais de um elemento de programação que tem o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="0445e-135">You might also have to qualify a name reference if your application has access to more than one programming element that has the same name.</span></span> <span data-ttu-id="0445e-136">Por exemplo, o <xref:System.Windows.Forms> e <xref:System.Web.UI.WebControls> namespaces ambos contêm uma `Label` classe (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> e <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="0445e-136">For example, the <xref:System.Windows.Forms> and <xref:System.Web.UI.WebControls> namespaces both contain a `Label` class (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>).</span></span> <span data-ttu-id="0445e-137">Se seu aplicativo usa ambos, ou se ele define sua própria `Label` classe, você deve distinguir diferentes `Label` objetos.</span><span class="sxs-lookup"><span data-stu-id="0445e-137">If your application uses both, or if it defines its own `Label` class, you must distinguish the different `Label` objects.</span></span> <span data-ttu-id="0445e-138">Inclua o alias de namespace ou de importação na declaração da variável.</span><span class="sxs-lookup"><span data-stu-id="0445e-138">Include the namespace or import alias in the variable declaration.</span></span> <span data-ttu-id="0445e-139">O exemplo a seguir usa o alias de importação.</span><span class="sxs-lookup"><span data-stu-id="0445e-139">The following example uses the import alias.</span></span>  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a><span data-ttu-id="0445e-140">Membros de outros elementos que contém</span><span class="sxs-lookup"><span data-stu-id="0445e-140">Members of Other Containing Elements</span></span>  
 <span data-ttu-id="0445e-141">Quando você usa um membro não compartilhado de outra classe ou estrutura, primeiro você deve qualificar o nome do membro com uma variável ou expressão que aponta para uma instância da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="0445e-141">When you use a nonshared member of another class or structure, you must first qualify the member name with a variable or expression that points to an instance of the class or structure.</span></span> <span data-ttu-id="0445e-142">No exemplo a seguir, `demoClass` é uma instância de uma classe denominada `class1`.</span><span class="sxs-lookup"><span data-stu-id="0445e-142">In the following example, `demoClass` is an instance of a class named `class1`.</span></span>  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 <span data-ttu-id="0445e-143">Você não pode usar o nome da classe para qualificar um membro que não seja [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="0445e-143">You cannot use the class name itself to qualify a member that is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="0445e-144">Você deve primeiro criar uma instância em uma variável de objeto (nesse caso `demoClass`) e, em seguida, referenciá-lo pelo nome da variável.</span><span class="sxs-lookup"><span data-stu-id="0445e-144">You must first create an instance in an object variable (in this case `demoClass`) and then reference it by the variable name.</span></span>  
  
 <span data-ttu-id="0445e-145">Se uma classe ou estrutura tiver um `Shared` membro, você pode qualificar desse membro com o nome de classe ou estrutura ou com uma variável ou expressão que aponta para uma instância.</span><span class="sxs-lookup"><span data-stu-id="0445e-145">If a class or structure has a `Shared` member, you can qualify that member either with the class or structure name or with a variable or expression that points to an instance.</span></span>  
  
 <span data-ttu-id="0445e-146">Um módulo não tem nenhuma instância separada, e todos os seus membros são `Shared` por padrão.</span><span class="sxs-lookup"><span data-stu-id="0445e-146">A module does not have any separate instances, and all its members are `Shared` by default.</span></span> <span data-ttu-id="0445e-147">Portanto, você pode qualificar um membro de módulo com o nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="0445e-147">Therefore, you qualify a module member with the module name.</span></span>  
  
 <span data-ttu-id="0445e-148">O exemplo a seguir mostra referências qualificadas a procedimentos de membro de módulo.</span><span class="sxs-lookup"><span data-stu-id="0445e-148">The following example shows qualified references to module member procedures.</span></span> <span data-ttu-id="0445e-149">O exemplo declara duas `Sub` procedimentos, nomeados `perform`, em diferentes módulos em um projeto.</span><span class="sxs-lookup"><span data-stu-id="0445e-149">The example declares two `Sub` procedures, both named `perform`, in different modules in a project.</span></span> <span data-ttu-id="0445e-150">Cada um deles pode ser especificado sem qualificação no seu próprio módulo, mas deve ser qualificado se referenciado de qualquer outro lugar.</span><span class="sxs-lookup"><span data-stu-id="0445e-150">Each one can be specified without qualification within its own module but must be qualified if referenced from anywhere else.</span></span> <span data-ttu-id="0445e-151">Como referência final em `module3` não se qualifica `perform`, o compilador não pode resolver essa referência.</span><span class="sxs-lookup"><span data-stu-id="0445e-151">Because the final reference in `module3` does not qualify `perform`, the compiler cannot resolve that reference.</span></span>  
  
```vb  
' Assume these three modules are all in the same assembly.  
Module module1  
    Public Sub perform()  
        MsgBox("module1.perform() now returning")  
    End Sub  
End Module  
Module module2  
    Public Sub perform()  
        MsgBox("module2.perform() now returning")  
    End Sub  
    Public Sub doSomething()  
        ' The following statement calls perform in module2, the active module.  
        perform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
    End Sub  
End Module  
Module module3  
    Public Sub callPerform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
        ' The following statement makes an unresolvable name reference  
        ' and therefore generates a COMPILER ERROR.  
        perform() ' INVALID statement  
    End Sub  
End Module  
```  
  
## <a name="references-to-projects"></a><span data-ttu-id="0445e-152">Referências a projetos</span><span class="sxs-lookup"><span data-stu-id="0445e-152">References to Projects</span></span>  
 <span data-ttu-id="0445e-153">Para usar [pública](../../../../visual-basic/language-reference/modifiers/public.md) elementos definidos em outro projeto, você deve primeiro definir um *referência* à biblioteca de tipo ou assembly do projeto.</span><span class="sxs-lookup"><span data-stu-id="0445e-153">To use [Public](../../../../visual-basic/language-reference/modifiers/public.md) elements defined in another project, you must first set a *reference* to that project's assembly or type library.</span></span> <span data-ttu-id="0445e-154">Para definir uma referência, clique em **adicionar referência** no **projeto** menu ou use o [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) opção de compilador de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="0445e-154">To set a reference, click **Add Reference** on the **Project** menu, or use the [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) command-line compiler option.</span></span>  
  
 <span data-ttu-id="0445e-155">Por exemplo, você pode usar o modelo de objeto do XML para o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0445e-155">For example, you can use the XML object model of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="0445e-156">Se você definir uma referência o <xref:System.Xml> namespace, você pode declarar e usar qualquer uma das suas classes, como <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="0445e-156">If you set a reference to the <xref:System.Xml> namespace, you can declare and use any of its classes, such as <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="0445e-157">O exemplo a seguir usa <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="0445e-157">The following example uses <xref:System.Xml.XmlDocument>.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a><span data-ttu-id="0445e-158">Importando que contém elementos</span><span class="sxs-lookup"><span data-stu-id="0445e-158">Importing Containing Elements</span></span>  
 <span data-ttu-id="0445e-159">Você pode usar o [instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para *importar* os namespaces que contêm os módulos ou classes que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="0445e-159">You can use the [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to *import* the namespaces that contain the modules or classes that you want to use.</span></span> <span data-ttu-id="0445e-160">Isso permite que você se refira aos elementos definidos em um namespace importado sem qualificar totalmente seus nomes.</span><span class="sxs-lookup"><span data-stu-id="0445e-160">This enables you to refer to the elements defined in an imported namespace without fully qualifying their names.</span></span> <span data-ttu-id="0445e-161">O exemplo a seguir reescreve o exemplo anterior para importar o <xref:System.Xml> namespace.</span><span class="sxs-lookup"><span data-stu-id="0445e-161">The following example rewrites the previous example to import the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 <span data-ttu-id="0445e-162">Além disso, o `Imports` instrução pode definir um *alias de importação* para cada namespace importado.</span><span class="sxs-lookup"><span data-stu-id="0445e-162">In addition, the `Imports` statement can define an *import alias* for each imported namespace.</span></span> <span data-ttu-id="0445e-163">Isso pode tornar o código-fonte mais curto e mais fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="0445e-163">This can make the source code shorter and easier to read.</span></span> <span data-ttu-id="0445e-164">O exemplo a seguir reescreve o exemplo anterior para usar `xD` como um alias para o <xref:System.Xml> namespace.</span><span class="sxs-lookup"><span data-stu-id="0445e-164">The following example rewrites the previous example to use `xD` as an alias for the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 <span data-ttu-id="0445e-165">O `Imports` instrução não torna os elementos de outros projetos disponíveis para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0445e-165">The `Imports` statement does not make elements from other projects available to your application.</span></span> <span data-ttu-id="0445e-166">Ou seja, ela não leva o lugar de uma referência de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="0445e-166">That is, it does not take the place of setting a reference.</span></span> <span data-ttu-id="0445e-167">Importar um namespace apenas remove a necessidade de qualificar nomes definidos nesse namespace.</span><span class="sxs-lookup"><span data-stu-id="0445e-167">Importing a namespace just removes the requirement to qualify the names defined in that namespace.</span></span>  
  
 <span data-ttu-id="0445e-168">Você também pode usar o `Imports` instrução para importar os módulos, classes, estruturas e enumerações.</span><span class="sxs-lookup"><span data-stu-id="0445e-168">You can also use the `Imports` statement to import modules, classes, structures, and enumerations.</span></span> <span data-ttu-id="0445e-169">Você pode usar os membros de tais elementos importados sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="0445e-169">You can then use the members of such imported elements without qualification.</span></span> <span data-ttu-id="0445e-170">No entanto, você sempre deve qualificar os membros não compartilhados de classes e estruturas com uma variável ou expressão que é avaliada como uma instância da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="0445e-170">However, you must always qualify nonshared members of classes and structures with a variable or expression that evaluates to an instance of the class or structure.</span></span>  
  
## <a name="naming-guidelines"></a><span data-ttu-id="0445e-171">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="0445e-171">Naming Guidelines</span></span>  
 <span data-ttu-id="0445e-172">Quando você define dois ou mais elementos de programação que têm o mesmo nome, um *nome ambiguidade* podem ocorrer quando o compilador tenta resolver uma referência a esse nome.</span><span class="sxs-lookup"><span data-stu-id="0445e-172">When you define two or more programming elements that have the same name, a *name ambiguity* can result when the compiler attempts to resolve a reference to that name.</span></span> <span data-ttu-id="0445e-173">Se mais de uma definição está no escopo, ou se nenhuma definição estiver no escopo, a referência é possível resolver.</span><span class="sxs-lookup"><span data-stu-id="0445e-173">If more than one definition is in scope, or if no definition is in scope, the reference is irresolvable.</span></span> <span data-ttu-id="0445e-174">Para obter um exemplo, consulte "Exemplo de referência qualificada" nessa página da Ajuda.</span><span class="sxs-lookup"><span data-stu-id="0445e-174">For an example, see "Qualified Reference Example" on this Help page.</span></span>  
  
 <span data-ttu-id="0445e-175">Você pode evitar ambiguidade de nomes fornecendo nomes exclusivos a todos os seus elementos.</span><span class="sxs-lookup"><span data-stu-id="0445e-175">You can avoid name ambiguity by giving all your elements unique names.</span></span> <span data-ttu-id="0445e-176">Em seguida, você pode fazer referência a qualquer elemento sem ter que qualificar o nome com um namespace, módulo ou classe.</span><span class="sxs-lookup"><span data-stu-id="0445e-176">Then you can make reference to any element without having to qualify its name with a namespace, module, or class.</span></span> <span data-ttu-id="0445e-177">Você também pode reduzir as chances de acidentalmente se referir ao elemento errado.</span><span class="sxs-lookup"><span data-stu-id="0445e-177">You also reduce the chances of accidentally referring to the wrong element.</span></span>  
  
## <a name="shadowing"></a><span data-ttu-id="0445e-178">Sombreamento</span><span class="sxs-lookup"><span data-stu-id="0445e-178">Shadowing</span></span>  
 <span data-ttu-id="0445e-179">Quando dois elementos de programação compartilham o mesmo nome, um deles pode ocultar, ou *sombra*, outro.</span><span class="sxs-lookup"><span data-stu-id="0445e-179">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="0445e-180">Um elemento sombreado não está disponível para referência; em vez disso, quando seu código usa o nome do elemento sombreado, o compilador do Visual Basic resolve para o elemento de sombreamento.</span><span class="sxs-lookup"><span data-stu-id="0445e-180">A shadowed element is not available for reference; instead, when your code uses the shadowed element name, the Visual Basic compiler resolves it to the shadowing element.</span></span> <span data-ttu-id="0445e-181">Para obter uma explicação mais detalhada com exemplos, consulte [sombreamento no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="0445e-181">For a more detailed explanation with examples, see [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0445e-182">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0445e-182">See Also</span></span>  
 [<span data-ttu-id="0445e-183">Nomes de Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="0445e-183">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="0445e-184">Características do Elemento Declarado</span><span class="sxs-lookup"><span data-stu-id="0445e-184">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="0445e-185">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="0445e-185">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="0445e-186">Variáveis</span><span class="sxs-lookup"><span data-stu-id="0445e-186">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [<span data-ttu-id="0445e-187">Instrução Imports (Tipo e Namespace .NET)</span><span class="sxs-lookup"><span data-stu-id="0445e-187">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="0445e-188">Operador New</span><span class="sxs-lookup"><span data-stu-id="0445e-188">New Operator</span></span>](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [<span data-ttu-id="0445e-189">Público</span><span class="sxs-lookup"><span data-stu-id="0445e-189">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)
