---
title: Acesso de membro compartilhado por meio de uma instância; a expressão de qualificação não será avaliada
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 311f4c025072162e0cfb6b87587f8602d33fcd19
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64646875"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a><span data-ttu-id="53bf8-102">Acesso de membro compartilhado por meio de uma instância; a expressão de qualificação não será avaliada</span><span class="sxs-lookup"><span data-stu-id="53bf8-102">Access of shared member through an instance; qualifying expression will not be evaluated</span></span>
<span data-ttu-id="53bf8-103">Uma variável de instância de uma classe ou estrutura é usada para acessar um `Shared` variável, propriedade, procedimento ou evento definido na classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="53bf8-103">An instance variable of a class or structure is used to access a `Shared` variable, property, procedure, or event defined in that class or structure.</span></span> <span data-ttu-id="53bf8-104">Esse aviso também pode ocorrer se uma variável de instância é usada para acessar um membro implicitamente compartilhado de uma classe ou estrutura, como uma constante ou enumeração, ou uma classe aninhada ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="53bf8-104">This warning can also occur if an instance variable is used to access an implicitly shared member of a class or structure, such as a constant or enumeration, or a nested class or structure.</span></span>  
  
 <span data-ttu-id="53bf8-105">A finalidade de compartilhar um membro é apenas uma única cópia desse membro de criar e disponibilizar essa cópia única para todas as instâncias da classe ou estrutura na qual ela é declarada.</span><span class="sxs-lookup"><span data-stu-id="53bf8-105">The purpose of sharing a member is to create only a single copy of that member and make that single copy available to every instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="53bf8-106">Ele fiquem consistentes com essa finalidade para acessar um `Shared` membro por meio do nome de sua classe ou estrutura, em vez de por meio de uma variável que contém uma instância individual da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="53bf8-106">It is consistent with this purpose to access a `Shared` member through the name of its class or structure, rather than through a variable that holds an individual instance of that class or structure.</span></span>  
  
 <span data-ttu-id="53bf8-107">Acessando uma `Shared` membro por meio de uma variável de instância pode tornar seu código mais difícil de entender, ocultando o fato de que o membro é `Shared`.</span><span class="sxs-lookup"><span data-stu-id="53bf8-107">Accessing a `Shared` member through an instance variable can make your code more difficult to understand by obscuring the fact that the member is `Shared`.</span></span> <span data-ttu-id="53bf8-108">Além disso, se tal acesso for parte de uma expressão que executa outras ações, como um `Function` procedimento que retorna uma instância de membro compartilhado, o Visual Basic ignora a expressão e quaisquer outras ações que ele executaria.</span><span class="sxs-lookup"><span data-stu-id="53bf8-108">Furthermore, if such access is part of an expression that performs other actions, such as a `Function` procedure that returns an instance of the shared member, Visual Basic bypasses the expression and any other actions it would otherwise perform.</span></span>  
  
 <span data-ttu-id="53bf8-109">Para obter mais informações e um exemplo, consulte [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="53bf8-109">For more information and an example, see [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
 <span data-ttu-id="53bf8-110">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="53bf8-110">By default, this message is a warning.</span></span> <span data-ttu-id="53bf8-111">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="53bf8-111">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="53bf8-112">**ID do erro:** BC42025</span><span class="sxs-lookup"><span data-stu-id="53bf8-112">**Error ID:** BC42025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="53bf8-113">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="53bf8-113">To correct this error</span></span>  
  
- <span data-ttu-id="53bf8-114">Use o nome da classe ou estrutura que define o `Shared` membro para acessá-lo, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="53bf8-114">Use the name of the class or structure that defines the `Shared` member to access it, as shown in the following example.</span></span>  
  
```vb  
Public Class testClass  
    Public Shared Sub sayHello()  
        MsgBox("Hello")  
    End Sub  
End Class  
  
Module testModule  
    Public Sub Main()  
        ' Access a shared method through an instance variable.  
        ' This generates a warning.  
        Dim tc As New testClass  
        tc.sayHello()  
  
        ' Access a shared method by using the class name.  
        ' This does not generate a warning.  
        testClass.sayHello()  
    End Sub  
End Module  
```  
  
> [!NOTE]
>  <span data-ttu-id="53bf8-115">Ser alerta para os efeitos de escopo quando dois elementos de programação têm o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="53bf8-115">Be alert for the effects of scope when two programming elements have the same name.</span></span> <span data-ttu-id="53bf8-116">No exemplo anterior, se você declarar uma instância por meio `Dim testClass as testClass = Nothing`, o compilador trata uma chamada para `testClass.sayHello()` como um acesso do método por meio do nome de classe e nenhum aviso ocorre.</span><span class="sxs-lookup"><span data-stu-id="53bf8-116">In the previous example, if you declare an instance by using `Dim testClass as testClass = Nothing`, the compiler treats a call to `testClass.sayHello()` as an access of the method through the class name, and no warning occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53bf8-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53bf8-117">See also</span></span>

- [<span data-ttu-id="53bf8-118">Compartilhado</span><span class="sxs-lookup"><span data-stu-id="53bf8-118">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="53bf8-119">Escopo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="53bf8-119">Scope in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
