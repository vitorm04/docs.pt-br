---
title: Criando e implementando Interfaces (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: af9305deb60637b642d091501e743f2c7a57ccad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653605"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a><span data-ttu-id="40ed1-102">Instruções passo a passo: criando e implementando interfaces (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40ed1-102">Walkthrough: Creating and Implementing Interfaces (Visual Basic)</span></span>

<span data-ttu-id="40ed1-103">Interfaces descrevem as características de propriedades, métodos e eventos, mas deixam os detalhes de implementação até classes ou estruturas.</span><span class="sxs-lookup"><span data-stu-id="40ed1-103">Interfaces describe the characteristics of properties, methods, and events, but leave the implementation details up to structures or classes.</span></span>  
  
 <span data-ttu-id="40ed1-104">Este passo a passo demonstra como declarar e implementar uma interface.</span><span class="sxs-lookup"><span data-stu-id="40ed1-104">This walkthrough demonstrates how to declare and implement an interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40ed1-105">Este passo a passo não fornece informações sobre como criar uma interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="40ed1-105">This walkthrough doesn't provide information about how to create a user interface.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a><span data-ttu-id="40ed1-106">Para definir uma interface</span><span class="sxs-lookup"><span data-stu-id="40ed1-106">To define an interface</span></span>
  
1.  <span data-ttu-id="40ed1-107">Abra um novo projeto de aplicativo do Windows Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="40ed1-107">Open a new Visual Basic Windows Application project.</span></span>  
  
2.  <span data-ttu-id="40ed1-108">Adicionar um novo módulo ao projeto clicando **Adicionar módulo** no **projeto** menu.</span><span class="sxs-lookup"><span data-stu-id="40ed1-108">Add a new module to the project by clicking **Add Module** on the **Project** menu.</span></span>  
  
3.  <span data-ttu-id="40ed1-109">Nomeie o novo módulo `Module1.vb` e clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="40ed1-109">Name the new module `Module1.vb` and click **Add**.</span></span> <span data-ttu-id="40ed1-110">O código para o novo módulo é exibido.</span><span class="sxs-lookup"><span data-stu-id="40ed1-110">The code for the new module is displayed.</span></span>  
  
4.  <span data-ttu-id="40ed1-111">Definir uma interface denominada `TestInterface` em `Module1` digitando `Interface TestInterface` entre o `Module` e `End Module` instruções e, em seguida, pressionando ENTER.</span><span class="sxs-lookup"><span data-stu-id="40ed1-111">Define an interface named `TestInterface` within `Module1` by typing `Interface TestInterface` between the `Module` and `End Module` statements, and then pressing ENTER.</span></span> <span data-ttu-id="40ed1-112">O **Editor de códigos** recuos o `Interface` palavra-chave e adiciona um `End Interface` instrução para formar um bloco de código.</span><span class="sxs-lookup"><span data-stu-id="40ed1-112">The **Code Editor** indents the `Interface` keyword and adds an `End Interface` statement to form a code block.</span></span>  
  
5.  <span data-ttu-id="40ed1-113">Definir uma propriedade, método e evento para a interface, colocando o código a seguir entre a `Interface` e `End Interface` instruções:</span><span class="sxs-lookup"><span data-stu-id="40ed1-113">Define a property, method, and event for the interface by placing the following code between the `Interface` and `End Interface` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a><span data-ttu-id="40ed1-114">Implementação</span><span class="sxs-lookup"><span data-stu-id="40ed1-114">Implementation</span></span>

 <span data-ttu-id="40ed1-115">Você pode perceber que a sintaxe usada para declarar membros de interface é diferente da sintaxe usada para declarar membros de classe.</span><span class="sxs-lookup"><span data-stu-id="40ed1-115">You may notice that the syntax used to declare interface members is different from the syntax used to declare class members.</span></span> <span data-ttu-id="40ed1-116">Essa diferença reflete o fato de que interfaces não podem conter código de implementação.</span><span class="sxs-lookup"><span data-stu-id="40ed1-116">This difference reflects the fact that interfaces cannot contain implementation code.</span></span>  
  
### <a name="to-implement-the-interface"></a><span data-ttu-id="40ed1-117">Para implementar a interface</span><span class="sxs-lookup"><span data-stu-id="40ed1-117">To implement the interface</span></span>
  
1.  <span data-ttu-id="40ed1-118">Adicione uma classe denominada `ImplementationClass` adicionando a seguinte instrução para `Module1`, depois o `End Interface` instrução mas antes de `End Module` instrução e, em seguida, pressionando ENTER:</span><span class="sxs-lookup"><span data-stu-id="40ed1-118">Add a class named `ImplementationClass` by adding the following statement to `Module1`, after the `End Interface` statement but before the `End Module` statement, and then pressing ENTER:</span></span>  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     <span data-ttu-id="40ed1-119">Se você estiver trabalhando no ambiente de desenvolvimento integrado, a **Editor de códigos** fornece uma correspondência `End Class` instrução quando você pressiona ENTER.</span><span class="sxs-lookup"><span data-stu-id="40ed1-119">If you are working within the integrated development environment, the **Code Editor** supplies a matching `End Class` statement when you press ENTER.</span></span>  
  
2.  <span data-ttu-id="40ed1-120">Adicione o seguinte `Implements` instrução `ImplementationClass`, que chama a interface a classe implementa:</span><span class="sxs-lookup"><span data-stu-id="40ed1-120">Add the following `Implements` statement to `ImplementationClass`, which names the interface the class implements:</span></span>  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     <span data-ttu-id="40ed1-121">Quando listados separadamente de outros itens na parte superior de uma classe ou estrutura, o `Implements` instrução indica que a classe ou estrutura implementa uma interface.</span><span class="sxs-lookup"><span data-stu-id="40ed1-121">When listed separately from other items at the top of a class or structure, the `Implements` statement indicates that the class or structure implements an interface.</span></span>  
  
     <span data-ttu-id="40ed1-122">Se você estiver trabalhando no ambiente de desenvolvimento integrado, a **Editor de códigos** implementa os membros de classe exigidos pelo `TestInterface` quando você pressiona ENTER, e você pode ignorar a próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="40ed1-122">If you are working within the integrated development environment, the **Code Editor** implements the class members required by `TestInterface` when you press ENTER, and you can skip the next step.</span></span>  
  
3.  <span data-ttu-id="40ed1-123">Se você não estiver trabalhando no ambiente de desenvolvimento integrado, você deve implementar todos os membros da interface `MyInterface`.</span><span class="sxs-lookup"><span data-stu-id="40ed1-123">If you are not working within the integrated development environment, you must implement all the members of the interface `MyInterface`.</span></span> <span data-ttu-id="40ed1-124">Adicione o seguinte código para `ImplementationClass` implementar `Event1`, `Method1`, e `Prop1`:</span><span class="sxs-lookup"><span data-stu-id="40ed1-124">Add the following code to `ImplementationClass` to implement `Event1`, `Method1`, and `Prop1`:</span></span>  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     <span data-ttu-id="40ed1-125">O `Implements` instrução nomeia a interface e o membro de interface que está sendo implementada.</span><span class="sxs-lookup"><span data-stu-id="40ed1-125">The `Implements` statement names the interface and interface member being implemented.</span></span>  
  
4.  <span data-ttu-id="40ed1-126">Conclua a definição de `Prop1` adicionando um campo particular para a classe que o valor da propriedade de armazenados:</span><span class="sxs-lookup"><span data-stu-id="40ed1-126">Complete the definition of `Prop1` by adding a private field to the class that stored the property value:</span></span>  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     <span data-ttu-id="40ed1-127">O valor de retorno de `pval` da propriedade de acessador get.</span><span class="sxs-lookup"><span data-stu-id="40ed1-127">Return the value of the `pval` from the property get accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     <span data-ttu-id="40ed1-128">Defina o valor de `pval` na propriedade de acessador set.</span><span class="sxs-lookup"><span data-stu-id="40ed1-128">Set the value of `pval` in the property set accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5.  <span data-ttu-id="40ed1-129">Conclua a definição de `Method1` adicionando o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="40ed1-129">Complete the definition of `Method1` by adding the following code.</span></span>  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a><span data-ttu-id="40ed1-130">Para testar a implementação da interface</span><span class="sxs-lookup"><span data-stu-id="40ed1-130">To test the implementation of the interface</span></span>
  
1.  <span data-ttu-id="40ed1-131">Clique o formulário de inicialização para seu projeto no **Solution Explorer**e clique em **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="40ed1-131">Right-click the startup form for your project in the **Solution Explorer**, and click **View Code**.</span></span> <span data-ttu-id="40ed1-132">O editor exibe a classe para o formulário de inicialização.</span><span class="sxs-lookup"><span data-stu-id="40ed1-132">The editor displays the class for your startup form.</span></span> <span data-ttu-id="40ed1-133">Por padrão, o formulário de inicialização é chamado `Form1`.</span><span class="sxs-lookup"><span data-stu-id="40ed1-133">By default, the startup form is called `Form1`.</span></span>  
  
2.  <span data-ttu-id="40ed1-134">Adicione o seguinte `testInstance` campo para o `Form1` classe:</span><span class="sxs-lookup"><span data-stu-id="40ed1-134">Add the following `testInstance` field to the `Form1` class:</span></span>  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     <span data-ttu-id="40ed1-135">Declarando `testInstance` como `WithEvents`, o `Form1` classe pode manipular seus eventos.</span><span class="sxs-lookup"><span data-stu-id="40ed1-135">By declaring `testInstance` as `WithEvents`, the `Form1` class can handle its events.</span></span>  
  
3.  <span data-ttu-id="40ed1-136">Adicionar manipulador de eventos para o `Form1` classe para manipular eventos gerados por `testInstance`:</span><span class="sxs-lookup"><span data-stu-id="40ed1-136">Add the following event handler to the `Form1` class to handle events raised by `testInstance`:</span></span>  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4.  <span data-ttu-id="40ed1-137">Adicionar uma sub-rotina chamada `Test` para o `Form1` classe para testar a classe de implementação:</span><span class="sxs-lookup"><span data-stu-id="40ed1-137">Add a subroutine named `Test` to the `Form1` class to test the implementation class:</span></span>  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     <span data-ttu-id="40ed1-138">O `Test` procedimento cria uma instância da classe que implementa `MyInterface`, atribui essa instância para o `testInstance` define uma propriedade de campo e executa um método por meio da interface.</span><span class="sxs-lookup"><span data-stu-id="40ed1-138">The `Test` procedure creates an instance of the class that implements `MyInterface`, assigns that instance to the `testInstance` field, sets a property, and runs a method through the interface.</span></span>  
  
5.  <span data-ttu-id="40ed1-139">Adicione código para chamar o `Test` procedimento o `Form1 Load` procedimento do formulário de inicialização:</span><span class="sxs-lookup"><span data-stu-id="40ed1-139">Add code to call the `Test` procedure from the `Form1 Load` procedure of your startup form:</span></span>  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6.  <span data-ttu-id="40ed1-140">Execute o `Test` procedimento pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="40ed1-140">Run the `Test` procedure by pressing F5.</span></span> <span data-ttu-id="40ed1-141">A mensagem "Prop1 foi definido como 9" é exibida.</span><span class="sxs-lookup"><span data-stu-id="40ed1-141">The message "Prop1 was set to 9" is displayed.</span></span> <span data-ttu-id="40ed1-142">Depois que você clicar em Okey, a mensagem "o parâmetro X Method1 é 5" é exibida.</span><span class="sxs-lookup"><span data-stu-id="40ed1-142">After you click OK, the message "The X parameter for Method1 is 5" is displayed.</span></span> <span data-ttu-id="40ed1-143">Clique em Okey e a mensagem "o manipulador de eventos capturou o evento" é exibida.</span><span class="sxs-lookup"><span data-stu-id="40ed1-143">Click OK, and the message "The event handler caught the event" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40ed1-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40ed1-144">See also</span></span>

 [<span data-ttu-id="40ed1-145">Instrução Implements</span><span class="sxs-lookup"><span data-stu-id="40ed1-145">Implements Statement</span></span>](../../../../visual-basic/language-reference/statements/implements-statement.md)  
 [<span data-ttu-id="40ed1-146">Interfaces</span><span class="sxs-lookup"><span data-stu-id="40ed1-146">Interfaces</span></span>](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 [<span data-ttu-id="40ed1-147">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="40ed1-147">Interface Statement</span></span>](../../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="40ed1-148">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="40ed1-148">Event Statement</span></span>](../../../../visual-basic/language-reference/statements/event-statement.md)  