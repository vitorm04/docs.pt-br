---
title: "Acesso de membro compartilhado através de uma instância; a expressão de qualificação não será avaliada | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42025
- BC42025
dev_langs:
- VB
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
caps.latest.revision: 23
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
ms.openlocfilehash: 49dc785131e257b19d0d1d57627ccb6cf8a3c63e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a><span data-ttu-id="bb8f4-102">Acesso de membro compartilhado por meio de uma instância; a expressão de qualificação não será avaliada</span><span class="sxs-lookup"><span data-stu-id="bb8f4-102">Access of shared member through an instance; qualifying expression will not be evaluated</span></span>
<span data-ttu-id="bb8f4-103">Uma variável de instância de uma classe ou estrutura é usada para acessar um `Shared` variável, propriedade, procedimento ou evento definido na classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="bb8f4-103">An instance variable of a class or structure is used to access a `Shared` variable, property, procedure, or event defined in that class or structure.</span></span> <span data-ttu-id="bb8f4-104">Esse aviso também pode ocorrer se uma variável de instância é usada para acessar um membro implicitamente compartilhado de uma classe ou estrutura, como uma constante de enumeração, ou uma classe aninhada ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="bb8f4-104">This warning can also occur if an instance variable is used to access an implicitly shared member of a class or structure, such as a constant or enumeration, or a nested class or structure.</span></span>  
  
 <span data-ttu-id="bb8f4-105">A finalidade de compartilhar um membro é criar uma única cópia do membro e disponibilizar essa cópia única para cada instância da classe ou estrutura na qual ela é declarada.</span><span class="sxs-lookup"><span data-stu-id="bb8f4-105">The purpose of sharing a member is to create only a single copy of that member and make that single copy available to every instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="bb8f4-106">É consistente com essa finalidade para acessar um `Shared` membro através do nome de sua classe ou estrutura, e não por meio de uma variável que contém uma instância individual da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="bb8f4-106">It is consistent with this purpose to access a `Shared` member through the name of its class or structure, rather than through a variable that holds an individual instance of that class or structure.</span></span>  
  
 <span data-ttu-id="bb8f4-107">Acessando um `Shared` membro por meio de uma variável de instância pode tornar seu código mais difícil de entender, ocultando o fato de que o membro é `Shared`.</span><span class="sxs-lookup"><span data-stu-id="bb8f4-107">Accessing a `Shared` member through an instance variable can make your code more difficult to understand by obscuring the fact that the member is `Shared`.</span></span> <span data-ttu-id="bb8f4-108">Além disso, se esse acesso é parte de uma expressão que executa outras ações, como um `Function` procedimento que retorna uma instância de membro compartilhado, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ignora a expressão e quaisquer outras ações executaria caso contrário.</span><span class="sxs-lookup"><span data-stu-id="bb8f4-108">Furthermore, if such access is part of an expression that performs other actions, such as a `Function` procedure that returns an instance of the shared member, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] bypasses the expression and any other actions it would otherwise perform.</span></span>  
  
 <span data-ttu-id="bb8f4-109">Para obter mais informações e um exemplo, consulte [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="bb8f4-109">For more information and an example, see [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
 <span data-ttu-id="bb8f4-110">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="bb8f4-110">By default, this message is a warning.</span></span> <span data-ttu-id="bb8f4-111">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="bb8f4-111">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="bb8f4-112">**ID do erro:** BC42025</span><span class="sxs-lookup"><span data-stu-id="bb8f4-112">**Error ID:** BC42025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bb8f4-113">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="bb8f4-113">To correct this error</span></span>  
  
-   <span data-ttu-id="bb8f4-114">Use o nome da classe ou estrutura que define o `Shared` membro para acessá-lo, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="bb8f4-114">Use the name of the class or structure that defines the `Shared` member to access it, as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="bb8f4-115">Esteja alerta os efeitos do escopo quando dois elementos de programação com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="bb8f4-115">Be alert for the effects of scope when two programming elements have the same name.</span></span> <span data-ttu-id="bb8f4-116">No exemplo anterior, se você declarar uma instância usando `Dim testClass as testClass = Nothing`, o compilador trata uma chamada para `testClass.sayHello()` quando ocorre um acesso do método com o nome da classe e nenhum aviso.</span><span class="sxs-lookup"><span data-stu-id="bb8f4-116">In the previous example, if you declare an instance by using `Dim testClass as testClass = Nothing`, the compiler treats a call to `testClass.sayHello()` as an access of the method through the class name, and no warning occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb8f4-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb8f4-117">See Also</span></span>  
 <span data-ttu-id="bb8f4-118">[Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md) </span><span class="sxs-lookup"><span data-stu-id="bb8f4-118">[Shared](../../../visual-basic/language-reference/modifiers/shared.md) </span></span>  
<span data-ttu-id="bb8f4-119"> [Escopo no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)</span><span class="sxs-lookup"><span data-stu-id="bb8f4-119"> [Scope in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)</span></span>
