---
title: "Chamando uma propriedade ou método usando um nome de cadeia de caracteres (Visual Basic) | Documentos do Microsoft"
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
- passing operators
- strings [Visual Basic], passing new operators as
- objects [Visual Basic], setting properties
- setting properties, object properties at run time
- method calls, strings
- methods [Visual Basic], calling with string names
- calling methods, string names
- properties [Visual Basic], setting at run time
- CallByName function
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
caps.latest.revision: 17
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
ms.openlocfilehash: 6de5e655b3d4d42283b81507d7f08e0eb0b9424d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a><span data-ttu-id="16864-102">Chamando uma propriedade ou um método usando o nome de uma cadeia de caracteres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16864-102">Calling a Property or Method Using a String Name (Visual Basic)</span></span>
<span data-ttu-id="16864-103">Na maioria dos casos, você pode descobrir as propriedades e métodos de um objeto em tempo de design e escrever código para lidar com eles.</span><span class="sxs-lookup"><span data-stu-id="16864-103">In most cases, you can discover the properties and methods of an object at design time, and write code to handle them.</span></span> <span data-ttu-id="16864-104">No entanto, em alguns casos você pode não saber sobre propriedades e métodos de um objeto com antecedência, ou você pode apenas querer a flexibilidade de ativar um usuário final especificar propriedades ou executar métodos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="16864-104">However, in some cases you may not know about an object's properties and methods in advance, or you may just want the flexibility of enabling an end user to specify properties or execute methods at run time.</span></span>  
  
## <a name="callbyname-function"></a><span data-ttu-id="16864-105">Função CallByName</span><span class="sxs-lookup"><span data-stu-id="16864-105">CallByName Function</span></span>  
 <span data-ttu-id="16864-106">Considere, por exemplo, um aplicativo cliente que avalia as expressões inseridas pelo usuário, passando um operador para um componente COM.</span><span class="sxs-lookup"><span data-stu-id="16864-106">Consider, for example, a client application that evaluates expressions entered by the user by passing an operator to a COM component.</span></span> <span data-ttu-id="16864-107">Suponha que você está constantemente adicionando novas funções ao componente que exigem novos operadores.</span><span class="sxs-lookup"><span data-stu-id="16864-107">Suppose you are constantly adding new functions to the component that require new operators.</span></span> <span data-ttu-id="16864-108">Quando você usa técnicas de acesso a objeto padrão, você deve recompilar e redistribuir o aplicativo cliente antes ele pudesse usar os novos operadores.</span><span class="sxs-lookup"><span data-stu-id="16864-108">When you use standard object access techniques, you must recompile and redistribute the client application before it could use the new operators.</span></span> <span data-ttu-id="16864-109">Para evitar isso, você pode usar o `CallByName` função passar os novos operadores como cadeias de caracteres, sem alterar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="16864-109">To avoid this, you can use the `CallByName` function to pass the new operators as strings, without changing the application.</span></span>  
  
 <span data-ttu-id="16864-110">O `CallByName` função permite que você use uma cadeia de caracteres para especificar uma propriedade ou método em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="16864-110">The `CallByName` function lets you use a string to specify a property or method at run time.</span></span> <span data-ttu-id="16864-111">A assinatura para o `CallByName` função tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="16864-111">The signature for the `CallByName` function looks like this:</span></span>  
  
 <span data-ttu-id="16864-112">*Result* = `CallByName`(*Object*, *ProcedureName*, *CallType*, *Arguments*())</span><span class="sxs-lookup"><span data-stu-id="16864-112">*Result* = `CallByName`(*Object*, *ProcedureName*, *CallType*, *Arguments*())</span></span>  
  
 <span data-ttu-id="16864-113">O primeiro argumento, *objeto*, utiliza o nome do objeto que você deseja agir.</span><span class="sxs-lookup"><span data-stu-id="16864-113">The first argument, *Object*, takes the name of the object you want to act upon.</span></span> <span data-ttu-id="16864-114">O *ProcedureName* argumento tem uma cadeia de caracteres que contém o nome do procedimento de método ou propriedade a ser chamado.</span><span class="sxs-lookup"><span data-stu-id="16864-114">The *ProcedureName* argument takes a string that contains the name of the method or property procedure to be invoked.</span></span> <span data-ttu-id="16864-115">O *CallType* argumento leva uma constante que representa o tipo de procedimento para chamar: um método (`Microsoft.VisualBasic.CallType.Method`), uma propriedade leitura (`Microsoft.VisualBasic.CallType.Get`), ou um conjunto de propriedades (`Microsoft.VisualBasic.CallType.Set`).</span><span class="sxs-lookup"><span data-stu-id="16864-115">The *CallType* argument takes a constant that represents the type of procedure to invoke: a method (`Microsoft.VisualBasic.CallType.Method`), a property read (`Microsoft.VisualBasic.CallType.Get`), or a property set (`Microsoft.VisualBasic.CallType.Set`).</span></span> <span data-ttu-id="16864-116">O *argumentos* argumento, que é opcional, leva uma matriz do tipo `Object` que contém quaisquer argumentos para o procedimento.</span><span class="sxs-lookup"><span data-stu-id="16864-116">The *Arguments* argument, which is optional, takes an array of type `Object` that contains any arguments to the procedure.</span></span>  
  
 <span data-ttu-id="16864-117">Você pode usar `CallByName` com classes em sua solução atual, mas geralmente é usado para acessar objetos COM ou de [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies.</span><span class="sxs-lookup"><span data-stu-id="16864-117">You can use `CallByName` with classes in your current solution, but it is most often used to access COM objects or objects from [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies.</span></span>  
  
 <span data-ttu-id="16864-118">Suponha que você adicione uma referência a um assembly que contém uma classe chamada `MathClass`, que tem uma nova função chamada `SquareRoot`, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="16864-118">Suppose you add a reference to an assembly that contains a class named `MathClass`, which has a new function named `SquareRoot`, as shown in the following code:</span></span>  
  
 <span data-ttu-id="16864-119">[!code-vb[VbVbalrOOP&#53;](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="16864-119">[!code-vb[VbVbalrOOP#53](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_1.vb)]</span></span>  
  
 <span data-ttu-id="16864-120">Seu aplicativo pode usar controles de caixa de texto para o controle de qual método será chamado e seus argumentos.</span><span class="sxs-lookup"><span data-stu-id="16864-120">Your application could use text box controls to control which method will be called and its arguments.</span></span> <span data-ttu-id="16864-121">Por exemplo, se `TextBox1` contém a expressão a ser avaliada, e `TextBox2` é usado para inserir o nome da função, você pode usar o seguinte código para chamar o `SquareRoot` função na expressão em `TextBox1`:</span><span class="sxs-lookup"><span data-stu-id="16864-121">For example, if `TextBox1` contains the expression to be evaluated, and `TextBox2` is used to enter the name of the function, you can use the following code to invoke the `SquareRoot` function on the expression in `TextBox1`:</span></span>  
  
 <span data-ttu-id="16864-122">[!code-vb[VbVbalrOOP&#54;](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="16864-122">[!code-vb[VbVbalrOOP#54](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_2.vb)]</span></span>  
  
 <span data-ttu-id="16864-123">Se você inserir "64" `TextBox1`, "SquareRoot" no `TextBox2`e, em seguida, chame o `CallMath` procedimento, a raiz quadrada do número em `TextBox1` é avaliada.</span><span class="sxs-lookup"><span data-stu-id="16864-123">If you enter "64" in `TextBox1`, "SquareRoot" in `TextBox2`, and then call the `CallMath` procedure, the square root of the number in `TextBox1` is evaluated.</span></span> <span data-ttu-id="16864-124">O código no exemplo chama o `SquareRoot` função (que usa uma cadeia de caracteres que contém a expressão a ser avaliada como um argumento necessário) e retorna "8" em `TextBox1` (a raiz quadrada de 64).</span><span class="sxs-lookup"><span data-stu-id="16864-124">The code in the example invokes the `SquareRoot` function (which takes a string that contains the expression to be evaluated as a required argument) and returns "8" in `TextBox1` (the square root of 64).</span></span> <span data-ttu-id="16864-125">Obviamente, se o usuário insere uma cadeia de caracteres inválida `TextBox2`, se a cadeia de caracteres contém o nome de uma propriedade em vez de um método, ou se o método tinha um argumento adicional necessário, ocorrerá um erro de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="16864-125">Of course, if the user enters an invalid string in `TextBox2`, if the string contains the name of a property instead of a method, or if the method had an additional required argument, a run-time error occurs.</span></span> <span data-ttu-id="16864-126">Você precisa adicionar código de tratamento de erros robusto ao usar `CallByName` para prever essas ou quaisquer outros erros.</span><span class="sxs-lookup"><span data-stu-id="16864-126">You have to add robust error-handling code when you use `CallByName` to anticipate these or any other errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16864-127">Enquanto o `CallByName` função pode ser útil em alguns casos, você deve avaliar sua utilidade contra as implicações de desempenho — usando `CallByName` chamar um procedimento é um pouco mais lenta do que uma chamada de ligação tardia.</span><span class="sxs-lookup"><span data-stu-id="16864-127">While the `CallByName` function may be useful in some cases, you must weigh its usefulness against the performance implications — using `CallByName` to invoke a procedure is slightly slower than a late-bound call.</span></span> <span data-ttu-id="16864-128">Se você estiver chamando uma função que é chamada repetidamente, tais como dentro de um loop, `CallByName` pode ter um grave efeito no desempenho.</span><span class="sxs-lookup"><span data-stu-id="16864-128">If you are invoking a function that is called repeatedly, such as inside a loop, `CallByName` can have a severe effect on performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16864-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16864-129">See Also</span></span>  
 <span data-ttu-id="16864-130"><xref:Microsoft.VisualBasic.Interaction.CallByName%2A></xref:Microsoft.VisualBasic.Interaction.CallByName%2A></span><span class="sxs-lookup"><span data-stu-id="16864-130"><xref:Microsoft.VisualBasic.Interaction.CallByName%2A></span></span>   
<span data-ttu-id="16864-131"> [Determinando o Tipo de Objeto](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)</span><span class="sxs-lookup"><span data-stu-id="16864-131"> [Determining Object Type](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)</span></span>
