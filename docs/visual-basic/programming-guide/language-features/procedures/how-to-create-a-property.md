---
title: 'Como: criar uma propriedade (Visual Basic) | Documentos do Microsoft'
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
- procedures, defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
caps.latest.revision: 15
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
ms.openlocfilehash: 1cdb2e7c4a5fe9a32c64c9d0c4d07c4efb417d0f
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-a-property-visual-basic"></a><span data-ttu-id="77f80-102">Como criar uma propriedade (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77f80-102">How to: Create a Property (Visual Basic)</span></span>
<span data-ttu-id="77f80-103">Coloque uma definição de propriedade entre uma `Property` instrução e um `End Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="77f80-103">You enclose a property definition between a `Property` statement and an `End Property` statement.</span></span> <span data-ttu-id="77f80-104">Nessa definição você define um `Get` procedimento, uma `Set` procedimento, ou ambos.</span><span class="sxs-lookup"><span data-stu-id="77f80-104">Within this definition you define a `Get` procedure, a `Set` procedure, or both.</span></span> <span data-ttu-id="77f80-105">Todo o código da propriedade está situado nesses procedimentos.</span><span class="sxs-lookup"><span data-stu-id="77f80-105">All the property's code lies within these procedures.</span></span>  
  
 <span data-ttu-id="77f80-106">O `Get` procedimento recupera o valor da propriedade e o `Set` procedimento armazena um valor.</span><span class="sxs-lookup"><span data-stu-id="77f80-106">The `Get` procedure retrieves the property's value, and the `Set` procedure stores a value.</span></span> <span data-ttu-id="77f80-107">Se desejar que a propriedade tenha acesso de leitura/gravação, você deve definir os dois procedimentos.</span><span class="sxs-lookup"><span data-stu-id="77f80-107">If you want the property to have read/write access, you must define both procedures.</span></span> <span data-ttu-id="77f80-108">Para uma propriedade somente leitura, você define apenas `Get`, e para uma propriedade somente gravação, você define apenas `Set`.</span><span class="sxs-lookup"><span data-stu-id="77f80-108">For a read-only property, you define only `Get`, and for a write-only property, you define only `Set`.</span></span>  
  
### <a name="to-create-a-property"></a><span data-ttu-id="77f80-109">Para criar uma propriedade</span><span class="sxs-lookup"><span data-stu-id="77f80-109">To create a property</span></span>  
  
1.  <span data-ttu-id="77f80-110">Fora de qualquer propriedade ou procedimento, utilize uma [declaração de propriedade](../../../../visual-basic/language-reference/statements/property-statement.md), seguido por um `End Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="77f80-110">Outside any property or procedure, use a [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md), followed by an `End Property` statement.</span></span>  
  
2.  <span data-ttu-id="77f80-111">Se a propriedade recebe parâmetros, execute o `Property` palavra-chave com o nome do procedimento, a lista de parâmetros entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="77f80-111">If the property takes parameters, follow the `Property` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="77f80-112">Siga os parênteses com uma `As` cláusula para especificar o tipo de dados do valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="77f80-112">Follow the parentheses with an `As` clause to specify the data type of the property's value.</span></span> <span data-ttu-id="77f80-113">Você deve especificar o tipo de dados, mesmo para uma propriedade somente gravação.</span><span class="sxs-lookup"><span data-stu-id="77f80-113">You must specify the data type even for a write-only property.</span></span>  
  
4.  <span data-ttu-id="77f80-114">Adicionar `Get` e `Set` procedimentos, conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="77f80-114">Add `Get` and `Set` procedures, as appropriate.</span></span> <span data-ttu-id="77f80-115">Consulte as instruções a seguir.</span><span class="sxs-lookup"><span data-stu-id="77f80-115">See the following directions.</span></span>  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a><span data-ttu-id="77f80-116">Para criar um procedimento Get que recupera um valor de propriedade</span><span class="sxs-lookup"><span data-stu-id="77f80-116">To create a Get procedure that retrieves a property value</span></span>  
  
1.  <span data-ttu-id="77f80-117">Entre o `Property` e `End Property` instruções, escrever um [instrução Get](../../../../visual-basic/language-reference/statements/get-statement.md), seguido por um `End Get` instrução.</span><span class="sxs-lookup"><span data-stu-id="77f80-117">Between the `Property` and `End Property` statements, write a [Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md), followed by an `End Get` statement.</span></span> <span data-ttu-id="77f80-118">Você não precisa definir nenhum parâmetro para o `Get` procedimento.</span><span class="sxs-lookup"><span data-stu-id="77f80-118">You do not need to define any parameters for the `Get` procedure.</span></span>  
  
2.  <span data-ttu-id="77f80-119">Coloque as declarações de código para recuperar o valor da propriedade entre o `Get` e `End Get` instruções.</span><span class="sxs-lookup"><span data-stu-id="77f80-119">Place the code statements to retrieve the property's value between the `Get` and `End Get` statements.</span></span> <span data-ttu-id="77f80-120">Esse código pode incluir outros cálculos e manipulações de dados, além de gerar e retornar o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="77f80-120">This code can include other calculations and data manipulations in addition to generating and returning the property's value.</span></span>  
  
3.  <span data-ttu-id="77f80-121">Use um `Return` instrução para retornar o valor da propriedade para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="77f80-121">Use a `Return` statement to return the property's value to the calling code.</span></span>  
  
 <span data-ttu-id="77f80-122">Você deve escrever uma `Get` procedimento para uma propriedade de leitura / gravação e para uma propriedade somente leitura.</span><span class="sxs-lookup"><span data-stu-id="77f80-122">You must write a `Get` procedure for a read-write property and for a read-only property.</span></span> <span data-ttu-id="77f80-123">Você não deve definir um `Get` procedimento para uma propriedade somente gravação.</span><span class="sxs-lookup"><span data-stu-id="77f80-123">You must not define a `Get` procedure for a write-only property.</span></span>  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a><span data-ttu-id="77f80-124">Para criar um procedimento definido que grava um valor de propriedade</span><span class="sxs-lookup"><span data-stu-id="77f80-124">To create a Set procedure that writes a property's value</span></span>  
  
1.  <span data-ttu-id="77f80-125">Entre o `Property` e `End Property` instruções, escrever um [instrução Set](../../../../visual-basic/language-reference/statements/set-statement.md), seguido por um `End Set` instrução.</span><span class="sxs-lookup"><span data-stu-id="77f80-125">Between the `Property` and `End Property` statements, write a [Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md), followed by an `End Set` statement.</span></span>  
  
2.  <span data-ttu-id="77f80-126">No `Set` instrução, siga o `Set` palavra-chave com uma lista de parâmetros entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="77f80-126">In the `Set` statement, follow the `Set` keyword with a parameter list in parentheses.</span></span> <span data-ttu-id="77f80-127">Esta lista de parâmetros deve incluir pelo menos um parâmetro de valor passado pelo código de chamada.</span><span class="sxs-lookup"><span data-stu-id="77f80-127">This parameter list must include at least a value parameter for the value passed by the calling code.</span></span> <span data-ttu-id="77f80-128">O nome padrão para este parâmetro de valor é `Value`, mas você pode usar um nome diferente se apropriado.</span><span class="sxs-lookup"><span data-stu-id="77f80-128">The default name for this value parameter is `Value`, but you can use a different name if appropriate.</span></span> <span data-ttu-id="77f80-129">O parâmetro de valor deve ter os mesmos dados de tipo da propriedade.</span><span class="sxs-lookup"><span data-stu-id="77f80-129">The value parameter must have the same data type as the property itself.</span></span>  
  
3.  <span data-ttu-id="77f80-130">Coloque as declarações de código para armazenar um valor na propriedade entre o `Set` e `End Set` instruções.</span><span class="sxs-lookup"><span data-stu-id="77f80-130">Place the code statements to store a value in the property between the `Set` and `End Set` statements.</span></span> <span data-ttu-id="77f80-131">Esse código pode incluir outros cálculos e manipulações de dados, além de validar e armazenar o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="77f80-131">This code can include other calculations and data manipulations in addition to validating and storing the property's value.</span></span>  
  
4.  <span data-ttu-id="77f80-132">Use o parâmetro value para aceitar o valor fornecido pelo código de chamada.</span><span class="sxs-lookup"><span data-stu-id="77f80-132">Use the value parameter to accept the value supplied by the calling code.</span></span> <span data-ttu-id="77f80-133">Você pode armazenar esse valor diretamente em uma instrução de atribuição ou usá-lo em uma expressão para calcular o valor interno a ser armazenado.</span><span class="sxs-lookup"><span data-stu-id="77f80-133">You can either store this value directly in an assignment statement, or use it in an expression to calculate the internal value to be stored.</span></span>  
  
 <span data-ttu-id="77f80-134">Você deve escrever uma `Set` procedimento para uma propriedade de leitura / gravação e para uma propriedade somente gravação.</span><span class="sxs-lookup"><span data-stu-id="77f80-134">You must write a `Set` procedure for a read-write property and for a write-only property.</span></span> <span data-ttu-id="77f80-135">Você não deve definir um `Set` procedimento para uma propriedade somente leitura.</span><span class="sxs-lookup"><span data-stu-id="77f80-135">You must not define a `Set` procedure for a read-only property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77f80-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="77f80-136">Example</span></span>  
 <span data-ttu-id="77f80-137">O exemplo a seguir cria uma propriedade de leitura/gravação que armazena um nome completo como dois nomes constituintes, o primeiro nome e o sobrenome.</span><span class="sxs-lookup"><span data-stu-id="77f80-137">The following example creates a read/write property that stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="77f80-138">Quando o código de chamada lê `fullName`, o `Get` procedimento combina as duas partes e retorna o nome completo.</span><span class="sxs-lookup"><span data-stu-id="77f80-138">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="77f80-139">Quando o código de chamada atribui um novo nome completo, o `Set` procedimento tenta dividi-lo em duas partes.</span><span class="sxs-lookup"><span data-stu-id="77f80-139">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="77f80-140">Se não encontrar um espaço, ele armazena como o nome.</span><span class="sxs-lookup"><span data-stu-id="77f80-140">If it does not find a space, it stores it all as the first name.</span></span>  
  
 <span data-ttu-id="77f80-141">[!code-vb[VbVbcnProcedures n º&8;](./codesnippet/VisualBasic/how-to-create-a-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="77f80-141">[!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/how-to-create-a-property_1.vb)]</span></span>  
  
 <span data-ttu-id="77f80-142">O exemplo a seguir mostra chamadas típicas para os procedimentos de propriedade `fullName`.</span><span class="sxs-lookup"><span data-stu-id="77f80-142">The following example shows typical calls to the property procedures of `fullName`.</span></span> <span data-ttu-id="77f80-143">A primeira chamada define o valor da propriedade e a segunda chamada o recupera.</span><span class="sxs-lookup"><span data-stu-id="77f80-143">The first call sets the property value and the second call retrieves it.</span></span>  
  
 <span data-ttu-id="77f80-144">[!code-vb[VbVbcnProcedures n º&9;](./codesnippet/VisualBasic/how-to-create-a-property_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="77f80-144">[!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/how-to-create-a-property_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77f80-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77f80-145">See Also</span></span>  
 <span data-ttu-id="77f80-146">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="77f80-146">[Procedures](./index.md) </span></span>  
<span data-ttu-id="77f80-147"> [Procedimentos de propriedade](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="77f80-147"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="77f80-148"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="77f80-148"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="77f80-149"> [Diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="77f80-149"> [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md) </span></span>  
<span data-ttu-id="77f80-150"> [Como: declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="77f80-150"> [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md) </span></span>  
<span data-ttu-id="77f80-151"> [Como: chamar um procedimento de propriedade](./how-to-call-a-property-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="77f80-151"> [How to: Call a Property Procedure](./how-to-call-a-property-procedure.md) </span></span>  
<span data-ttu-id="77f80-152"> [Como: declarar e chamar uma propriedade padrão no Visual Basic](./how-to-declare-and-call-a-default-property.md) </span><span class="sxs-lookup"><span data-stu-id="77f80-152"> [How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md) </span></span>  
<span data-ttu-id="77f80-153"> [Como: inserir um valor em uma propriedade](./how-to-put-a-value-in-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="77f80-153"> [How to: Put a Value in a Property](./how-to-put-a-value-in-a-property.md) </span></span>  
<span data-ttu-id="77f80-154">Como obter um valor de uma propriedade (Visual Basic) [Como obter um valor de uma propriedade](./how-to-get-a-value-from-a-property.md)</span><span class="sxs-lookup"><span data-stu-id="77f80-154"> [How to: Get a Value from a Property](./how-to-get-a-value-from-a-property.md)</span></span>
