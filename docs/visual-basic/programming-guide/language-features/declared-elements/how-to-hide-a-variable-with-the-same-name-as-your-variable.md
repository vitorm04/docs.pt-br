---
title: Como ocultar uma variável com o mesmo nome que a variável
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
ms.openlocfilehash: c1f4c2fbf339358be77e76468b1db94616bf04a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357226"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a><span data-ttu-id="c1105-102">Como ocultar uma variável com o mesmo nome que a variável (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1105-102">How to: Hide a Variable with the Same Name as Your Variable (Visual Basic)</span></span>

<span data-ttu-id="c1105-103">Você pode ocultar uma variável *sombreando* -a, ou seja, redefinindo-a com uma variável de mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="c1105-103">You can hide a variable by *shadowing* it, that is, by redefining it with a variable of the same name.</span></span> <span data-ttu-id="c1105-104">Você pode sombrear a variável que deseja ocultar de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="c1105-104">You can shadow the variable you want to hide in two ways:</span></span>

- <span data-ttu-id="c1105-105">**Sombreamento por meio do escopo.**</span><span class="sxs-lookup"><span data-stu-id="c1105-105">**Shadowing Through Scope.**</span></span> <span data-ttu-id="c1105-106">Você pode sombrear a ti por meio do escopo, redeclarando-a dentro de uma sub-região da região que contém a variável que você deseja ocultar.</span><span class="sxs-lookup"><span data-stu-id="c1105-106">You can shadow it through scope by redeclaring it inside a subregion of the region containing the variable you want to hide.</span></span>

- <span data-ttu-id="c1105-107">**Sombreamento por meio de herança.**</span><span class="sxs-lookup"><span data-stu-id="c1105-107">**Shadowing Through Inheritance.**</span></span> <span data-ttu-id="c1105-108">Se a variável que você deseja ocultar estiver definida no nível de classe, você poderá sombrear a ti por meio da herança redeclarando-a com a palavra-chave [Shadows](../../../language-reference/modifiers/shadows.md) em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c1105-108">If the variable you want to hide is defined at class level, you can shadow it through inheritance by redeclaring it with the [Shadows](../../../language-reference/modifiers/shadows.md) keyword in a derived class.</span></span>

## <a name="two-ways-to-hide-a-variable"></a><span data-ttu-id="c1105-109">Duas maneiras de ocultar uma variável</span><span class="sxs-lookup"><span data-stu-id="c1105-109">Two Ways to Hide a Variable</span></span>

#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a><span data-ttu-id="c1105-110">Para ocultar uma variável Sombreando-a por escopo</span><span class="sxs-lookup"><span data-stu-id="c1105-110">To hide a variable by shadowing it through scope</span></span>

1. <span data-ttu-id="c1105-111">Determine a região que define a variável que você deseja ocultar e determine uma sub-região na qual redefini-la com sua variável.</span><span class="sxs-lookup"><span data-stu-id="c1105-111">Determine the region defining the variable you want to hide, and determine a subregion in which to redefine it with your variable.</span></span>

    |<span data-ttu-id="c1105-112">Região da variável</span><span class="sxs-lookup"><span data-stu-id="c1105-112">Variable's region</span></span>|<span data-ttu-id="c1105-113">Subregião permitida para redefini-la</span><span class="sxs-lookup"><span data-stu-id="c1105-113">Allowable subregion for redefining it</span></span>|
    |-----------------------|-------------------------------------------|
    |<span data-ttu-id="c1105-114">Módulo</span><span class="sxs-lookup"><span data-stu-id="c1105-114">Module</span></span>|<span data-ttu-id="c1105-115">Uma classe dentro do módulo</span><span class="sxs-lookup"><span data-stu-id="c1105-115">A class within the module</span></span>|
    |<span data-ttu-id="c1105-116">Classe</span><span class="sxs-lookup"><span data-stu-id="c1105-116">Class</span></span>|<span data-ttu-id="c1105-117">Uma subclasse dentro da classe</span><span class="sxs-lookup"><span data-stu-id="c1105-117">A subclass within the class</span></span><br /><br /> <span data-ttu-id="c1105-118">Um procedimento dentro da classe</span><span class="sxs-lookup"><span data-stu-id="c1105-118">A procedure within the class</span></span>|

    <span data-ttu-id="c1105-119">Você não pode redefinir uma variável de procedimento em um bloco dentro desse procedimento, por exemplo, em uma `If` construção... `End If` ou em um `For` loop.</span><span class="sxs-lookup"><span data-stu-id="c1105-119">You cannot redefine a procedure variable in a block within that procedure, for example in an `If`...`End If` construction or a `For` loop.</span></span>

2. <span data-ttu-id="c1105-120">Crie a subregião se ela ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="c1105-120">Create the subregion if it does not already exist.</span></span>

3. <span data-ttu-id="c1105-121">Dentro da sub-região, escreva uma [instrução Dim](../../../language-reference/statements/dim-statement.md) declarando a variável de sombreamento.</span><span class="sxs-lookup"><span data-stu-id="c1105-121">Within the subregion, write a [Dim Statement](../../../language-reference/statements/dim-statement.md) declaring the shadowing variable.</span></span>

    <span data-ttu-id="c1105-122">Quando o código dentro da sub-região refere-se ao nome da variável, o compilador resolve a referência à variável de sombreamento.</span><span class="sxs-lookup"><span data-stu-id="c1105-122">When code inside the subregion refers to the variable name, the compiler resolves the reference to the shadowing variable.</span></span>

    <span data-ttu-id="c1105-123">O exemplo a seguir ilustra o sombreamento por meio do escopo, bem como uma referência que ignora o sombreamento.</span><span class="sxs-lookup"><span data-stu-id="c1105-123">The following example illustrates shadowing through scope, as well as a reference that bypasses the shadowing.</span></span>

    ```vb
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

    <span data-ttu-id="c1105-124">O exemplo anterior declara a variável `num` no nível do módulo e no nível do procedimento (no procedimento `show` ).</span><span class="sxs-lookup"><span data-stu-id="c1105-124">The preceding example declares the variable `num` both at module level and at procedure level (in the procedure `show`).</span></span> <span data-ttu-id="c1105-125">A variável local `num` sombreia a variável em nível de módulo `num` dentro `show` , portanto, a variável local é definida como 2.</span><span class="sxs-lookup"><span data-stu-id="c1105-125">The local variable `num` shadows the module-level variable `num` within `show`, so the local variable is set to 2.</span></span> <span data-ttu-id="c1105-126">No entanto, não há nenhuma variável local para sombrear `num` no `useModuleLevelNum` procedimento.</span><span class="sxs-lookup"><span data-stu-id="c1105-126">However, there is no local variable to shadow `num` in the `useModuleLevelNum` procedure.</span></span> <span data-ttu-id="c1105-127">Portanto, `useModuleLevelNum` define o valor da variável em nível de módulo como 1.</span><span class="sxs-lookup"><span data-stu-id="c1105-127">Therefore, `useModuleLevelNum` sets the value of the module-level variable to 1.</span></span>

    <span data-ttu-id="c1105-128">A `MsgBox` chamada dentro `show` ignora o mecanismo de sombreamento qualificando `num` com o nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="c1105-128">The `MsgBox` call inside `show` bypasses the shadowing mechanism by qualifying `num` with the module name.</span></span> <span data-ttu-id="c1105-129">Portanto, ele exibe a variável em nível de módulo em vez da variável local.</span><span class="sxs-lookup"><span data-stu-id="c1105-129">Therefore, it displays the module-level variable instead of the local variable.</span></span>

#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a><span data-ttu-id="c1105-130">Para ocultar uma variável Sombreando-a por meio de herança</span><span class="sxs-lookup"><span data-stu-id="c1105-130">To hide a variable by shadowing it through inheritance</span></span>

1. <span data-ttu-id="c1105-131">Certifique-se de que a variável que você deseja ocultar seja declarada em uma classe e no nível de classe (fora de qualquer procedimento).</span><span class="sxs-lookup"><span data-stu-id="c1105-131">Be sure the variable you want to hide is declared in a class, and at class level (outside any procedure).</span></span> <span data-ttu-id="c1105-132">Caso contrário, não será possível sombrear a ti por meio de herança.</span><span class="sxs-lookup"><span data-stu-id="c1105-132">Otherwise you cannot shadow it through inheritance.</span></span>

2. <span data-ttu-id="c1105-133">Defina uma classe derivada da classe da variável, caso ainda não exista uma.</span><span class="sxs-lookup"><span data-stu-id="c1105-133">Define a class derived from the variable's class if one does not already exist.</span></span>

3. <span data-ttu-id="c1105-134">Dentro da classe derivada, escreva uma `Dim` instrução que declare sua variável.</span><span class="sxs-lookup"><span data-stu-id="c1105-134">Inside the derived class, write a `Dim` statement declaring your variable.</span></span> <span data-ttu-id="c1105-135">Inclua a palavra-chave [Shadows](../../../language-reference/modifiers/shadows.md) na declaração.</span><span class="sxs-lookup"><span data-stu-id="c1105-135">Include the [Shadows](../../../language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>

    <span data-ttu-id="c1105-136">Quando o código na classe derivada se refere ao nome da variável, o compilador resolve a referência à sua variável.</span><span class="sxs-lookup"><span data-stu-id="c1105-136">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>

    <span data-ttu-id="c1105-137">O exemplo a seguir ilustra o sombreamento por meio de herança.</span><span class="sxs-lookup"><span data-stu-id="c1105-137">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="c1105-138">Ele faz duas referências, uma que acessa a variável de sombreamento e outra que ignora o sombreamento.</span><span class="sxs-lookup"><span data-stu-id="c1105-138">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>

    ```vb
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

    <span data-ttu-id="c1105-139">O exemplo anterior declara a variável `shadowString` na classe base e a sombreia na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c1105-139">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="c1105-140">O procedimento `showStrings` na classe derivada exibe a versão de sombreamento da cadeia de caracteres quando o nome `shadowString` não é qualificado.</span><span class="sxs-lookup"><span data-stu-id="c1105-140">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="c1105-141">Em seguida, ele exibe a versão sombreada quando `shadowString` é qualificado com a `MyBase` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="c1105-141">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="c1105-142">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="c1105-142">Robust Programming</span></span>

<span data-ttu-id="c1105-143">O sombreamento apresenta mais de uma versão de uma variável com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="c1105-143">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="c1105-144">Quando uma instrução de código se refere ao nome da variável, a versão para a qual o compilador resolve a referência depende de fatores como o local da instrução do código e a presença de uma cadeia de caracteres de qualificação.</span><span class="sxs-lookup"><span data-stu-id="c1105-144">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="c1105-145">Isso pode aumentar o risco de se referir a uma versão não intencional de uma variável sombreada.</span><span class="sxs-lookup"><span data-stu-id="c1105-145">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="c1105-146">Você pode reduzir esse risco Qualificando totalmente todas as referências a uma variável sombreada.</span><span class="sxs-lookup"><span data-stu-id="c1105-146">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1105-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="c1105-147">See also</span></span>

- [<span data-ttu-id="c1105-148">Referências a elementos declarados</span><span class="sxs-lookup"><span data-stu-id="c1105-148">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="c1105-149">Sombreamento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c1105-149">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="c1105-150">Diferenças entre sombreamento e sobreposição</span><span class="sxs-lookup"><span data-stu-id="c1105-150">Differences Between Shadowing and Overriding</span></span>](differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="c1105-151">Como ocultar uma variável herdada</span><span class="sxs-lookup"><span data-stu-id="c1105-151">How to: Hide an Inherited Variable</span></span>](how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="c1105-152">Como acessar uma variável oculta por uma classe derivada</span><span class="sxs-lookup"><span data-stu-id="c1105-152">How to: Access a Variable Hidden by a Derived Class</span></span>](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="c1105-153">Substituições</span><span class="sxs-lookup"><span data-stu-id="c1105-153">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="c1105-154">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="c1105-154">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="c1105-155">Noções básicas de herança</span><span class="sxs-lookup"><span data-stu-id="c1105-155">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
