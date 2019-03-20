---
title: Criar com tipos de referência que permitem valor nulo
description: Este tutorial avançado fornece uma introdução aos tipos de referência que permitem valor nulo. Você aprenderá a expressar sua intenção de design quando os valores de referência puderem ser nulos e ter o compilador obrigatório quando eles não puderem ser nulos.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: 7f071dedd2e7a611b08a3fd37a7c0b3182be049b
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "57846578"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="bb87e-104">Tutorial: Expressar sua intenção de design mais claramente com tipos de referência que permitem valor nulo e tipos de referência que não permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="bb87e-104">Tutorial: Express your design intent more clearly with nullable and non-nullable reference types</span></span>

<span data-ttu-id="bb87e-105">O C# 8 introduz **tipos de referência que permitem valor nulo** que complementam os tipos de referência da mesma maneira que os tipos de valor que permitem valor nulo complementam os tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="bb87e-105">C# 8 introduces **nullable reference types**, which complement reference types the same way nullable value types complement value types.</span></span> <span data-ttu-id="bb87e-106">Para declarar que uma variável é um **tipo de referência que permite valor nulo**, anexe um `?` ao tipo.</span><span class="sxs-lookup"><span data-stu-id="bb87e-106">You declare a variable to be a **nullable reference type** by appending a `?` to the type.</span></span> <span data-ttu-id="bb87e-107">Por exemplo, `string?` representa uma `string` que permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bb87e-107">For example, `string?` represents a nullable `string`.</span></span> <span data-ttu-id="bb87e-108">Você pode usar esses novos tipos para expressar mais claramente sua intenção de design: algumas variáveis *devem sempre ter um valor*, outras *podem ter um valor* ausente.</span><span class="sxs-lookup"><span data-stu-id="bb87e-108">You can use these new types to more clearly express your design intent: some variables *must always have a value*, others *may be missing a value*.</span></span>

<span data-ttu-id="bb87e-109">Neste tutorial, você aprenderá a:</span><span class="sxs-lookup"><span data-stu-id="bb87e-109">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="bb87e-110">Incorporar tipos de referência que permitem valores nulos e tipos de referência que não permitem valores nulos aos designs</span><span class="sxs-lookup"><span data-stu-id="bb87e-110">Incorporate nullable and non-nullable reference types into your designs</span></span>
> * <span data-ttu-id="bb87e-111">Habilitar verificações de tipo de referência que permitem valor nulo em todo o código.</span><span class="sxs-lookup"><span data-stu-id="bb87e-111">Enable nullable reference type checks throughout your code.</span></span>
> * <span data-ttu-id="bb87e-112">Gravar código em locais onde o compilador imponha essas decisões de design.</span><span class="sxs-lookup"><span data-stu-id="bb87e-112">Write code where the compiler enforces those design decisions.</span></span>
> * <span data-ttu-id="bb87e-113">Usar o recurso de referência que permite valor nulo em seus próprios designs</span><span class="sxs-lookup"><span data-stu-id="bb87e-113">Use the nullable reference feature in your own designs</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bb87e-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="bb87e-114">Prerequisites</span></span>

<span data-ttu-id="bb87e-115">Você precisará configurar seu computador para executar o .NET Core, incluindo o compilador beta do C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="bb87e-115">You'll need to set up your machine to run .NET Core, including the C# 8.0 beta compiler.</span></span> <span data-ttu-id="bb87e-116">O compilador beta do C# 8 está disponível com o [Visual Studio 2019 versão prévia 4](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+preview) ou o [.NET Core 3.0 versão prévia 3](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="bb87e-116">The C# 8 beta compiler is available with [Visual Studio 2019 preview 4](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+preview), or [.NET Core 3.0 preview 3](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="bb87e-117">Este tutorial pressupõe que você esteja familiarizado com o C# e .NET, incluindo o Visual Studio ou a CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bb87e-117">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="incorporate-nullable-reference-types-into-your-designs"></a><span data-ttu-id="bb87e-118">Incorporar tipos de referência que permitem valor nulo aos designs</span><span class="sxs-lookup"><span data-stu-id="bb87e-118">Incorporate nullable reference types into your designs</span></span>

<span data-ttu-id="bb87e-119">Neste tutorial, você criará uma biblioteca para modelar a executar uma pesquisa.</span><span class="sxs-lookup"><span data-stu-id="bb87e-119">In this tutorial, you'll build a library that models running a survey.</span></span> <span data-ttu-id="bb87e-120">O código usa tipos de referência que permitem valores nulos e tipos de referência que não permitem valores nulos para representar os conceitos do mundo real.</span><span class="sxs-lookup"><span data-stu-id="bb87e-120">The code uses both nullable reference types and non-nullable reference types to represent the real-world concepts.</span></span> <span data-ttu-id="bb87e-121">As perguntas da pesquisa nunca podem ser um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bb87e-121">The survey questions can never be null.</span></span> <span data-ttu-id="bb87e-122">Um entrevistado pode optar por não responder a uma pergunta.</span><span class="sxs-lookup"><span data-stu-id="bb87e-122">A respondent might prefer not to answer a question.</span></span> <span data-ttu-id="bb87e-123">As respostas devem ser valores nulos nesse caso.</span><span class="sxs-lookup"><span data-stu-id="bb87e-123">The responses might be null in this case.</span></span>

<span data-ttu-id="bb87e-124">O código que você gravará para este exemplo expressa essa intenção e o compilador a aplica.</span><span class="sxs-lookup"><span data-stu-id="bb87e-124">The code you'll write for this sample expresses that intent, and the compiler enforces that intent.</span></span>

## <a name="create-the-application-and-enable-nullable-reference-types"></a><span data-ttu-id="bb87e-125">Criar o aplicativo e habilitar os tipos de referência que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="bb87e-125">Create the application and enable nullable reference types</span></span>

<span data-ttu-id="bb87e-126">Crie um novo aplicativo de console no Visual Studio ou na linha de comando usando `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="bb87e-126">Create a new console application either in Visual Studio or from the command line using `dotnet new console`.</span></span> <span data-ttu-id="bb87e-127">Dê o nome `NullableIntroduction` ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bb87e-127">Name the application `NullableIntroduction`.</span></span> <span data-ttu-id="bb87e-128">Depois de criar o aplicativo, será preciso ativar os recursos beta do C# 8.</span><span class="sxs-lookup"><span data-stu-id="bb87e-128">Once you've created the application, you'll need to enable C# 8 beta features.</span></span> <span data-ttu-id="bb87e-129">Abra o arquivo `csproj` e adicione um elemento `LangVersion` ao elemento `PropertyGroup`.</span><span class="sxs-lookup"><span data-stu-id="bb87e-129">Open the `csproj` file and add a `LangVersion` element to the `PropertyGroup` element.</span></span> <span data-ttu-id="bb87e-130">Você deve aceitar o recurso dos **tipos de referência que permitem valor nulo**, mesmo em projetos do C# 8.</span><span class="sxs-lookup"><span data-stu-id="bb87e-130">You must opt into the **nullable reference types** feature, even in C# 8 projects.</span></span> <span data-ttu-id="bb87e-131">Isso porque, quando o recurso é ativado, as declarações de variáveis de referência existentes tornam-se **tipos de referência que não permitem valor nulo**.</span><span class="sxs-lookup"><span data-stu-id="bb87e-131">That's because once the feature is turned on, existing reference variable declarations become **non-nullable reference types**.</span></span> <span data-ttu-id="bb87e-132">Embora essa decisão auxilie na localização de problemas nos quais o código existente pode não ter verificações de valores nulos adequadas, ela pode não refletir com precisão a intenção original do design.</span><span class="sxs-lookup"><span data-stu-id="bb87e-132">While that decision will help find issues where existing code may not have proper null-checks, it may not accurately reflect your original design intent.</span></span> <span data-ttu-id="bb87e-133">Ative o recurso definindo o elemento `NullableContextOptions` como `enable`:</span><span class="sxs-lookup"><span data-stu-id="bb87e-133">You turn on the feature by setting the `NullableContextOptions` element to `enable`:</span></span>

```xml
<LangVersion>8.0</LangVersion>
<NullableContextOptions>enable</NullableContextOptions>
```

> [!NOTE]
> <span data-ttu-id="bb87e-134">Quando C# 8 for lançado (não no modo de versão prévia), o elemento `NullableContextOptions` será adicionado por novos modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="bb87e-134">When C# 8 is released (not in preview mode), the `NullableContextOptions` element will be added by new project templates.</span></span> <span data-ttu-id="bb87e-135">Até lá, será necessário adicioná-lo manualmente.</span><span class="sxs-lookup"><span data-stu-id="bb87e-135">Until then, you'll need to add it manually.</span></span>


### <a name="design-the-types-for-the-application"></a><span data-ttu-id="bb87e-136">Criar os tipos para o aplicativo</span><span class="sxs-lookup"><span data-stu-id="bb87e-136">Design the types for the application</span></span>

<span data-ttu-id="bb87e-137">Este aplicativo de pesquisa requer a criação de várias classes:</span><span class="sxs-lookup"><span data-stu-id="bb87e-137">This survey application requires creating a number of classes:</span></span>

- <span data-ttu-id="bb87e-138">Uma classe que modela a lista de perguntas.</span><span class="sxs-lookup"><span data-stu-id="bb87e-138">A class that models the list of questions.</span></span>
- <span data-ttu-id="bb87e-139">Uma classe que modela uma lista de pessoas contatadas para a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="bb87e-139">A class that models a list of people contacted for the survey.</span></span>
- <span data-ttu-id="bb87e-140">Uma classe que modela as respostas de uma pessoa que participou da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="bb87e-140">A class that models the answers from a person that took the survey.</span></span>

<span data-ttu-id="bb87e-141">Esses tipos usarão os tipos de referência que permitem valor nulo e tipos de referência que não permitem valor nulo para expressar quais membros são obrigatórios e quais são opcionais.</span><span class="sxs-lookup"><span data-stu-id="bb87e-141">These types will make use of both nullable and non-nullable reference types to express which members are required and which members are optional.</span></span> <span data-ttu-id="bb87e-142">Os tipos de referência que permitem valor nulo informam claramente essa intenção de design:</span><span class="sxs-lookup"><span data-stu-id="bb87e-142">Nullable reference types communicate that design intent clearly:</span></span>

- <span data-ttu-id="bb87e-143">As perguntas que fazem parte da pesquisa nunca podem ser nulas: Não faz sentido fazer uma pergunta vazia.</span><span class="sxs-lookup"><span data-stu-id="bb87e-143">The questions that are part of the survey can never be null: It makes no sense to ask an empty question.</span></span>
- <span data-ttu-id="bb87e-144">Os entrevistados nunca poderão ser nulos.</span><span class="sxs-lookup"><span data-stu-id="bb87e-144">The respondents can never be null.</span></span> <span data-ttu-id="bb87e-145">Convém controlar as pessoas contatadas, mesmo os entrevistados que se recusaram a participar.</span><span class="sxs-lookup"><span data-stu-id="bb87e-145">You'll want to track people you contacted, even respondents that declined to participate.</span></span>
- <span data-ttu-id="bb87e-146">Qualquer resposta a uma pergunta pode ser um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bb87e-146">Any response to a question may be null.</span></span> <span data-ttu-id="bb87e-147">Os entrevistados podem se recusar a responder a algumas ou a todas as perguntas.</span><span class="sxs-lookup"><span data-stu-id="bb87e-147">Respondents can decline to answer some or all questions.</span></span>

<span data-ttu-id="bb87e-148">Se já tiver programado em C#, pode estar tão acostumado a fazer referência a tipos que permitem valor nulo que poderá ter perdido outras oportunidades de declarar instâncias que não permitem valor nulo:</span><span class="sxs-lookup"><span data-stu-id="bb87e-148">If you've programmed in C#, you may be so accustomed to reference types that allow null values that you may have missed other opportunities to declare non-nullable instances:</span></span>

- <span data-ttu-id="bb87e-149">O conjunto de perguntas não deve permitir um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bb87e-149">The collection of questions should be non-nullable.</span></span>
- <span data-ttu-id="bb87e-150">O conjunto de entrevistados não deve permitir um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bb87e-150">The collection of respondents should be non-nullable.</span></span>

<span data-ttu-id="bb87e-151">Conforme grava o código, você verá que um tipo de referência que não permite valor nulo como padrão para referências evita erros comuns que podem levar a exceções de referências que permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bb87e-151">As you write the code, you'll see that a non-nullable reference type as the default for references avoids common mistakes that could lead to null reference exceptions.</span></span> <span data-ttu-id="bb87e-152">Uma das lições retirada deste tutorial é que você tomou decisões sobre quais variáveis poderiam ou não permitir valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bb87e-152">One lesson from this tutorial is that you made decisions about which variables could or could not be null.</span></span> <span data-ttu-id="bb87e-153">O idioma não forneceu sintaxe para expressar essas decisões.</span><span class="sxs-lookup"><span data-stu-id="bb87e-153">The language didn't provide syntax to express those decisions.</span></span> <span data-ttu-id="bb87e-154">Agora ele já fornece.</span><span class="sxs-lookup"><span data-stu-id="bb87e-154">Now it does.</span></span>

<span data-ttu-id="bb87e-155">O aplicativo que será compilado seguirá as etapas a seguir:</span><span class="sxs-lookup"><span data-stu-id="bb87e-155">The app you'll build will do the following steps:</span></span>

1. <span data-ttu-id="bb87e-156">Criar uma pesquisa e adicionar perguntas a ela.</span><span class="sxs-lookup"><span data-stu-id="bb87e-156">Create a survey and add questions to it.</span></span>
1. <span data-ttu-id="bb87e-157">Criar um conjunto pseudoaleatório de entrevistados para a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="bb87e-157">Create a pseudo-random set of respondents for the survey.</span></span>
1. <span data-ttu-id="bb87e-158">Entre em contato com os entrevistados até que o tamanho da pesquisa preenchida atinja o número da meta.</span><span class="sxs-lookup"><span data-stu-id="bb87e-158">Contact respondents until the completed survey size reaches the goal number.</span></span>
1. <span data-ttu-id="bb87e-159">Anote estatísticas importantes sobre as respostas da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="bb87e-159">Write out important statistics on the survey responses.</span></span>

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a><span data-ttu-id="bb87e-160">Criar a pesquisa com tipos que permitem valor nulo e tipos que não permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="bb87e-160">Build the survey with nullable and non-nullable types</span></span>

<span data-ttu-id="bb87e-161">O primeiro código gravado criará a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="bb87e-161">The first code you'll write creates the survey.</span></span> <span data-ttu-id="bb87e-162">Você escreverá classes para modelar uma pergunta da pesquisa e uma execução da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="bb87e-162">You'll write classes to model a survey question and a survey run.</span></span> <span data-ttu-id="bb87e-163">A pesquisa tem três tipos de perguntas, diferenciadas pelo formato da resposta: Respostas Sim/Não, respostas de números e respostas de texto.</span><span class="sxs-lookup"><span data-stu-id="bb87e-163">Your survey has three types of questions, distinguished by the format of the answer: Yes/No answers, number answers, and text answers.</span></span> <span data-ttu-id="bb87e-164">Crie uma classe `public` `SurveyQuestion`:</span><span class="sxs-lookup"><span data-stu-id="bb87e-164">Create a `public` `SurveyQuestion` class:</span></span>

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

<span data-ttu-id="bb87e-165">O compilador interpreta cada declaração de variável de tipo de referência como um tipo de referência **não anulável** para código em um contexto que permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bb87e-165">The compiler interprets every reference type variable declaration as a **non-nullable** reference type for code in a nullable enabled context.</span></span> <span data-ttu-id="bb87e-166">Para ver seu primeiro aviso, adicione propriedades ao texto da pergunta e tipo de pergunta, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="bb87e-166">You can see your first warning by adding properties for the question text and the type of question, as shown in the following code:</span></span>

```csharp
namespace NullableIntroduction
{
    public enum QuestionType
    {
        YesNo,
        Number,
        Text
    }

    public class SurveyQuestion
    {
        public string QuestionText { get; }
        public QuestionType TypeOfQuestion { get; }
    }
}
```

<span data-ttu-id="bb87e-167">Como você não inicializou `QuestionText`, o compilador emitirá um aviso informando que uma propriedade que não permite valor nulo não foi inicializada.</span><span class="sxs-lookup"><span data-stu-id="bb87e-167">Because you haven't initialized `QuestionText`, the compiler issues a warning that a non-nullable property hasn't been initialized.</span></span> <span data-ttu-id="bb87e-168">Seu design exige que o texto da pergunta não seja um valor nulo, portanto, você inclui um construtor para inicializá-lo e o valor `QuestionType` também.</span><span class="sxs-lookup"><span data-stu-id="bb87e-168">Your design requires the question text to be non-null, so you add a constructor to initialize it and the `QuestionType` value as well.</span></span> <span data-ttu-id="bb87e-169">A definição da classe concluída se parece com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="bb87e-169">The finished class definition looks like the following code:</span></span>

[!code-csharp[DefineQuestion](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

<span data-ttu-id="bb87e-170">A adição do construtor removerá o aviso.</span><span class="sxs-lookup"><span data-stu-id="bb87e-170">Adding the constructor removes the warning.</span></span> <span data-ttu-id="bb87e-171">O argumento do construtor também é um tipo de referência que não permite valor nulo, portanto, o compilador não emite avisos.</span><span class="sxs-lookup"><span data-stu-id="bb87e-171">The constructor argument is also a non-nullable reference type, so the compiler doesn't issue any warnings.</span></span>

<span data-ttu-id="bb87e-172">Em seguida, crie uma classe `public` chamada `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="bb87e-172">Next, create a `public` class named `SurveyRun`.</span></span> <span data-ttu-id="bb87e-173">Esta classe contém uma lista de métodos e objetos `SurveyQuestion` para adicionar perguntas à pesquisa, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="bb87e-173">This class contains a list of `SurveyQuestion` objects and methods to add questions to the survey, as shown in the following code:</span></span>

```csharp
using System.Collections.Generic;

namespace NullableIntroduction
{
    public class SurveyRun
    {
        private List<SurveyQuestion> surveyQuestions = new List<SurveyQuestion>();

        public void AddQuestion(QuestionType type, string question) =>
            AddQuestion(new SurveyQuestion(type, question));
        public void AddQuestion(SurveyQuestion surveyQuestion) => surveyQuestions.Add(surveyQuestion);
    }
}
```

<span data-ttu-id="bb87e-174">Como foi feito anteriormente, você deve inicializar o objeto de lista com um valor não nulo ou o compilador emitirá um aviso.</span><span class="sxs-lookup"><span data-stu-id="bb87e-174">As before, you must initialize the list object to a non-null value or the compiler issues a warning.</span></span> <span data-ttu-id="bb87e-175">Não há verificações de nulo na segunda sobrecarga de `AddQuestion` porque elas não são necessárias: Você declarou essa variável como não permitindo valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bb87e-175">There are no null checks in the second overload of `AddQuestion` because they aren't needed: You've declared that variable to be non-nullable.</span></span> <span data-ttu-id="bb87e-176">Seu valor não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="bb87e-176">Its value can't be `null`.</span></span>

<span data-ttu-id="bb87e-177">Alterne para `Program.cs` no editor e substitua o conteúdo de `Main` pelas seguintes linhas de código:</span><span class="sxs-lookup"><span data-stu-id="bb87e-177">Switch to `Program.cs` in your editor and replace the contents of `Main` with the following lines of code:</span></span>

[!code-csharp[AddQuestions](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

<span data-ttu-id="bb87e-178">Como todo o projeto está em um contexto que permite valor nulo, você receberá avisos quando passar `null` a qualquer método que esteja esperando um tipo de referência não anulável.</span><span class="sxs-lookup"><span data-stu-id="bb87e-178">Because the entire project is in a nullable enabled context, you'll get warnings when you pass `null` to any method expecting a non-nullable reference type.</span></span> <span data-ttu-id="bb87e-179">Experimente adicionar a seguinte linha a `Main`:</span><span class="sxs-lookup"><span data-stu-id="bb87e-179">Try it by adding the following line to `Main`:</span></span>

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a><span data-ttu-id="bb87e-180">Criar entrevistados e obter respostas para a pesquisa</span><span class="sxs-lookup"><span data-stu-id="bb87e-180">Create respondents and get answers to the survey</span></span>

<span data-ttu-id="bb87e-181">Em seguida, grave o código que gerará respostas para a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="bb87e-181">Next, write the code that generates answers to the survey.</span></span> <span data-ttu-id="bb87e-182">Esse processo envolve várias tarefas pequenas:</span><span class="sxs-lookup"><span data-stu-id="bb87e-182">This process involves several small tasks:</span></span>

1. <span data-ttu-id="bb87e-183">Criar um método para gerar objetos dos entrevistados.</span><span class="sxs-lookup"><span data-stu-id="bb87e-183">Build a method that generates respondent objects.</span></span> <span data-ttu-id="bb87e-184">Eles representam pessoas solicitadas a preencher a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="bb87e-184">These represent people asked to fill out the survey.</span></span>
1. <span data-ttu-id="bb87e-185">Criar lógica para simular a realização de perguntas para um pesquisado e coletar respostas ou perceber que um pesquisado não respondeu.</span><span class="sxs-lookup"><span data-stu-id="bb87e-185">Build logic to simulate asking the questions to a respondent and collecting answers or noting that a respondent didn't answer.</span></span>
1. <span data-ttu-id="bb87e-186">Repetir até que entrevistados suficientes tenham respondido à pesquisa.</span><span class="sxs-lookup"><span data-stu-id="bb87e-186">Repeat until enough respondents have answered the survey.</span></span>

<span data-ttu-id="bb87e-187">Será necessária uma classe para representar uma resposta da pesquisa. Adicione-a agora.</span><span class="sxs-lookup"><span data-stu-id="bb87e-187">You'll need a class to represent a survey response, so add that now.</span></span> <span data-ttu-id="bb87e-188">Habilitar o suporte para tipos que permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bb87e-188">Enable nullable support.</span></span> <span data-ttu-id="bb87e-189">Adicione uma propriedade `Id` e um construtor para inicializá-la, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="bb87e-189">Add an `Id` property and a constructor that initializes it, as shown in the following code:</span></span>

```csharp
namespace NullableIntroduction
{
    public class SurveyResponse
    {
        public int Id { get; }

        public SurveyResponse(int id) => Id = id;
    }
}
```

<span data-ttu-id="bb87e-190">Em seguida, adicione um método `static` para criar novos participantes ao gerar uma ID aleatória:</span><span class="sxs-lookup"><span data-stu-id="bb87e-190">Next, add a `static` method to create new participants by generating a random ID:</span></span>

[!code-csharp[GenerateRespondents](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

<span data-ttu-id="bb87e-191">A principal responsabilidade dessa classe é gerar as respostas de um participante para as perguntas da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="bb87e-191">The main responsibility of this class is to generate the responses for a participant to the questions in the survey.</span></span> <span data-ttu-id="bb87e-192">Essa responsabilidade conta com algumas etapas:</span><span class="sxs-lookup"><span data-stu-id="bb87e-192">This responsibility has a few steps:</span></span>

1. <span data-ttu-id="bb87e-193">Peça para participar da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="bb87e-193">Ask for participation in the survey.</span></span> <span data-ttu-id="bb87e-194">Se a pessoa não consentir, retorne uma resposta de ausente (ou de valor nulo).</span><span class="sxs-lookup"><span data-stu-id="bb87e-194">If the person doesn't consent, return a missing (or null) response.</span></span>
1. <span data-ttu-id="bb87e-195">Faça as perguntas e registre a resposta.</span><span class="sxs-lookup"><span data-stu-id="bb87e-195">Ask each question and record the answer.</span></span> <span data-ttu-id="bb87e-196">As respostas também pode ser ausentes (ou de valor nulo).</span><span class="sxs-lookup"><span data-stu-id="bb87e-196">Each answer may also be missing (or null).</span></span>

<span data-ttu-id="bb87e-197">Adicione o seguinte código à classe `SurveyResponse`:</span><span class="sxs-lookup"><span data-stu-id="bb87e-197">Add the following code to your `SurveyResponse` class:</span></span>

[!code-csharp[AnswerSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

<span data-ttu-id="bb87e-198">O armazenamento das respostas da pesquisa é um `Dictionary<int, string>?`, indicando que ele pode ser um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bb87e-198">The storage for the survey answers is a `Dictionary<int, string>?`, indicating that it may be null.</span></span> <span data-ttu-id="bb87e-199">Você está usando o novo recurso de idioma para declarar sua intenção de design, tanto para o compilador quanto para qualquer pessoa que leia seu código posteriormente.</span><span class="sxs-lookup"><span data-stu-id="bb87e-199">You're using the new language feature to declare your design intent, both to the compiler and to anyone reading your code later.</span></span> <span data-ttu-id="bb87e-200">Se você já tiver desconsiderado `surveyResponses` sem verificar o valor nulo primeiro, receberá um aviso do compilador.</span><span class="sxs-lookup"><span data-stu-id="bb87e-200">If you ever dereference `surveyResponses` without checking for the null value first, you'll get a compiler warning.</span></span> <span data-ttu-id="bb87e-201">Você não receberá um aviso no método `AnswerSurvey` porque o compilador pode determinar que a variável `surveyResponses` foi definida como um valor não nulo acima.</span><span class="sxs-lookup"><span data-stu-id="bb87e-201">You don't get a warning in the `AnswerSurvey` method because the compiler can determine the `surveyResponses` variable was set to a non-null value above.</span></span>

<span data-ttu-id="bb87e-202">O uso de `null` para respostas ausentes destaca um ponto importante para trabalhar com tipos de referência anuláveis: seu objetivo não é remover todos os valores `null` de seu programa.</span><span class="sxs-lookup"><span data-stu-id="bb87e-202">Using `null` for missing answers highlights a key point for working with nullable reference types: your goal isn't to remove all `null` values from your program.</span></span> <span data-ttu-id="bb87e-203">Em vez disso, sua meta é garantir que o código escrito expresse a intenção do seu design.</span><span class="sxs-lookup"><span data-stu-id="bb87e-203">Rather, your goal is to ensure that the code you write expresses the intent of your design.</span></span> <span data-ttu-id="bb87e-204">Os valores ausentes representam um conceito que precisa ser expresso em seu código.</span><span class="sxs-lookup"><span data-stu-id="bb87e-204">Missing values are a necessary concept to express in your code.</span></span> <span data-ttu-id="bb87e-205">O valor `null` é uma forma clara de expressar esses valores ausentes.</span><span class="sxs-lookup"><span data-stu-id="bb87e-205">The `null` value is a clear way to express those missing values.</span></span> <span data-ttu-id="bb87e-206">Tentar remover todos os valores `null` leva somente à definição de alguma outra maneira de expressar esses valores ausentes sem `null`.</span><span class="sxs-lookup"><span data-stu-id="bb87e-206">Trying to remove all `null` values only leads to defining some other way to express those missing values without `null`.</span></span>

<span data-ttu-id="bb87e-207">Em seguida, é necessário gravar o método `PerformSurvey` na classe `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="bb87e-207">Next, you need to write the `PerformSurvey` method in the `SurveyRun` class.</span></span> <span data-ttu-id="bb87e-208">Adicione o seguinte código à classe `SurveyRun`:</span><span class="sxs-lookup"><span data-stu-id="bb87e-208">Add the following code in the `SurveyRun` class:</span></span>

[!code-csharp[PerformSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

<span data-ttu-id="bb87e-209">Aqui, novamente, sua opção por uma `List<SurveyResponse>?` que permite valor nulo indica que a resposta pode ser um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bb87e-209">Here again, your choice of a nullable `List<SurveyResponse>?` indicates the response may be null.</span></span> <span data-ttu-id="bb87e-210">Isso indica que a pesquisa ainda não foi entregue a nenhum pesquisado.</span><span class="sxs-lookup"><span data-stu-id="bb87e-210">That indicates the survey hasn't been given to any respondents yet.</span></span> <span data-ttu-id="bb87e-211">Observe que os entrevistados são adicionados até que um suficiente de pessoas tiver consentido.</span><span class="sxs-lookup"><span data-stu-id="bb87e-211">Notice that respondents are added until enough have consented.</span></span>

<span data-ttu-id="bb87e-212">A última etapa para executar a pesquisa é adicionar uma chamada para executar a pesquisa no final do método `Main`:</span><span class="sxs-lookup"><span data-stu-id="bb87e-212">The last step to run the survey is to add a call to perform the survey at the end of the `Main` method:</span></span>

[!code-csharp[RunSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a><span data-ttu-id="bb87e-213">Examinar as respostas da pesquisa</span><span class="sxs-lookup"><span data-stu-id="bb87e-213">Examine survey responses</span></span>

<span data-ttu-id="bb87e-214">A última etapa é exibir os resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="bb87e-214">The last step is to display survey results.</span></span> <span data-ttu-id="bb87e-215">Você adicionará código a várias classes gravadas.</span><span class="sxs-lookup"><span data-stu-id="bb87e-215">You'll add code to many of the classes you've written.</span></span> <span data-ttu-id="bb87e-216">Este código demonstra o valor da distinção dos tipos de referência que permitem valor nulo e tipos de referência que não permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bb87e-216">This code demonstrates the value of distinguishing nullable and non-nullable reference types.</span></span> <span data-ttu-id="bb87e-217">Comece adicionando os dois membros com corpo de expressão à classe `SurveyResponse`:</span><span class="sxs-lookup"><span data-stu-id="bb87e-217">Start by adding the following two expression-bodied members to the `SurveyResponse` class:</span></span>

[!code-csharp[ReportResponses](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

<span data-ttu-id="bb87e-218">Como `surveyResponses` é um tipo de referência que não permite valor nulo, nenhuma verificação é necessária antes de desreferenciá-lo.</span><span class="sxs-lookup"><span data-stu-id="bb87e-218">Because `surveyResponses` is a non-nullable reference type, no checks are necessary before de-referencing it.</span></span> <span data-ttu-id="bb87e-219">O método `Answer` retorna uma cadeia de caracteres que não permite valor nulo, portanto, escolha a sobrecarga de `GetValueOrDefault` que recebe um segundo argumento para o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="bb87e-219">The `Answer` method returns a non-nullable string, so choose the overload of `GetValueOrDefault` that takes a second argument for the default value.</span></span>

<span data-ttu-id="bb87e-220">Em seguida, adicione esses três membros com corpo de expressão à classe `SurveyRun`:</span><span class="sxs-lookup"><span data-stu-id="bb87e-220">Next, add these three expression-bodied members to the `SurveyRun` class:</span></span>

[!code-csharp[ReportResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

<span data-ttu-id="bb87e-221">O membro `AllParticipants` deve levar em conta que a variável `respondents` pode ser um valor nulo, mas o valor de retorno não pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="bb87e-221">The `AllParticipants` member must take into account that the `respondents` variable might be null, but the return value can't be null.</span></span> <span data-ttu-id="bb87e-222">Se você alterar essa expressão removendo `??` e a sequência vazia que se segue, o compilador avisará que o método poderá retornar `null` e sua assinatura de retorno retornará um tipo que não permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bb87e-222">If you change that expression by removing the `??` and the empty sequence that follows, the compiler warns you the method might return `null` and its return signature returns a non-nullable type.</span></span>

<span data-ttu-id="bb87e-223">Por fim, adicione o seguinte loop à parte inferior do método `Main`:</span><span class="sxs-lookup"><span data-stu-id="bb87e-223">Finally, add the following loop at the bottom of the `Main` method:</span></span>

[!code-csharp[DisplaySurveyResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

<span data-ttu-id="bb87e-224">Você não precisa de verificações de `null` neste código porque criou as interfaces subjacentes para que todas elas retornem tipos de referência que não permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bb87e-224">You don't need any `null` checks in this code because you've designed the underlying interfaces so that they all return non-nullable reference types.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="bb87e-225">Obter o código</span><span class="sxs-lookup"><span data-stu-id="bb87e-225">Get the code</span></span>

<span data-ttu-id="bb87e-226">Obtenha o código do tutorial concluído em nosso repositório de [amostras](https://github.com/dotnet/samples) na pasta [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction).</span><span class="sxs-lookup"><span data-stu-id="bb87e-226">You can get the code for the finished tutorial from our [samples](https://github.com/dotnet/samples) repository in the [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) folder.</span></span>

<span data-ttu-id="bb87e-227">Experimente alterar as declarações de tipo entre os tipos de referência que permitem valor nulo e tipos de referência que não permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bb87e-227">Experiment by changing the type declarations between nullable and non-nullable reference types.</span></span> <span data-ttu-id="bb87e-228">Veja como isso gera avisos diferentes para garantir que um `null` não será acidentalmente cancelado.</span><span class="sxs-lookup"><span data-stu-id="bb87e-228">See how that generates different warnings to ensure you don't accidentally dereference a `null`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="bb87e-229">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="bb87e-229">Next steps</span></span>

<span data-ttu-id="bb87e-230">Saiba mais migrando um aplicativo existente para usar tipos de referência anuláveis:</span><span class="sxs-lookup"><span data-stu-id="bb87e-230">Learn more by migrating an existing application to use nullable reference types:</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="bb87e-231">Atualizar um aplicativo a fim de usar tipos de referência anuláveis</span><span class="sxs-lookup"><span data-stu-id="bb87e-231">Upgrade an application to use nullable reference types</span></span>](upgrade-to-nullable-references.md)
