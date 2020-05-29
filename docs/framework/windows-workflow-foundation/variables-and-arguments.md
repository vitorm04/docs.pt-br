---
title: Variáveis e argumentos
description: Este artigo descreve variáveis, que representam o armazenamento de dados e argumentos, que representam o fluxo de dados de/para uma atividade no Workflow Foundation.
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: 5cce9931e9b0a37d5fafbfb84527ffd543a0a50f
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201951"
---
# <a name="variables-and-arguments"></a><span data-ttu-id="061f6-103">Variáveis e argumentos</span><span class="sxs-lookup"><span data-stu-id="061f6-103">Variables and Arguments</span></span>
<span data-ttu-id="061f6-104">No Windows Workflow Foundation (WF), as variáveis representam o armazenamento de dados e os argumentos representam o fluxo de dados para dentro e fora de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="061f6-104">In Windows Workflow Foundation (WF), variables represent the storage of data and arguments represent the flow of data into and out of an activity.</span></span> <span data-ttu-id="061f6-105">Uma atividade tem um conjunto de argumentos e compõem a assinatura de atividade.</span><span class="sxs-lookup"><span data-stu-id="061f6-105">An activity has a set of arguments and they make up the signature of the activity.</span></span> <span data-ttu-id="061f6-106">Além disso, uma atividade pode manter uma lista de variáveis para que um desenvolvedor pode adicionar ou remover variáveis durante o design de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="061f6-106">Additionally, an activity can maintain a list of variables to which a developer can add or remove variables during the design of a workflow.</span></span> <span data-ttu-id="061f6-107">Um argumento é associado usando uma expressão que retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="061f6-107">An argument is bound using an expression that returns a value.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="061f6-108">Variáveis</span><span class="sxs-lookup"><span data-stu-id="061f6-108">Variables</span></span>  
 <span data-ttu-id="061f6-109">As variáveis são local de armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="061f6-109">Variables are storage locations for data.</span></span> <span data-ttu-id="061f6-110">As variáveis são declaradas como parte da definição de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="061f6-110">Variables are declared as part of the definition of a workflow.</span></span> <span data-ttu-id="061f6-111">Variáveis têm em valores em runtime e esses valores são armazenados como parte do estado de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="061f6-111">Variables take on values at runtime and these values are stored as part of the state of a workflow instance.</span></span> <span data-ttu-id="061f6-112">Uma definição variável especifica o tipo de variável e opcionalmente, o nome.</span><span class="sxs-lookup"><span data-stu-id="061f6-112">A variable definition specifies the type of the variable and optionally, the name.</span></span> <span data-ttu-id="061f6-113">O código a seguir mostra como declarar uma variável, atribui um valor que usa uma atividade de <xref:System.Activities.Statements.Assign%601> , e o exibe em seu valor para o console usando uma atividade de <xref:System.Activities.Statements.WriteLine> .</span><span class="sxs-lookup"><span data-stu-id="061f6-113">The following code shows how to declare a variable, assign a value to it using an <xref:System.Activities.Statements.Assign%601> activity, and then display its value to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
```csharp  
// Define a variable named "str" of type string.  
Variable<string> var = new Variable<string>  
{  
    Name = "str"  
};  
  
// Declare the variable within a Sequence, assign  
// a value to it, and then display it.  
Activity wf = new Sequence()  
{  
    Variables = { var },  
    Activities =  
    {  
        new Assign<string>  
        {  
            To = var,  
            Value = "Hello World."  
        },  
        new WriteLine  
        {  
            Text = var  
        }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 <span data-ttu-id="061f6-114">Uma expressão de valor padrão opcionalmente pode ser especificada como parte de uma declaração de variável.</span><span class="sxs-lookup"><span data-stu-id="061f6-114">A default value expression can optionally be specified as part of a variable declaration.</span></span> <span data-ttu-id="061f6-115">Variáveis também podem ter modificadores.</span><span class="sxs-lookup"><span data-stu-id="061f6-115">Variables also can have modifiers.</span></span> <span data-ttu-id="061f6-116">Por exemplo, se um variável é somente leitura no modificador somente leitura de <xref:System.Activities.VariableModifiers> pode ser aplicado.</span><span class="sxs-lookup"><span data-stu-id="061f6-116">For example, if a variable is read-only then the read-only <xref:System.Activities.VariableModifiers> modifier can be applied.</span></span> <span data-ttu-id="061f6-117">No exemplo a seguir, uma variável somente leitura é criado que tem um valor padrão atribuído.</span><span class="sxs-lookup"><span data-stu-id="061f6-117">In the following example, a read-only variable is created that has a default value assigned.</span></span>  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a><span data-ttu-id="061f6-118">Escopo variável</span><span class="sxs-lookup"><span data-stu-id="061f6-118">Variable Scoping</span></span>  
 <span data-ttu-id="061f6-119">O tempo de vida de uma variável em runtime é igual ao tempo de vida de atividade que a declara.</span><span class="sxs-lookup"><span data-stu-id="061f6-119">The lifetime of a variable at runtime is equal to the lifetime of the activity that declares it.</span></span> <span data-ttu-id="061f6-120">Quando uma atividade concluir, suas variáveis são limpados e não podem mais ser referenciados.</span><span class="sxs-lookup"><span data-stu-id="061f6-120">When an activity completes, its variables are cleaned up and can no longer be referenced.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="061f6-121">Argumentos</span><span class="sxs-lookup"><span data-stu-id="061f6-121">Arguments</span></span>  
 <span data-ttu-id="061f6-122">Os autores de atividade usam argumentos para definir os fluxos de dados de maneira e fora de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="061f6-122">Activity authors use arguments to define the way data flows into and out of an activity.</span></span> <span data-ttu-id="061f6-123">Cada argumento possui uma direção especificada: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, ou <xref:System.Activities.ArgumentDirection.InOut>.</span><span class="sxs-lookup"><span data-stu-id="061f6-123">Each argument has a specified direction: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, or <xref:System.Activities.ArgumentDirection.InOut>.</span></span>  
  
 <span data-ttu-id="061f6-124">O runtime de fluxo de trabalho faz as seguintes garantias sobre o controle de tempo de movimentação de dados de e para atividades:</span><span class="sxs-lookup"><span data-stu-id="061f6-124">The workflow runtime makes the following guarantees about the timing of data movement into and out of activities:</span></span>  
  
1. <span data-ttu-id="061f6-125">Quando uma atividade se inicia, os valores dos argumentos de entrada e de arquivos entrada/saída são calculados.</span><span class="sxs-lookup"><span data-stu-id="061f6-125">When an activity starts executing, the values of all of its input and input/output arguments are calculated.</span></span> <span data-ttu-id="061f6-126">Por exemplo, independentemente de <xref:System.Activities.Argument.Get%2A> quando é chamado, o valor retornado é calculado no runtime antes da chamada de `Execute`.</span><span class="sxs-lookup"><span data-stu-id="061f6-126">For example, regardless of when <xref:System.Activities.Argument.Get%2A> is called, the value returned is the one calculated by the runtime prior to its invocation of `Execute`.</span></span>  
  
2. <span data-ttu-id="061f6-127">Quando <xref:System.Activities.InOutArgument%601.Set%2A> é chamado, o runtime define o valor imediatamente.</span><span class="sxs-lookup"><span data-stu-id="061f6-127">When <xref:System.Activities.InOutArgument%601.Set%2A> is called, the runtime sets the value immediately.</span></span>  
  
3. <span data-ttu-id="061f6-128">Os argumentos podem opcionalmente ter seu <xref:System.Activities.Argument.EvaluationOrder%2A> especificado.</span><span class="sxs-lookup"><span data-stu-id="061f6-128">Arguments can optionally have their <xref:System.Activities.Argument.EvaluationOrder%2A> specified.</span></span> <span data-ttu-id="061f6-129"><xref:System.Activities.Argument.EvaluationOrder%2A> é um valor com base zero que especifica a ordem em que o argumento é avaliado.</span><span class="sxs-lookup"><span data-stu-id="061f6-129"><xref:System.Activities.Argument.EvaluationOrder%2A> is a zero-based value that specifies the order in which the argument is evaluated.</span></span> <span data-ttu-id="061f6-130">Por padrão, a ordem de classificação de argumento é especificado e não é igual ao valor de <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> .</span><span class="sxs-lookup"><span data-stu-id="061f6-130">By default, the evaluation order of the argument is unspecified and is equal to the <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> value.</span></span> <span data-ttu-id="061f6-131">Definir <xref:System.Activities.Argument.EvaluationOrder%2A> para um valor maior ou igual a zero para especificar uma ordem de classificação para esse argumento.</span><span class="sxs-lookup"><span data-stu-id="061f6-131">Set <xref:System.Activities.Argument.EvaluationOrder%2A> to a value greater or equal to zero to specify an evaluation order for this argument.</span></span> <span data-ttu-id="061f6-132">Windows Workflow Foundation avalia argumentos com uma ordem de avaliação especificada em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="061f6-132">Windows Workflow Foundation evaluates arguments with a specified evaluation order in ascending order.</span></span> <span data-ttu-id="061f6-133">Observe que os argumentos com uma ordem não-especificada de avaliação são avaliados antes que esses especificado com uma ordem de classificação.</span><span class="sxs-lookup"><span data-stu-id="061f6-133">Note that arguments with an unspecified evaluation order are evaluated before those with a specified evaluation order.</span></span>  
  
 <span data-ttu-id="061f6-134">Um autor de atividade pode usar um mecanismo fortemente tipado para expor seus argumentos.</span><span class="sxs-lookup"><span data-stu-id="061f6-134">An activity author can use a strongly typed mechanism for exposing its arguments.</span></span> <span data-ttu-id="061f6-135">Isso é feito declarando propriedades do tipo <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, e <xref:System.Activities.InOutArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="061f6-135">This is accomplished by declaring properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="061f6-136">Isso permite que um autor de atividade estabeleça um contrato específico sobre os dados que vão e fora de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="061f6-136">This allows an activity author to establish a specific contract about the data going into and out of an activity.</span></span>  
  
### <a name="defining-the-arguments-on-an-activity"></a><span data-ttu-id="061f6-137">Definindo os argumentos em uma atividade</span><span class="sxs-lookup"><span data-stu-id="061f6-137">Defining the Arguments on an Activity</span></span>  
 <span data-ttu-id="061f6-138">Os argumentos podem ser definidos em uma atividade especificando propriedades do tipo <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, e <xref:System.Activities.InOutArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="061f6-138">Arguments can be defined on an activity by specifying properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="061f6-139">O código a seguir mostra como definir os argumentos para uma atividade de `Prompt` que reduz uma cadeia de caracteres para exibir ao usuário e retorna uma cadeia de caracteres que contém a resposta do usuário.</span><span class="sxs-lookup"><span data-stu-id="061f6-139">The following code shows how to define the arguments for a `Prompt` activity that takes in a string to display to the user and returns a string that contains the user's response.</span></span>  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="061f6-140">As atividades que retornam um valor único podem derivar de <xref:System.Activities.Activity%601>, de <xref:System.Activities.NativeActivity%601>, ou de <xref:System.Activities.CodeActivity%601>.</span><span class="sxs-lookup"><span data-stu-id="061f6-140">Activities that return a single value can derive from <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, or <xref:System.Activities.CodeActivity%601>.</span></span> <span data-ttu-id="061f6-141">Essas atividades têm <xref:System.Activities.OutArgument%601> bem definido chamado <xref:System.Activities.Activity%601.Result%2A> que contém o valor de retorno da atividade.</span><span class="sxs-lookup"><span data-stu-id="061f6-141">These activities have a well-defined <xref:System.Activities.OutArgument%601> named <xref:System.Activities.Activity%601.Result%2A> that contains the return value of the activity.</span></span>  
  
### <a name="using-variables-and-arguments-in-workflows"></a><span data-ttu-id="061f6-142">Usando variáveis e argumentos em fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="061f6-142">Using Variables and Arguments in Workflows</span></span>  
 <span data-ttu-id="061f6-143">O exemplo a seguir mostra como variáveis e os argumentos são usados em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="061f6-143">The following example shows how variables and arguments are used in a workflow.</span></span> <span data-ttu-id="061f6-144">O fluxo de trabalho é uma sequência que declara três variáveis: `var1`, `var2`, e `var3`.</span><span class="sxs-lookup"><span data-stu-id="061f6-144">The workflow is a sequence that declares three variables: `var1`, `var2`, and `var3`.</span></span> <span data-ttu-id="061f6-145">A primeira atividade no fluxo de trabalho é uma atividade de `Assign` que atribui o valor da variável `var1``var2`variável.</span><span class="sxs-lookup"><span data-stu-id="061f6-145">The first activity in the workflow is an `Assign` activity that assigns the value of variable `var1` to the variable `var2`.</span></span> <span data-ttu-id="061f6-146">Isso é seguido por uma atividade de `WriteLine` que imprimir o valor da variável de `var2` .</span><span class="sxs-lookup"><span data-stu-id="061f6-146">This is followed by a `WriteLine` activity that prints the value of the `var2` variable.</span></span> <span data-ttu-id="061f6-147">Em seguida é outra atividade de `Assign` que atribui o valor da variável `var2``var3`variável.</span><span class="sxs-lookup"><span data-stu-id="061f6-147">Next is another `Assign` activity that assigns the value of variable `var2` to the variable `var3`.</span></span> <span data-ttu-id="061f6-148">Finalmente há outra atividade de `WriteLine` que imprimir o valor da variável de `var3` .</span><span class="sxs-lookup"><span data-stu-id="061f6-148">Finally there is another `WriteLine` activity that prints the value of the `var3` variable.</span></span> <span data-ttu-id="061f6-149">A primeira atividade de `Assign` usa `InArgument<string>` e `OutArgument<string>` objetos que representa explicitamente as associações para os argumentos de atividade.</span><span class="sxs-lookup"><span data-stu-id="061f6-149">The first `Assign` activity uses `InArgument<string>` and `OutArgument<string>` objects that explicitly represent the bindings for the activity's arguments.</span></span> <span data-ttu-id="061f6-150">`InArgument<string>` é usado para <xref:System.Activities.Statements.Assign.Value%2A> porque o valor é fluxo na atividade de <xref:System.Activities.Statements.Assign%601> através de seu argumento de <xref:System.Activities.Statements.Assign.Value%2A> , e `OutArgument<string>` é usado para <xref:System.Activities.Statements.Assign.To%2A> porque o valor de fluxo está fora do argumento de <xref:System.Activities.Statements.Assign.To%2A> na variável.</span><span class="sxs-lookup"><span data-stu-id="061f6-150">`InArgument<string>` is used for <xref:System.Activities.Statements.Assign.Value%2A> because the value is flowing into the <xref:System.Activities.Statements.Assign%601> activity through its <xref:System.Activities.Statements.Assign.Value%2A> argument, and `OutArgument<string>` is used for <xref:System.Activities.Statements.Assign.To%2A> because the value is flowing out of the <xref:System.Activities.Statements.Assign.To%2A> argument into the variable.</span></span> <span data-ttu-id="061f6-151">A segunda atividade de `Assign` realiza a mesma coisa com mais sintaxe compacta mas equivalente que usa conversões implícitas.</span><span class="sxs-lookup"><span data-stu-id="061f6-151">The second `Assign` activity accomplishes the same thing with more compact but equivalent syntax that uses implicit casts.</span></span> <span data-ttu-id="061f6-152">As atividades de `WriteLine` também usam a sintaxe compacta.</span><span class="sxs-lookup"><span data-stu-id="061f6-152">The `WriteLine` activities also use the compact syntax.</span></span>  
  
```csharp  
// Declare three variables; the first one is given an initial value.  
Variable<string> var1 = new Variable<string>()  
{  
    Default = "one"  
};  
Variable<string> var2 = new Variable<string>();  
Variable<string> var3 = new Variable<string>();  
  
// Define the workflow  
Activity wf = new Sequence  
{  
    Variables = { var1, var2, var3 },  
    Activities =
    {  
        new Assign<string>()  
        {  
            Value = new InArgument<string>(var1),  
            To = new OutArgument<string>(var2)  
        },  
        new WriteLine() { Text = var2 },  
        new Assign<string>()  
        {  
            Value = var2,  
            To = var3  
        },  
        new WriteLine() { Text = var3 }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a><span data-ttu-id="061f6-153">Usando variáveis e argumentos código com base em atividades</span><span class="sxs-lookup"><span data-stu-id="061f6-153">Using Variables and Arguments in Code-Based Activities</span></span>  
 <span data-ttu-id="061f6-154">Os exemplos anteriores mostram como usar argumentos e variáveis em fluxos de trabalho e em atividades declarativas.</span><span class="sxs-lookup"><span data-stu-id="061f6-154">The previous examples show how to use arguments and variables in workflows and declarative activities.</span></span> <span data-ttu-id="061f6-155">Os argumentos e variáveis também são usados em atividades código com base.</span><span class="sxs-lookup"><span data-stu-id="061f6-155">Arguments and variables are also used in code-based activities.</span></span> <span data-ttu-id="061f6-156">Conceitualmente o uso é muito semelhante.</span><span class="sxs-lookup"><span data-stu-id="061f6-156">Conceptually the usage is very similar.</span></span> <span data-ttu-id="061f6-157">Variáveis representam o armazenamento de dados dentro da atividade, e os argumentos representam o fluxo de dados ou fora da atividade, e são associados pelo autor de fluxo de trabalho a outras variáveis ou argumentos no fluxo de trabalho que representam de onde os fluxos de dados ou a.</span><span class="sxs-lookup"><span data-stu-id="061f6-157">Variables represent data storage within the activity, and arguments represent the flow of data into or out of the activity, and are bound by the workflow author to other variables or arguments in the workflow that represent where the data flows to or from.</span></span> <span data-ttu-id="061f6-158">Para obter ou definir o valor de uma variável ou um argumento em uma atividade, um contexto de atividade deve ser usado que representa o ambiente de execução atual da atividade.</span><span class="sxs-lookup"><span data-stu-id="061f6-158">To get or set the value of a variable or argument in an activity, an activity context must be used that represents the current execution environment of the activity.</span></span> <span data-ttu-id="061f6-159">Isso é passado para o método de <xref:System.Activities.CodeActivity%601.Execute%2A> de atividade em runtime de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="061f6-159">This is passed into the <xref:System.Activities.CodeActivity%601.Execute%2A> method of the activity by the workflow runtime.</span></span> <span data-ttu-id="061f6-160">Nesse exemplo, uma atividade de `Add` personalizado é definida que possui dois argumentos de <xref:System.Activities.ArgumentDirection.In> .</span><span class="sxs-lookup"><span data-stu-id="061f6-160">In this example, a custom `Add` activity is defined that has two <xref:System.Activities.ArgumentDirection.In> arguments.</span></span> <span data-ttu-id="061f6-161">Para acessar o valor de argumentos, o método de <xref:System.Activities.Argument.Get%2A> é usado e o contexto que foi passado em runtime de fluxo de trabalho é usado.</span><span class="sxs-lookup"><span data-stu-id="061f6-161">To access the value of the arguments, the <xref:System.Activities.Argument.Get%2A> method is used and the context that was passed in by the workflow runtime is used.</span></span>  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 <span data-ttu-id="061f6-162">Para obter mais informações sobre como trabalhar com argumentos, variáveis e expressões no código, consulte criação de fluxos de trabalho [, atividades e expressões usando código imperativo](authoring-workflows-activities-and-expressions-using-imperative-code.md) e [argumentos necessários e grupos de sobrecarga](required-arguments-and-overload-groups.md).</span><span class="sxs-lookup"><span data-stu-id="061f6-162">For more information about working with arguments, variables, and expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md) and [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>
