---
title: Criando e implementando Interfaces (Visual Basic) | Documentos do Microsoft
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
- interfaces, walkthroughs
- interfaces, testing
- interface implementation, walkthrough
- interfaces, creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
caps.latest.revision: 22
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
ms.openlocfilehash: ef1ec16005bf0a7967d396054ae23c1023143c2a
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a><span data-ttu-id="19817-102">Instruções passo a passo: criando e implementando interfaces (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19817-102">Walkthrough: Creating and Implementing Interfaces (Visual Basic)</span></span>
<span data-ttu-id="19817-103">Interfaces descrevem as características de propriedades, métodos e eventos, mas deixe os detalhes de implementação para classes ou estruturas.</span><span class="sxs-lookup"><span data-stu-id="19817-103">Interfaces describe the characteristics of properties, methods, and events, but leave the implementation details up to structures or classes.</span></span>  
  
 <span data-ttu-id="19817-104">Este passo a passo demonstra como declarar e implementar uma interface.</span><span class="sxs-lookup"><span data-stu-id="19817-104">This walkthrough demonstrates how to declare and implement an interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19817-105">Este passo a passo não fornece informações sobre como criar uma interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="19817-105">This walkthrough doesn't provide information about how to create a user interface.</span></span>  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-define-an-interface"></a><span data-ttu-id="19817-106">Para definir uma interface</span><span class="sxs-lookup"><span data-stu-id="19817-106">To define an interface</span></span>  
  
1.  <span data-ttu-id="19817-107">Abra um novo [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projeto aplicativo do Windows.</span><span class="sxs-lookup"><span data-stu-id="19817-107">Open a new [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] Windows Application project.</span></span>  
  
2.  <span data-ttu-id="19817-108">Adicionar um novo módulo para o projeto clicando em **Adicionar módulo** sobre o **projeto** menu.</span><span class="sxs-lookup"><span data-stu-id="19817-108">Add a new module to the project by clicking **Add Module** on the **Project** menu.</span></span>  
  
3.  <span data-ttu-id="19817-109">Nomeie o novo módulo `Module1.vb` e clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="19817-109">Name the new module `Module1.vb` and click **Add**.</span></span> <span data-ttu-id="19817-110">O código para o novo módulo é exibido.</span><span class="sxs-lookup"><span data-stu-id="19817-110">The code for the new module is displayed.</span></span>  
  
4.  <span data-ttu-id="19817-111">Definir uma interface denominada `TestInterface` na `Module1` digitando `Interface TestInterface` entre o `Module` e `End Module` instruções e pressionando ENTER.</span><span class="sxs-lookup"><span data-stu-id="19817-111">Define an interface named `TestInterface` within `Module1` by typing `Interface TestInterface` between the `Module` and `End Module` statements, and then pressing ENTER.</span></span> <span data-ttu-id="19817-112">O **Editor de códigos** recua o `Interface` palavra-chave e adiciona um `End Interface` instrução para formar um bloco de código.</span><span class="sxs-lookup"><span data-stu-id="19817-112">The **Code Editor** indents the `Interface` keyword and adds an `End Interface` statement to form a code block.</span></span>  
  
5.  <span data-ttu-id="19817-113">Definir uma propriedade, método e evento para a interface, colocando o código a seguir entre o `Interface` e `End Interface` instruções:</span><span class="sxs-lookup"><span data-stu-id="19817-113">Define a property, method, and event for the interface by placing the following code between the `Interface` and `End Interface` statements:</span></span>  
  
     <span data-ttu-id="19817-114">[!code-vb[VbVbalrOOP&#98;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="19817-114">[!code-vb[VbVbalrOOP#98](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_1.vb)]</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="19817-115">Implementação</span><span class="sxs-lookup"><span data-stu-id="19817-115">Implementation</span></span>  
 <span data-ttu-id="19817-116">Você notará que a sintaxe usada para declarar membros de interface é diferente da sintaxe usada para declarar membros de classe.</span><span class="sxs-lookup"><span data-stu-id="19817-116">You may notice that the syntax used to declare interface members is different from the syntax used to declare class members.</span></span> <span data-ttu-id="19817-117">Essa diferença reflete o fato de que interfaces não podem conter código de implementação.</span><span class="sxs-lookup"><span data-stu-id="19817-117">This difference reflects the fact that interfaces cannot contain implementation code.</span></span>  
  
#### <a name="to-implement-the-interface"></a><span data-ttu-id="19817-118">Para implementar a interface</span><span class="sxs-lookup"><span data-stu-id="19817-118">To implement the interface</span></span>  
  
1.  <span data-ttu-id="19817-119">Adicione uma classe chamada `ImplementationClass` adicionando a seguinte instrução para `Module1`, após o `End Interface` instrução mas antes de `End Module` instrução e pressione ENTER:</span><span class="sxs-lookup"><span data-stu-id="19817-119">Add a class named `ImplementationClass` by adding the following statement to `Module1`, after the `End Interface` statement but before the `End Module` statement, and then pressing ENTER:</span></span>  
  
     <span data-ttu-id="19817-120">[!code-vb[VbVbalrOOP&#99;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="19817-120">[!code-vb[VbVbalrOOP#99](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_2.vb)]</span></span>  
  
     <span data-ttu-id="19817-121">Se você estiver trabalhando no ambiente de desenvolvimento integrado, o **Editor de códigos** fornece uma correspondência `End Class` instrução quando você pressiona ENTER.</span><span class="sxs-lookup"><span data-stu-id="19817-121">If you are working within the integrated development environment, the **Code Editor** supplies a matching `End Class` statement when you press ENTER.</span></span>  
  
2.  <span data-ttu-id="19817-122">Adicione o seguinte `Implements` instrução `ImplementationClass`, que chama a interface a classe implementa:</span><span class="sxs-lookup"><span data-stu-id="19817-122">Add the following `Implements` statement to `ImplementationClass`, which names the interface the class implements:</span></span>  
  
     <span data-ttu-id="19817-123">[!code-vb[VbVbalrOOP&#100;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="19817-123">[!code-vb[VbVbalrOOP#100](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_3.vb)]</span></span>  
  
     <span data-ttu-id="19817-124">Quando listados separadamente de outros itens na parte superior de uma classe ou estrutura, o `Implements` instrução indica que a classe ou estrutura implementa uma interface.</span><span class="sxs-lookup"><span data-stu-id="19817-124">When listed separately from other items at the top of a class or structure, the `Implements` statement indicates that the class or structure implements an interface.</span></span>  
  
     <span data-ttu-id="19817-125">Se você estiver trabalhando no ambiente de desenvolvimento integrado, o **Editor de códigos** implementa os membros de classe exigidos pelo `TestInterface` quando você pressiona ENTER, e você pode ignorar a próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="19817-125">If you are working within the integrated development environment, the **Code Editor** implements the class members required by `TestInterface` when you press ENTER, and you can skip the next step.</span></span>  
  
3.  <span data-ttu-id="19817-126">Se você não estiver trabalhando no ambiente de desenvolvimento integrado, você deve implementar todos os membros da interface `MyInterface`.</span><span class="sxs-lookup"><span data-stu-id="19817-126">If you are not working within the integrated development environment, you must implement all the members of the interface `MyInterface`.</span></span> <span data-ttu-id="19817-127">Adicione o seguinte código para `ImplementationClass` implementar `Event1`, `Method1`, e `Prop1`:</span><span class="sxs-lookup"><span data-stu-id="19817-127">Add the following code to `ImplementationClass` to implement `Event1`, `Method1`, and `Prop1`:</span></span>  
  
     <span data-ttu-id="19817-128">[!code-vb[VbVbalrOOP&#101;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="19817-128">[!code-vb[VbVbalrOOP#101](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_4.vb)]</span></span>  
  
     <span data-ttu-id="19817-129">O `Implements` instrução nomeia a interface e o membro de interface que está sendo implementado.</span><span class="sxs-lookup"><span data-stu-id="19817-129">The `Implements` statement names the interface and interface member being implemented.</span></span>  
  
4.  <span data-ttu-id="19817-130">Concluir a definição de `Prop1` adicionando um campo particular para a classe que armazenado o valor da propriedade:</span><span class="sxs-lookup"><span data-stu-id="19817-130">Complete the definition of `Prop1` by adding a private field to the class that stored the property value:</span></span>  
  
     <span data-ttu-id="19817-131">[!code-vb[VbVbalrOOP&#102;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="19817-131">[!code-vb[VbVbalrOOP#102](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_5.vb)]</span></span>  
  
     <span data-ttu-id="19817-132">Retornar o valor de `pval` da propriedade de acessador get.</span><span class="sxs-lookup"><span data-stu-id="19817-132">Return the value of the `pval` from the property get accessor.</span></span>  
  
     <span data-ttu-id="19817-133">[!code-vb[VbVbalrOOP&#103;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="19817-133">[!code-vb[VbVbalrOOP#103](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_6.vb)]</span></span>  
  
     <span data-ttu-id="19817-134">Defina o valor de `pval` na propriedade de acessador set.</span><span class="sxs-lookup"><span data-stu-id="19817-134">Set the value of `pval` in the property set accessor.</span></span>  
  
     <span data-ttu-id="19817-135">[!code-vb[VbVbalrOOP&#104;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="19817-135">[!code-vb[VbVbalrOOP#104](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_7.vb)]</span></span>  
  
5.  <span data-ttu-id="19817-136">Concluir a definição de `Method1` adicionando o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="19817-136">Complete the definition of `Method1` by adding the following code.</span></span>  
  
     <span data-ttu-id="19817-137">[!code-vb[VbVbalrOOP&#105;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="19817-137">[!code-vb[VbVbalrOOP#105](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_8.vb)]</span></span>  
  
#### <a name="to-test-the-implementation-of-the-interface"></a><span data-ttu-id="19817-138">Para testar a implementação da interface</span><span class="sxs-lookup"><span data-stu-id="19817-138">To test the implementation of the interface</span></span>  
  
1.  <span data-ttu-id="19817-139">Clique com botão direito do formulário de inicialização para seu projeto no **Solution Explorer**e clique em **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="19817-139">Right-click the startup form for your project in the **Solution Explorer**, and click **View Code**.</span></span> <span data-ttu-id="19817-140">O editor exibe a classe para o formulário de inicialização.</span><span class="sxs-lookup"><span data-stu-id="19817-140">The editor displays the class for your startup form.</span></span> <span data-ttu-id="19817-141">Por padrão, o formulário de inicialização é chamado `Form1`.</span><span class="sxs-lookup"><span data-stu-id="19817-141">By default, the startup form is called `Form1`.</span></span>  
  
2.  <span data-ttu-id="19817-142">Adicione o seguinte `testInstance` campo para o `Form1` classe:</span><span class="sxs-lookup"><span data-stu-id="19817-142">Add the following `testInstance` field to the `Form1` class:</span></span>  
  
     <span data-ttu-id="19817-143">[!code-vb[VbVbalrOOP&#120;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="19817-143">[!code-vb[VbVbalrOOP#120](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_9.vb)]</span></span>  
  
     <span data-ttu-id="19817-144">Declarando `testInstance` como `WithEvents`, a `Form1` classe pode manipular seus eventos.</span><span class="sxs-lookup"><span data-stu-id="19817-144">By declaring `testInstance` as `WithEvents`, the `Form1` class can handle its events.</span></span>  
  
3.  <span data-ttu-id="19817-145">Adicione o seguinte manipulador de eventos para o `Form1` classe para manipular eventos acionados por `testInstance`:</span><span class="sxs-lookup"><span data-stu-id="19817-145">Add the following event handler to the `Form1` class to handle events raised by `testInstance`:</span></span>  
  
     <span data-ttu-id="19817-146">[!code-vb[VbVbalrOOP&#106;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="19817-146">[!code-vb[VbVbalrOOP#106](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_10.vb)]</span></span>  
  
4.  <span data-ttu-id="19817-147">Adicionar uma sub-rotina chamada `Test` para o `Form1` classe para testar a classe de implementação:</span><span class="sxs-lookup"><span data-stu-id="19817-147">Add a subroutine named `Test` to the `Form1` class to test the implementation class:</span></span>  
  
     <span data-ttu-id="19817-148">[!code-vb[VbVbalrOOP&#107;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="19817-148">[!code-vb[VbVbalrOOP#107](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_11.vb)]</span></span>  
  
     <span data-ttu-id="19817-149">O `Test` procedimento cria uma instância da classe que implementa `MyInterface`, atribui essa instância para o `testInstance` define uma propriedade de campo e executa um método por meio da interface.</span><span class="sxs-lookup"><span data-stu-id="19817-149">The `Test` procedure creates an instance of the class that implements `MyInterface`, assigns that instance to the `testInstance` field, sets a property, and runs a method through the interface.</span></span>  
  
5.  <span data-ttu-id="19817-150">Adicionar código para chamar o `Test` procedimento o `Form1 Load` procedimento de seu formulário de inicialização:</span><span class="sxs-lookup"><span data-stu-id="19817-150">Add code to call the `Test` procedure from the `Form1 Load` procedure of your startup form:</span></span>  
  
     <span data-ttu-id="19817-151">[!code-vb[VbVbalrOOP&#108;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_12.vb)]</span><span class="sxs-lookup"><span data-stu-id="19817-151">[!code-vb[VbVbalrOOP#108](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_12.vb)]</span></span>  
  
6.  <span data-ttu-id="19817-152">Execute o `Test` procedimento pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="19817-152">Run the `Test` procedure by pressing F5.</span></span> <span data-ttu-id="19817-153">A mensagem "Prop1 foi definido como 9" é exibida.</span><span class="sxs-lookup"><span data-stu-id="19817-153">The message "Prop1 was set to 9" is displayed.</span></span> <span data-ttu-id="19817-154">Depois de clicar em Okey, a mensagem "o parâmetro X Method1 é 5" é exibida.</span><span class="sxs-lookup"><span data-stu-id="19817-154">After you click OK, the message "The X parameter for Method1 is 5" is displayed.</span></span> <span data-ttu-id="19817-155">Clique em Okey e a mensagem "detectada ao manipulador de eventos do evento" é exibida.</span><span class="sxs-lookup"><span data-stu-id="19817-155">Click OK, and the message "The event handler caught the event" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19817-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19817-156">See Also</span></span>  
 <span data-ttu-id="19817-157">[Instrução Implements](../../../../visual-basic/language-reference/statements/implements-statement.md) </span><span class="sxs-lookup"><span data-stu-id="19817-157">[Implements Statement](../../../../visual-basic/language-reference/statements/implements-statement.md) </span></span>  
<span data-ttu-id="19817-158"> [Interfaces](../../../../visual-basic/programming-guide/language-features/interfaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="19817-158"> [Interfaces](../../../../visual-basic/programming-guide/language-features/interfaces/index.md) </span></span>  
<span data-ttu-id="19817-159"> [Instrução interface](../../../../visual-basic/language-reference/statements/interface-statement.md) </span><span class="sxs-lookup"><span data-stu-id="19817-159"> [Interface Statement](../../../../visual-basic/language-reference/statements/interface-statement.md) </span></span>  
<span data-ttu-id="19817-160"> [Instrução Event](../../../../visual-basic/language-reference/statements/event-statement.md)</span><span class="sxs-lookup"><span data-stu-id="19817-160"> [Event Statement](../../../../visual-basic/language-reference/statements/event-statement.md)</span></span>

