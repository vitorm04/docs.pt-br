---
title: Como agilizar o acesso a um objeto com um demarcador de qualificação longo (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: d52d13feb0f85065c0623b5937f558b841c036dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650193"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="077fa-102">Como agilizar o acesso a um objeto com um demarcador de qualificação longo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="077fa-102">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>
<span data-ttu-id="077fa-103">Se você acessar frequentemente um objeto que requer um caminho de qualificação de vários métodos e propriedades, você pode acelerar o seu código não repetindo o caminho de qualificação.</span><span class="sxs-lookup"><span data-stu-id="077fa-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>  
  
 <span data-ttu-id="077fa-104">Há duas maneiras de evitar repetir o caminho de qualificação.</span><span class="sxs-lookup"><span data-stu-id="077fa-104">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="077fa-105">Você pode atribuir o objeto a uma variável, ou você pode usá-lo em um `With`... `End With` bloco.</span><span class="sxs-lookup"><span data-stu-id="077fa-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="077fa-106">Para agilizar o acesso a um objeto intensamente qualificado atribuindo-a uma variável</span><span class="sxs-lookup"><span data-stu-id="077fa-106">To speed up access to a heavily qualified object by assigning it to a variable</span></span>  
  
1.  <span data-ttu-id="077fa-107">Declare uma variável do tipo de objeto que você está acessando com frequência.</span><span class="sxs-lookup"><span data-stu-id="077fa-107">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="077fa-108">Especifique o caminho de qualificação na parte da declaração de inicialização.</span><span class="sxs-lookup"><span data-stu-id="077fa-108">Specify the qualification path in the initialization part of the declaration.</span></span>  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2.  <span data-ttu-id="077fa-109">Use a variável para acessar os membros do objeto.</span><span class="sxs-lookup"><span data-stu-id="077fa-109">Use the variable to access the object's members.</span></span>  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="077fa-110">Para agilizar o acesso a um objeto intensamente qualificado usando um With... Bloco End With</span><span class="sxs-lookup"><span data-stu-id="077fa-110">To speed up access to a heavily qualified object by using a With...End With block</span></span>  
  
1.  <span data-ttu-id="077fa-111">Coloque o caminho de qualificação em um `With` instrução.</span><span class="sxs-lookup"><span data-stu-id="077fa-111">Put the qualification path in a `With` statement.</span></span>  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2.  <span data-ttu-id="077fa-112">Acesse membros do objeto dentro de `With` bloquear, antes de `End With` instrução.</span><span class="sxs-lookup"><span data-stu-id="077fa-112">Access the object's members inside the `With` block, before the `End With` statement.</span></span>  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="077fa-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="077fa-113">See Also</span></span>  
 [<span data-ttu-id="077fa-114">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="077fa-114">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="077fa-115">Instrução With ... End With</span><span class="sxs-lookup"><span data-stu-id="077fa-115">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
