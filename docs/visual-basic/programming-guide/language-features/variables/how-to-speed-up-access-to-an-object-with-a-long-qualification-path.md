---
title: Como agilizar o acesso a um objeto com um demarcador de qualificação longo
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: 83670ae6af0904156b08398024658cf504b7663f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346824"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="873b5-102">Como agilizar o acesso a um objeto com um demarcador de qualificação longo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="873b5-102">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>

<span data-ttu-id="873b5-103">Se você acessar com frequência um objeto que requer um caminho de qualificação de vários métodos e propriedades, você pode acelerar seu código não repetindo o caminho de qualificação.</span><span class="sxs-lookup"><span data-stu-id="873b5-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>

<span data-ttu-id="873b5-104">Há duas maneiras de evitar a repetição do caminho de qualificação.</span><span class="sxs-lookup"><span data-stu-id="873b5-104">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="873b5-105">Você pode atribuir o objeto a uma variável ou pode usá-lo em um bloco `With`...`End With`.</span><span class="sxs-lookup"><span data-stu-id="873b5-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="873b5-106">Para acelerar o acesso a um objeto muito qualificado atribuindo-o a uma variável</span><span class="sxs-lookup"><span data-stu-id="873b5-106">To speed up access to a heavily qualified object by assigning it to a variable</span></span>

1. <span data-ttu-id="873b5-107">Declare uma variável do tipo do objeto que você está acessando com frequência.</span><span class="sxs-lookup"><span data-stu-id="873b5-107">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="873b5-108">Especifique o caminho de qualificação na parte de inicialização da declaração.</span><span class="sxs-lookup"><span data-stu-id="873b5-108">Specify the qualification path in the initialization part of the declaration.</span></span>

    ```vb
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="873b5-109">Use a variável para acessar os membros do objeto.</span><span class="sxs-lookup"><span data-stu-id="873b5-109">Use the variable to access the object's members.</span></span>

    ```vb
    ctrlActv.Text = "Test"
    ctrlActv.Location = New Point(100, 100)
    ctrlActv.Show()
    ```

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="873b5-110">Para acelerar o acesso a um objeto muito qualificado usando um com... Terminar com bloco</span><span class="sxs-lookup"><span data-stu-id="873b5-110">To speed up access to a heavily qualified object by using a With...End With block</span></span>

1. <span data-ttu-id="873b5-111">Coloque o caminho de qualificação em uma instrução `With`.</span><span class="sxs-lookup"><span data-stu-id="873b5-111">Put the qualification path in a `With` statement.</span></span>

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="873b5-112">Acesse os membros do objeto dentro do bloco de `With`, antes da instrução `End With`.</span><span class="sxs-lookup"><span data-stu-id="873b5-112">Access the object's members inside the `With` block, before the `End With` statement.</span></span>

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a><span data-ttu-id="873b5-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="873b5-113">See also</span></span>

- [<span data-ttu-id="873b5-114">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="873b5-114">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="873b5-115">Instrução With ... End With</span><span class="sxs-lookup"><span data-stu-id="873b5-115">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
