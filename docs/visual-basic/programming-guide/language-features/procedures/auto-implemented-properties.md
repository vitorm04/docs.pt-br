---
title: Propriedades autoimplementadas (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: 4577609c78271ac91e011b20ef6a8b4066072428
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649668"
---
# <a name="auto-implemented-properties-visual-basic"></a><span data-ttu-id="01ea6-102">Propriedades autoimplementadas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01ea6-102">Auto-Implemented Properties (Visual Basic)</span></span>
<span data-ttu-id="01ea6-103">*Propriedades autoimplementadas* permitem que você especifique uma propriedade de uma classe rapidamente sem a necessidade de escrever código para as propriedades `Get` e `Set` .</span><span class="sxs-lookup"><span data-stu-id="01ea6-103">*Auto-implemented properties* enable you to quickly specify a property of a class without having to write code to `Get` and `Set` the property.</span></span> <span data-ttu-id="01ea6-104">uando você escreve código criando uma propriedade implementada automaticamente, o compilador do Visual Basic cria automaticamente um campo *private* para armazenar a variável de propriedade, além de criar os procedimentos `Get` e `Set` associados.</span><span class="sxs-lookup"><span data-stu-id="01ea6-104">When you write code for an auto-implemented property, the Visual Basic compiler automatically creates a private field to store the property variable in addition to creating the associated `Get` and `Set` procedures.</span></span>  
  
 <span data-ttu-id="01ea6-105">Com Propriedades autoimplementadas, uma propriedade, incluindo um valor padrão, pode ser declarada em uma única linha.</span><span class="sxs-lookup"><span data-stu-id="01ea6-105">With auto-implemented properties, a property, including a default value, can be declared in a single line.</span></span> <span data-ttu-id="01ea6-106">O exemplo a seguir mostra três declarações de propriedade.</span><span class="sxs-lookup"><span data-stu-id="01ea6-106">The following example shows three property declarations.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#1)]  
  
 <span data-ttu-id="01ea6-107">Uma propriedade implementada automaticamente é equivalente a uma propriedade para o qual o valor da propriedade é armazenado em um campo particular.</span><span class="sxs-lookup"><span data-stu-id="01ea6-107">An auto-implemented property is equivalent to a property for which the property value is stored in a private field.</span></span> <span data-ttu-id="01ea6-108">O exemplo de código a seguir mostra uma propriedade implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="01ea6-108">The following code example shows an auto-implemented property.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#5)]  
  
 <span data-ttu-id="01ea6-109">O exemplo de código a seguir mostra o código equivalente no exemplo anterior da propriedade implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="01ea6-109">The following code example shows the equivalent code for the previous auto-implemented property example.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#2)]  
  
 <span data-ttu-id="01ea6-110">O código a seguir mostra como implementar propriedades somente leitura:</span><span class="sxs-lookup"><span data-stu-id="01ea6-110">The following code show implementing readonly properties:</span></span>  
  
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
  
 <span data-ttu-id="01ea6-111">Você pode atribuir a propriedade com expressões de inicialização, conforme mostrado no exemplo, ou você pode atribuir às propriedades do construtor do tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="01ea6-111">You can assign to the property with initialization expressions as shown in the example, or you can assign to the properties in the containing type’s constructor.</span></span>  <span data-ttu-id="01ea6-112">Você pode atribuir a campos de suporte das propriedades somente leitura a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="01ea6-112">You can assign to the backing fields of readonly properties at any time.</span></span>  
  
## <a name="backing-field"></a><span data-ttu-id="01ea6-113">Campo de suporte</span><span class="sxs-lookup"><span data-stu-id="01ea6-113">Backing Field</span></span>  
 <span data-ttu-id="01ea6-114">Quando você declara uma propriedade implementada automaticamente, o Visual Basic cria automaticamente um campo particular oculto chamado o *campo de support* para conter o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="01ea6-114">When you declare an auto-implemented property, Visual Basic automatically creates a hidden private field called the *backing field* to contain the property value.</span></span> <span data-ttu-id="01ea6-115">O nome do campo de suporte é o nome da propriedade implementada automaticamente precedido por um sublinhado (_).</span><span class="sxs-lookup"><span data-stu-id="01ea6-115">The backing field name is the auto-implemented property name preceded by an underscore (_).</span></span> <span data-ttu-id="01ea6-116">Por exemplo, se você declarar uma propriedade implementada automaticamente denominada `ID`, o campo de suporte é denominado `_ID`.</span><span class="sxs-lookup"><span data-stu-id="01ea6-116">For example, if you declare an auto-implemented property named `ID`, the backing field is named `_ID`.</span></span> <span data-ttu-id="01ea6-117">Se você incluir um membro da sua classe que também é chamado `_ID`, isso produzirá um conflito de nomeação e o Visual Basic vai relatar um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="01ea6-117">If you include a member of your class that is also named `_ID`, you produce a naming conflict and Visual Basic reports a compiler error.</span></span>  
  
 <span data-ttu-id="01ea6-118">O campo de suporte também tem as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="01ea6-118">The backing field also has the following characteristics:</span></span>  
  
- <span data-ttu-id="01ea6-119">O modificador de acesso para o campo de suporte é sempre `Private`, mesmo quando a própria propriedade tem um nível de acesso diferentes, como `Public`.</span><span class="sxs-lookup"><span data-stu-id="01ea6-119">The access modifier for the backing field is always `Private`, even when the property itself has a different access level, such as `Public`.</span></span>  
  
- <span data-ttu-id="01ea6-120">Se a propriedade é marcada como `Shared`, o campo de suporte também é compartilhado.</span><span class="sxs-lookup"><span data-stu-id="01ea6-120">If the property is marked as `Shared`, the backing field also is shared.</span></span>  
  
- <span data-ttu-id="01ea6-121">Atributos especificados para a propriedade não se aplicam ao campo de suporte.</span><span class="sxs-lookup"><span data-stu-id="01ea6-121">Attributes specified for the property do not apply to the backing field.</span></span>  
  
- <span data-ttu-id="01ea6-122">O campo de suporte pode ser acessado do código dentro da classe e de ferramentas de depuração, como a janela de inspeção.</span><span class="sxs-lookup"><span data-stu-id="01ea6-122">The backing field can be accessed from code within the class and from debugging tools such as the Watch window.</span></span> <span data-ttu-id="01ea6-123">No entanto, o campo de suporte não aparece na lista de conclusão do IntelliSense word.</span><span class="sxs-lookup"><span data-stu-id="01ea6-123">However, the backing field does not show in an IntelliSense word completion list.</span></span>  
  
## <a name="initializing-an-auto-implemented-property"></a><span data-ttu-id="01ea6-124">Inicializando uma propriedade implementada automaticamente</span><span class="sxs-lookup"><span data-stu-id="01ea6-124">Initializing an Auto-Implemented Property</span></span>  
 <span data-ttu-id="01ea6-125">Qualquer expressão que pode ser usada para inicializar um campo é válida para a inicialização de uma propriedade implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="01ea6-125">Any expression that can be used to initialize a field is valid for initializing an auto-implemented property.</span></span> <span data-ttu-id="01ea6-126">Quando você inicializa uma propriedade implementada automaticamente, a expressão é avaliada e passada para o `Set` procedimento para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="01ea6-126">When you initialize an auto-implemented property, the expression is evaluated and passed to the `Set` procedure for the property.</span></span> <span data-ttu-id="01ea6-127">Os exemplos de código a seguir mostram algumas propriedades autoimplementadas que incluem valores iniciais.</span><span class="sxs-lookup"><span data-stu-id="01ea6-127">The following code examples show some auto-implemented properties that include initial values.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 <span data-ttu-id="01ea6-128">Você não pode inicializar uma propriedade autoimplementada que é um membro de um `Interface`, ou que está marcado como `MustOverride`.</span><span class="sxs-lookup"><span data-stu-id="01ea6-128">You cannot initialize an auto-implemented property that is a member of an `Interface`, or one that is marked `MustOverride`.</span></span>  
  
 <span data-ttu-id="01ea6-129">Quando você declara uma propriedade implementada automaticamente como um membro de um `Structure`, você só pode inicializar a propriedade implementada automaticamente se ele está marcado como `Shared`.</span><span class="sxs-lookup"><span data-stu-id="01ea6-129">When you declare an auto-implemented property as a member of a `Structure`, you can only initialize the auto-implemented property if it is marked as `Shared`.</span></span>  
  
 <span data-ttu-id="01ea6-130">Quando você declara uma propriedade implementada automaticamente como uma matriz, você não pode especificar os limites de matriz explícita.</span><span class="sxs-lookup"><span data-stu-id="01ea6-130">When you declare an auto-implemented property as an array, you cannot specify explicit array bounds.</span></span> <span data-ttu-id="01ea6-131">No entanto, você pode fornecer um valor usando um inicializador de matriz, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="01ea6-131">However, you can supply a value by using an array initializer, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a><span data-ttu-id="01ea6-132">Definições de propriedade que exigem a sintaxe padrão</span><span class="sxs-lookup"><span data-stu-id="01ea6-132">Property Definitions That Require Standard Syntax</span></span>  
 <span data-ttu-id="01ea6-133">Propriedades autoimplementadas são convenientes e dar suporte a muitos cenários de programação.</span><span class="sxs-lookup"><span data-stu-id="01ea6-133">Auto-implemented properties are convenient and support many programming scenarios.</span></span> <span data-ttu-id="01ea6-134">No entanto, há situações em que você não pode usar uma propriedade implementada automaticamente e em vez disso, deve usar o padrão, ou *expandido*, sintaxe de propriedade.</span><span class="sxs-lookup"><span data-stu-id="01ea6-134">However, there are situations in which you cannot use an auto-implemented property and must instead use standard, or *expanded*, property syntax.</span></span>  
  
 <span data-ttu-id="01ea6-135">Você precisa usar a sintaxe de definição de propriedade expandido se você quiser fazer qualquer um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="01ea6-135">You have to use expanded property-definition syntax if you want to do any one of the following:</span></span>  
  
- <span data-ttu-id="01ea6-136">Adicione código para o `Get` ou `Set` procedimento de uma propriedade, como o código para validar valores de entrada no `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="01ea6-136">Add code to the `Get` or `Set` procedure of a property, such as code to validate incoming values in the `Set` procedure.</span></span> <span data-ttu-id="01ea6-137">Por exemplo, você talvez queira verificar se uma cadeia de caracteres que representa um número de telefone contém o número necessário de numerais antes de definir o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="01ea6-137">For example, you might want to verify that a string that represents a telephone number contains the required number of numerals before setting the property value.</span></span>  
  
- <span data-ttu-id="01ea6-138">Especificar a acessibilidade diferente para o `Get` e `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="01ea6-138">Specify different accessibility for the `Get` and `Set` procedure.</span></span> <span data-ttu-id="01ea6-139">Por exemplo, você talvez queira fazer a `Set` procedimento `Private` e o `Get` procedimento `Public`.</span><span class="sxs-lookup"><span data-stu-id="01ea6-139">For example, you might want to make the `Set` procedure `Private` and the `Get` procedure `Public`.</span></span>  
  
- <span data-ttu-id="01ea6-140">Criar propriedades que são `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="01ea6-140">Create properties that are `WriteOnly`.</span></span>  
  
- <span data-ttu-id="01ea6-141">Usar propriedades parametrizadas (incluindo `Default` propriedades).</span><span class="sxs-lookup"><span data-stu-id="01ea6-141">Use parameterized properties (including `Default` properties).</span></span> <span data-ttu-id="01ea6-142">Você deve declarar uma propriedade expandida para especificar um parâmetro para a propriedade, ou para especificar parâmetros adicionais para o `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="01ea6-142">You must declare an expanded property in order to specify a parameter for the property, or to specify additional parameters for the `Set` procedure.</span></span>  
  
- <span data-ttu-id="01ea6-143">Colocar um atributo no campo de suporte, ou alterar o nível de acesso do campo de backup.</span><span class="sxs-lookup"><span data-stu-id="01ea6-143">Place an attribute on the backing field, or change the access level of the backing field.</span></span>  
  
- <span data-ttu-id="01ea6-144">Fornece comentários XML para o campo de suporte.</span><span class="sxs-lookup"><span data-stu-id="01ea6-144">Provide XML comments for the backing field.</span></span>  
  
## <a name="expanding-an-auto-implemented-property"></a><span data-ttu-id="01ea6-145">Expandindo uma propriedade implementada automaticamente</span><span class="sxs-lookup"><span data-stu-id="01ea6-145">Expanding an Auto-Implemented Property</span></span>  
 <span data-ttu-id="01ea6-146">Se você precisar converter uma propriedade implementada automaticamente a uma propriedade expandida que contém um `Get` ou `Set` procedimento, o Editor de código do Visual Basic pode gerar automaticamente o `Get` e `Set` eprocedimentos`End Property`instrução para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="01ea6-146">If you have to convert an auto-implemented property to an expanded property that contains a `Get` or `Set` procedure, the Visual Basic Code Editor can automatically generate the `Get` and `Set` procedures and `End Property` statement for the property.</span></span> <span data-ttu-id="01ea6-147">O código é gerado se você colocar o cursor em uma linha em branco após o `Property` instrução, digite um `G` (para `Get`) ou uma `S` (para `Set`) e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="01ea6-147">The code is generated if you put the cursor on a blank line following the `Property` statement, type a `G` (for `Get`) or an `S` (for `Set`) and press ENTER.</span></span> <span data-ttu-id="01ea6-148">Editor de código do Visual Basic gera automaticamente a `Get` ou `Set` procedimento para propriedades somente leitura e somente gravação ao pressionar ENTER no final de um `Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="01ea6-148">The Visual Basic Code Editor automatically generates the `Get` or `Set` procedure for read-only and write-only properties when you press ENTER at the end of a `Property` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01ea6-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01ea6-149">See also</span></span>

- [<span data-ttu-id="01ea6-150">Como: Declarar e chamar uma propriedade padrão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="01ea6-150">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="01ea6-151">Como: Declarar uma propriedade com níveis de acesso mistos</span><span class="sxs-lookup"><span data-stu-id="01ea6-151">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="01ea6-152">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="01ea6-152">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="01ea6-153">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="01ea6-153">ReadOnly</span></span>](../../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="01ea6-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="01ea6-154">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="01ea6-155">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="01ea6-155">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
