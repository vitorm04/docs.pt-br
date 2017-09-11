---
title: "Como: acessar uma variável ocultada por uma classe derivada (Visual Basic) | Documentos do Microsoft"
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
- qualification, of element names
- base classes, accessing elements
- element names, qualification
- references, declared elements
- declared elements, referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
caps.latest.revision: 20
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
ms.openlocfilehash: b102b93c98962fe9a2992b7d285f175508ef628e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a><span data-ttu-id="3ae7f-102">Como acessar uma variável oculta por uma classe derivada (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ae7f-102">How to: Access a Variable Hidden by a Derived Class (Visual Basic)</span></span>
<span data-ttu-id="3ae7f-103">Quando o código em uma classe derivada acessa uma variável, o compilador resolve normalmente a referência para a versão mais acessível, ou seja, a versão acessível as menor etapas derivacionais para trás da classe de acesso.</span><span class="sxs-lookup"><span data-stu-id="3ae7f-103">When code in a derived class accesses a variable, the compiler normally resolves the reference to the closest accessible version, that is, the accessible version the fewest derivational steps backward from the accessing class.</span></span> <span data-ttu-id="3ae7f-104">Se a variável é definida na classe derivada, o código normalmente acessa essa definição.</span><span class="sxs-lookup"><span data-stu-id="3ae7f-104">If the variable is defined in the derived class, the code normally accesses that definition.</span></span>  
  
 <span data-ttu-id="3ae7f-105">Se a variável de classe derivada sombreia uma variável na classe base, ele oculta a versão da classe base.</span><span class="sxs-lookup"><span data-stu-id="3ae7f-105">If the derived class variable shadows a variable in the base class, it hides the base class version.</span></span> <span data-ttu-id="3ae7f-106">No entanto, você pode acessar a variável de classe base usando o `MyBase` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="3ae7f-106">However, you can access the base class variable by qualifying it with the `MyBase` keyword.</span></span>  
  
### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a><span data-ttu-id="3ae7f-107">Para acessar uma variável ocultada por uma classe derivada da classe base</span><span class="sxs-lookup"><span data-stu-id="3ae7f-107">To access a base class variable hidden by a derived class</span></span>  
  
-   <span data-ttu-id="3ae7f-108">Em uma expressão ou instrução de atribuição, preceda o nome da variável com o `MyBase` palavra-chave e um período (`.`).</span><span class="sxs-lookup"><span data-stu-id="3ae7f-108">In an expression or assignment statement, precede the variable name with the `MyBase` keyword and a period (`.`).</span></span>  
  
     <span data-ttu-id="3ae7f-109">O compilador resolve a referência à versão da classe base da variável.</span><span class="sxs-lookup"><span data-stu-id="3ae7f-109">The compiler resolves the reference to the base class version of the variable.</span></span>  
  
     <span data-ttu-id="3ae7f-110">O exemplo a seguir ilustra sombreamento através de herança.</span><span class="sxs-lookup"><span data-stu-id="3ae7f-110">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="3ae7f-111">Ele faz duas referências, que acessa a variável de sombreamento e outra que ignora o sombreamento.</span><span class="sxs-lookup"><span data-stu-id="3ae7f-111">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>  
  
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
  
     <span data-ttu-id="3ae7f-112">O exemplo anterior declara a variável `shadowString` na classe base e a sombreia na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="3ae7f-112">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="3ae7f-113">O procedimento `showStrings` na classe derivada exibe a versão sombreada da cadeia de caracteres quando o nome `shadowString` não está qualificado.</span><span class="sxs-lookup"><span data-stu-id="3ae7f-113">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="3ae7f-114">Em seguida, exibe a versão sombreada quando `shadowString` qualificado com o `MyBase` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="3ae7f-114">It then displays the shadowed version when `shadowString` is qualified with the `MyBase`  keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3ae7f-115">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="3ae7f-115">Robust Programming</span></span>  
 <span data-ttu-id="3ae7f-116">Para reduzir o risco de se referir a uma versão não intencional de uma variável sombreada, você pode qualificar totalmente todas as referências a uma variável sombreada.</span><span class="sxs-lookup"><span data-stu-id="3ae7f-116">To lower the risk of referring to an unintended version of a shadowed variable, you can fully qualify all references to a shadowed variable.</span></span> <span data-ttu-id="3ae7f-117">Sombreamento introduz mais de uma versão de uma variável com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="3ae7f-117">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="3ae7f-118">Quando uma declaração de código refere-se ao nome da variável, a versão para que o compilador resolve a referência depende de fatores como o local da instrução do código e a presença de uma cadeia de caracteres de qualificação.</span><span class="sxs-lookup"><span data-stu-id="3ae7f-118">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="3ae7f-119">Isso pode aumentar o risco de se referir à versão errada da variável.</span><span class="sxs-lookup"><span data-stu-id="3ae7f-119">This can increase the risk of referring to the wrong version of the variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ae7f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ae7f-120">See Also</span></span>  
 <span data-ttu-id="3ae7f-121">[Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span><span class="sxs-lookup"><span data-stu-id="3ae7f-121">[References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span></span>  
<span data-ttu-id="3ae7f-122"> [Sombreamento no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md) </span><span class="sxs-lookup"><span data-stu-id="3ae7f-122"> [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md) </span></span>  
<span data-ttu-id="3ae7f-123"> [Diferenças entre sombreamento e sobreposição](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md) </span><span class="sxs-lookup"><span data-stu-id="3ae7f-123"> [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md) </span></span>  
<span data-ttu-id="3ae7f-124"> [Como: ocultar uma variável com o mesmo nome que sua variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) </span><span class="sxs-lookup"><span data-stu-id="3ae7f-124"> [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) </span></span>  
<span data-ttu-id="3ae7f-125"> [Como: ocultar uma variável herdada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md) </span><span class="sxs-lookup"><span data-stu-id="3ae7f-125"> [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md) </span></span>  
<span data-ttu-id="3ae7f-126"> [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md) </span><span class="sxs-lookup"><span data-stu-id="3ae7f-126"> [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) </span></span>  
<span data-ttu-id="3ae7f-127"> [Substituições](../../../../visual-basic/language-reference/modifiers/overrides.md) </span><span class="sxs-lookup"><span data-stu-id="3ae7f-127"> [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md) </span></span>  
<span data-ttu-id="3ae7f-128"> [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md) </span><span class="sxs-lookup"><span data-stu-id="3ae7f-128"> [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md) </span></span>  
<span data-ttu-id="3ae7f-129"> [Noções Básicas de Herança](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)</span><span class="sxs-lookup"><span data-stu-id="3ae7f-129"> [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)</span></span>
