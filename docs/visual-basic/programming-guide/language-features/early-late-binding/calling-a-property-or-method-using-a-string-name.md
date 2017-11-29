---
title: "Chamando uma propriedade ou um método usando o nome de uma cadeia de caracteres (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- passing operators [Visual Basic]
- strings [Visual Basic], passing new operators as
- objects [Visual Basic], setting properties
- setting properties, object properties at run time
- method calls [Visual Basic], strings
- methods [Visual Basic], calling with string names
- calling methods [Visual Basic], string names
- properties [Visual Basic], setting at run time
- CallByName function
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c5974257fb82fe83c66a480225da200c14338898
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a><span data-ttu-id="e7b8c-102">Chamando uma propriedade ou um método usando o nome de uma cadeia de caracteres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7b8c-102">Calling a Property or Method Using a String Name (Visual Basic)</span></span>
<span data-ttu-id="e7b8c-103">Na maioria dos casos, você pode descobrir as propriedades e métodos de um objeto em tempo de design e escrever código para lidar com eles.</span><span class="sxs-lookup"><span data-stu-id="e7b8c-103">In most cases, you can discover the properties and methods of an object at design time, and write code to handle them.</span></span> <span data-ttu-id="e7b8c-104">No entanto, em alguns casos você talvez não saiba sobre as propriedades e métodos de um objeto com antecedência, ou você pode apenas querer a flexibilidade de habilitação de um usuário final especificar propriedades ou executar métodos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e7b8c-104">However, in some cases you may not know about an object's properties and methods in advance, or you may just want the flexibility of enabling an end user to specify properties or execute methods at run time.</span></span>  
  
## <a name="callbyname-function"></a><span data-ttu-id="e7b8c-105">Função CallByName</span><span class="sxs-lookup"><span data-stu-id="e7b8c-105">CallByName Function</span></span>  
 <span data-ttu-id="e7b8c-106">Considere, por exemplo, um aplicativo cliente que avalia as expressões inseridas pelo usuário, passando um operador para um componente COM.</span><span class="sxs-lookup"><span data-stu-id="e7b8c-106">Consider, for example, a client application that evaluates expressions entered by the user by passing an operator to a COM component.</span></span> <span data-ttu-id="e7b8c-107">Suponha que você está constantemente adicionando novas funções ao componente que exigem novos operadores.</span><span class="sxs-lookup"><span data-stu-id="e7b8c-107">Suppose you are constantly adding new functions to the component that require new operators.</span></span> <span data-ttu-id="e7b8c-108">Quando você usa técnicas de acesso a objeto padrão, você deve recompilar e redistribuir o aplicativo cliente antes que ele poderia usar os novos operadores.</span><span class="sxs-lookup"><span data-stu-id="e7b8c-108">When you use standard object access techniques, you must recompile and redistribute the client application before it could use the new operators.</span></span> <span data-ttu-id="e7b8c-109">Para evitar isso, você pode usar o `CallByName` função para passar os novos operadores como cadeias de caracteres, sem alterar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e7b8c-109">To avoid this, you can use the `CallByName` function to pass the new operators as strings, without changing the application.</span></span>  
  
 <span data-ttu-id="e7b8c-110">O `CallByName` função permite que você use uma cadeia de caracteres para especificar uma propriedade ou método em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e7b8c-110">The `CallByName` function lets you use a string to specify a property or method at run time.</span></span> <span data-ttu-id="e7b8c-111">A assinatura para o `CallByName` função tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="e7b8c-111">The signature for the `CallByName` function looks like this:</span></span>  
  
 <span data-ttu-id="e7b8c-112">*Resultado* = `CallByName`(*objeto*, *ProcedureName*, *CallType*, *argumentos*())</span><span class="sxs-lookup"><span data-stu-id="e7b8c-112">*Result* = `CallByName`(*Object*, *ProcedureName*, *CallType*, *Arguments*())</span></span>  
  
 <span data-ttu-id="e7b8c-113">O primeiro argumento, *objeto*, obtém o nome do objeto que você deseja agir.</span><span class="sxs-lookup"><span data-stu-id="e7b8c-113">The first argument, *Object*, takes the name of the object you want to act upon.</span></span> <span data-ttu-id="e7b8c-114">O *ProcedureName* argumento tem uma cadeia de caracteres que contém o nome do procedimento de propriedade ou método a ser invocado.</span><span class="sxs-lookup"><span data-stu-id="e7b8c-114">The *ProcedureName* argument takes a string that contains the name of the method or property procedure to be invoked.</span></span> <span data-ttu-id="e7b8c-115">O *CallType* argumento leva uma constante que representa o tipo de procedimento para chamar: um método (`Microsoft.VisualBasic.CallType.Method`), uma propriedade de leitura (`Microsoft.VisualBasic.CallType.Get`), ou um conjunto de propriedades (`Microsoft.VisualBasic.CallType.Set`).</span><span class="sxs-lookup"><span data-stu-id="e7b8c-115">The *CallType* argument takes a constant that represents the type of procedure to invoke: a method (`Microsoft.VisualBasic.CallType.Method`), a property read (`Microsoft.VisualBasic.CallType.Get`), or a property set (`Microsoft.VisualBasic.CallType.Set`).</span></span> <span data-ttu-id="e7b8c-116">O *argumentos* argumento, que é opcional, leva uma matriz do tipo `Object` que contém quaisquer argumentos para o procedimento.</span><span class="sxs-lookup"><span data-stu-id="e7b8c-116">The *Arguments* argument, which is optional, takes an array of type `Object` that contains any arguments to the procedure.</span></span>  
  
 <span data-ttu-id="e7b8c-117">Você pode usar `CallByName` com classes em sua solução atual, mas geralmente é usado para acessar objetos COM ou objetos de [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies.</span><span class="sxs-lookup"><span data-stu-id="e7b8c-117">You can use `CallByName` with classes in your current solution, but it is most often used to access COM objects or objects from [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies.</span></span>  
  
 <span data-ttu-id="e7b8c-118">Suponha que você adicionar uma referência a um assembly que contém uma classe denominada `MathClass`, que tem uma nova função chamada `SquareRoot`, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="e7b8c-118">Suppose you add a reference to an assembly that contains a class named `MathClass`, which has a new function named `SquareRoot`, as shown in the following code:</span></span>  
  
 [!code-vb[VbVbalrOOP#53](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_1.vb)]  
  
 <span data-ttu-id="e7b8c-119">Seu aplicativo pode usar controles de caixa de texto para controlar qual método será chamado e seus argumentos.</span><span class="sxs-lookup"><span data-stu-id="e7b8c-119">Your application could use text box controls to control which method will be called and its arguments.</span></span> <span data-ttu-id="e7b8c-120">Por exemplo, se `TextBox1` contém a expressão a ser avaliada, e `TextBox2` é usado para inserir o nome da função, você pode usar o seguinte código para chamar o `SquareRoot` função na expressão em `TextBox1`:</span><span class="sxs-lookup"><span data-stu-id="e7b8c-120">For example, if `TextBox1` contains the expression to be evaluated, and `TextBox2` is used to enter the name of the function, you can use the following code to invoke the `SquareRoot` function on the expression in `TextBox1`:</span></span>  
  
 [!code-vb[VbVbalrOOP#54](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_2.vb)]  
  
 <span data-ttu-id="e7b8c-121">Se você inserir "64" `TextBox1`, "SquareRoot" no `TextBox2`e, em seguida, chame o `CallMath` procedimento, a raiz quadrada do número em `TextBox1` é avaliada.</span><span class="sxs-lookup"><span data-stu-id="e7b8c-121">If you enter "64" in `TextBox1`, "SquareRoot" in `TextBox2`, and then call the `CallMath` procedure, the square root of the number in `TextBox1` is evaluated.</span></span> <span data-ttu-id="e7b8c-122">O código de exemplo invoca o `SquareRoot` função (que utiliza uma cadeia de caracteres que contém a expressão a ser avaliada como um argumento necessário) e retorna "8" `TextBox1` (a raiz quadrada de 64).</span><span class="sxs-lookup"><span data-stu-id="e7b8c-122">The code in the example invokes the `SquareRoot` function (which takes a string that contains the expression to be evaluated as a required argument) and returns "8" in `TextBox1` (the square root of 64).</span></span> <span data-ttu-id="e7b8c-123">Obviamente, se o usuário insere uma cadeia de caracteres inválida em `TextBox2`, se a cadeia de caracteres contém o nome de uma propriedade em vez de um método, ou se o método tinha um argumento adicional necessário, ocorrerá um erro de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e7b8c-123">Of course, if the user enters an invalid string in `TextBox2`, if the string contains the name of a property instead of a method, or if the method had an additional required argument, a run-time error occurs.</span></span> <span data-ttu-id="e7b8c-124">Você precisa adicionar o código de tratamento de erros robusto ao usar `CallByName` para prever essas ou quaisquer outros erros.</span><span class="sxs-lookup"><span data-stu-id="e7b8c-124">You have to add robust error-handling code when you use `CallByName` to anticipate these or any other errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7b8c-125">Enquanto o `CallByName` função pode ser útil em alguns casos, você deve avaliar sua utilidade contra as implicações de desempenho — usando `CallByName` chamar um procedimento é um pouco mais lenta do que uma chamada de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="e7b8c-125">While the `CallByName` function may be useful in some cases, you must weigh its usefulness against the performance implications — using `CallByName` to invoke a procedure is slightly slower than a late-bound call.</span></span> <span data-ttu-id="e7b8c-126">Se você estiver chamando uma função que é chamada repetidamente, tais como dentro de um loop, `CallByName` pode ter um grave efeito no desempenho.</span><span class="sxs-lookup"><span data-stu-id="e7b8c-126">If you are invoking a function that is called repeatedly, such as inside a loop, `CallByName` can have a severe effect on performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7b8c-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7b8c-127">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>  
 [<span data-ttu-id="e7b8c-128">Determinando o Tipo de Objeto</span><span class="sxs-lookup"><span data-stu-id="e7b8c-128">Determining Object Type</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)
