---
title: Objetos e classes
ms.date: 05/26/2020
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: 10e257a1cbc8778565a9838aeef423522f9d2970
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290611"
---
# <a name="objects-and-classes-in-visual-basic"></a><span data-ttu-id="0e8de-102">Objetos e classes no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0e8de-102">Objects and classes in Visual Basic</span></span>

<span data-ttu-id="0e8de-103">Um *objeto* é uma combinação de código e dados que podem ser tratados como uma unidade.</span><span class="sxs-lookup"><span data-stu-id="0e8de-103">An *object* is a combination of code and data that can be treated as a unit.</span></span> <span data-ttu-id="0e8de-104">Um objeto pode ser uma parte de um aplicativo, como um controle ou um formulário.</span><span class="sxs-lookup"><span data-stu-id="0e8de-104">An object can be a piece of an application, like a control or a form.</span></span> <span data-ttu-id="0e8de-105">Todo o aplicativo também pode ser um objeto.</span><span class="sxs-lookup"><span data-stu-id="0e8de-105">An entire application can also be an object.</span></span>

<span data-ttu-id="0e8de-106">Ao criar um aplicativo no Visual Basic, você trabalha constantemente com objetos.</span><span class="sxs-lookup"><span data-stu-id="0e8de-106">When you create an application in Visual Basic, you constantly work with objects.</span></span> <span data-ttu-id="0e8de-107">Você pode usar objetos fornecidos por Visual Basic, como controles, formulários e objetos de acesso a dados.</span><span class="sxs-lookup"><span data-stu-id="0e8de-107">You can use objects provided by Visual Basic, such as controls, forms, and data access objects.</span></span> <span data-ttu-id="0e8de-108">Você também pode usar objetos de outros aplicativos dentro de seu aplicativo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0e8de-108">You can also use objects from other applications within your Visual Basic application.</span></span> <span data-ttu-id="0e8de-109">Você pode até mesmo criar seus próprios objetos e definir propriedades e métodos adicionais para eles.</span><span class="sxs-lookup"><span data-stu-id="0e8de-109">You can even create your own objects and define additional properties and methods for them.</span></span> <span data-ttu-id="0e8de-110">Os objetos atuam como blocos de construção pré-fabricados para programas. Eles permitem que você escreva um trecho de código uma vez e reutilize repetidamente.</span><span class="sxs-lookup"><span data-stu-id="0e8de-110">Objects act like prefabricated building blocks for programs — they let you write a piece of code once and reuse it over and over.</span></span>

<span data-ttu-id="0e8de-111">Este tópico discute os objetos em detalhes.</span><span class="sxs-lookup"><span data-stu-id="0e8de-111">This topic discusses objects in detail.</span></span>

## <a name="objects-and-classes"></a><span data-ttu-id="0e8de-112">Objetos e classes</span><span class="sxs-lookup"><span data-stu-id="0e8de-112">Objects and classes</span></span>

<span data-ttu-id="0e8de-113">Cada objeto no Visual Basic é definido por uma *classe*.</span><span class="sxs-lookup"><span data-stu-id="0e8de-113">Each object in Visual Basic is defined by a *class*.</span></span> <span data-ttu-id="0e8de-114">Uma classe descreve as variáveis, as propriedades, os procedimentos e os eventos de um objeto.</span><span class="sxs-lookup"><span data-stu-id="0e8de-114">A class describes the variables, properties, procedures, and events of an object.</span></span> <span data-ttu-id="0e8de-115">Os objetos são instâncias de classes. Você pode criar a quantidade de objetos que precisar após ter definido uma classe.</span><span class="sxs-lookup"><span data-stu-id="0e8de-115">Objects are instances of classes; you can create as many objects you need once you have defined a class.</span></span>

<span data-ttu-id="0e8de-116">Para entender a relação entre um objeto e sua classe, pense em cookies e cortadores de cookie.</span><span class="sxs-lookup"><span data-stu-id="0e8de-116">To understand the relationship between an object and its class, think of cookie cutters and cookies.</span></span> <span data-ttu-id="0e8de-117">O cortador de cookie é a classe.</span><span class="sxs-lookup"><span data-stu-id="0e8de-117">The cookie cutter is the class.</span></span> <span data-ttu-id="0e8de-118">Ele define as características de cada cookie, por exemplo, tamanho e forma.</span><span class="sxs-lookup"><span data-stu-id="0e8de-118">It defines the characteristics of each cookie, for example size and shape.</span></span> <span data-ttu-id="0e8de-119">A classe é usada para criar objetos.</span><span class="sxs-lookup"><span data-stu-id="0e8de-119">The class is used to create objects.</span></span> <span data-ttu-id="0e8de-120">Os objetos são os cookies.</span><span class="sxs-lookup"><span data-stu-id="0e8de-120">The objects are the cookies.</span></span>

<span data-ttu-id="0e8de-121">Você deve criar um objeto antes de poder acessar seus membros, exceto para [`Shared`](../../../language-reference/modifiers/shared.md) Membros que podem ser acessados sem um objeto da classe.</span><span class="sxs-lookup"><span data-stu-id="0e8de-121">You must create an object before you can access its members, except for [`Shared`](../../../language-reference/modifiers/shared.md) members which can be accessed without an object of the class.</span></span>

### <a name="create-an-object-from-a-class"></a><span data-ttu-id="0e8de-122">Criar um objeto a partir de uma classe</span><span class="sxs-lookup"><span data-stu-id="0e8de-122">Create an object from a class</span></span>

1. <span data-ttu-id="0e8de-123">Determine de qual classe você deseja criar um objeto ou defina sua própria classe.</span><span class="sxs-lookup"><span data-stu-id="0e8de-123">Determine from which class you want to create an object, or define your own class.</span></span> <span data-ttu-id="0e8de-124">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="0e8de-124">For example:</span></span>

   ```vb
   Public Class Customer
       Public Property AccountNumber As Integer
   End Class
   ```

2. <span data-ttu-id="0e8de-125">Escreva uma [instrução Dim](../../../language-reference/statements/dim-statement.md) para criar uma variável a qual você pode atribuir uma instância da classe.</span><span class="sxs-lookup"><span data-stu-id="0e8de-125">Write a [Dim Statement](../../../language-reference/statements/dim-statement.md) to create a variable to which you can assign a class instance.</span></span> <span data-ttu-id="0e8de-126">A variável deve ser do tipo da classe desejada.</span><span class="sxs-lookup"><span data-stu-id="0e8de-126">The variable should be of the type of the desired class.</span></span>

   ```vb
   Dim nextCustomer As Customer
   ```

3. <span data-ttu-id="0e8de-127">Adicione a palavra-chave [novo operador](../../../language-reference/operators/new-operator.md) para inicializar a variável a uma nova instância da classe.</span><span class="sxs-lookup"><span data-stu-id="0e8de-127">Add the [New Operator](../../../language-reference/operators/new-operator.md) keyword to initialize the variable to a new instance of the class.</span></span>

   ```vb
   Dim nextCustomer As New Customer
   ```

4. <span data-ttu-id="0e8de-128">Agora você pode acessar os membros da classe pela variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="0e8de-128">You can now access the members of the class through the object variable.</span></span>

   ```vb
   nextCustomer.AccountNumber = lastAccountNumber + 1
   ```

> [!NOTE]
> <span data-ttu-id="0e8de-129">Sempre que possível, você deve declarar a variável para ser do tipo de classe que você pretende atribuir a ela.</span><span class="sxs-lookup"><span data-stu-id="0e8de-129">Whenever possible, you should declare the variable to be of the class type you intend to assign to it.</span></span> <span data-ttu-id="0e8de-130">Isso é chamado de *associação inicial*.</span><span class="sxs-lookup"><span data-stu-id="0e8de-130">This is called *early binding*.</span></span> <span data-ttu-id="0e8de-131">Se não souber o tipo de classe no tempo de compilação, você poderá invocar a *associação tardia*, declarando a variável como o [Tipo de Dados do Objeto](../../../language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="0e8de-131">If you don't know the class type at compile time, you can invoke *late binding* by declaring the variable to be of the [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="0e8de-132">Entretanto, a associação tardia pode tornar o desempenho mais lento e limitar o acesso a membros do objeto do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0e8de-132">However, late binding can make performance slower and limit access to the run-time object's members.</span></span> <span data-ttu-id="0e8de-133">Para obter mais informações, consulte [Declaração de variável de objeto](../variables/object-variable-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0e8de-133">For more information, see [Object Variable Declaration](../variables/object-variable-declaration.md).</span></span>

### <a name="multiple-instances"></a><span data-ttu-id="0e8de-134">Várias instâncias</span><span class="sxs-lookup"><span data-stu-id="0e8de-134">Multiple instances</span></span>

<span data-ttu-id="0e8de-135">Objetos recentemente criados de uma classe geralmente são idênticos entre si.</span><span class="sxs-lookup"><span data-stu-id="0e8de-135">Objects newly created from a class are often identical to each other.</span></span> <span data-ttu-id="0e8de-136">Assim que existem como objetos individuais, no entanto, suas propriedades e variáveis podem ser alteradas independentemente de outras instâncias.</span><span class="sxs-lookup"><span data-stu-id="0e8de-136">Once they exist as individual objects, however, their variables and properties can be changed independently of the other instances.</span></span> <span data-ttu-id="0e8de-137">Por exemplo, se você adicionar três caixas de seleção a um formulário, cada objeto da caixa de seleção será uma instância da classe <xref:System.Windows.Forms.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="0e8de-137">For example, if you add three check boxes to a form, each check box object is an instance of the <xref:System.Windows.Forms.CheckBox> class.</span></span> <span data-ttu-id="0e8de-138">Os objetos <xref:System.Windows.Forms.CheckBox> individuais compartilham um conjunto comum de características e recursos (propriedades, variáveis, procedimentos e eventos) definidos pela classe.</span><span class="sxs-lookup"><span data-stu-id="0e8de-138">The individual <xref:System.Windows.Forms.CheckBox> objects share a common set of characteristics and capabilities (properties, variables, procedures, and events) defined by the class.</span></span> <span data-ttu-id="0e8de-139">No entanto, cada um tem seu próprio nome, pode ser separadamente habilitado e desabilitado e pode ser colocado em um local diferente no formulário.</span><span class="sxs-lookup"><span data-stu-id="0e8de-139">However, each has its own name, can be separately enabled and disabled, and can be placed in a different location on the form.</span></span>

## <a name="object-members"></a><span data-ttu-id="0e8de-140">Membros do objeto</span><span class="sxs-lookup"><span data-stu-id="0e8de-140">Object members</span></span>

<span data-ttu-id="0e8de-141">Um objeto é um elemento de um aplicativo, que representa uma *instância* de uma classe.</span><span class="sxs-lookup"><span data-stu-id="0e8de-141">An object is an element of an application, representing an *instance* of a class.</span></span> <span data-ttu-id="0e8de-142">Campos, propriedades, métodos e eventos são os blocos de construção de objetos e constituem seus *membros*.</span><span class="sxs-lookup"><span data-stu-id="0e8de-142">Fields, properties, methods, and events are the building blocks of objects and constitute their *members*.</span></span>

### <a name="member-access"></a><span data-ttu-id="0e8de-143">Acesso de membro</span><span class="sxs-lookup"><span data-stu-id="0e8de-143">Member Access</span></span>

<span data-ttu-id="0e8de-144">É possível acessar um membro de um objeto especificando, em ordem, o nome da variável do objeto, um período (`.`) e o nome do membro.</span><span class="sxs-lookup"><span data-stu-id="0e8de-144">You access a member of an object by specifying, in order, the name of the object variable, a period (`.`), and the name of the member.</span></span> <span data-ttu-id="0e8de-145">O exemplo a seguir define a propriedade <xref:System.Windows.Forms.Control.Text%2A> de um objeto <xref:System.Windows.Forms.Label>.</span><span class="sxs-lookup"><span data-stu-id="0e8de-145">The following example sets the <xref:System.Windows.Forms.Control.Text%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a><span data-ttu-id="0e8de-146">Lista do IntelliSense de membros</span><span class="sxs-lookup"><span data-stu-id="0e8de-146">IntelliSense listing of members</span></span>

<span data-ttu-id="0e8de-147">O IntelliSense lista os membros de uma classe quando você invoca sua opção de membros da lista, por exemplo, ao digitar um ponto final (`.`) como um operador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="0e8de-147">IntelliSense lists members of a class when you invoke its List Members option, for example when you type a period (`.`) as a member-access operator.</span></span> <span data-ttu-id="0e8de-148">Se você digitar o período após o nome de uma variável declarada como uma instância da classe, o IntelliSense listará todos os membros de instância e nenhum dos membros compartilhados.</span><span class="sxs-lookup"><span data-stu-id="0e8de-148">If you type the period following the name of a variable declared as an instance of that class, IntelliSense lists all the instance members and none of the shared members.</span></span> <span data-ttu-id="0e8de-149">Se você digitar o ponto final após o nome da classe, o IntelliSense listará todos os membros compartilhados e nenhum dos membros de instância.</span><span class="sxs-lookup"><span data-stu-id="0e8de-149">If you type the period following the class name itself, IntelliSense lists all the shared members and none of the instance members.</span></span> <span data-ttu-id="0e8de-150">Para obter mais informações, veja [Usando o IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="0e8de-150">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>

### <a name="fields-and-properties"></a><span data-ttu-id="0e8de-151">Campos e propriedades</span><span class="sxs-lookup"><span data-stu-id="0e8de-151">Fields and properties</span></span>

<span data-ttu-id="0e8de-152">Os *campos* e as *propriedades* representam as informações armazenadas em um objeto.</span><span class="sxs-lookup"><span data-stu-id="0e8de-152">*Fields* and *properties* represent information stored in an object.</span></span> <span data-ttu-id="0e8de-153">Você recupera e define seus valores com instruções de atribuição da mesma maneira que você recupera e define variáveis locais em um procedimento.</span><span class="sxs-lookup"><span data-stu-id="0e8de-153">You retrieve and set their values with assignment statements the same way you retrieve and set local variables in a procedure.</span></span> <span data-ttu-id="0e8de-154">O exemplo a seguir recupera a propriedade <xref:System.Windows.Forms.Control.Width%2A> e define a propriedade <xref:System.Windows.Forms.Control.ForeColor%2A> de um objeto <xref:System.Windows.Forms.Label>.</span><span class="sxs-lookup"><span data-stu-id="0e8de-154">The following example retrieves the <xref:System.Windows.Forms.Control.Width%2A> property and sets the <xref:System.Windows.Forms.Control.ForeColor%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

<span data-ttu-id="0e8de-155">Observe que um campo também é chamado de uma *variável membro*.</span><span class="sxs-lookup"><span data-stu-id="0e8de-155">Note that a field is also called a *member variable*.</span></span>

<span data-ttu-id="0e8de-156">Use os procedimentos de propriedade quando:</span><span class="sxs-lookup"><span data-stu-id="0e8de-156">Use property procedures when:</span></span>

- <span data-ttu-id="0e8de-157">Precisar controlar quando e como um valor é definido ou recuperado.</span><span class="sxs-lookup"><span data-stu-id="0e8de-157">You need to control when and how a value is set or retrieved.</span></span>

- <span data-ttu-id="0e8de-158">A propriedade tiver um conjunto bem definido de valores que precisam ser validados.</span><span class="sxs-lookup"><span data-stu-id="0e8de-158">The property has a well-defined set of values that need to be validated.</span></span>

- <span data-ttu-id="0e8de-159">Definir o valor causa algumas alterações perceptíveis no estado do objeto, como um propriedade `IsVisible`.</span><span class="sxs-lookup"><span data-stu-id="0e8de-159">Setting the value causes some perceptible change in the object's state, such as an `IsVisible` property.</span></span>

- <span data-ttu-id="0e8de-160">Definir a propriedade faz alterações em outras variáveis internas ou nos valores de outras propriedades.</span><span class="sxs-lookup"><span data-stu-id="0e8de-160">Setting the property causes changes to other internal variables or to the values of other properties.</span></span>

- <span data-ttu-id="0e8de-161">Um conjunto de etapas deve ser executado antes de a propriedade pode ser definida ou recuperada.</span><span class="sxs-lookup"><span data-stu-id="0e8de-161">A set of steps must be performed before the property can be set or retrieved.</span></span>

<span data-ttu-id="0e8de-162">Use os campos quando:</span><span class="sxs-lookup"><span data-stu-id="0e8de-162">Use fields when:</span></span>

- <span data-ttu-id="0e8de-163">O valor for de um tipo de validação automática.</span><span class="sxs-lookup"><span data-stu-id="0e8de-163">The value is of a self-validating type.</span></span> <span data-ttu-id="0e8de-164">Por exemplo, um erro ou a conversão automática de dados ocorrerá se um valor diferente de `True` ou `False` for atribuído a uma variável `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="0e8de-164">For example, an error or automatic data conversion occurs if a value other than `True` or `False` is assigned to a `Boolean` variable.</span></span>

- <span data-ttu-id="0e8de-165">Qualquer valor no intervalo com suporte do tipo de dados é válido.</span><span class="sxs-lookup"><span data-stu-id="0e8de-165">Any value in the range supported by the data type is valid.</span></span> <span data-ttu-id="0e8de-166">Isso é verdadeiro para muitas propriedades de tipo `Single` ou `Double`.</span><span class="sxs-lookup"><span data-stu-id="0e8de-166">This is true of many properties of type `Single` or `Double`.</span></span>

- <span data-ttu-id="0e8de-167">A propriedade é um tipo de dados `String` e não há restrição sobre o tamanho ou o valor da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0e8de-167">The property is a `String` data type, and there is no constraint on the size or value of the string.</span></span>

- <span data-ttu-id="0e8de-168">Para obter mais informações, consulte [Procedimentos de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0e8de-168">For more information, see [Property Procedures](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).</span></span>

> [!TIP]
> <span data-ttu-id="0e8de-169">Sempre mantenha os campos não constantes particulares.</span><span class="sxs-lookup"><span data-stu-id="0e8de-169">Always keep the non-constant fields private.</span></span> <span data-ttu-id="0e8de-170">Quando você quiser torná-lo público, use uma propriedade em vez disso.</span><span class="sxs-lookup"><span data-stu-id="0e8de-170">When you want to make it public, use a property instead.</span></span>

### <a name="methods"></a><span data-ttu-id="0e8de-171">Métodos</span><span class="sxs-lookup"><span data-stu-id="0e8de-171">Methods</span></span>

<span data-ttu-id="0e8de-172">Um *método* é uma ação que um objeto pode executar.</span><span class="sxs-lookup"><span data-stu-id="0e8de-172">A *method* is an action that an object can perform.</span></span> <span data-ttu-id="0e8de-173">Por exemplo, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> é um método do objeto <xref:System.Windows.Forms.ComboBox> que adiciona uma nova entrada para uma caixa de combinação.</span><span class="sxs-lookup"><span data-stu-id="0e8de-173">For example, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> is a method of the <xref:System.Windows.Forms.ComboBox> object that adds a new entry to a combo box.</span></span>

<span data-ttu-id="0e8de-174">O exemplo a seguir demonstra o método <xref:System.Windows.Forms.Timer.Start%2A> de um objeto <xref:System.Windows.Forms.Timer>.</span><span class="sxs-lookup"><span data-stu-id="0e8de-174">The following example demonstrates the <xref:System.Windows.Forms.Timer.Start%2A> method of a <xref:System.Windows.Forms.Timer> object.</span></span>

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

<span data-ttu-id="0e8de-175">Observe que um método é simplesmente um *procedimento* que é exposto por um objeto.</span><span class="sxs-lookup"><span data-stu-id="0e8de-175">Note that a method is simply a *procedure* that is exposed by an object.</span></span>

<span data-ttu-id="0e8de-176">Para obter mais informações, consulte [Procedimentos](../procedures/index.md).</span><span class="sxs-lookup"><span data-stu-id="0e8de-176">For more information, see [Procedures](../procedures/index.md).</span></span>

### <a name="events"></a><span data-ttu-id="0e8de-177">Eventos</span><span class="sxs-lookup"><span data-stu-id="0e8de-177">Events</span></span>

<span data-ttu-id="0e8de-178">Um evento é uma ação reconhecida por um objeto, como clicar com o mouse ou pressionar uma tecla e para o qual você pode escrever código para responder.</span><span class="sxs-lookup"><span data-stu-id="0e8de-178">An event is an action recognized by an object, such as clicking the mouse or pressing a key, and for which you can write code to respond.</span></span> <span data-ttu-id="0e8de-179">Os eventos podem ocorrer como resultado de uma ação do usuário ou código do programa, ou eles podem ser causados pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="0e8de-179">Events can occur as a result of a user action or program code, or they can be caused by the system.</span></span> <span data-ttu-id="0e8de-180">O código que sinaliza um evento *aciona* o evento e o código que responde a ele *lida* com ele.</span><span class="sxs-lookup"><span data-stu-id="0e8de-180">Code that signals an event is said to *raise* the event, and code that responds to it is said to *handle* it.</span></span>

<span data-ttu-id="0e8de-181">Você também pode desenvolver seus próprios eventos personalizados para serem acionados por seus objetos e manipulados por outros objetos.</span><span class="sxs-lookup"><span data-stu-id="0e8de-181">You can also develop your own custom events to be raised by your objects and handled by other objects.</span></span> <span data-ttu-id="0e8de-182">Para obter mais informações, consulte [Eventos](../events/index.md).</span><span class="sxs-lookup"><span data-stu-id="0e8de-182">For more information, see [Events](../events/index.md).</span></span>

### <a name="instance-members-and-shared-members"></a><span data-ttu-id="0e8de-183">Membros de instância e membros compartilhados</span><span class="sxs-lookup"><span data-stu-id="0e8de-183">Instance members and shared members</span></span>

<span data-ttu-id="0e8de-184">Quando você cria um objeto de uma classe, o resultado é uma instância dessa classe.</span><span class="sxs-lookup"><span data-stu-id="0e8de-184">When you create an object from a class, the result is an instance of that class.</span></span> <span data-ttu-id="0e8de-185">Membros que não são declarados com a palavra-chave [compartilhado](../../../language-reference/modifiers/shared.md) são *membros de instância*, que pertencem estritamente a essa instância em particular.</span><span class="sxs-lookup"><span data-stu-id="0e8de-185">Members that are not declared with the [Shared](../../../language-reference/modifiers/shared.md) keyword are *instance members*, which belong strictly to that particular instance.</span></span> <span data-ttu-id="0e8de-186">Um membro de instância em uma instância é independente do mesmo membro em outra instância da mesma classe.</span><span class="sxs-lookup"><span data-stu-id="0e8de-186">An instance member in one instance is independent of the same member in another instance of the same class.</span></span> <span data-ttu-id="0e8de-187">Por exemplo, uma variável de membro de instância pode ter valores diferentes em instâncias diferentes.</span><span class="sxs-lookup"><span data-stu-id="0e8de-187">An instance member variable, for example, can have different values in different instances.</span></span>

<span data-ttu-id="0e8de-188">Membros declarados com a palavra-chave `Shared` são *membros compartilhados*, que pertencem à classe como um todo e não a qualquer instância específica.</span><span class="sxs-lookup"><span data-stu-id="0e8de-188">Members declared with the `Shared` keyword are *shared members*, which belong to the class as a whole and not to any particular instance.</span></span> <span data-ttu-id="0e8de-189">Um membro compartilhado existe somente uma vez, independentemente de quantas instâncias de sua classe você cria ou mesmo se você não criar nenhuma instância.</span><span class="sxs-lookup"><span data-stu-id="0e8de-189">A shared member exists only once, no matter how many instances of its class you create, or even if you create no instances.</span></span> <span data-ttu-id="0e8de-190">Uma variável de membro compartilhado, por exemplo, tem apenas um valor, que está disponível para todo o código que pode acessar a classe.</span><span class="sxs-lookup"><span data-stu-id="0e8de-190">A shared member variable, for example, has only one value, which is available to all code that can access the class.</span></span>

#### <a name="accessing-non-shared-members"></a><span data-ttu-id="0e8de-191">Acessando membros não compartilhados</span><span class="sxs-lookup"><span data-stu-id="0e8de-191">Accessing non-shared members</span></span>

1. <span data-ttu-id="0e8de-192">Verifique se o objeto foi criado com base na sua classe e atribuído a uma variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="0e8de-192">Make sure the object has been created from its class and assigned to an object variable.</span></span>

   ```vb
   Dim secondForm As New System.Windows.Forms.Form
   ```

2. <span data-ttu-id="0e8de-193">Na instrução que acessa o membro, siga o nome da variável de objeto com o *operador de acesso para membro* ( `.` ) e, em seguida, o nome do membro.</span><span class="sxs-lookup"><span data-stu-id="0e8de-193">In the statement that accesses the member, follow the object variable name with the *member-access operator* (`.`) and then the member name.</span></span>

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a><span data-ttu-id="0e8de-194">Acessando membros compartilhados</span><span class="sxs-lookup"><span data-stu-id="0e8de-194">Accessing shared members</span></span>

- <span data-ttu-id="0e8de-195">Siga o nome da classe com o *operador de acesso para membro* ( `.` ) e, em seguida, o nome do membro.</span><span class="sxs-lookup"><span data-stu-id="0e8de-195">Follow the class name with the *member-access operator* (`.`) and then the member name.</span></span> <span data-ttu-id="0e8de-196">Você sempre deve acessar um membro do objeto `Shared` diretamente pelo nome da classe.</span><span class="sxs-lookup"><span data-stu-id="0e8de-196">You should always access a `Shared` member of the object directly through the class name.</span></span>

   ```vb
   Console.WriteLine("This computer is called " & Environment.MachineName)
   ```

- <span data-ttu-id="0e8de-197">Se já tiver criado um objeto da classe, você também poderá acessar um membro `Shared` pela variável do objeto.</span><span class="sxs-lookup"><span data-stu-id="0e8de-197">If you have already created an object from the class, you can alternatively access a `Shared` member through the object's variable.</span></span>

### <a name="differences-between-classes-and-modules"></a><span data-ttu-id="0e8de-198">Diferenças entre classes e módulos</span><span class="sxs-lookup"><span data-stu-id="0e8de-198">Differences between classes and modules</span></span>

<span data-ttu-id="0e8de-199">A principal diferença entre classes e módulos é que as classes podem ser instanciadas como objetos enquanto os módulos padrão não podem.</span><span class="sxs-lookup"><span data-stu-id="0e8de-199">The main difference between classes and modules is that classes can be instantiated as objects while standard modules cannot.</span></span> <span data-ttu-id="0e8de-200">Como há apenas uma cópia dos dados de um módulo padrão, quando uma parte do seu programa altera uma variável pública em um módulo padrão, qualquer outra parte do programa obtém o mesmo valor se ler essa variável.</span><span class="sxs-lookup"><span data-stu-id="0e8de-200">Because there is only one copy of a standard module's data, when one part of your program changes a public variable in a standard module, any other part of the program gets the same value if it then reads that variable.</span></span> <span data-ttu-id="0e8de-201">Em contraste, os dados do objeto existem separadamente para cada objeto instanciado.</span><span class="sxs-lookup"><span data-stu-id="0e8de-201">In contrast, object data exists separately for each instantiated object.</span></span> <span data-ttu-id="0e8de-202">Outra diferença é que, diferentemente dos módulos padrão, as classes podem implementar interfaces.</span><span class="sxs-lookup"><span data-stu-id="0e8de-202">Another difference is that unlike standard modules, classes can implement interfaces.</span></span> <span data-ttu-id="0e8de-203">Se uma classe for marcada com o modificador [MustInherit](../../../language-reference/modifiers/mustinherit.md) , ela não poderá ser instanciada diretamente.</span><span class="sxs-lookup"><span data-stu-id="0e8de-203">If a class is marked with the [MustInherit](../../../language-reference/modifiers/mustinherit.md) modifier, it can't be instantiated directly.</span></span> <span data-ttu-id="0e8de-204">No entanto, ele ainda é diferente de um módulo, pois pode ser herdado enquanto os módulos não podem ser herdados.</span><span class="sxs-lookup"><span data-stu-id="0e8de-204">However, it's still different from a module as it can be inherited while modules can't be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="0e8de-205">Quando o modificador `Shared` é aplicado a um membro de classe, ele é associado à classe em si em vez de uma determinada instância da classe.</span><span class="sxs-lookup"><span data-stu-id="0e8de-205">When the `Shared` modifier is applied to a class member, it is associated with the class itself instead of a particular instance of the class.</span></span> <span data-ttu-id="0e8de-206">O membro é acessado diretamente usando o nome de classe, do mesmo que os membros do módulo são acessados.</span><span class="sxs-lookup"><span data-stu-id="0e8de-206">The member is accessed directly by using the class name, the same way module members are accessed.</span></span>

<span data-ttu-id="0e8de-207">Classes e módulos também usam escopos diferentes para seus membros.</span><span class="sxs-lookup"><span data-stu-id="0e8de-207">Classes and modules also use different scopes for their members.</span></span> <span data-ttu-id="0e8de-208">Membros definidos em uma classe têm escopo em uma instância específica da classe e existem somente para o tempo de vida do objeto.</span><span class="sxs-lookup"><span data-stu-id="0e8de-208">Members defined within a class are scoped within a specific instance of the class and exist only for the lifetime of the object.</span></span> <span data-ttu-id="0e8de-209">Para acessar membros de classe de fora de uma classe, você deve usar nomes totalmente qualificados no formato de *Objeto*.*Membro*.</span><span class="sxs-lookup"><span data-stu-id="0e8de-209">To access class members from outside a class, you must use fully qualified names in the format of *Object*.*Member*.</span></span>

<span data-ttu-id="0e8de-210">Por outro lado, os membros declarados dentro de um módulo são acessíveis publicamente por padrão e podem ser acessados por qualquer código que pode acessar o módulo.</span><span class="sxs-lookup"><span data-stu-id="0e8de-210">On the other hand, members declared within a module are publicly accessible by default, and can be accessed by any code that can access the module.</span></span> <span data-ttu-id="0e8de-211">Isso significa que variáveis em um módulo padrão são variáveis globais efetivamente porque elas são visíveis de qualquer lugar em seu projeto e existem durante a vida útil do programa.</span><span class="sxs-lookup"><span data-stu-id="0e8de-211">This means that variables in a standard module are effectively global variables because they are visible from anywhere in your project, and they exist for the life of the program.</span></span>

## <a name="reusing-classes-and-objects"></a><span data-ttu-id="0e8de-212">Reutilização de classes e objetos</span><span class="sxs-lookup"><span data-stu-id="0e8de-212">Reusing classes and objects</span></span>

<span data-ttu-id="0e8de-213">Os objetos permitem que você declare variáveis e procedimentos uma vez e reutilize-os quando necessário.</span><span class="sxs-lookup"><span data-stu-id="0e8de-213">Objects let you declare variables and procedures once and then reuse them whenever needed.</span></span> <span data-ttu-id="0e8de-214">Por exemplo, se desejar adicionar um verificador ortográfico a um aplicativo, defina todas as variáveis e funções de suporte para fornecer a funcionalidade de verificação ortográfica.</span><span class="sxs-lookup"><span data-stu-id="0e8de-214">For example, if you want to add a spelling checker to an application you could define all the variables and support functions to provide spell-checking functionality.</span></span> <span data-ttu-id="0e8de-215">Se criar o verificador de ortografia como uma classe, você poderá reutilizá-lo em outros aplicativos adicionando uma referência ao assembly compilado.</span><span class="sxs-lookup"><span data-stu-id="0e8de-215">If you create your spelling checker as a class, you can then reuse it in other applications by adding a reference to the compiled assembly.</span></span> <span data-ttu-id="0e8de-216">Melhor ainda, você poderá diminuir seu trabalho usando uma classe de verificador ortográfico que alguém já desenvolveu.</span><span class="sxs-lookup"><span data-stu-id="0e8de-216">Better yet, you may be able to save yourself some work by using a spelling checker class that someone else has already developed.</span></span>

<span data-ttu-id="0e8de-217">O .NET fornece muitos exemplos de componentes que estão disponíveis para uso.</span><span class="sxs-lookup"><span data-stu-id="0e8de-217">.NET provides many examples of components that are available for use.</span></span> <span data-ttu-id="0e8de-218">O exemplo a seguir usa a classe <xref:System.TimeZone> no namespace <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="0e8de-218">The following example uses the <xref:System.TimeZone> class in the <xref:System> namespace.</span></span> <span data-ttu-id="0e8de-219"><xref:System.TimeZone> fornece membros que permitem que você recupere informações sobre o fuso horário do sistema atual do computador.</span><span class="sxs-lookup"><span data-stu-id="0e8de-219"><xref:System.TimeZone> provides members that allow you to retrieve information about the time zone of the current computer system.</span></span>

```vb
Public Sub ExamineTimeZone()
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone
    Dim s As String = "Current time zone is "
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "
    s &= "different from UTC (coordinated universal time)"
    s &= vbCrLf & "and is currently "
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "
    s &= "on ""summer time""."
    Console.WriteLine(s)
End Sub
```

<span data-ttu-id="0e8de-220">No exemplo anterior, o primeiro [Demonstrativo Esmaecido](../../../language-reference/statements/dim-statement.md) declara uma variável de objeto do tipo <xref:System.TimeZone> e atribui a ele um objeto <xref:System.TimeZone> retornado pela propriedade <xref:System.TimeZone.CurrentTimeZone%2A>.</span><span class="sxs-lookup"><span data-stu-id="0e8de-220">In the preceding example, the first [Dim Statement](../../../language-reference/statements/dim-statement.md) declares an object variable of type <xref:System.TimeZone> and assigns to it a <xref:System.TimeZone> object returned by the <xref:System.TimeZone.CurrentTimeZone%2A> property.</span></span>

## <a name="relationships-among-objects"></a><span data-ttu-id="0e8de-221">Relacionamentos entre objetos</span><span class="sxs-lookup"><span data-stu-id="0e8de-221">Relationships among objects</span></span>

<span data-ttu-id="0e8de-222">Os objetos podem estar relacionados entre si de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="0e8de-222">Objects can be related to each other in several ways.</span></span> <span data-ttu-id="0e8de-223">Os principais tipos de relação são *hierárquico* e *confinamento*.</span><span class="sxs-lookup"><span data-stu-id="0e8de-223">The principal kinds of relationship are *hierarchical* and *containment*.</span></span>

### <a name="hierarchical-relationship"></a><span data-ttu-id="0e8de-224">Relação hierárquica</span><span class="sxs-lookup"><span data-stu-id="0e8de-224">Hierarchical relationship</span></span>

<span data-ttu-id="0e8de-225">Quando classes são derivadas de classes mais fundamentais, elas devem ter um *relacionamento hierárquico*.</span><span class="sxs-lookup"><span data-stu-id="0e8de-225">When classes are derived from more fundamental classes, they are said to have a *hierarchical relationship*.</span></span> <span data-ttu-id="0e8de-226">As hierarquias de classe são úteis para descrever itens que são um subtipo de uma classe mais geral.</span><span class="sxs-lookup"><span data-stu-id="0e8de-226">Class hierarchies are useful when describing items that are a subtype of a more general class.</span></span>

<span data-ttu-id="0e8de-227">No exemplo a seguir, suponha que você deseja definir um tipo especial de <xref:System.Windows.Forms.Button> que atua como um <xref:System.Windows.Forms.Button> normal, mas também expõe um método que reverte as cores de primeiro plano e da tela de fundo.</span><span class="sxs-lookup"><span data-stu-id="0e8de-227">In the following example, suppose you want to define a special kind of <xref:System.Windows.Forms.Button> that acts like a normal <xref:System.Windows.Forms.Button> but also exposes a method that reverses the foreground and background colors.</span></span>

#### <a name="define-a-class-that-is-derived-from-an-already-existing-class"></a><span data-ttu-id="0e8de-228">Definir uma classe que é derivada de uma classe já existente</span><span class="sxs-lookup"><span data-stu-id="0e8de-228">Define a class that is derived from an already existing class</span></span>

1. <span data-ttu-id="0e8de-229">Use uma [instrução Class](../../../language-reference/statements/class-statement.md) para definir uma classe da qual criar o objeto que você precisa.</span><span class="sxs-lookup"><span data-stu-id="0e8de-229">Use a [Class Statement](../../../language-reference/statements/class-statement.md) to define a class from which to create the object you need.</span></span>

   ```vb
   Public Class ReversibleButton
   ```

   <span data-ttu-id="0e8de-230">Certifique-se de que uma instrução `End Class` segue a última linha de código em sua classe.</span><span class="sxs-lookup"><span data-stu-id="0e8de-230">Be sure an `End Class` statement follows the last line of code in your class.</span></span> <span data-ttu-id="0e8de-231">Por padrão, o IDE (ambiente de desenvolvimento integrado) gera automaticamente um `End Class` quando você insere uma instrução `Class`.</span><span class="sxs-lookup"><span data-stu-id="0e8de-231">By default, the integrated development environment (IDE) automatically generates an `End Class` when you enter a `Class` statement.</span></span>

2. <span data-ttu-id="0e8de-232">Siga a instrução `Class` imediatamente com uma [instrução Inherits](../../../language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0e8de-232">Follow the `Class` statement immediately with an [Inherits Statement](../../../language-reference/statements/inherits-statement.md).</span></span> <span data-ttu-id="0e8de-233">Especifique a classe da qual a nova classe deriva.</span><span class="sxs-lookup"><span data-stu-id="0e8de-233">Specify the class from which your new class derives.</span></span>

   ```vb
   Inherits System.Windows.Forms.Button
   ```

   <span data-ttu-id="0e8de-234">A nova classe herda todos os membros definidos pela classe base.</span><span class="sxs-lookup"><span data-stu-id="0e8de-234">Your new class inherits all the members defined by the base class.</span></span>

3. <span data-ttu-id="0e8de-235">Adicione o código para os membros adicionais que sua classe derivada expõe.</span><span class="sxs-lookup"><span data-stu-id="0e8de-235">Add the code for the additional members your derived class exposes.</span></span> <span data-ttu-id="0e8de-236">Por exemplo, você pode adicionar um método `ReverseColors` e sua classe derivada será semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="0e8de-236">For example, you might add a `ReverseColors` method, and your derived class might look as follows:</span></span>

   ```vb
   Public Class ReversibleButton
       Inherits System.Windows.Forms.Button
           Public Sub ReverseColors()
               Dim saveColor As System.Drawing.Color = Me.BackColor
               Me.BackColor = Me.ForeColor
               Me.ForeColor = saveColor
          End Sub
   End Class
   ```

   <span data-ttu-id="0e8de-237">Se você criar um objeto da `ReversibleButton` classe, ele poderá acessar todos os membros da <xref:System.Windows.Forms.Button> classe, bem como o `ReverseColors` método e quaisquer outros novos membros que você definir no `ReversibleButton` .</span><span class="sxs-lookup"><span data-stu-id="0e8de-237">If you create an object from the `ReversibleButton` class, it can access all the members of the <xref:System.Windows.Forms.Button> class, as well as the `ReverseColors` method and any other new members you define in `ReversibleButton`.</span></span>

<span data-ttu-id="0e8de-238">As classes derivadas herdam membros da classe que eles se baseiam, permitindo que você adicione complexidade enquanto progride em uma hierarquia de classe.</span><span class="sxs-lookup"><span data-stu-id="0e8de-238">Derived classes inherit members from the class they are based on, allowing you to add complexity as you progress in a class hierarchy.</span></span> <span data-ttu-id="0e8de-239">Para obter mais informações, consulte [Noções básicas de herança](inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="0e8de-239">For more information, see [Inheritance Basics](inheritance-basics.md).</span></span>

### <a name="compile-the-code"></a><span data-ttu-id="0e8de-240">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="0e8de-240">Compile the code</span></span>

<span data-ttu-id="0e8de-241">Certifique-se de que o compilador pode acessar a classe da qual você pretende derivar sua nova classe.</span><span class="sxs-lookup"><span data-stu-id="0e8de-241">Be sure the compiler can access the class from which you intend to derive your new class.</span></span> <span data-ttu-id="0e8de-242">Isso pode significar qualificar totalmente seu nome, como no exemplo anterior, ou identificar seu namespace em uma [Instrução Imports (Tipo e Namespace .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="0e8de-242">This might mean fully qualifying its name, as in the preceding example, or identifying its namespace in an [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="0e8de-243">Se a classe estiver em um projeto diferente, você precisará adicionar uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="0e8de-243">If the class is in a different project, you might need to add a reference to that project.</span></span> <span data-ttu-id="0e8de-244">Para obter mais informações, consulte [Gerenciando referências em um projeto](/visualstudio/ide/managing-references-in-a-project).</span><span class="sxs-lookup"><span data-stu-id="0e8de-244">For more information, see [Managing references in a project](/visualstudio/ide/managing-references-in-a-project).</span></span>

### <a name="containment-relationship"></a><span data-ttu-id="0e8de-245">Relação de confinamento</span><span class="sxs-lookup"><span data-stu-id="0e8de-245">Containment relationship</span></span>

<span data-ttu-id="0e8de-246">Outro modo de relação dos objetos é a *relação de confinamento*.</span><span class="sxs-lookup"><span data-stu-id="0e8de-246">Another way that objects can be related is a *containment relationship*.</span></span> <span data-ttu-id="0e8de-247">Os objetos de contêiner encapsulam logicamente outros objetos.</span><span class="sxs-lookup"><span data-stu-id="0e8de-247">Container objects logically encapsulate other objects.</span></span> <span data-ttu-id="0e8de-248">Por exemplo, o objeto <xref:System.OperatingSystem> logicamente contém um objeto <xref:System.Version>, que ele retorna por intermédio de sua propriedade <xref:System.OperatingSystem.Version%2A>.</span><span class="sxs-lookup"><span data-stu-id="0e8de-248">For example, the <xref:System.OperatingSystem> object logically contains a <xref:System.Version> object, which it returns through its <xref:System.OperatingSystem.Version%2A> property.</span></span> <span data-ttu-id="0e8de-249">Observe que o objeto de contêiner não contém fisicamente qualquer outro objeto.</span><span class="sxs-lookup"><span data-stu-id="0e8de-249">Note that the container object does not physically contain any other object.</span></span>

#### <a name="collections"></a><span data-ttu-id="0e8de-250">Coleções</span><span class="sxs-lookup"><span data-stu-id="0e8de-250">Collections</span></span>

<span data-ttu-id="0e8de-251">Um tipo específico de confinamento de objeto é representado pelas *coleções*.</span><span class="sxs-lookup"><span data-stu-id="0e8de-251">One particular type of object containment is represented by *collections*.</span></span> <span data-ttu-id="0e8de-252">As coleções são grupos de objetos semelhantes que podem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="0e8de-252">Collections are groups of similar objects that can be enumerated.</span></span> <span data-ttu-id="0e8de-253">Visual Basic dá suporte a uma sintaxe específica no [para cada... Próxima instrução](../../../language-reference/statements/for-each-next-statement.md) que permite que você itere pelos itens de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="0e8de-253">Visual Basic supports a specific syntax in the [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md) that allows you to iterate through the items of a collection.</span></span> <span data-ttu-id="0e8de-254">Além disso, as coleções permitem, com frequência, que você use um <xref:Microsoft.VisualBasic.Collection.Item%2A> para recuperar elementos pelo índice ou associando-os com uma cadeia de caracteres exclusiva.</span><span class="sxs-lookup"><span data-stu-id="0e8de-254">Additionally, collections often allow you to use an <xref:Microsoft.VisualBasic.Collection.Item%2A> to retrieve elements by their index or by associating them with a unique string.</span></span> <span data-ttu-id="0e8de-255">As coleções podem ser mais fáceis de usar que matrizes porque elas permitem que você adicione ou remova itens sem usar índices.</span><span class="sxs-lookup"><span data-stu-id="0e8de-255">Collections can be easier to use than arrays because they allow you to add or remove items without using indexes.</span></span> <span data-ttu-id="0e8de-256">Devido à facilidade de uso, as coleções geralmente são usadas para armazenar formulários e controles.</span><span class="sxs-lookup"><span data-stu-id="0e8de-256">Because of their ease of use, collections are often used to store forms and controls.</span></span>

## <a name="related-topics"></a><span data-ttu-id="0e8de-257">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="0e8de-257">Related topics</span></span>

<span data-ttu-id="0e8de-258">[Walkthrough: definindo classes](walkthrough-defining-classes.md)</span><span class="sxs-lookup"><span data-stu-id="0e8de-258">[Walkthrough: Defining Classes](walkthrough-defining-classes.md)</span></span>\
<span data-ttu-id="0e8de-259">Fornece uma descrição passo a passo de como criar uma classe.</span><span class="sxs-lookup"><span data-stu-id="0e8de-259">Provides a step-by-step description of how to create a class.</span></span>

<span data-ttu-id="0e8de-260">[Propriedades e métodos sobrecarregados](overloaded-properties-and-methods.md)</span><span class="sxs-lookup"><span data-stu-id="0e8de-260">[Overloaded Properties and Methods](overloaded-properties-and-methods.md)</span></span>\
<span data-ttu-id="0e8de-261">Propriedades e métodos sobrecarregados</span><span class="sxs-lookup"><span data-stu-id="0e8de-261">Overloaded Properties and Methods</span></span>

<span data-ttu-id="0e8de-262">[Noções básicas de herança](inheritance-basics.md)</span><span class="sxs-lookup"><span data-stu-id="0e8de-262">[Inheritance Basics](inheritance-basics.md)</span></span>\
<span data-ttu-id="0e8de-263">Aborda modificadores de herança, substituindo métodos e propriedades, MyClass e MyBase.</span><span class="sxs-lookup"><span data-stu-id="0e8de-263">Covers inheritance modifiers, overriding methods and properties, MyClass, and MyBase.</span></span>

<span data-ttu-id="0e8de-264">[Tempo de vida do objeto: como os objetos são criados e destruídos](object-lifetime-how-objects-are-created-and-destroyed.md)</span><span class="sxs-lookup"><span data-stu-id="0e8de-264">[Object Lifetime: How Objects Are Created and Destroyed](object-lifetime-how-objects-are-created-and-destroyed.md)</span></span>\
<span data-ttu-id="0e8de-265">Aborda a criação e descarte de instâncias de classe.</span><span class="sxs-lookup"><span data-stu-id="0e8de-265">Discusses creating and disposing of class instances.</span></span>

<span data-ttu-id="0e8de-266">[Tipos anônimos](anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="0e8de-266">[Anonymous Types](anonymous-types.md)</span></span>\
<span data-ttu-id="0e8de-267">Descreve como criar e usar tipos anônimos, que permitem que você crie objetos sem escrever uma definição de classe para o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="0e8de-267">Describes how to create and use anonymous types, which allow you to create objects without writing a class definition for the data type.</span></span>

<span data-ttu-id="0e8de-268">[Inicializadores de objeto: tipos nomeados e anônimos](object-initializers-named-and-anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="0e8de-268">[Object Initializers: Named and Anonymous Types](object-initializers-named-and-anonymous-types.md)</span></span>\
<span data-ttu-id="0e8de-269">Discute inicializadores de objeto, que são usados para criar instâncias de tipos nomeados e anônimos usando uma única expressão.</span><span class="sxs-lookup"><span data-stu-id="0e8de-269">Discusses object initializers, which are used to create instances of named and anonymous types by using a single expression.</span></span>

<span data-ttu-id="0e8de-270">[Como: inferir nomes e tipos de propriedade em declarações de tipo anônimo](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span><span class="sxs-lookup"><span data-stu-id="0e8de-270">[How to: Infer Property Names and Types in Anonymous Type Declarations](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span></span>\
<span data-ttu-id="0e8de-271">Explica como inferir nomes e tipos de propriedade em declarações de tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="0e8de-271">Explains how to infer property names and types in anonymous type declarations.</span></span> <span data-ttu-id="0e8de-272">Fornece exemplos de inferência de tipos com e sem êxito.</span><span class="sxs-lookup"><span data-stu-id="0e8de-272">Provides examples of successful and unsuccessful inference.</span></span>
