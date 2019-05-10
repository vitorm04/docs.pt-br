---
title: Métodos parciais (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 50d7f24fd9f854d36bb2ed48c2e41a996c29dfe8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638879"
---
# <a name="partial-methods-visual-basic"></a><span data-ttu-id="ab955-102">Métodos parciais (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab955-102">Partial Methods (Visual Basic)</span></span>
<span data-ttu-id="ab955-103">Métodos parciais permitem que os desenvolvedores insiram lógica personalizada no código.</span><span class="sxs-lookup"><span data-stu-id="ab955-103">Partial methods enable developers to insert custom logic into code.</span></span> <span data-ttu-id="ab955-104">Normalmente, o código é parte de uma classe gerado pelo designer.</span><span class="sxs-lookup"><span data-stu-id="ab955-104">Typically, the code is part of a designer-generated class.</span></span> <span data-ttu-id="ab955-105">Métodos parciais são definidos em uma classe parcial que é criada por um gerador de código, e elas são usadas para fornecer uma notificação de que algo foi alterado.</span><span class="sxs-lookup"><span data-stu-id="ab955-105">Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed.</span></span> <span data-ttu-id="ab955-106">Eles permitem ao desenvolvedor especificar o comportamento personalizado em resposta à alteração.</span><span class="sxs-lookup"><span data-stu-id="ab955-106">They enable the developer to specify custom behavior in response to the change.</span></span>  
  
 <span data-ttu-id="ab955-107">O designer do gerador de código define apenas a assinatura do método e uma ou mais chamadas para o método.</span><span class="sxs-lookup"><span data-stu-id="ab955-107">The designer of the code generator defines only the method signature and one or more calls to the method.</span></span> <span data-ttu-id="ab955-108">Os desenvolvedores, em seguida, podem fornecer implementações para o método se desejar personalizar o comportamento do código gerado.</span><span class="sxs-lookup"><span data-stu-id="ab955-108">Developers can then provide implementations for the method if they want to customize the behavior of the generated code.</span></span> <span data-ttu-id="ab955-109">Quando nenhuma implementação for fornecida, chamadas ao método são removidas pelo compilador, resultando em nenhuma sobrecarga de desempenho adicional.</span><span class="sxs-lookup"><span data-stu-id="ab955-109">When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.</span></span>  
  
## <a name="declaration"></a><span data-ttu-id="ab955-110">Declaração</span><span class="sxs-lookup"><span data-stu-id="ab955-110">Declaration</span></span>  
 <span data-ttu-id="ab955-111">O código gerado marca a definição de um método parcial, colocando a palavra-chave `Partial` no início da linha de assinatura.</span><span class="sxs-lookup"><span data-stu-id="ab955-111">The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.</span></span>  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 <span data-ttu-id="ab955-112">A definição deve atender aos seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="ab955-112">The definition must meet the following conditions:</span></span>  
  
- <span data-ttu-id="ab955-113">O método deve ser um `Sub`, e não um `Function`.</span><span class="sxs-lookup"><span data-stu-id="ab955-113">The method must be a `Sub`, not a `Function`.</span></span>  
  
- <span data-ttu-id="ab955-114">O corpo do método deve ser deixado vazio.</span><span class="sxs-lookup"><span data-stu-id="ab955-114">The body of the method must be left empty.</span></span>  
  
- <span data-ttu-id="ab955-115">O modificador de acesso deve ser `Private`.</span><span class="sxs-lookup"><span data-stu-id="ab955-115">The access modifier must be `Private`.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="ab955-116">Implementação</span><span class="sxs-lookup"><span data-stu-id="ab955-116">Implementation</span></span>  
 <span data-ttu-id="ab955-117">A implementação consiste basicamente em preencher o corpo do método parcial.</span><span class="sxs-lookup"><span data-stu-id="ab955-117">The implementation consists primarily of filling in the body of the partial method.</span></span> <span data-ttu-id="ab955-118">A implementação é normalmente em uma classe parcial separada da definição e é escrita por um desenvolvedor que deseja estender o código gerado.</span><span class="sxs-lookup"><span data-stu-id="ab955-118">The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.</span></span>  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 <span data-ttu-id="ab955-119">O exemplo anterior duplica a assinatura na declaração exatamente, mas variações são possíveis.</span><span class="sxs-lookup"><span data-stu-id="ab955-119">The previous example duplicates the signature in the declaration exactly, but variations are possible.</span></span> <span data-ttu-id="ab955-120">Em particular, outros modificadores podem ser adicionados, tais como `Overloads` ou `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="ab955-120">In particular, other modifiers can be added, such as `Overloads` or `Overrides`.</span></span> <span data-ttu-id="ab955-121">Apenas um `Overrides` modificador é permitido.</span><span class="sxs-lookup"><span data-stu-id="ab955-121">Only one `Overrides` modifier is permitted.</span></span> <span data-ttu-id="ab955-122">Para obter mais informações sobre o método modificadores, consulte [instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ab955-122">For more information about method modifiers, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="use"></a><span data-ttu-id="ab955-123">Use</span><span class="sxs-lookup"><span data-stu-id="ab955-123">Use</span></span>  
 <span data-ttu-id="ab955-124">Chamar um método parcial como você poderia chamar qualquer outro `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="ab955-124">You call a partial method as you would call any other `Sub` procedure.</span></span> <span data-ttu-id="ab955-125">Se o método tiver sido implementado, os argumentos são avaliados e o corpo do método é executado.</span><span class="sxs-lookup"><span data-stu-id="ab955-125">If the method has been implemented, the arguments are evaluated and the body of the method is executed.</span></span> <span data-ttu-id="ab955-126">No entanto, lembre-se de que a implementação de um método parcial é opcional.</span><span class="sxs-lookup"><span data-stu-id="ab955-126">However, remember that implementing a partial method is optional.</span></span> <span data-ttu-id="ab955-127">Se o método não está implementado, uma chamada para que ele não tem nenhum efeito e expressões passadas como argumentos para o método não são avaliadas.</span><span class="sxs-lookup"><span data-stu-id="ab955-127">If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab955-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ab955-128">Example</span></span>  
 <span data-ttu-id="ab955-129">Em um arquivo denominado Product.Designer.vb, defina uma `Product` classe que tem um `Quantity` propriedade.</span><span class="sxs-lookup"><span data-stu-id="ab955-129">In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 <span data-ttu-id="ab955-130">Em um arquivo denominado Product vb, fornecer uma implementação para `QuantityChanged`.</span><span class="sxs-lookup"><span data-stu-id="ab955-130">In a file named Product.vb, provide an implementation for `QuantityChanged`.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 <span data-ttu-id="ab955-131">Por fim, no método principal de um projeto, declarar uma `Product` da instância e fornecer um valor inicial para sua `Quantity` propriedade.</span><span class="sxs-lookup"><span data-stu-id="ab955-131">Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 <span data-ttu-id="ab955-132">Deve aparecer uma caixa de mensagem que exibe esta mensagem:</span><span class="sxs-lookup"><span data-stu-id="ab955-132">A message box should appear that displays this message:</span></span>  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a><span data-ttu-id="ab955-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab955-133">See also</span></span>

- [<span data-ttu-id="ab955-134">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="ab955-134">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="ab955-135">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="ab955-135">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="ab955-136">Parâmetros Opcionais</span><span class="sxs-lookup"><span data-stu-id="ab955-136">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="ab955-137">Parcial</span><span class="sxs-lookup"><span data-stu-id="ab955-137">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)
- [<span data-ttu-id="ab955-138">Geração de código em LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ab955-138">Code Generation in LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="ab955-139">Adicionando a lógica de negócios usando métodos parciais</span><span class="sxs-lookup"><span data-stu-id="ab955-139">Adding Business Logic By Using Partial Methods</span></span>](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
