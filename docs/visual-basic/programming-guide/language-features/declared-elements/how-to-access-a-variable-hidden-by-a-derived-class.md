---
title: Como acessar uma variável oculta por uma classe derivada
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: 276cb1411c66e1f7205507a1b1053cc8642c7cb0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345400"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a><span data-ttu-id="6e578-102">Como acessar uma variável oculta por uma classe derivada (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e578-102">How to: Access a Variable Hidden by a Derived Class (Visual Basic)</span></span>

<span data-ttu-id="6e578-103">Quando o código em uma classe derivada acessa uma variável, o compilador normalmente resolve a referência à versão acessível mais próxima, ou seja, a versão acessível o menor número de etapas de derivação para trás da classe de acesso.</span><span class="sxs-lookup"><span data-stu-id="6e578-103">When code in a derived class accesses a variable, the compiler normally resolves the reference to the closest accessible version, that is, the accessible version the fewest derivational steps backward from the accessing class.</span></span> <span data-ttu-id="6e578-104">Se a variável for definida na classe derivada, o código normalmente acessará essa definição.</span><span class="sxs-lookup"><span data-stu-id="6e578-104">If the variable is defined in the derived class, the code normally accesses that definition.</span></span>

<span data-ttu-id="6e578-105">Se a variável de classe derivada sombreia uma variável na classe base, ela ocultará a versão da classe base.</span><span class="sxs-lookup"><span data-stu-id="6e578-105">If the derived class variable shadows a variable in the base class, it hides the base class version.</span></span> <span data-ttu-id="6e578-106">No entanto, você pode acessar a variável de classe base qualificando-a com a palavra-chave `MyBase`.</span><span class="sxs-lookup"><span data-stu-id="6e578-106">However, you can access the base class variable by qualifying it with the `MyBase` keyword.</span></span>

### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a><span data-ttu-id="6e578-107">Para acessar uma variável de classe base ocultada por uma classe derivada</span><span class="sxs-lookup"><span data-stu-id="6e578-107">To access a base class variable hidden by a derived class</span></span>

- <span data-ttu-id="6e578-108">Em uma expressão ou instrução de atribuição, preceda o nome da variável com a palavra-chave `MyBase` e um ponto (`.`).</span><span class="sxs-lookup"><span data-stu-id="6e578-108">In an expression or assignment statement, precede the variable name with the `MyBase` keyword and a period (`.`).</span></span>

    <span data-ttu-id="6e578-109">O compilador resolve a referência à versão da classe base da variável.</span><span class="sxs-lookup"><span data-stu-id="6e578-109">The compiler resolves the reference to the base class version of the variable.</span></span>

    <span data-ttu-id="6e578-110">O exemplo a seguir ilustra o sombreamento por meio de herança.</span><span class="sxs-lookup"><span data-stu-id="6e578-110">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="6e578-111">Ele faz duas referências, uma que acessa a variável de sombreamento e outra que ignora o sombreamento.</span><span class="sxs-lookup"><span data-stu-id="6e578-111">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>

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

    <span data-ttu-id="6e578-112">O exemplo anterior declara a variável `shadowString` na classe base e a sombreia na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="6e578-112">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="6e578-113">O procedimento `showStrings` na classe derivada exibe a versão de sombreamento da cadeia de caracteres quando o nome `shadowString` não é qualificado.</span><span class="sxs-lookup"><span data-stu-id="6e578-113">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="6e578-114">Em seguida, ele exibe a versão sombreada quando `shadowString` é qualificado com a palavra-chave `MyBase`.</span><span class="sxs-lookup"><span data-stu-id="6e578-114">It then displays the shadowed version when `shadowString` is qualified with the `MyBase`  keyword.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="6e578-115">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="6e578-115">Robust Programming</span></span>

<span data-ttu-id="6e578-116">Para reduzir o risco de se referir a uma versão não intencional de uma variável sombreada, você pode qualificar totalmente todas as referências a uma variável sombreada.</span><span class="sxs-lookup"><span data-stu-id="6e578-116">To lower the risk of referring to an unintended version of a shadowed variable, you can fully qualify all references to a shadowed variable.</span></span> <span data-ttu-id="6e578-117">O sombreamento apresenta mais de uma versão de uma variável com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="6e578-117">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="6e578-118">Quando uma instrução de código se refere ao nome da variável, a versão para a qual o compilador resolve a referência depende de fatores como o local da instrução do código e a presença de uma cadeia de caracteres de qualificação.</span><span class="sxs-lookup"><span data-stu-id="6e578-118">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="6e578-119">Isso pode aumentar o risco de se referir à versão errada da variável.</span><span class="sxs-lookup"><span data-stu-id="6e578-119">This can increase the risk of referring to the wrong version of the variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e578-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e578-120">See also</span></span>

- [<span data-ttu-id="6e578-121">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="6e578-121">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="6e578-122">Sombreamento em Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6e578-122">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="6e578-123">Diferenças entre sombreamento e sobreposição</span><span class="sxs-lookup"><span data-stu-id="6e578-123">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="6e578-124">Como ocultar uma variável com o mesmo nome que a variável</span><span class="sxs-lookup"><span data-stu-id="6e578-124">How to: Hide a Variable with the Same Name as Your Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="6e578-125">Como ocultar uma variável herdada</span><span class="sxs-lookup"><span data-stu-id="6e578-125">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="6e578-126">Sombras</span><span class="sxs-lookup"><span data-stu-id="6e578-126">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="6e578-127">Substituições</span><span class="sxs-lookup"><span data-stu-id="6e578-127">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="6e578-128">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="6e578-128">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="6e578-129">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="6e578-129">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
