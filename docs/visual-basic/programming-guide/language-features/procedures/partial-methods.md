---
title: "Métodos parciais (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.PartialMethod
- PartialMethod
helpviewer_keywords:
- custom logic into code [Visual Basic]
- partial methods [Visual Basic]
- partial [Visual Basic], methods [Visual Basic]
- methods [Visual Basic], partial methods
- inserting custom logic into code
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8ebedd6f8173e3c349240d24ddaf16e4841f67a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="partial-methods-visual-basic"></a><span data-ttu-id="6981a-102">Métodos parciais (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6981a-102">Partial Methods (Visual Basic)</span></span>
<span data-ttu-id="6981a-103">Métodos parciais permitem aos desenvolvedores inserir a lógica personalizada em código.</span><span class="sxs-lookup"><span data-stu-id="6981a-103">Partial methods enable developers to insert custom logic into code.</span></span> <span data-ttu-id="6981a-104">Normalmente, o código é parte de uma classe gerado pelo designer.</span><span class="sxs-lookup"><span data-stu-id="6981a-104">Typically, the code is part of a designer-generated class.</span></span> <span data-ttu-id="6981a-105">Métodos parciais são definidos em uma classe parcial que é criada por um gerador de código, e eles são usados para fornecer notificação de que algo foi alterado.</span><span class="sxs-lookup"><span data-stu-id="6981a-105">Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed.</span></span> <span data-ttu-id="6981a-106">Elas permitem que o desenvolvedor especificar o comportamento personalizado em resposta a alterações.</span><span class="sxs-lookup"><span data-stu-id="6981a-106">They enable the developer to specify custom behavior in response to the change.</span></span>  
  
 <span data-ttu-id="6981a-107">O designer do gerador de código define apenas a assinatura de método e uma ou mais chamadas para o método.</span><span class="sxs-lookup"><span data-stu-id="6981a-107">The designer of the code generator defines only the method signature and one or more calls to the method.</span></span> <span data-ttu-id="6981a-108">Os desenvolvedores poderá fornecer implementações para o método se desejar personalizar o comportamento do código gerado.</span><span class="sxs-lookup"><span data-stu-id="6981a-108">Developers can then provide implementations for the method if they want to customize the behavior of the generated code.</span></span> <span data-ttu-id="6981a-109">Quando nenhuma implementação for fornecida, chamadas ao método são removidas pelo compilador, resultando em nenhuma sobrecarga de desempenho adicionais.</span><span class="sxs-lookup"><span data-stu-id="6981a-109">When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.</span></span>  
  
## <a name="declaration"></a><span data-ttu-id="6981a-110">Declaração</span><span class="sxs-lookup"><span data-stu-id="6981a-110">Declaration</span></span>  
 <span data-ttu-id="6981a-111">O código gerado marca a definição de um método parcial, colocando a palavra-chave `Partial` no início da linha de assinatura.</span><span class="sxs-lookup"><span data-stu-id="6981a-111">The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.</span></span>  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 <span data-ttu-id="6981a-112">A definição deve atender aos seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="6981a-112">The definition must meet the following conditions:</span></span>  
  
-   <span data-ttu-id="6981a-113">O método deve ser um `Sub`, não um `Function`.</span><span class="sxs-lookup"><span data-stu-id="6981a-113">The method must be a `Sub`, not a `Function`.</span></span>  
  
-   <span data-ttu-id="6981a-114">O corpo do método deve ser deixado vazio.</span><span class="sxs-lookup"><span data-stu-id="6981a-114">The body of the method must be left empty.</span></span>  
  
-   <span data-ttu-id="6981a-115">O modificador de acesso deve ser `Private`.</span><span class="sxs-lookup"><span data-stu-id="6981a-115">The access modifier must be `Private`.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="6981a-116">Implementação</span><span class="sxs-lookup"><span data-stu-id="6981a-116">Implementation</span></span>  
 <span data-ttu-id="6981a-117">A implementação consiste principalmente preencher o corpo do método parcial.</span><span class="sxs-lookup"><span data-stu-id="6981a-117">The implementation consists primarily of filling in the body of the partial method.</span></span> <span data-ttu-id="6981a-118">A implementação normalmente é uma classe parcial separada da definição e é escrita por um desenvolvedor que deseja estender o código gerado.</span><span class="sxs-lookup"><span data-stu-id="6981a-118">The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.</span></span>  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 <span data-ttu-id="6981a-119">O exemplo anterior duplica a assinatura na declaração exatamente, mas são variações possíveis.</span><span class="sxs-lookup"><span data-stu-id="6981a-119">The previous example duplicates the signature in the declaration exactly, but variations are possible.</span></span> <span data-ttu-id="6981a-120">Em particular, outros modificadores podem ser adicionados, como `Overloads` ou `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="6981a-120">In particular, other modifiers can be added, such as `Overloads` or `Overrides`.</span></span> <span data-ttu-id="6981a-121">Apenas um `Overrides` modificador é permitido.</span><span class="sxs-lookup"><span data-stu-id="6981a-121">Only one `Overrides` modifier is permitted.</span></span> <span data-ttu-id="6981a-122">Para obter mais informações sobre o método modificadores, consulte [instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6981a-122">For more information about method modifiers, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="use"></a><span data-ttu-id="6981a-123">Use</span><span class="sxs-lookup"><span data-stu-id="6981a-123">Use</span></span>  
 <span data-ttu-id="6981a-124">Chamar um método parcial como você poderia chamar qualquer outro `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="6981a-124">You call a partial method as you would call any other `Sub` procedure.</span></span> <span data-ttu-id="6981a-125">Se o método tiver sido implementado, os argumentos são avaliados e o corpo do método é executado.</span><span class="sxs-lookup"><span data-stu-id="6981a-125">If the method has been implemented, the arguments are evaluated and the body of the method is executed.</span></span> <span data-ttu-id="6981a-126">No entanto, lembre-se de que a implementação de um método parcial é opcional.</span><span class="sxs-lookup"><span data-stu-id="6981a-126">However, remember that implementing a partial method is optional.</span></span> <span data-ttu-id="6981a-127">Se o método não está implementado, uma chamada para que ele não tem nenhum efeito e expressões passadas como argumentos para o método não são avaliadas.</span><span class="sxs-lookup"><span data-stu-id="6981a-127">If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6981a-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6981a-128">Example</span></span>  
 <span data-ttu-id="6981a-129">Em um arquivo denominado Product.Designer.vb, defina um `Product` classe que tem um `Quantity` propriedade.</span><span class="sxs-lookup"><span data-stu-id="6981a-129">In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#4](./codesnippet/VisualBasic/partial-methods_1.vb)]  
  
 <span data-ttu-id="6981a-130">Em um arquivo denominado Product vb, forneça uma implementação para `QuantityChanged`.</span><span class="sxs-lookup"><span data-stu-id="6981a-130">In a file named Product.vb, provide an implementation for `QuantityChanged`.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#5](./codesnippet/VisualBasic/partial-methods_2.vb)]  
  
 <span data-ttu-id="6981a-131">Finalmente, o método principal de um projeto, declare um `Product` instância e forneça um valor inicial para sua `Quantity` propriedade.</span><span class="sxs-lookup"><span data-stu-id="6981a-131">Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#6](./codesnippet/VisualBasic/partial-methods_3.vb)]  
  
 <span data-ttu-id="6981a-132">Deve aparecer uma caixa de mensagem que exibe esta mensagem:</span><span class="sxs-lookup"><span data-stu-id="6981a-132">A message box should appear that displays this message:</span></span>  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a><span data-ttu-id="6981a-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6981a-133">See Also</span></span>  
 [<span data-ttu-id="6981a-134">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="6981a-134">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="6981a-135">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="6981a-135">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="6981a-136">Parâmetros Opcionais</span><span class="sxs-lookup"><span data-stu-id="6981a-136">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="6981a-137">Parcial</span><span class="sxs-lookup"><span data-stu-id="6981a-137">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [<span data-ttu-id="6981a-138">Geração de código em LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="6981a-138">Code Generation in LINQ to SQL</span></span>](https://msdn.microsoft.com/library/bb399400)  
 [<span data-ttu-id="6981a-139">Adicionando lógica comercial usando métodos parciais</span><span class="sxs-lookup"><span data-stu-id="6981a-139">Adding Business Logic By Using Partial Methods</span></span>](https://msdn.microsoft.com/library/bb546176)
