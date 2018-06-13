---
title: Como ocultar uma variável com o mesmo nome que a variável (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- declarations [Visual Basic], elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
ms.openlocfilehash: a7ebc4eb44592800decd5ef943750f0cd845afb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653112"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a><span data-ttu-id="23cfc-102">Como ocultar uma variável com o mesmo nome que a variável (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23cfc-102">How to: Hide a Variable with the Same Name as Your Variable (Visual Basic)</span></span>
<span data-ttu-id="23cfc-103">Você pode ocultar uma variável por *sombreamento* -lo, ou seja, redefinindo-o com uma variável de mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="23cfc-103">You can hide a variable by *shadowing* it, that is, by redefining it with a variable of the same name.</span></span> <span data-ttu-id="23cfc-104">Você pode sombrear a variável que você deseja ocultar de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="23cfc-104">You can shadow the variable you want to hide in two ways:</span></span>  
  
-   <span data-ttu-id="23cfc-105">**Sombreamento através de escopo.**</span><span class="sxs-lookup"><span data-stu-id="23cfc-105">**Shadowing Through Scope.**</span></span> <span data-ttu-id="23cfc-106">Você pode sombreá-lo através de escopo, se está redeclarando dentro uma sub-região da região que contém a variável que você deseja ocultar.</span><span class="sxs-lookup"><span data-stu-id="23cfc-106">You can shadow it through scope by redeclaring it inside a subregion of the region containing the variable you want to hide.</span></span>  
  
-   <span data-ttu-id="23cfc-107">**Sombreamento através de herança.**</span><span class="sxs-lookup"><span data-stu-id="23cfc-107">**Shadowing Through Inheritance.**</span></span> <span data-ttu-id="23cfc-108">Se a variável que você deseja ocultar é definida no nível de classe, você pode sombreá-lo por meio da herança por declarar novamente com o [sombras](../../../../visual-basic/language-reference/modifiers/shadows.md) palavra-chave em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="23cfc-108">If the variable you want to hide is defined at class level, you can shadow it through inheritance by redeclaring it with the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in a derived class.</span></span>  
  
## <a name="two-ways-to-hide-a-variable"></a><span data-ttu-id="23cfc-109">Duas maneiras para ocultar uma variável</span><span class="sxs-lookup"><span data-stu-id="23cfc-109">Two Ways to Hide a Variable</span></span>  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a><span data-ttu-id="23cfc-110">Para ocultar uma variável de sombreamento-lo através de escopo</span><span class="sxs-lookup"><span data-stu-id="23cfc-110">To hide a variable by shadowing it through scope</span></span>  
  
1.  <span data-ttu-id="23cfc-111">Determinar a região definindo a variável que você deseja ocultar e determinar uma sub-região no qual redefini-la com sua variável.</span><span class="sxs-lookup"><span data-stu-id="23cfc-111">Determine the region defining the variable you want to hide, and determine a subregion in which to redefine it with your variable.</span></span>  
  
    |<span data-ttu-id="23cfc-112">Região da variável</span><span class="sxs-lookup"><span data-stu-id="23cfc-112">Variable's region</span></span>|<span data-ttu-id="23cfc-113">Sub-região permitido para redefinir a ele</span><span class="sxs-lookup"><span data-stu-id="23cfc-113">Allowable subregion for redefining it</span></span>|  
    |-----------------------|-------------------------------------------|  
    |<span data-ttu-id="23cfc-114">Módulo</span><span class="sxs-lookup"><span data-stu-id="23cfc-114">Module</span></span>|<span data-ttu-id="23cfc-115">Uma classe dentro do módulo</span><span class="sxs-lookup"><span data-stu-id="23cfc-115">A class within the module</span></span>|  
    |<span data-ttu-id="23cfc-116">Classe</span><span class="sxs-lookup"><span data-stu-id="23cfc-116">Class</span></span>|<span data-ttu-id="23cfc-117">Uma subclasse da classe</span><span class="sxs-lookup"><span data-stu-id="23cfc-117">A subclass within the class</span></span><br /><br /> <span data-ttu-id="23cfc-118">Um procedimento dentro da classe</span><span class="sxs-lookup"><span data-stu-id="23cfc-118">A procedure within the class</span></span>|  
  
     <span data-ttu-id="23cfc-119">Você não pode redefinir uma variável de procedimento em um bloco dentro desse procedimento, por exemplo em um `If`... `End If` construção ou `For` loop.</span><span class="sxs-lookup"><span data-stu-id="23cfc-119">You cannot redefine a procedure variable in a block within that procedure, for example in an `If`...`End If` construction or a `For` loop.</span></span>  
  
2.  <span data-ttu-id="23cfc-120">Crie a sub-região se ele ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="23cfc-120">Create the subregion if it does not already exist.</span></span>  
  
3.  <span data-ttu-id="23cfc-121">Dentro da sub-região, gravar um [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) declarar a variável de sombreamento.</span><span class="sxs-lookup"><span data-stu-id="23cfc-121">Within the subregion, write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declaring the shadowing variable.</span></span>  
  
     <span data-ttu-id="23cfc-122">Quando o código dentro a sub-região refere-se ao nome da variável, o compilador resolve a referência à variável de sombreamento.</span><span class="sxs-lookup"><span data-stu-id="23cfc-122">When code inside the subregion refers to the variable name, the compiler resolves the reference to the shadowing variable.</span></span>  
  
     <span data-ttu-id="23cfc-123">O exemplo a seguir ilustra sombreamento através de escopo, bem como uma referência que ignora o sombreamento.</span><span class="sxs-lookup"><span data-stu-id="23cfc-123">The following example illustrates shadowing through scope, as well as a reference that bypasses the shadowing.</span></span>  
  
    ```  
    Module shadowByScope  
        ' The following statement declares num as a module-level variable.  
        Public num As Integer  
        Sub show()  
            ' The following statement declares num as a local variable.  
            Dim num As Integer  
            ' The following statement sets the value of the local variable.  
            num = 2  
            ' The following statement displays the module-level variable.  
            MsgBox(CStr(shadowByScope.num))  
        End Sub  
        Sub useModuleLevelNum()  
            ' The following statement sets the value of the module-level variable.  
            num = 1  
            show()  
        End Sub  
    End Module  
    ```  
  
     <span data-ttu-id="23cfc-124">O exemplo anterior declara a variável `num` no nível de módulo e no nível de procedimento (no procedimento `show`).</span><span class="sxs-lookup"><span data-stu-id="23cfc-124">The preceding example declares the variable `num` both at module level and at procedure level (in the procedure `show`).</span></span> <span data-ttu-id="23cfc-125">A variável local `num` sombreia a variável de nível de módulo `num` em `show`, portanto, a variável local é definida como 2.</span><span class="sxs-lookup"><span data-stu-id="23cfc-125">The local variable `num` shadows the module-level variable `num` within `show`, so the local variable is set to 2.</span></span> <span data-ttu-id="23cfc-126">No entanto, não há nenhuma variável local para sombra `num` no `useModuleLevelNum` procedimento.</span><span class="sxs-lookup"><span data-stu-id="23cfc-126">However, there is no local variable to shadow `num` in the `useModuleLevelNum` procedure.</span></span> <span data-ttu-id="23cfc-127">Portanto, `useModuleLevelNum` define o valor da variável de nível de módulo como 1.</span><span class="sxs-lookup"><span data-stu-id="23cfc-127">Therefore, `useModuleLevelNum` sets the value of the module-level variable to 1.</span></span>  
  
     <span data-ttu-id="23cfc-128">O `MsgBox` chamar dentro de `show` ignora o mecanismo de sombreamento qualificando `num` com o nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="23cfc-128">The `MsgBox` call inside `show` bypasses the shadowing mechanism by qualifying `num` with the module name.</span></span> <span data-ttu-id="23cfc-129">Portanto, ele exibe a variável de nível de módulo em vez da variável local.</span><span class="sxs-lookup"><span data-stu-id="23cfc-129">Therefore, it displays the module-level variable instead of the local variable.</span></span>  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a><span data-ttu-id="23cfc-130">Para ocultar uma variável de sombreamento-lo através de herança</span><span class="sxs-lookup"><span data-stu-id="23cfc-130">To hide a variable by shadowing it through inheritance</span></span>  
  
1.  <span data-ttu-id="23cfc-131">Certifique-se de que a variável que você deseja ocultar é declarada em uma classe e no nível de classe (fora de qualquer procedimento).</span><span class="sxs-lookup"><span data-stu-id="23cfc-131">Be sure the variable you want to hide is declared in a class, and at class level (outside any procedure).</span></span> <span data-ttu-id="23cfc-132">Caso contrário, você não pode sombreá-lo por meio da herança.</span><span class="sxs-lookup"><span data-stu-id="23cfc-132">Otherwise you cannot shadow it through inheritance.</span></span>  
  
2.  <span data-ttu-id="23cfc-133">Defina uma classe derivada da classe de variável, se ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="23cfc-133">Define a class derived from the variable's class if one does not already exist.</span></span>  
  
3.  <span data-ttu-id="23cfc-134">Dentro da classe derivada, escreva um `Dim` declarar a variável de instrução.</span><span class="sxs-lookup"><span data-stu-id="23cfc-134">Inside the derived class, write a `Dim` statement declaring your variable.</span></span> <span data-ttu-id="23cfc-135">Incluir o [sombras](../../../../visual-basic/language-reference/modifiers/shadows.md) palavra-chave na declaração.</span><span class="sxs-lookup"><span data-stu-id="23cfc-135">Include the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>  
  
     <span data-ttu-id="23cfc-136">Quando o código na classe derivada refere-se ao nome da variável, o compilador resolve a referência à sua variável.</span><span class="sxs-lookup"><span data-stu-id="23cfc-136">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>  
  
     <span data-ttu-id="23cfc-137">O exemplo a seguir ilustra sombreamento através de herança.</span><span class="sxs-lookup"><span data-stu-id="23cfc-137">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="23cfc-138">Ele faz duas referências, uma que acessa a variável de sombreamento e outra que ignora o sombreamento.</span><span class="sxs-lookup"><span data-stu-id="23cfc-138">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>  
  
    ```  
    Public Class shadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class shadowDerivedClass  
        Inherits shadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub showStrings()  
            Dim s As String = "Unqualified shadowString: " & shadowString &  
                 vbCrLf & "MyBase.shadowString: " & MyBase.shadowString  
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     <span data-ttu-id="23cfc-139">O exemplo anterior declara a variável `shadowString` na classe base e a sombreia na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="23cfc-139">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="23cfc-140">O procedimento `showStrings` na classe derivada exibe a versão sombreada da cadeia de caracteres quando o nome `shadowString` não está qualificado.</span><span class="sxs-lookup"><span data-stu-id="23cfc-140">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="23cfc-141">Em seguida, exibe a versão sombreada quando `shadowString` é qualificado com o `MyBase` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="23cfc-141">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="23cfc-142">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="23cfc-142">Robust Programming</span></span>  
 <span data-ttu-id="23cfc-143">Sombreamento apresenta mais de uma versão de uma variável com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="23cfc-143">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="23cfc-144">Quando uma declaração de código se refere ao nome da variável, a versão para o qual o compilador resolve a referência depende de fatores como o local da instrução do código e a presença de uma cadeia de caracteres de qualificação.</span><span class="sxs-lookup"><span data-stu-id="23cfc-144">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="23cfc-145">Isso pode aumentar o risco de fazer referência a uma versão não intencional de uma variável sombreada.</span><span class="sxs-lookup"><span data-stu-id="23cfc-145">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="23cfc-146">Você pode reduzir esse risco qualificando totalmente todas as referências a uma variável sombreada.</span><span class="sxs-lookup"><span data-stu-id="23cfc-146">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23cfc-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23cfc-147">See Also</span></span>  
 [<span data-ttu-id="23cfc-148">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="23cfc-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="23cfc-149">Sombreamento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="23cfc-149">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="23cfc-150">Diferenças entre sombreamento e sobreposição</span><span class="sxs-lookup"><span data-stu-id="23cfc-150">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [<span data-ttu-id="23cfc-151">Como ocultar uma variável herdada</span><span class="sxs-lookup"><span data-stu-id="23cfc-151">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [<span data-ttu-id="23cfc-152">Como acessar uma variável oculta por uma classe derivada</span><span class="sxs-lookup"><span data-stu-id="23cfc-152">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [<span data-ttu-id="23cfc-153">Substituições</span><span class="sxs-lookup"><span data-stu-id="23cfc-153">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="23cfc-154">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="23cfc-154">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="23cfc-155">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="23cfc-155">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
