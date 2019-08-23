---
title: Criando e implementando interfaces (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 62e301e9eb366d14b58088d3e2cda3b567d17f5b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923313"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a><span data-ttu-id="7807f-102">Passo a passo: Criando e implementando interfaces (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7807f-102">Walkthrough: Creating and Implementing Interfaces (Visual Basic)</span></span>

<span data-ttu-id="7807f-103">As interfaces descrevem as características das propriedades, métodos e eventos, mas deixam os detalhes de implementação até estruturas ou classes.</span><span class="sxs-lookup"><span data-stu-id="7807f-103">Interfaces describe the characteristics of properties, methods, and events, but leave the implementation details up to structures or classes.</span></span>  
  
 <span data-ttu-id="7807f-104">Este tutorial demonstra como declarar e implementar uma interface.</span><span class="sxs-lookup"><span data-stu-id="7807f-104">This walkthrough demonstrates how to declare and implement an interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7807f-105">Este tutorial não fornece informações sobre como criar uma interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="7807f-105">This walkthrough doesn't provide information about how to create a user interface.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a><span data-ttu-id="7807f-106">Para definir uma interface</span><span class="sxs-lookup"><span data-stu-id="7807f-106">To define an interface</span></span>
  
1. <span data-ttu-id="7807f-107">Abra um novo projeto de aplicativo do Windows Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7807f-107">Open a new Visual Basic Windows Application project.</span></span>  
  
2. <span data-ttu-id="7807f-108">Adicione um novo módulo ao projeto clicando em **Adicionar módulo** no menu **projeto** .</span><span class="sxs-lookup"><span data-stu-id="7807f-108">Add a new module to the project by clicking **Add Module** on the **Project** menu.</span></span>  
  
3. <span data-ttu-id="7807f-109">Nomeie o novo módulo `Module1.vb` e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="7807f-109">Name the new module `Module1.vb` and click **Add**.</span></span> <span data-ttu-id="7807f-110">O código para o novo módulo é exibido.</span><span class="sxs-lookup"><span data-stu-id="7807f-110">The code for the new module is displayed.</span></span>  
  
4. <span data-ttu-id="7807f-111">Defina uma interface chamada `TestInterface` no `Module1` digitando `Interface TestInterface` entre as `Module` instruções `End Module` e e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="7807f-111">Define an interface named `TestInterface` within `Module1` by typing `Interface TestInterface` between the `Module` and `End Module` statements, and then pressing ENTER.</span></span> <span data-ttu-id="7807f-112">O **Editor de código** recua a `Interface` palavra-chave e `End Interface` adiciona uma instrução para formar um bloco de código.</span><span class="sxs-lookup"><span data-stu-id="7807f-112">The **Code Editor** indents the `Interface` keyword and adds an `End Interface` statement to form a code block.</span></span>  
  
5. <span data-ttu-id="7807f-113">Defina uma propriedade, um método e um evento para a interface colocando o seguinte código entre as `Interface` instruções `End Interface` e:</span><span class="sxs-lookup"><span data-stu-id="7807f-113">Define a property, method, and event for the interface by placing the following code between the `Interface` and `End Interface` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a><span data-ttu-id="7807f-114">Implementação</span><span class="sxs-lookup"><span data-stu-id="7807f-114">Implementation</span></span>

 <span data-ttu-id="7807f-115">Você pode observar que a sintaxe usada para declarar membros de interface é diferente da sintaxe usada para declarar membros de classe.</span><span class="sxs-lookup"><span data-stu-id="7807f-115">You may notice that the syntax used to declare interface members is different from the syntax used to declare class members.</span></span> <span data-ttu-id="7807f-116">Essa diferença reflete o fato de que as interfaces não podem conter código de implementação.</span><span class="sxs-lookup"><span data-stu-id="7807f-116">This difference reflects the fact that interfaces cannot contain implementation code.</span></span>  
  
### <a name="to-implement-the-interface"></a><span data-ttu-id="7807f-117">Para implementar a interface</span><span class="sxs-lookup"><span data-stu-id="7807f-117">To implement the interface</span></span>
  
1. <span data-ttu-id="7807f-118">Adicione uma classe chamada `ImplementationClass` adicionando a seguinte instrução a `Module1`, após a `End Interface` instrução, mas antes da `End Module` instrução, e pressione ENTER:</span><span class="sxs-lookup"><span data-stu-id="7807f-118">Add a class named `ImplementationClass` by adding the following statement to `Module1`, after the `End Interface` statement but before the `End Module` statement, and then pressing ENTER:</span></span>  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     <span data-ttu-id="7807f-119">Se você estiver trabalhando dentro do ambiente de desenvolvimento integrado, o **Editor de código** fornecerá uma instrução correspondente `End Class` quando você pressionar Enter.</span><span class="sxs-lookup"><span data-stu-id="7807f-119">If you are working within the integrated development environment, the **Code Editor** supplies a matching `End Class` statement when you press ENTER.</span></span>  
  
2. <span data-ttu-id="7807f-120">Adicione a seguinte `Implements` instrução a `ImplementationClass`, que nomeia a interface que a classe implementa:</span><span class="sxs-lookup"><span data-stu-id="7807f-120">Add the following `Implements` statement to `ImplementationClass`, which names the interface the class implements:</span></span>  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     <span data-ttu-id="7807f-121">Quando listado separadamente de outros itens na parte superior de uma classe ou estrutura, a `Implements` instrução indica que a classe ou estrutura implementa uma interface.</span><span class="sxs-lookup"><span data-stu-id="7807f-121">When listed separately from other items at the top of a class or structure, the `Implements` statement indicates that the class or structure implements an interface.</span></span>  
  
     <span data-ttu-id="7807f-122">Se você estiver trabalhando no ambiente de desenvolvimento integrado, o **Editor de código** implementará os membros de `TestInterface` classe necessários ao pressionar Enter, e você poderá ignorar a próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="7807f-122">If you are working within the integrated development environment, the **Code Editor** implements the class members required by `TestInterface` when you press ENTER, and you can skip the next step.</span></span>  
  
3. <span data-ttu-id="7807f-123">Se você não estiver trabalhando no ambiente de desenvolvimento integrado, deverá implementar todos os membros da interface `MyInterface`.</span><span class="sxs-lookup"><span data-stu-id="7807f-123">If you are not working within the integrated development environment, you must implement all the members of the interface `MyInterface`.</span></span> <span data-ttu-id="7807f-124">Adicione o seguinte código ao `ImplementationClass` para implementar `Event1`, `Method1`e `Prop1`:</span><span class="sxs-lookup"><span data-stu-id="7807f-124">Add the following code to `ImplementationClass` to implement `Event1`, `Method1`, and `Prop1`:</span></span>  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     <span data-ttu-id="7807f-125">A `Implements` instrução nomeia a interface e o membro de interface que está sendo implementado.</span><span class="sxs-lookup"><span data-stu-id="7807f-125">The `Implements` statement names the interface and interface member being implemented.</span></span>  
  
4. <span data-ttu-id="7807f-126">Conclua a definição `Prop1` de adicionando um campo particular à classe que armazenou o valor da propriedade:</span><span class="sxs-lookup"><span data-stu-id="7807f-126">Complete the definition of `Prop1` by adding a private field to the class that stored the property value:</span></span>  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     <span data-ttu-id="7807f-127">Retornar o valor do `pval` do acessador get da propriedade.</span><span class="sxs-lookup"><span data-stu-id="7807f-127">Return the value of the `pval` from the property get accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     <span data-ttu-id="7807f-128">Defina o valor de `pval` no acessador do conjunto de propriedades.</span><span class="sxs-lookup"><span data-stu-id="7807f-128">Set the value of `pval` in the property set accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. <span data-ttu-id="7807f-129">Conclua a definição `Method1` de adicionando o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7807f-129">Complete the definition of `Method1` by adding the following code.</span></span>  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a><span data-ttu-id="7807f-130">Para testar a implementação da interface</span><span class="sxs-lookup"><span data-stu-id="7807f-130">To test the implementation of the interface</span></span>
  
1. <span data-ttu-id="7807f-131">Clique com o botão direito do mouse no formulário de inicialização do seu projeto no **Gerenciador de soluções**e clique em **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="7807f-131">Right-click the startup form for your project in the **Solution Explorer**, and click **View Code**.</span></span> <span data-ttu-id="7807f-132">O editor exibe a classe para o formulário de inicialização.</span><span class="sxs-lookup"><span data-stu-id="7807f-132">The editor displays the class for your startup form.</span></span> <span data-ttu-id="7807f-133">Por padrão, o formulário de inicialização é `Form1`chamado.</span><span class="sxs-lookup"><span data-stu-id="7807f-133">By default, the startup form is called `Form1`.</span></span>  
  
2. <span data-ttu-id="7807f-134">Adicione o seguinte `testInstance` campo `Form1` à classe:</span><span class="sxs-lookup"><span data-stu-id="7807f-134">Add the following `testInstance` field to the `Form1` class:</span></span>  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     <span data-ttu-id="7807f-135">Ao declarar `testInstance` como `WithEvents`, a `Form1` classe pode manipular seus eventos.</span><span class="sxs-lookup"><span data-stu-id="7807f-135">By declaring `testInstance` as `WithEvents`, the `Form1` class can handle its events.</span></span>  
  
3. <span data-ttu-id="7807f-136">Adicione o seguinte manipulador de eventos à `Form1` classe para manipular eventos gerados por `testInstance`:</span><span class="sxs-lookup"><span data-stu-id="7807f-136">Add the following event handler to the `Form1` class to handle events raised by `testInstance`:</span></span>  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. <span data-ttu-id="7807f-137">Adicione uma sub-rotina nomeada `Test` `Form1` à classe para testar a classe de implementação:</span><span class="sxs-lookup"><span data-stu-id="7807f-137">Add a subroutine named `Test` to the `Form1` class to test the implementation class:</span></span>  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     <span data-ttu-id="7807f-138">O `Test` procedimento cria uma instância da classe que implementa `MyInterface`, atribui essa instância ao `testInstance` campo, define uma propriedade e executa um método por meio da interface.</span><span class="sxs-lookup"><span data-stu-id="7807f-138">The `Test` procedure creates an instance of the class that implements `MyInterface`, assigns that instance to the `testInstance` field, sets a property, and runs a method through the interface.</span></span>  
  
5. <span data-ttu-id="7807f-139">Adicione o código para chamar `Test` o procedimento a `Form1 Load` partir do procedimento de seu formulário de inicialização:</span><span class="sxs-lookup"><span data-stu-id="7807f-139">Add code to call the `Test` procedure from the `Form1 Load` procedure of your startup form:</span></span>  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. <span data-ttu-id="7807f-140">Execute o `Test` procedimento pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="7807f-140">Run the `Test` procedure by pressing F5.</span></span> <span data-ttu-id="7807f-141">A mensagem "Prop1 foi definido como 9" é exibida.</span><span class="sxs-lookup"><span data-stu-id="7807f-141">The message "Prop1 was set to 9" is displayed.</span></span> <span data-ttu-id="7807f-142">Depois de clicar em OK, a mensagem "o parâmetro X para Method1 é 5" é exibido.</span><span class="sxs-lookup"><span data-stu-id="7807f-142">After you click OK, the message "The X parameter for Method1 is 5" is displayed.</span></span> <span data-ttu-id="7807f-143">Clique em OK e a mensagem "o manipulador de eventos capturou o evento" é exibida.</span><span class="sxs-lookup"><span data-stu-id="7807f-143">Click OK, and the message "The event handler caught the event" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7807f-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7807f-144">See also</span></span>

- [<span data-ttu-id="7807f-145">Instrução Implements</span><span class="sxs-lookup"><span data-stu-id="7807f-145">Implements Statement</span></span>](../../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="7807f-146">Interfaces</span><span class="sxs-lookup"><span data-stu-id="7807f-146">Interfaces</span></span>](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [<span data-ttu-id="7807f-147">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="7807f-147">Interface Statement</span></span>](../../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="7807f-148">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="7807f-148">Event Statement</span></span>](../../../../visual-basic/language-reference/statements/event-statement.md)
