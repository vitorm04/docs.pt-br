---
title: Como ocultar uma variável herdada (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
- variables [Visual Basic], hiding inherited
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
ms.openlocfilehash: c59fdd8c6c6d2444b8d687c78c61f4e0d4bf9a52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649133"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a><span data-ttu-id="98758-102">Como ocultar uma variável herdada (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98758-102">How to: Hide an Inherited Variable (Visual Basic)</span></span>
<span data-ttu-id="98758-103">Uma classe derivada herda todas as definições de sua classe base.</span><span class="sxs-lookup"><span data-stu-id="98758-103">A derived class inherits all the definitions of its base class.</span></span> <span data-ttu-id="98758-104">Se você quiser definir uma variável usando o mesmo nome que um elemento da classe base, você pode ocultar, ou *sombra*, esse elemento de classe base quando você define sua variável na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="98758-104">If you want to define a variable using the same name as an element of the base class, you can hide, or *shadow*, that base class element when you define your variable in the derived class.</span></span> <span data-ttu-id="98758-105">Se você fizer isso, o código na classe derivada acessa sua variável, a menos que explicitamente ignora o mecanismo de sombreamento.</span><span class="sxs-lookup"><span data-stu-id="98758-105">If you do this, code in the derived class accesses your variable unless it explicitly bypasses the shadowing mechanism.</span></span>  
  
 <span data-ttu-id="98758-106">Outro motivo, que talvez você queira ocultar uma variável herdada é proteger contra a revisão de classe base.</span><span class="sxs-lookup"><span data-stu-id="98758-106">Another reason you might want to hide an inherited variable is to protect against base class revision.</span></span> <span data-ttu-id="98758-107">A classe base pode passar por uma mudança que altere o elemento que são herdadas.</span><span class="sxs-lookup"><span data-stu-id="98758-107">The base class might undergo a change that alters the element you are inheriting.</span></span> <span data-ttu-id="98758-108">Se isso acontecer, o `Shadows` modificador obriga referências da classe derivada a ser resolvido para a variável, em vez de para o elemento de classe base.</span><span class="sxs-lookup"><span data-stu-id="98758-108">If this happens, the `Shadows` modifier forces references from the derived class to be resolved to your variable, instead of to the base class element.</span></span>  
  
### <a name="to-hide-an-inherited-variable"></a><span data-ttu-id="98758-109">Para ocultar uma variável herdada</span><span class="sxs-lookup"><span data-stu-id="98758-109">To hide an inherited variable</span></span>  
  
1.  <span data-ttu-id="98758-110">Certifique-se de que a variável que você deseja ocultar é declarada no nível de classe (fora de qualquer procedimento).</span><span class="sxs-lookup"><span data-stu-id="98758-110">Be sure the variable you want to hide is declared at class level (outside any procedure).</span></span> <span data-ttu-id="98758-111">Caso contrário, você não precisa ocultá-lo.</span><span class="sxs-lookup"><span data-stu-id="98758-111">Otherwise you do not need to hide it.</span></span>  
  
2.  <span data-ttu-id="98758-112">Dentro de sua classe derivada, escreva uma [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) declarar a variável.</span><span class="sxs-lookup"><span data-stu-id="98758-112">Inside your derived class, write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declaring your variable.</span></span> <span data-ttu-id="98758-113">Use o mesmo nome da variável herdada.</span><span class="sxs-lookup"><span data-stu-id="98758-113">Use the same name as that of the inherited variable.</span></span>  
  
3.  <span data-ttu-id="98758-114">Incluir o [sombras](../../../../visual-basic/language-reference/modifiers/shadows.md) palavra-chave na declaração.</span><span class="sxs-lookup"><span data-stu-id="98758-114">Include the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>  
  
     <span data-ttu-id="98758-115">Quando o código na classe derivada refere-se ao nome da variável, o compilador resolve a referência à sua variável.</span><span class="sxs-lookup"><span data-stu-id="98758-115">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>  
  
     <span data-ttu-id="98758-116">O exemplo a seguir ilustra sombreamento de uma variável herdada.</span><span class="sxs-lookup"><span data-stu-id="98758-116">The following example illustrates shadowing of an inherited variable.</span></span>  
  
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
  
     <span data-ttu-id="98758-117">O exemplo anterior declara a variável `shadowString` na classe base e a sombreia na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="98758-117">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="98758-118">O procedimento `showStrings` na classe derivada exibe a versão sombreada da cadeia de caracteres quando o nome `shadowString` não está qualificado.</span><span class="sxs-lookup"><span data-stu-id="98758-118">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="98758-119">Em seguida, exibe a versão sombreada quando `shadowString` é qualificado com o `MyBase` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="98758-119">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="98758-120">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="98758-120">Robust Programming</span></span>  
 <span data-ttu-id="98758-121">Sombreamento apresenta mais de uma versão de uma variável com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="98758-121">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="98758-122">Quando uma declaração de código se refere ao nome da variável, a versão para o qual o compilador resolve a referência depende de fatores como o local da instrução do código e a presença de uma cadeia de caracteres de qualificação.</span><span class="sxs-lookup"><span data-stu-id="98758-122">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="98758-123">Isso pode aumentar o risco de fazer referência a uma versão não intencional de uma variável sombreada.</span><span class="sxs-lookup"><span data-stu-id="98758-123">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="98758-124">Você pode reduzir esse risco qualificando totalmente todas as referências a uma variável sombreada.</span><span class="sxs-lookup"><span data-stu-id="98758-124">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98758-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98758-125">See Also</span></span>  
 [<span data-ttu-id="98758-126">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="98758-126">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="98758-127">Sombreamento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="98758-127">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="98758-128">Diferenças entre sombreamento e sobreposição</span><span class="sxs-lookup"><span data-stu-id="98758-128">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [<span data-ttu-id="98758-129">Como ocultar uma variável com o mesmo nome que a variável</span><span class="sxs-lookup"><span data-stu-id="98758-129">How to: Hide a Variable with the Same Name as Your Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [<span data-ttu-id="98758-130">Como acessar uma variável oculta por uma classe derivada</span><span class="sxs-lookup"><span data-stu-id="98758-130">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [<span data-ttu-id="98758-131">Substituições</span><span class="sxs-lookup"><span data-stu-id="98758-131">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="98758-132">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="98758-132">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="98758-133">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="98758-133">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
