---
title: "Referências a elementos declarados (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declared elements
- references, declared elements
- qualified names
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5de39ac5c30b1cff2a8bfd0cd606dee33c078514
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="references-to-declared-elements-visual-basic"></a><span data-ttu-id="a7348-102">Referências a elementos declarados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7348-102">References to Declared Elements (Visual Basic)</span></span>
<span data-ttu-id="a7348-103">Quando seu código se refere a um elemento declarado, o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador corresponde ao nome na sua referência com a declaração adequada daquele nome.</span><span class="sxs-lookup"><span data-stu-id="a7348-103">When your code refers to a declared element, the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler matches the name in your reference to the appropriate declaration of that name.</span></span> <span data-ttu-id="a7348-104">Se mais de um elemento é declarado com o mesmo nome, você pode controlar qual desses elementos deve ser referenciada por *qualificado* seu nome.</span><span class="sxs-lookup"><span data-stu-id="a7348-104">If more than one element is declared with the same name, you can control which of those elements is to be referenced by *qualifying* its name.</span></span>  
  
 <span data-ttu-id="a7348-105">O compilador tenta coincidir uma referência de nome a uma declaração de nome com o *escopo mais restrito*.</span><span class="sxs-lookup"><span data-stu-id="a7348-105">The compiler attempts to match a name reference to a name declaration with the *narrowest scope*.</span></span> <span data-ttu-id="a7348-106">Isso significa que ele começa com o código fazendo a referência e trabalha externamente através de níveis sucessivos de elementos recipientes.</span><span class="sxs-lookup"><span data-stu-id="a7348-106">This means it starts with the code making the reference and works outward through successive levels of containing elements.</span></span>  
  
 <span data-ttu-id="a7348-107">O exemplo a seguir mostra referências a duas variáveis com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="a7348-107">The following example shows references to two variables with the same name.</span></span> <span data-ttu-id="a7348-108">O exemplo declara duas variáveis, cada uma nomeada `totalCount`, em diferentes níveis de escopo no módulo `container`.</span><span class="sxs-lookup"><span data-stu-id="a7348-108">The example declares two variables, each named `totalCount`, at different levels of scope in module `container`.</span></span> <span data-ttu-id="a7348-109">Quando o procedimento `showCount` exibe `totalCount` sem qualificação, o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador resolve a referência para a declaração com o escopo mais restrito, ou seja, a declaração dentro de `showCount`.</span><span class="sxs-lookup"><span data-stu-id="a7348-109">When the procedure `showCount` displays `totalCount` without qualification, the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler resolves the reference to the declaration with the narrowest scope, namely the local declaration inside `showCount`.</span></span> <span data-ttu-id="a7348-110">Quando ele qualifica `totalCount` com o módulo recipiente `container`, o compilador resolve a referência para a declaração com o escopo mais amplo.</span><span class="sxs-lookup"><span data-stu-id="a7348-110">When it qualifies `totalCount` with the containing module `container`, the compiler resolves the reference to the declaration with the broader scope.</span></span>  
  
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
  
## <a name="qualifying-an-element-name"></a><span data-ttu-id="a7348-111">Um nome de elemento de qualificação</span><span class="sxs-lookup"><span data-stu-id="a7348-111">Qualifying an Element Name</span></span>  
 <span data-ttu-id="a7348-112">Se você quiser substituir esse processo de pesquisa e especificar um nome declarado em um escopo mais amplo, você deve *qualificar* o nome com o elemento que contém o escopo mais amplo.</span><span class="sxs-lookup"><span data-stu-id="a7348-112">If you want to override this search process and specify a name declared in a broader scope, you must *qualify* the name with the containing element of the broader scope.</span></span> <span data-ttu-id="a7348-113">Em alguns casos, você também pode precisar qualificar o elemento que contém.</span><span class="sxs-lookup"><span data-stu-id="a7348-113">In some cases, you might also have to qualify the containing element.</span></span>  
  
 <span data-ttu-id="a7348-114">Classificar um nome significa precedê-lo na sua declaração de código-fonte com informações que identificam onde o elemento de destino é definido.</span><span class="sxs-lookup"><span data-stu-id="a7348-114">Qualifying a name means preceding it in your source statement with information that identifies where the target element is defined.</span></span> <span data-ttu-id="a7348-115">Esta informação é chamada uma *sequência de qualificação*.</span><span class="sxs-lookup"><span data-stu-id="a7348-115">This information is called a *qualification string*.</span></span> <span data-ttu-id="a7348-116">Ele pode incluir um ou mais namespaces e um módulo, classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="a7348-116">It can include one or more namespaces and a module, class, or structure.</span></span>  
  
 <span data-ttu-id="a7348-117">A cadeia de caracteres de qualificação inequivocamente deve especificar o módulo, classe ou estrutura que contém o elemento de destino.</span><span class="sxs-lookup"><span data-stu-id="a7348-117">The qualification string should unambiguously specify the module, class, or structure containing the target element.</span></span> <span data-ttu-id="a7348-118">O contêiner por sua vez pode ser localizado em outro contendo elemento, normalmente um namespace.</span><span class="sxs-lookup"><span data-stu-id="a7348-118">The container might in turn be located in another containing element, usually a namespace.</span></span> <span data-ttu-id="a7348-119">Talvez seja necessário incluir vários elementos continentes na cadeia de caracteres de qualificação.</span><span class="sxs-lookup"><span data-stu-id="a7348-119">You might need to include several containing elements in the qualification string.</span></span>  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a><span data-ttu-id="a7348-120">Para acessar um elemento declarado classificando seu nome</span><span class="sxs-lookup"><span data-stu-id="a7348-120">To access a declared element by qualifying its name</span></span>  
  
1.  <span data-ttu-id="a7348-121">Determine o local no qual o elemento foi definido.</span><span class="sxs-lookup"><span data-stu-id="a7348-121">Determine the location in which the element has been defined.</span></span> <span data-ttu-id="a7348-122">Isso pode incluir um namespace, ou mesmo uma hierarquia de namespaces.</span><span class="sxs-lookup"><span data-stu-id="a7348-122">This might include a namespace, or even a hierarchy of namespaces.</span></span> <span data-ttu-id="a7348-123">Dentro do namespace de nível mais baixo, o elemento deve estar contido em um módulo, classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="a7348-123">Within the lowest-level namespace, the element must be contained in a module, class, or structure.</span></span>  
  
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
  
2.  <span data-ttu-id="a7348-124">Determine um caminho de qualificação com base na localização do elemento de destino.</span><span class="sxs-lookup"><span data-stu-id="a7348-124">Determine a qualification path based on the target element's location.</span></span> <span data-ttu-id="a7348-125">Inicie com o namespace de nível mais alto, vá para o namespace de nível mais baixo e terminar com o módulo, classe ou estrutura que contém o elemento de destino.</span><span class="sxs-lookup"><span data-stu-id="a7348-125">Start with the highest-level namespace, proceed to the lowest-level namespace, and end with the module, class, or structure containing the target element.</span></span> <span data-ttu-id="a7348-126">Cada elemento no caminho deve conter um elemento que o segue.</span><span class="sxs-lookup"><span data-stu-id="a7348-126">Each element in the path must contain the element that follows it.</span></span>  
  
     <span data-ttu-id="a7348-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span><span class="sxs-lookup"><span data-stu-id="a7348-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span></span>  
  
3.  <span data-ttu-id="a7348-128">Prepare a cadeia de caracteres de qualificação para o elemento de destino.</span><span class="sxs-lookup"><span data-stu-id="a7348-128">Prepare the qualification string for the target element.</span></span> <span data-ttu-id="a7348-129">Coloque um ponto final (`.`) após cada elemento no caminho.</span><span class="sxs-lookup"><span data-stu-id="a7348-129">Place a period (`.`) after every element in the path.</span></span> <span data-ttu-id="a7348-130">Seu aplicativo deve ter acesso a todos os elementos na cadeia de caracteres de qualificação.</span><span class="sxs-lookup"><span data-stu-id="a7348-130">Your application must have access to every element in your qualification string.</span></span>  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4.  <span data-ttu-id="a7348-131">Escreva a expressão ou instrução de atribuição referindo-se ao elemento de destino da maneira normal.</span><span class="sxs-lookup"><span data-stu-id="a7348-131">Write the expression or assignment statement referring to the target element in the normal way.</span></span>  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5.  <span data-ttu-id="a7348-132">Preceda o nome do elemento de destino com a cadeia de caracteres de qualificação.</span><span class="sxs-lookup"><span data-stu-id="a7348-132">Precede the target element name with the qualification string.</span></span> <span data-ttu-id="a7348-133">O nome deve seguir imediatamente o período (`.`) que segue o módulo, classe ou estrutura que contém o elemento.</span><span class="sxs-lookup"><span data-stu-id="a7348-133">The name should immediately follow the period (`.`) that follows the module, class, or structure that contains the element.</span></span>  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6.  <span data-ttu-id="a7348-134">O compilador usa a cadeia de caracteres de qualificação para localizar uma declaração clara e inequívoca para que ela pode corresponder a referência de elemento de destino.</span><span class="sxs-lookup"><span data-stu-id="a7348-134">The compiler uses the qualification string to find a clear, unambiguous declaration to which it can match the target element reference.</span></span>  
  
 <span data-ttu-id="a7348-135">Você também pode precisar qualificar uma referência de nome se seu aplicativo tem acesso a mais de um elemento de programação que tem o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="a7348-135">You might also have to qualify a name reference if your application has access to more than one programming element that has the same name.</span></span> <span data-ttu-id="a7348-136">Por exemplo, o <xref:System.Windows.Forms>e <xref:System.Web.UI.WebControls>os dois namespaces contêm uma `Label` classe (<xref:System.Windows.Forms.Label?displayProperty=fullName> e <xref:System.Web.UI.WebControls.Label?displayProperty=fullName>).</xref:System.Web.UI.WebControls.Label?displayProperty=fullName> </xref:System.Windows.Forms.Label?displayProperty=fullName> </xref:System.Web.UI.WebControls> </xref:System.Windows.Forms></span><span class="sxs-lookup"><span data-stu-id="a7348-136">For example, the <xref:System.Windows.Forms> and <xref:System.Web.UI.WebControls> namespaces both contain a `Label` class (<xref:System.Windows.Forms.Label?displayProperty=fullName> and <xref:System.Web.UI.WebControls.Label?displayProperty=fullName>).</span></span> <span data-ttu-id="a7348-137">Se o aplicativo usa ambas, ou se ele define sua própria `Label` classe, você deve distinguir diferentes `Label` objetos.</span><span class="sxs-lookup"><span data-stu-id="a7348-137">If your application uses both, or if it defines its own `Label` class, you must distinguish the different `Label` objects.</span></span> <span data-ttu-id="a7348-138">Inclua o alias de namespace ou de importação na declaração da variável.</span><span class="sxs-lookup"><span data-stu-id="a7348-138">Include the namespace or import alias in the variable declaration.</span></span> <span data-ttu-id="a7348-139">O exemplo a seguir usa o alias de importação.</span><span class="sxs-lookup"><span data-stu-id="a7348-139">The following example uses the import alias.</span></span>  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a><span data-ttu-id="a7348-140">Membros de outros elementos recipientes</span><span class="sxs-lookup"><span data-stu-id="a7348-140">Members of Other Containing Elements</span></span>  
 <span data-ttu-id="a7348-141">Quando você usa um membro não compartilhado de outra classe ou estrutura, primeiro você deve qualificar o nome do membro com uma variável ou expressão que aponta para uma instância da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="a7348-141">When you use a nonshared member of another class or structure, you must first qualify the member name with a variable or expression that points to an instance of the class or structure.</span></span> <span data-ttu-id="a7348-142">No exemplo a seguir, `demoClass` é uma instância de uma classe chamada `class1`.</span><span class="sxs-lookup"><span data-stu-id="a7348-142">In the following example, `demoClass` is an instance of a class named `class1`.</span></span>  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 <span data-ttu-id="a7348-143">Você não pode usar o nome da classe para qualificar um membro que não seja [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="a7348-143">You cannot use the class name itself to qualify a member that is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="a7348-144">Você deve primeiro criar uma instância em uma variável de objeto (nesse caso `demoClass`) e, em seguida, fazer referência a ela, pelo nome da variável.</span><span class="sxs-lookup"><span data-stu-id="a7348-144">You must first create an instance in an object variable (in this case `demoClass`) and then reference it by the variable name.</span></span>  
  
 <span data-ttu-id="a7348-145">Se uma classe ou estrutura tiver um `Shared` membro, você pode qualificar desse membro com o nome de classe ou estrutura ou com uma variável ou expressão que aponta para uma instância.</span><span class="sxs-lookup"><span data-stu-id="a7348-145">If a class or structure has a `Shared` member, you can qualify that member either with the class or structure name or with a variable or expression that points to an instance.</span></span>  
  
 <span data-ttu-id="a7348-146">Um módulo não tem nenhuma instância separada, e todos os seus membros são `Shared` por padrão.</span><span class="sxs-lookup"><span data-stu-id="a7348-146">A module does not have any separate instances, and all its members are `Shared` by default.</span></span> <span data-ttu-id="a7348-147">Portanto, você pode qualificar um membro de módulo com o nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="a7348-147">Therefore, you qualify a module member with the module name.</span></span>  
  
 <span data-ttu-id="a7348-148">O exemplo a seguir mostra referências qualificadas a procedimentos de membro de módulo.</span><span class="sxs-lookup"><span data-stu-id="a7348-148">The following example shows qualified references to module member procedures.</span></span> <span data-ttu-id="a7348-149">O exemplo declara dois `Sub` procedimentos, nomeados `perform`, em diferentes módulos em um projeto.</span><span class="sxs-lookup"><span data-stu-id="a7348-149">The example declares two `Sub` procedures, both named `perform`, in different modules in a project.</span></span> <span data-ttu-id="a7348-150">Cada um deles pode ser especificado sem qualificação no seu próprio módulo mas deve ser qualificado se referenciado de qualquer outro lugar.</span><span class="sxs-lookup"><span data-stu-id="a7348-150">Each one can be specified without qualification within its own module but must be qualified if referenced from anywhere else.</span></span> <span data-ttu-id="a7348-151">Como referência final em `module3` não se qualificam `perform`, o compilador não pode resolver essa referência.</span><span class="sxs-lookup"><span data-stu-id="a7348-151">Because the final reference in `module3` does not qualify `perform`, the compiler cannot resolve that reference.</span></span>  
  
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
  
## <a name="references-to-projects"></a><span data-ttu-id="a7348-152">Referências a projetos</span><span class="sxs-lookup"><span data-stu-id="a7348-152">References to Projects</span></span>  
 <span data-ttu-id="a7348-153">Usar [pública](../../../../visual-basic/language-reference/modifiers/public.md) elementos definidos em outro projeto, você deve primeiro definir um *referência* à biblioteca de tipo ou assembly do projeto.</span><span class="sxs-lookup"><span data-stu-id="a7348-153">To use [Public](../../../../visual-basic/language-reference/modifiers/public.md) elements defined in another project, you must first set a *reference* to that project's assembly or type library.</span></span> <span data-ttu-id="a7348-154">Para definir uma referência, clique em **adicionar referência** sobre o **projeto** menu ou use o [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) opção de compilador de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="a7348-154">To set a reference, click **Add Reference** on the **Project** menu, or use the [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) command-line compiler option.</span></span>  
  
 <span data-ttu-id="a7348-155">Por exemplo, você pode usar o modelo de objeto XML a [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span><span class="sxs-lookup"><span data-stu-id="a7348-155">For example, you can use the XML object model of the [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span></span> <span data-ttu-id="a7348-156">Se você definir uma referência para o <xref:System.Xml>namespace, você pode declarar e usar qualquer uma das suas classes, como <xref:System.Xml.XmlDocument>.</xref:System.Xml.XmlDocument> </xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="a7348-156">If you set a reference to the <xref:System.Xml> namespace, you can declare and use any of its classes, such as <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="a7348-157">O exemplo a seguir usa <xref:System.Xml.XmlDocument>.</xref:System.Xml.XmlDocument></span><span class="sxs-lookup"><span data-stu-id="a7348-157">The following example uses <xref:System.Xml.XmlDocument>.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a><span data-ttu-id="a7348-158">Importando contendo elementos</span><span class="sxs-lookup"><span data-stu-id="a7348-158">Importing Containing Elements</span></span>  
 <span data-ttu-id="a7348-159">Você pode usar o [instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para *importar* os namespaces que contêm os módulos ou classes que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="a7348-159">You can use the [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to *import* the namespaces that contain the modules or classes that you want to use.</span></span> <span data-ttu-id="a7348-160">Isso permite que você se refira aos elementos definidos em um namespace importado sem qualificar totalmente seus nomes.</span><span class="sxs-lookup"><span data-stu-id="a7348-160">This enables you to refer to the elements defined in an imported namespace without fully qualifying their names.</span></span> <span data-ttu-id="a7348-161">O exemplo a seguir reescreve o exemplo anterior para importar o <xref:System.Xml>namespace.</xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="a7348-161">The following example rewrites the previous example to import the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 <span data-ttu-id="a7348-162">Além disso, o `Imports` instrução pode definir um *alias de importação* para cada namespace importado.</span><span class="sxs-lookup"><span data-stu-id="a7348-162">In addition, the `Imports` statement can define an *import alias* for each imported namespace.</span></span> <span data-ttu-id="a7348-163">Isso pode tornar o código-fonte mais curto e fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="a7348-163">This can make the source code shorter and easier to read.</span></span> <span data-ttu-id="a7348-164">O exemplo a seguir reescreve o exemplo anterior para usar `xD` como um alias para o <xref:System.Xml>namespace.</xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="a7348-164">The following example rewrites the previous example to use `xD` as an alias for the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 <span data-ttu-id="a7348-165">O `Imports` instrução não torna os elementos de outros projetos disponíveis para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a7348-165">The `Imports` statement does not make elements from other projects available to your application.</span></span> <span data-ttu-id="a7348-166">Ou seja, ele não substitui o definindo uma referência.</span><span class="sxs-lookup"><span data-stu-id="a7348-166">That is, it does not take the place of setting a reference.</span></span> <span data-ttu-id="a7348-167">Importar um namespace apenas remove a necessidade de qualificar nomes definidos nesse namespace.</span><span class="sxs-lookup"><span data-stu-id="a7348-167">Importing a namespace just removes the requirement to qualify the names defined in that namespace.</span></span>  
  
 <span data-ttu-id="a7348-168">Você também pode usar o `Imports` instrução de importação de módulos, classes, estruturas e enumerações.</span><span class="sxs-lookup"><span data-stu-id="a7348-168">You can also use the `Imports` statement to import modules, classes, structures, and enumerations.</span></span> <span data-ttu-id="a7348-169">Você pode usar os membros de tais elementos importados sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="a7348-169">You can then use the members of such imported elements without qualification.</span></span> <span data-ttu-id="a7348-170">No entanto, você sempre deve qualificar os membros não compartilhados de classes e estruturas com uma variável ou expressão que é avaliada como uma instância da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="a7348-170">However, you must always qualify nonshared members of classes and structures with a variable or expression that evaluates to an instance of the class or structure.</span></span>  
  
## <a name="naming-guidelines"></a><span data-ttu-id="a7348-171">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="a7348-171">Naming Guidelines</span></span>  
 <span data-ttu-id="a7348-172">Quando você define dois ou mais elementos de programação que têm o mesmo nome, uma *nome ambiguidade* pode resultar quando o compilador tenta resolver uma referência a esse nome.</span><span class="sxs-lookup"><span data-stu-id="a7348-172">When you define two or more programming elements that have the same name, a *name ambiguity* can result when the compiler attempts to resolve a reference to that name.</span></span> <span data-ttu-id="a7348-173">Se mais de uma definição estiver em escopo, ou se nenhuma definição estiver em escopo, a referência é possível resolver.</span><span class="sxs-lookup"><span data-stu-id="a7348-173">If more than one definition is in scope, or if no definition is in scope, the reference is irresolvable.</span></span> <span data-ttu-id="a7348-174">Para obter um exemplo, consulte "Exemplo de referência qualificada" nessa página da Ajuda.</span><span class="sxs-lookup"><span data-stu-id="a7348-174">For an example, see "Qualified Reference Example" on this Help page.</span></span>  
  
 <span data-ttu-id="a7348-175">Você pode evitar ambiguidade de nomes fornecendo nomes exclusivos a todos os seus elementos.</span><span class="sxs-lookup"><span data-stu-id="a7348-175">You can avoid name ambiguity by giving all your elements unique names.</span></span> <span data-ttu-id="a7348-176">Em seguida, você pode fazer referência a qualquer elemento sem precisar qualificar seu nome com um namespace, módulo ou classe.</span><span class="sxs-lookup"><span data-stu-id="a7348-176">Then you can make reference to any element without having to qualify its name with a namespace, module, or class.</span></span> <span data-ttu-id="a7348-177">Você também pode reduzir as chances de acidentalmente se referir ao elemento errado.</span><span class="sxs-lookup"><span data-stu-id="a7348-177">You also reduce the chances of accidentally referring to the wrong element.</span></span>  
  
## <a name="shadowing"></a><span data-ttu-id="a7348-178">Sombreamento</span><span class="sxs-lookup"><span data-stu-id="a7348-178">Shadowing</span></span>  
 <span data-ttu-id="a7348-179">Quando dois elementos de programação compartilham o mesmo nome, um deles pode ocultar, ou *sombra*, outro.</span><span class="sxs-lookup"><span data-stu-id="a7348-179">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="a7348-180">Um elemento sombreado não está disponível para referência; em vez disso, quando seu código usa o nome do elemento sombreado, o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador resolve para o elemento de sombreamento.</span><span class="sxs-lookup"><span data-stu-id="a7348-180">A shadowed element is not available for reference; instead, when your code uses the shadowed element name, the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler resolves it to the shadowing element.</span></span> <span data-ttu-id="a7348-181">Para obter uma explicação mais detalhada com exemplos, consulte [sombreamento no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="a7348-181">For a more detailed explanation with examples, see [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7348-182">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7348-182">See Also</span></span>  
 <span data-ttu-id="a7348-183">[Nomes de elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span><span class="sxs-lookup"><span data-stu-id="a7348-183">[Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span></span>  
<span data-ttu-id="a7348-184"> [Características do elemento declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md) </span><span class="sxs-lookup"><span data-stu-id="a7348-184"> [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md) </span></span>  
<span data-ttu-id="a7348-185"> [PONTA como: modificar propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span><span class="sxs-lookup"><span data-stu-id="a7348-185"> [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span></span>  
<span data-ttu-id="a7348-186"> [Variáveis](../../../../visual-basic/programming-guide/language-features/variables/index.md) </span><span class="sxs-lookup"><span data-stu-id="a7348-186"> [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md) </span></span>  
<span data-ttu-id="a7348-187"> [Instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span><span class="sxs-lookup"><span data-stu-id="a7348-187"> [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span></span>  
<span data-ttu-id="a7348-188"> [Novo operador](../../../../visual-basic/language-reference/operators/new-operator.md) </span><span class="sxs-lookup"><span data-stu-id="a7348-188"> [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) </span></span>  
<span data-ttu-id="a7348-189"> [Público](../../../../visual-basic/language-reference/modifiers/public.md)</span><span class="sxs-lookup"><span data-stu-id="a7348-189"> [Public](../../../../visual-basic/language-reference/modifiers/public.md)</span></span>
