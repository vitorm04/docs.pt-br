---
title: "Como: acelerar o acesso a um objeto com um caminho de qualificação longo (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement
- With block
- object variables, accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
caps.latest.revision: 13
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
ms.openlocfilehash: 954e549435d4981f914122be7e437d6f21ea4d83
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="b8f19-102">Como agilizar o acesso a um objeto com um demarcador de qualificação longo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8f19-102">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>
<span data-ttu-id="b8f19-103">Se acessar um objeto que requer um caminho de qualificação de vários métodos e propriedades com frequência, você pode acelerar o seu código não repetindo o caminho de qualificação.</span><span class="sxs-lookup"><span data-stu-id="b8f19-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>  
  
 <span data-ttu-id="b8f19-104">Há duas maneiras de evitar repetir o caminho de qualificação.</span><span class="sxs-lookup"><span data-stu-id="b8f19-104">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="b8f19-105">Você pode atribuir o objeto a uma variável, ou você pode usá-lo em um `With`... `End With` bloco.</span><span class="sxs-lookup"><span data-stu-id="b8f19-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="b8f19-106">Para acelerar o acesso a um objeto intensamente qualificado atribuindo-a uma variável</span><span class="sxs-lookup"><span data-stu-id="b8f19-106">To speed up access to a heavily qualified object by assigning it to a variable</span></span>  
  
1.  <span data-ttu-id="b8f19-107">Declare uma variável do tipo de objeto que você está acessando com frequência.</span><span class="sxs-lookup"><span data-stu-id="b8f19-107">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="b8f19-108">Especifique o caminho de qualificação na parte da declaração de inicialização.</span><span class="sxs-lookup"><span data-stu-id="b8f19-108">Specify the qualification path in the initialization part of the declaration.</span></span>  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2.  <span data-ttu-id="b8f19-109">Use a variável para acessar membros do objeto.</span><span class="sxs-lookup"><span data-stu-id="b8f19-109">Use the variable to access the object's members.</span></span>  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="b8f19-110">Para acelerar o acesso a um objeto intensamente qualificado usando um bloco With... Bloco End With</span><span class="sxs-lookup"><span data-stu-id="b8f19-110">To speed up access to a heavily qualified object by using a With...End With block</span></span>  
  
1.  <span data-ttu-id="b8f19-111">Coloque o caminho de qualificação em uma `With` instrução.</span><span class="sxs-lookup"><span data-stu-id="b8f19-111">Put the qualification path in a `With` statement.</span></span>  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2.  <span data-ttu-id="b8f19-112">Acesse membros do objeto dentro do `With` bloquear, antes de `End With` instrução.</span><span class="sxs-lookup"><span data-stu-id="b8f19-112">Access the object's members inside the `With` block, before the `End With` statement.</span></span>  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b8f19-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8f19-113">See Also</span></span>  
 <span data-ttu-id="b8f19-114">[Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span><span class="sxs-lookup"><span data-stu-id="b8f19-114">[Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span></span>  
<span data-ttu-id="b8f19-115"> [Instrução With ... End With](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)</span><span class="sxs-lookup"><span data-stu-id="b8f19-115"> [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)</span></span>
