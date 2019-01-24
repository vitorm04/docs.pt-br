---
title: 'Como: Acelerar o acesso a um objeto com um demarcador de qualificação longo (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: 827d7d1574e85a30ec2724f7739f6c3a08dbd975
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519717"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="74fb9-102">Como: Acelerar o acesso a um objeto com um demarcador de qualificação longo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74fb9-102">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>
<span data-ttu-id="74fb9-103">Se você acessa com frequência um objeto que exija um demarcador de qualificação de vários métodos e propriedades, você pode acelerar o seu código não repetindo o demarcador de qualificação.</span><span class="sxs-lookup"><span data-stu-id="74fb9-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>  
  
 <span data-ttu-id="74fb9-104">Há duas maneiras de evitar repetir o demarcador de qualificação.</span><span class="sxs-lookup"><span data-stu-id="74fb9-104">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="74fb9-105">Você pode atribuir o objeto a uma variável, ou você pode usá-lo em um `With`... `End With` bloco.</span><span class="sxs-lookup"><span data-stu-id="74fb9-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="74fb9-106">Para acelerar o acesso a um objeto intensamente qualificado atribuindo-a uma variável</span><span class="sxs-lookup"><span data-stu-id="74fb9-106">To speed up access to a heavily qualified object by assigning it to a variable</span></span>  
  
1.  <span data-ttu-id="74fb9-107">Declare uma variável do tipo do objeto que você está acessando com frequência.</span><span class="sxs-lookup"><span data-stu-id="74fb9-107">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="74fb9-108">Especifique o caminho de qualificação na parte da declaração de inicialização.</span><span class="sxs-lookup"><span data-stu-id="74fb9-108">Specify the qualification path in the initialization part of the declaration.</span></span>  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2.  <span data-ttu-id="74fb9-109">Use a variável para acessar membros do objeto.</span><span class="sxs-lookup"><span data-stu-id="74fb9-109">Use the variable to access the object's members.</span></span>  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="74fb9-110">Para acelerar o acesso a um objeto intensamente qualificado usando um With... Bloco End With</span><span class="sxs-lookup"><span data-stu-id="74fb9-110">To speed up access to a heavily qualified object by using a With...End With block</span></span>  
  
1.  <span data-ttu-id="74fb9-111">Coloque o caminho de qualificação em um `With` instrução.</span><span class="sxs-lookup"><span data-stu-id="74fb9-111">Put the qualification path in a `With` statement.</span></span>  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2.  <span data-ttu-id="74fb9-112">Acessar membros do objeto dentro de `With` bloquear, antes de `End With` instrução.</span><span class="sxs-lookup"><span data-stu-id="74fb9-112">Access the object's members inside the `With` block, before the `End With` statement.</span></span>  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="74fb9-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74fb9-113">See also</span></span>
- [<span data-ttu-id="74fb9-114">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="74fb9-114">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="74fb9-115">Instrução With ... End With</span><span class="sxs-lookup"><span data-stu-id="74fb9-115">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
