---
title: "Como: ocultar uma variável herdada (Visual Basic) | Documentos do Microsoft"
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
- element names, qualification
- references, declared elements
- declaration statements, declared elements
- referencing declared elements
- declared elements, referencing
- declared elements, about declared elements
- variables [Visual Basic], hiding inherited
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
caps.latest.revision: 17
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
ms.openlocfilehash: 142ce593dab10a39ecd1c62cefa76ae261c4cb6f
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a><span data-ttu-id="00335-102">Como ocultar uma variável herdada (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00335-102">How to: Hide an Inherited Variable (Visual Basic)</span></span>
<span data-ttu-id="00335-103">Uma classe derivada herda todas as definições de sua classe base.</span><span class="sxs-lookup"><span data-stu-id="00335-103">A derived class inherits all the definitions of its base class.</span></span> <span data-ttu-id="00335-104">Se você quiser definir uma variável usando o mesmo nome como um elemento da classe base, você pode ocultar, ou *sombra*, esse elemento de classe base quando você define sua variável na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="00335-104">If you want to define a variable using the same name as an element of the base class, you can hide, or *shadow*, that base class element when you define your variable in the derived class.</span></span> <span data-ttu-id="00335-105">Se você fizer isso, o código na classe derivada acessa sua variável, a menos que explicitamente ignora o mecanismo de sombreamento.</span><span class="sxs-lookup"><span data-stu-id="00335-105">If you do this, code in the derived class accesses your variable unless it explicitly bypasses the shadowing mechanism.</span></span>  
  
 <span data-ttu-id="00335-106">Outro motivo, que talvez você queira ocultar uma variável herdada é proteger contra a revisão de classe base.</span><span class="sxs-lookup"><span data-stu-id="00335-106">Another reason you might want to hide an inherited variable is to protect against base class revision.</span></span> <span data-ttu-id="00335-107">A classe base pode passar por uma mudança que altere o elemento que você está herdando.</span><span class="sxs-lookup"><span data-stu-id="00335-107">The base class might undergo a change that alters the element you are inheriting.</span></span> <span data-ttu-id="00335-108">Se isso acontecer, o `Shadows` modificador obriga referências da classe derivada a ser resolvido para a variável, em vez de para o elemento de classe base.</span><span class="sxs-lookup"><span data-stu-id="00335-108">If this happens, the `Shadows` modifier forces references from the derived class to be resolved to your variable, instead of to the base class element.</span></span>  
  
### <a name="to-hide-an-inherited-variable"></a><span data-ttu-id="00335-109">Para ocultar uma variável herdada</span><span class="sxs-lookup"><span data-stu-id="00335-109">To hide an inherited variable</span></span>  
  
1.  <span data-ttu-id="00335-110">Certifique-se de que a variável que você deseja ocultar é declarada no nível de classe (fora de qualquer procedimento).</span><span class="sxs-lookup"><span data-stu-id="00335-110">Be sure the variable you want to hide is declared at class level (outside any procedure).</span></span> <span data-ttu-id="00335-111">Caso contrário, você não precisa ocultá-lo.</span><span class="sxs-lookup"><span data-stu-id="00335-111">Otherwise you do not need to hide it.</span></span>  
  
2.  <span data-ttu-id="00335-112">Dentro de sua classe derivada, escreva um [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) declarando sua variável.</span><span class="sxs-lookup"><span data-stu-id="00335-112">Inside your derived class, write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declaring your variable.</span></span> <span data-ttu-id="00335-113">Use o mesmo nome da variável herdada.</span><span class="sxs-lookup"><span data-stu-id="00335-113">Use the same name as that of the inherited variable.</span></span>  
  
3.  <span data-ttu-id="00335-114">Incluir o [sombras](../../../../visual-basic/language-reference/modifiers/shadows.md) palavra-chave na declaração.</span><span class="sxs-lookup"><span data-stu-id="00335-114">Include the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>  
  
     <span data-ttu-id="00335-115">Quando o código na classe derivada refere-se ao nome da variável, o compilador resolve a referência à variável.</span><span class="sxs-lookup"><span data-stu-id="00335-115">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>  
  
     <span data-ttu-id="00335-116">O exemplo a seguir ilustra sombreamento de uma variável herdada.</span><span class="sxs-lookup"><span data-stu-id="00335-116">The following example illustrates shadowing of an inherited variable.</span></span>  
  
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
  
     <span data-ttu-id="00335-117">O exemplo anterior declara a variável `shadowString` na classe base e a sombreia na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="00335-117">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="00335-118">O procedimento `showStrings` na classe derivada exibe a versão sombreada da cadeia de caracteres quando o nome `shadowString` não está qualificado.</span><span class="sxs-lookup"><span data-stu-id="00335-118">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="00335-119">Em seguida, exibe a versão sombreada quando `shadowString` qualificado com o `MyBase` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="00335-119">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="00335-120">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="00335-120">Robust Programming</span></span>  
 <span data-ttu-id="00335-121">Sombreamento introduz mais de uma versão de uma variável com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="00335-121">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="00335-122">Quando uma declaração de código refere-se ao nome da variável, a versão para que o compilador resolve a referência depende de fatores como o local da instrução do código e a presença de uma cadeia de caracteres de qualificação.</span><span class="sxs-lookup"><span data-stu-id="00335-122">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="00335-123">Isso pode aumentar o risco de se referir a uma versão não intencional de uma variável sombreada.</span><span class="sxs-lookup"><span data-stu-id="00335-123">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="00335-124">Você pode diminuir esse risco qualificar totalmente todas as referências a uma variável sombreada.</span><span class="sxs-lookup"><span data-stu-id="00335-124">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00335-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00335-125">See Also</span></span>  
 <span data-ttu-id="00335-126">[Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span><span class="sxs-lookup"><span data-stu-id="00335-126">[References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span></span>  
<span data-ttu-id="00335-127"> [Sombreamento no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md) </span><span class="sxs-lookup"><span data-stu-id="00335-127"> [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md) </span></span>  
<span data-ttu-id="00335-128"> [Diferenças entre sombreamento e sobreposição](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md) </span><span class="sxs-lookup"><span data-stu-id="00335-128"> [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md) </span></span>  
<span data-ttu-id="00335-129"> [Como: ocultar uma variável com o mesmo nome que sua variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) </span><span class="sxs-lookup"><span data-stu-id="00335-129"> [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) </span></span>  
<span data-ttu-id="00335-130"> [Como: acessar uma variável ocultada por uma classe derivada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md) </span><span class="sxs-lookup"><span data-stu-id="00335-130"> [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md) </span></span>  
<span data-ttu-id="00335-131"> [Substituições](../../../../visual-basic/language-reference/modifiers/overrides.md) </span><span class="sxs-lookup"><span data-stu-id="00335-131"> [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md) </span></span>  
<span data-ttu-id="00335-132"> [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md) </span><span class="sxs-lookup"><span data-stu-id="00335-132"> [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md) </span></span>  
<span data-ttu-id="00335-133"> [Noções Básicas de Herança](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)</span><span class="sxs-lookup"><span data-stu-id="00335-133"> [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)</span></span>
