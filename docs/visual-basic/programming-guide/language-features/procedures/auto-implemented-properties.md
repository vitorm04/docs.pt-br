---
title: Propriedades autoimplementadas
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: f50b1f40ef9843391c6622561bfd8a8eaae6fc17
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090048"
---
# <a name="auto-implemented-properties-visual-basic"></a><span data-ttu-id="6a25a-102">Propriedades autoimplementadas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a25a-102">Auto-Implemented Properties (Visual Basic)</span></span>

<span data-ttu-id="6a25a-103">*As propriedades implementadas automaticamente* permitem que você especifique rapidamente uma propriedade de uma classe sem precisar gravar o código `Get` e `Set` a propriedade.</span><span class="sxs-lookup"><span data-stu-id="6a25a-103">*Auto-implemented properties* enable you to quickly specify a property of a class without having to write code to `Get` and `Set` the property.</span></span> <span data-ttu-id="6a25a-104">Quando você escreve o código para uma propriedade implementada automaticamente, o compilador Visual Basic cria automaticamente um campo particular para armazenar a variável de propriedade, além de criar `Get` os `Set` procedimentos e associados.</span><span class="sxs-lookup"><span data-stu-id="6a25a-104">When you write code for an auto-implemented property, the Visual Basic compiler automatically creates a private field to store the property variable in addition to creating the associated `Get` and `Set` procedures.</span></span>  
  
 <span data-ttu-id="6a25a-105">Com propriedades implementadas automaticamente, uma propriedade, incluindo um valor padrão, pode ser declarada em uma única linha.</span><span class="sxs-lookup"><span data-stu-id="6a25a-105">With auto-implemented properties, a property, including a default value, can be declared in a single line.</span></span> <span data-ttu-id="6a25a-106">O exemplo a seguir mostra três declarações de propriedade.</span><span class="sxs-lookup"><span data-stu-id="6a25a-106">The following example shows three property declarations.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#1)]  
  
 <span data-ttu-id="6a25a-107">Uma propriedade implementada automaticamente é equivalente a uma propriedade para a qual o valor da propriedade é armazenado em um campo particular.</span><span class="sxs-lookup"><span data-stu-id="6a25a-107">An auto-implemented property is equivalent to a property for which the property value is stored in a private field.</span></span> <span data-ttu-id="6a25a-108">O exemplo de código a seguir mostra uma propriedade implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="6a25a-108">The following code example shows an auto-implemented property.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#5)]  
  
 <span data-ttu-id="6a25a-109">O exemplo de código a seguir mostra o código equivalente para o exemplo de propriedade implementada automaticamente anterior.</span><span class="sxs-lookup"><span data-stu-id="6a25a-109">The following code example shows the equivalent code for the previous auto-implemented property example.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#2)]  
  
 <span data-ttu-id="6a25a-110">O código a seguir mostra a implementação de propriedades ReadOnly:</span><span class="sxs-lookup"><span data-stu-id="6a25a-110">The following code show implementing readonly properties:</span></span>  
  
```vb  
Class Customer  
   Public ReadOnly Property Tags As New List(Of String)  
   Public ReadOnly Property Name As String = ""  
   Public ReadOnly Property File As String  
  
   Sub New(file As String)  
      Me.File = file  
   End Sub  
End Class  
```  
  
 <span data-ttu-id="6a25a-111">Você pode atribuir à propriedade com expressões de inicialização, conforme mostrado no exemplo, ou pode atribuir às propriedades no construtor do tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="6a25a-111">You can assign to the property with initialization expressions as shown in the example, or you can assign to the properties in the containing type’s constructor.</span></span>  <span data-ttu-id="6a25a-112">Você pode atribuir aos campos de backup das propriedades ReadOnly a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="6a25a-112">You can assign to the backing fields of readonly properties at any time.</span></span>  
  
## <a name="backing-field"></a><span data-ttu-id="6a25a-113">Campo de apoio</span><span class="sxs-lookup"><span data-stu-id="6a25a-113">Backing Field</span></span>  

 <span data-ttu-id="6a25a-114">Quando você declara uma propriedade implementada automaticamente, Visual Basic cria automaticamente um campo privado oculto chamado *campo de backup* para conter o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="6a25a-114">When you declare an auto-implemented property, Visual Basic automatically creates a hidden private field called the *backing field* to contain the property value.</span></span> <span data-ttu-id="6a25a-115">O nome do campo de backup é o nome da propriedade autoimplementada precedida por um sublinhado (_).</span><span class="sxs-lookup"><span data-stu-id="6a25a-115">The backing field name is the auto-implemented property name preceded by an underscore (_).</span></span> <span data-ttu-id="6a25a-116">Por exemplo, se você declarar uma propriedade implementada automaticamente chamada `ID` , o campo de backup será nomeado `_ID` .</span><span class="sxs-lookup"><span data-stu-id="6a25a-116">For example, if you declare an auto-implemented property named `ID`, the backing field is named `_ID`.</span></span> <span data-ttu-id="6a25a-117">Se você incluir um membro de sua classe que também é nomeado `_ID` , produzirá um conflito de nomenclatura e Visual Basic relatará um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="6a25a-117">If you include a member of your class that is also named `_ID`, you produce a naming conflict and Visual Basic reports a compiler error.</span></span>  
  
 <span data-ttu-id="6a25a-118">O campo de backup também tem as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="6a25a-118">The backing field also has the following characteristics:</span></span>  
  
- <span data-ttu-id="6a25a-119">O modificador de acesso para o campo de backup é sempre `Private` , mesmo quando a própria propriedade tem um nível de acesso diferente, como `Public` .</span><span class="sxs-lookup"><span data-stu-id="6a25a-119">The access modifier for the backing field is always `Private`, even when the property itself has a different access level, such as `Public`.</span></span>  
  
- <span data-ttu-id="6a25a-120">Se a propriedade estiver marcada como `Shared` , o campo de backup também será compartilhado.</span><span class="sxs-lookup"><span data-stu-id="6a25a-120">If the property is marked as `Shared`, the backing field also is shared.</span></span>  
  
- <span data-ttu-id="6a25a-121">Os atributos especificados para a propriedade não se aplicam ao campo de backup.</span><span class="sxs-lookup"><span data-stu-id="6a25a-121">Attributes specified for the property do not apply to the backing field.</span></span>  
  
- <span data-ttu-id="6a25a-122">O campo de backup pode ser acessado a partir do código dentro da classe e de ferramentas de depuração, como o janela Inspeção.</span><span class="sxs-lookup"><span data-stu-id="6a25a-122">The backing field can be accessed from code within the class and from debugging tools such as the Watch window.</span></span> <span data-ttu-id="6a25a-123">No entanto, o campo de backup não aparece em uma lista de preenchimento de palavra do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="6a25a-123">However, the backing field does not show in an IntelliSense word completion list.</span></span>  
  
## <a name="initializing-an-auto-implemented-property"></a><span data-ttu-id="6a25a-124">Inicializando uma propriedade implementada automaticamente</span><span class="sxs-lookup"><span data-stu-id="6a25a-124">Initializing an Auto-Implemented Property</span></span>  

 <span data-ttu-id="6a25a-125">Qualquer expressão que possa ser usada para inicializar um campo é válida para inicializar uma propriedade implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="6a25a-125">Any expression that can be used to initialize a field is valid for initializing an auto-implemented property.</span></span> <span data-ttu-id="6a25a-126">Quando você Inicializa uma propriedade implementada automaticamente, a expressão é avaliada e passada para o `Set` procedimento para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="6a25a-126">When you initialize an auto-implemented property, the expression is evaluated and passed to the `Set` procedure for the property.</span></span> <span data-ttu-id="6a25a-127">Os exemplos de código a seguir mostram algumas propriedades implementadas automaticamente que incluem valores iniciais.</span><span class="sxs-lookup"><span data-stu-id="6a25a-127">The following code examples show some auto-implemented properties that include initial values.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 <span data-ttu-id="6a25a-128">Não é possível inicializar uma propriedade implementada automaticamente que seja membro de um `Interface` ou um que esteja marcado como `MustOverride` .</span><span class="sxs-lookup"><span data-stu-id="6a25a-128">You cannot initialize an auto-implemented property that is a member of an `Interface`, or one that is marked `MustOverride`.</span></span>  
  
 <span data-ttu-id="6a25a-129">Ao declarar uma propriedade autoimplementada como membro de um `Structure` , você só poderá inicializar a propriedade autoimplementada se ela estiver marcada como `Shared` .</span><span class="sxs-lookup"><span data-stu-id="6a25a-129">When you declare an auto-implemented property as a member of a `Structure`, you can only initialize the auto-implemented property if it is marked as `Shared`.</span></span>  
  
 <span data-ttu-id="6a25a-130">Quando você declara uma propriedade implementada automaticamente como uma matriz, não é possível especificar limites de matriz explícitos.</span><span class="sxs-lookup"><span data-stu-id="6a25a-130">When you declare an auto-implemented property as an array, you cannot specify explicit array bounds.</span></span> <span data-ttu-id="6a25a-131">No entanto, você pode fornecer um valor usando um inicializador de matriz, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="6a25a-131">However, you can supply a value by using an array initializer, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a><span data-ttu-id="6a25a-132">Definições de propriedade que exigem sintaxe padrão</span><span class="sxs-lookup"><span data-stu-id="6a25a-132">Property Definitions That Require Standard Syntax</span></span>  

 <span data-ttu-id="6a25a-133">As propriedades implementadas automaticamente são convenientes e dão suporte a muitos cenários de programação.</span><span class="sxs-lookup"><span data-stu-id="6a25a-133">Auto-implemented properties are convenient and support many programming scenarios.</span></span> <span data-ttu-id="6a25a-134">No entanto, há situações em que você não pode usar uma propriedade autoimplementada e, em vez disso, usar a sintaxe de propriedade Standard ou *Expanded*.</span><span class="sxs-lookup"><span data-stu-id="6a25a-134">However, there are situations in which you cannot use an auto-implemented property and must instead use standard, or *expanded*, property syntax.</span></span>  
  
 <span data-ttu-id="6a25a-135">Você precisa usar a sintaxe de definição de propriedade expandida se desejar fazer um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="6a25a-135">You have to use expanded property-definition syntax if you want to do any one of the following:</span></span>  
  
- <span data-ttu-id="6a25a-136">Adicione código ao `Get` procedimento ou `Set` de uma propriedade, como código para validar os valores de entrada no `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="6a25a-136">Add code to the `Get` or `Set` procedure of a property, such as code to validate incoming values in the `Set` procedure.</span></span> <span data-ttu-id="6a25a-137">Por exemplo, talvez você queira verificar se uma cadeia de caracteres que representa um número de telefone contém o número necessário de numerais antes de definir o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="6a25a-137">For example, you might want to verify that a string that represents a telephone number contains the required number of numerals before setting the property value.</span></span>  
  
- <span data-ttu-id="6a25a-138">Especifique a acessibilidade diferente para `Get` o `Set` procedimento e.</span><span class="sxs-lookup"><span data-stu-id="6a25a-138">Specify different accessibility for the `Get` and `Set` procedure.</span></span> <span data-ttu-id="6a25a-139">Por exemplo, talvez você queira fazer o `Set` procedimento `Private` e o `Get` procedimento `Public` .</span><span class="sxs-lookup"><span data-stu-id="6a25a-139">For example, you might want to make the `Set` procedure `Private` and the `Get` procedure `Public`.</span></span>  
  
- <span data-ttu-id="6a25a-140">Crie propriedades que são `WriteOnly` .</span><span class="sxs-lookup"><span data-stu-id="6a25a-140">Create properties that are `WriteOnly`.</span></span>  
  
- <span data-ttu-id="6a25a-141">Use propriedades parametrizadas (incluindo `Default` Propriedades).</span><span class="sxs-lookup"><span data-stu-id="6a25a-141">Use parameterized properties (including `Default` properties).</span></span> <span data-ttu-id="6a25a-142">Você deve declarar uma propriedade expandida para especificar um parâmetro para a propriedade ou para especificar parâmetros adicionais para o `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="6a25a-142">You must declare an expanded property in order to specify a parameter for the property, or to specify additional parameters for the `Set` procedure.</span></span>  
  
- <span data-ttu-id="6a25a-143">Coloque um atributo no campo de apoio ou altere o nível de acesso do campo de backup.</span><span class="sxs-lookup"><span data-stu-id="6a25a-143">Place an attribute on the backing field, or change the access level of the backing field.</span></span>  
  
- <span data-ttu-id="6a25a-144">Forneça comentários XML para o campo de backup.</span><span class="sxs-lookup"><span data-stu-id="6a25a-144">Provide XML comments for the backing field.</span></span>  
  
## <a name="expanding-an-auto-implemented-property"></a><span data-ttu-id="6a25a-145">Expandindo uma propriedade implementada automaticamente</span><span class="sxs-lookup"><span data-stu-id="6a25a-145">Expanding an Auto-Implemented Property</span></span>  

 <span data-ttu-id="6a25a-146">Se você precisar converter uma propriedade autoimplementada em uma propriedade expandida que contenha `Get` um `Set` procedimento ou, o editor de código Visual Basic poderá gerar automaticamente os procedimentos e a `Get` instrução da `Set` `End Property` propriedade.</span><span class="sxs-lookup"><span data-stu-id="6a25a-146">If you have to convert an auto-implemented property to an expanded property that contains a `Get` or `Set` procedure, the Visual Basic Code Editor can automatically generate the `Get` and `Set` procedures and `End Property` statement for the property.</span></span> <span data-ttu-id="6a25a-147">O código será gerado se você colocar o cursor em uma linha em branco após a `Property` instrução, digite um `G` (para `Get` ) ou um `S` (para `Set` ) e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="6a25a-147">The code is generated if you put the cursor on a blank line following the `Property` statement, type a `G` (for `Get`) or an `S` (for `Set`) and press ENTER.</span></span> <span data-ttu-id="6a25a-148">O editor de código Visual Basic gera automaticamente `Get` o `Set` procedimento ou para propriedades somente leitura e somente gravação quando você pressiona Enter no final de uma `Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="6a25a-148">The Visual Basic Code Editor automatically generates the `Get` or `Set` procedure for read-only and write-only properties when you press ENTER at the end of a `Property` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a25a-149">Confira também</span><span class="sxs-lookup"><span data-stu-id="6a25a-149">See also</span></span>

- [<span data-ttu-id="6a25a-150">Como declarar e chamar uma propriedade padrão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6a25a-150">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="6a25a-151">Como declarar uma propriedade com níveis de acesso mistos</span><span class="sxs-lookup"><span data-stu-id="6a25a-151">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="6a25a-152">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="6a25a-152">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="6a25a-153">ReadOnly (somente-leitura)</span><span class="sxs-lookup"><span data-stu-id="6a25a-153">ReadOnly</span></span>](../../../language-reference/modifiers/readonly.md)
- [<span data-ttu-id="6a25a-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="6a25a-154">WriteOnly</span></span>](../../../language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="6a25a-155">Objetos e classes</span><span class="sxs-lookup"><span data-stu-id="6a25a-155">Objects and Classes</span></span>](../objects-and-classes/index.md)
