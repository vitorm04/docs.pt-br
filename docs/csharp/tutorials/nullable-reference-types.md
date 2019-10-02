---
title: Criar com tipos de referência que permitem valor nulo
description: Este tutorial avançado fornece uma introdução aos tipos de referência que permitem valor nulo. Você aprenderá a expressar sua intenção de design quando os valores de referência puderem ser nulos e ter o compilador obrigatório quando eles não puderem ser nulos.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: 8b7c512a2f6bd67b07d8e344ad126026048be172
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736740"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="99183-104">Tutorial: Expressar sua intenção de design mais claramente com tipos de referência que permitem valor nulo e tipos de referência que não permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="99183-104">Tutorial: Express your design intent more clearly with nullable and non-nullable reference types</span></span>

<span data-ttu-id="99183-105">O C# 8 introduz **tipos de referência que permitem valor nulo** que complementam os tipos de referência da mesma maneira que os tipos de valor que permitem valor nulo complementam os tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="99183-105">C# 8 introduces **nullable reference types**, which complement reference types the same way nullable value types complement value types.</span></span> <span data-ttu-id="99183-106">Para declarar que uma variável é um **tipo de referência que permite valor nulo**, anexe um `?` ao tipo.</span><span class="sxs-lookup"><span data-stu-id="99183-106">You declare a variable to be a **nullable reference type** by appending a `?` to the type.</span></span> <span data-ttu-id="99183-107">Por exemplo, `string?` representa uma `string` que permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="99183-107">For example, `string?` represents a nullable `string`.</span></span> <span data-ttu-id="99183-108">Você pode usar esses novos tipos para expressar mais claramente sua intenção de design: algumas variáveis *devem sempre ter um valor*, outras *podem ter um valor* ausente.</span><span class="sxs-lookup"><span data-stu-id="99183-108">You can use these new types to more clearly express your design intent: some variables *must always have a value*, others *may be missing a value*.</span></span>

<span data-ttu-id="99183-109">Neste tutorial, você aprenderá a:</span><span class="sxs-lookup"><span data-stu-id="99183-109">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="99183-110">Incorporar tipos de referência que permitem valores nulos e tipos de referência que não permitem valores nulos aos designs</span><span class="sxs-lookup"><span data-stu-id="99183-110">Incorporate nullable and non-nullable reference types into your designs</span></span>
> - <span data-ttu-id="99183-111">Habilitar verificações de tipo de referência que permitem valor nulo em todo o código.</span><span class="sxs-lookup"><span data-stu-id="99183-111">Enable nullable reference type checks throughout your code.</span></span>
> - <span data-ttu-id="99183-112">Gravar código em locais onde o compilador imponha essas decisões de design.</span><span class="sxs-lookup"><span data-stu-id="99183-112">Write code where the compiler enforces those design decisions.</span></span>
> - <span data-ttu-id="99183-113">Usar o recurso de referência que permite valor nulo em seus próprios designs</span><span class="sxs-lookup"><span data-stu-id="99183-113">Use the nullable reference feature in your own designs</span></span>

## <a name="prerequisites"></a><span data-ttu-id="99183-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="99183-114">Prerequisites</span></span>

<span data-ttu-id="99183-115">Você precisará configurar seu computador para executar o .NET Core, incluindo o C# compilador 8,0.</span><span class="sxs-lookup"><span data-stu-id="99183-115">You'll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="99183-116">O C# compilador 8 Beta está disponível com o [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)ou o [.NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="99183-116">The C# 8 beta compiler is available with [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or [.NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="99183-117">Este tutorial pressupõe que você esteja familiarizado com o C# e .NET, incluindo o Visual Studio ou a CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="99183-117">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="incorporate-nullable-reference-types-into-your-designs"></a><span data-ttu-id="99183-118">Incorporar tipos de referência que permitem valor nulo aos designs</span><span class="sxs-lookup"><span data-stu-id="99183-118">Incorporate nullable reference types into your designs</span></span>

<span data-ttu-id="99183-119">Neste tutorial, você criará uma biblioteca para modelar a executar uma pesquisa.</span><span class="sxs-lookup"><span data-stu-id="99183-119">In this tutorial, you'll build a library that models running a survey.</span></span> <span data-ttu-id="99183-120">O código usa tipos de referência que permitem valores nulos e tipos de referência que não permitem valores nulos para representar os conceitos do mundo real.</span><span class="sxs-lookup"><span data-stu-id="99183-120">The code uses both nullable reference types and non-nullable reference types to represent the real-world concepts.</span></span> <span data-ttu-id="99183-121">As perguntas da pesquisa nunca podem ser um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="99183-121">The survey questions can never be null.</span></span> <span data-ttu-id="99183-122">Um entrevistado pode optar por não responder a uma pergunta.</span><span class="sxs-lookup"><span data-stu-id="99183-122">A respondent might prefer not to answer a question.</span></span> <span data-ttu-id="99183-123">As respostas devem ser valores nulos nesse caso.</span><span class="sxs-lookup"><span data-stu-id="99183-123">The responses might be null in this case.</span></span>

<span data-ttu-id="99183-124">O código que você gravará para este exemplo expressa essa intenção e o compilador a aplica.</span><span class="sxs-lookup"><span data-stu-id="99183-124">The code you'll write for this sample expresses that intent, and the compiler enforces that intent.</span></span>

## <a name="create-the-application-and-enable-nullable-reference-types"></a><span data-ttu-id="99183-125">Criar o aplicativo e habilitar os tipos de referência que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="99183-125">Create the application and enable nullable reference types</span></span>

<span data-ttu-id="99183-126">Crie um novo aplicativo de console no Visual Studio ou na linha de comando usando `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="99183-126">Create a new console application either in Visual Studio or from the command line using `dotnet new console`.</span></span> <span data-ttu-id="99183-127">Dê o nome `NullableIntroduction` ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="99183-127">Name the application `NullableIntroduction`.</span></span> <span data-ttu-id="99183-128">Depois de criar o aplicativo, será preciso ativar os recursos beta do C# 8.</span><span class="sxs-lookup"><span data-stu-id="99183-128">Once you've created the application, you'll need to enable C# 8 beta features.</span></span> <span data-ttu-id="99183-129">Abra o arquivo `csproj` e adicione um elemento `LangVersion` ao elemento `PropertyGroup`.</span><span class="sxs-lookup"><span data-stu-id="99183-129">Open the `csproj` file and add a `LangVersion` element to the `PropertyGroup` element.</span></span> <span data-ttu-id="99183-130">Você deve aceitar o recurso dos **tipos de referência que permitem valor nulo**, mesmo em projetos do C# 8.</span><span class="sxs-lookup"><span data-stu-id="99183-130">You must opt into the **nullable reference types** feature, even in C# 8 projects.</span></span> <span data-ttu-id="99183-131">Isso porque, quando o recurso é ativado, as declarações de variáveis de referência existentes tornam-se **tipos de referência que não permitem valor nulo**.</span><span class="sxs-lookup"><span data-stu-id="99183-131">That's because once the feature is turned on, existing reference variable declarations become **non-nullable reference types**.</span></span> <span data-ttu-id="99183-132">Embora essa decisão auxilie na localização de problemas nos quais o código existente pode não ter verificações de valores nulos adequadas, ela pode não refletir com precisão a intenção original do design.</span><span class="sxs-lookup"><span data-stu-id="99183-132">While that decision will help find issues where existing code may not have proper null-checks, it may not accurately reflect your original design intent.</span></span> <span data-ttu-id="99183-133">Ative o recurso definindo o elemento `Nullable` como `enable`:</span><span class="sxs-lookup"><span data-stu-id="99183-133">You turn on the feature by setting the `Nullable` element to `enable`:</span></span>

```xml
<LangVersion>8.0</LangVersion>
<Nullable>enable</Nullable>
```

### <a name="design-the-types-for-the-application"></a><span data-ttu-id="99183-134">Criar os tipos para o aplicativo</span><span class="sxs-lookup"><span data-stu-id="99183-134">Design the types for the application</span></span>

<span data-ttu-id="99183-135">Este aplicativo de pesquisa requer a criação de várias classes:</span><span class="sxs-lookup"><span data-stu-id="99183-135">This survey application requires creating a number of classes:</span></span>

- <span data-ttu-id="99183-136">Uma classe que modela a lista de perguntas.</span><span class="sxs-lookup"><span data-stu-id="99183-136">A class that models the list of questions.</span></span>
- <span data-ttu-id="99183-137">Uma classe que modela uma lista de pessoas contatadas para a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="99183-137">A class that models a list of people contacted for the survey.</span></span>
- <span data-ttu-id="99183-138">Uma classe que modela as respostas de uma pessoa que participou da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="99183-138">A class that models the answers from a person that took the survey.</span></span>

<span data-ttu-id="99183-139">Esses tipos usarão os tipos de referência que permitem valor nulo e tipos de referência que não permitem valor nulo para expressar quais membros são obrigatórios e quais são opcionais.</span><span class="sxs-lookup"><span data-stu-id="99183-139">These types will make use of both nullable and non-nullable reference types to express which members are required and which members are optional.</span></span> <span data-ttu-id="99183-140">Os tipos de referência que permitem valor nulo informam claramente essa intenção de design:</span><span class="sxs-lookup"><span data-stu-id="99183-140">Nullable reference types communicate that design intent clearly:</span></span>

- <span data-ttu-id="99183-141">As perguntas que fazem parte da pesquisa nunca podem ser nulas: Não faz sentido fazer uma pergunta vazia.</span><span class="sxs-lookup"><span data-stu-id="99183-141">The questions that are part of the survey can never be null: It makes no sense to ask an empty question.</span></span>
- <span data-ttu-id="99183-142">Os entrevistados nunca poderão ser nulos.</span><span class="sxs-lookup"><span data-stu-id="99183-142">The respondents can never be null.</span></span> <span data-ttu-id="99183-143">Convém controlar as pessoas contatadas, mesmo os entrevistados que se recusaram a participar.</span><span class="sxs-lookup"><span data-stu-id="99183-143">You'll want to track people you contacted, even respondents that declined to participate.</span></span>
- <span data-ttu-id="99183-144">Qualquer resposta a uma pergunta pode ser um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="99183-144">Any response to a question may be null.</span></span> <span data-ttu-id="99183-145">Os entrevistados podem se recusar a responder a algumas ou a todas as perguntas.</span><span class="sxs-lookup"><span data-stu-id="99183-145">Respondents can decline to answer some or all questions.</span></span>

<span data-ttu-id="99183-146">Se já tiver programado em C#, pode estar tão acostumado a fazer referência a tipos que permitem valor nulo que poderá ter perdido outras oportunidades de declarar instâncias que não permitem valor nulo:</span><span class="sxs-lookup"><span data-stu-id="99183-146">If you've programmed in C#, you may be so accustomed to reference types that allow null values that you may have missed other opportunities to declare non-nullable instances:</span></span>

- <span data-ttu-id="99183-147">O conjunto de perguntas não deve permitir um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="99183-147">The collection of questions should be non-nullable.</span></span>
- <span data-ttu-id="99183-148">O conjunto de entrevistados não deve permitir um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="99183-148">The collection of respondents should be non-nullable.</span></span>

<span data-ttu-id="99183-149">Conforme grava o código, você verá que um tipo de referência que não permite valor nulo como padrão para referências evita erros comuns que podem levar a exceções de referências que permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="99183-149">As you write the code, you'll see that a non-nullable reference type as the default for references avoids common mistakes that could lead to null reference exceptions.</span></span> <span data-ttu-id="99183-150">Uma das lições retirada deste tutorial é que você tomou decisões sobre quais variáveis poderiam ou não permitir valor nulo.</span><span class="sxs-lookup"><span data-stu-id="99183-150">One lesson from this tutorial is that you made decisions about which variables could or could not be null.</span></span> <span data-ttu-id="99183-151">O idioma não forneceu sintaxe para expressar essas decisões.</span><span class="sxs-lookup"><span data-stu-id="99183-151">The language didn't provide syntax to express those decisions.</span></span> <span data-ttu-id="99183-152">Agora ele já fornece.</span><span class="sxs-lookup"><span data-stu-id="99183-152">Now it does.</span></span>

<span data-ttu-id="99183-153">O aplicativo que será compilado seguirá as etapas a seguir:</span><span class="sxs-lookup"><span data-stu-id="99183-153">The app you'll build will do the following steps:</span></span>

1. <span data-ttu-id="99183-154">Criar uma pesquisa e adicionar perguntas a ela.</span><span class="sxs-lookup"><span data-stu-id="99183-154">Create a survey and add questions to it.</span></span>
1. <span data-ttu-id="99183-155">Criar um conjunto pseudoaleatório de entrevistados para a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="99183-155">Create a pseudo-random set of respondents for the survey.</span></span>
1. <span data-ttu-id="99183-156">Entre em contato com os entrevistados até que o tamanho da pesquisa preenchida atinja o número da meta.</span><span class="sxs-lookup"><span data-stu-id="99183-156">Contact respondents until the completed survey size reaches the goal number.</span></span>
1. <span data-ttu-id="99183-157">Anote estatísticas importantes sobre as respostas da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="99183-157">Write out important statistics on the survey responses.</span></span>

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a><span data-ttu-id="99183-158">Criar a pesquisa com tipos que permitem valor nulo e tipos que não permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="99183-158">Build the survey with nullable and non-nullable types</span></span>

<span data-ttu-id="99183-159">O primeiro código gravado criará a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="99183-159">The first code you'll write creates the survey.</span></span> <span data-ttu-id="99183-160">Você escreverá classes para modelar uma pergunta da pesquisa e uma execução da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="99183-160">You'll write classes to model a survey question and a survey run.</span></span> <span data-ttu-id="99183-161">A pesquisa tem três tipos de perguntas, diferenciadas pelo formato da resposta: Respostas Sim/Não, respostas de números e respostas de texto.</span><span class="sxs-lookup"><span data-stu-id="99183-161">Your survey has three types of questions, distinguished by the format of the answer: Yes/No answers, number answers, and text answers.</span></span> <span data-ttu-id="99183-162">Crie uma classe `public` `SurveyQuestion`:</span><span class="sxs-lookup"><span data-stu-id="99183-162">Create a `public` `SurveyQuestion` class:</span></span>

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

<span data-ttu-id="99183-163">O compilador interpreta cada declaração de variável de tipo de referência como um tipo de referência **não anulável** para código em um contexto que permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="99183-163">The compiler interprets every reference type variable declaration as a **non-nullable** reference type for code in a nullable enabled context.</span></span> <span data-ttu-id="99183-164">Para ver seu primeiro aviso, adicione propriedades ao texto da pergunta e tipo de pergunta, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="99183-164">You can see your first warning by adding properties for the question text and the type of question, as shown in the following code:</span></span>

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

<span data-ttu-id="99183-165">Como você não inicializou `QuestionText`, o compilador emitirá um aviso informando que uma propriedade que não permite valor nulo não foi inicializada.</span><span class="sxs-lookup"><span data-stu-id="99183-165">Because you haven't initialized `QuestionText`, the compiler issues a warning that a non-nullable property hasn't been initialized.</span></span> <span data-ttu-id="99183-166">Seu design exige que o texto da pergunta não seja um valor nulo, portanto, você inclui um construtor para inicializá-lo e o valor `QuestionType` também.</span><span class="sxs-lookup"><span data-stu-id="99183-166">Your design requires the question text to be non-null, so you add a constructor to initialize it and the `QuestionType` value as well.</span></span> <span data-ttu-id="99183-167">A definição da classe concluída se parece com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="99183-167">The finished class definition looks like the following code:</span></span>

[!code-csharp[DefineQuestion](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

<span data-ttu-id="99183-168">A adição do construtor removerá o aviso.</span><span class="sxs-lookup"><span data-stu-id="99183-168">Adding the constructor removes the warning.</span></span> <span data-ttu-id="99183-169">O argumento do construtor também é um tipo de referência que não permite valor nulo, portanto, o compilador não emite avisos.</span><span class="sxs-lookup"><span data-stu-id="99183-169">The constructor argument is also a non-nullable reference type, so the compiler doesn't issue any warnings.</span></span>

<span data-ttu-id="99183-170">Em seguida, crie uma classe `public` chamada `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="99183-170">Next, create a `public` class named `SurveyRun`.</span></span> <span data-ttu-id="99183-171">Esta classe contém uma lista de métodos e objetos `SurveyQuestion` para adicionar perguntas à pesquisa, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="99183-171">This class contains a list of `SurveyQuestion` objects and methods to add questions to the survey, as shown in the following code:</span></span>

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

<span data-ttu-id="99183-172">Como foi feito anteriormente, você deve inicializar o objeto de lista com um valor não nulo ou o compilador emitirá um aviso.</span><span class="sxs-lookup"><span data-stu-id="99183-172">As before, you must initialize the list object to a non-null value or the compiler issues a warning.</span></span> <span data-ttu-id="99183-173">Não há verificações de nulo na segunda sobrecarga de `AddQuestion` porque elas não são necessárias: Você declarou essa variável como não permitindo valor nulo.</span><span class="sxs-lookup"><span data-stu-id="99183-173">There are no null checks in the second overload of `AddQuestion` because they aren't needed: You've declared that variable to be non-nullable.</span></span> <span data-ttu-id="99183-174">Seu valor não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="99183-174">Its value can't be `null`.</span></span>

<span data-ttu-id="99183-175">Alterne para `Program.cs` no editor e substitua o conteúdo de `Main` pelas seguintes linhas de código:</span><span class="sxs-lookup"><span data-stu-id="99183-175">Switch to `Program.cs` in your editor and replace the contents of `Main` with the following lines of code:</span></span>

[!code-csharp[AddQuestions](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

<span data-ttu-id="99183-176">Como todo o projeto está em um contexto que permite valor nulo, você receberá avisos quando passar `null` a qualquer método que esteja esperando um tipo de referência não anulável.</span><span class="sxs-lookup"><span data-stu-id="99183-176">Because the entire project is in a nullable enabled context, you'll get warnings when you pass `null` to any method expecting a non-nullable reference type.</span></span> <span data-ttu-id="99183-177">Experimente adicionar a seguinte linha a `Main`:</span><span class="sxs-lookup"><span data-stu-id="99183-177">Try it by adding the following line to `Main`:</span></span>

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a><span data-ttu-id="99183-178">Criar entrevistados e obter respostas para a pesquisa</span><span class="sxs-lookup"><span data-stu-id="99183-178">Create respondents and get answers to the survey</span></span>

<span data-ttu-id="99183-179">Em seguida, grave o código que gerará respostas para a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="99183-179">Next, write the code that generates answers to the survey.</span></span> <span data-ttu-id="99183-180">Esse processo envolve várias tarefas pequenas:</span><span class="sxs-lookup"><span data-stu-id="99183-180">This process involves several small tasks:</span></span>

1. <span data-ttu-id="99183-181">Criar um método para gerar objetos dos entrevistados.</span><span class="sxs-lookup"><span data-stu-id="99183-181">Build a method that generates respondent objects.</span></span> <span data-ttu-id="99183-182">Eles representam pessoas solicitadas a preencher a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="99183-182">These represent people asked to fill out the survey.</span></span>
1. <span data-ttu-id="99183-183">Criar lógica para simular a realização de perguntas para um pesquisado e coletar respostas ou perceber que um pesquisado não respondeu.</span><span class="sxs-lookup"><span data-stu-id="99183-183">Build logic to simulate asking the questions to a respondent and collecting answers or noting that a respondent didn't answer.</span></span>
1. <span data-ttu-id="99183-184">Repetir até que entrevistados suficientes tenham respondido à pesquisa.</span><span class="sxs-lookup"><span data-stu-id="99183-184">Repeat until enough respondents have answered the survey.</span></span>

<span data-ttu-id="99183-185">Será necessária uma classe para representar uma resposta da pesquisa. Adicione-a agora.</span><span class="sxs-lookup"><span data-stu-id="99183-185">You'll need a class to represent a survey response, so add that now.</span></span> <span data-ttu-id="99183-186">Habilitar o suporte para tipos que permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="99183-186">Enable nullable support.</span></span> <span data-ttu-id="99183-187">Adicione uma propriedade `Id` e um construtor para inicializá-la, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="99183-187">Add an `Id` property and a constructor that initializes it, as shown in the following code:</span></span>

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

<span data-ttu-id="99183-188">Em seguida, adicione um método `static` para criar novos participantes ao gerar uma ID aleatória:</span><span class="sxs-lookup"><span data-stu-id="99183-188">Next, add a `static` method to create new participants by generating a random ID:</span></span>

[!code-csharp[GenerateRespondents](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

<span data-ttu-id="99183-189">A principal responsabilidade dessa classe é gerar as respostas de um participante para as perguntas da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="99183-189">The main responsibility of this class is to generate the responses for a participant to the questions in the survey.</span></span> <span data-ttu-id="99183-190">Essa responsabilidade conta com algumas etapas:</span><span class="sxs-lookup"><span data-stu-id="99183-190">This responsibility has a few steps:</span></span>

1. <span data-ttu-id="99183-191">Peça para participar da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="99183-191">Ask for participation in the survey.</span></span> <span data-ttu-id="99183-192">Se a pessoa não consentir, retorne uma resposta de ausente (ou de valor nulo).</span><span class="sxs-lookup"><span data-stu-id="99183-192">If the person doesn't consent, return a missing (or null) response.</span></span>
1. <span data-ttu-id="99183-193">Faça as perguntas e registre a resposta.</span><span class="sxs-lookup"><span data-stu-id="99183-193">Ask each question and record the answer.</span></span> <span data-ttu-id="99183-194">As respostas também pode ser ausentes (ou de valor nulo).</span><span class="sxs-lookup"><span data-stu-id="99183-194">Each answer may also be missing (or null).</span></span>

<span data-ttu-id="99183-195">Adicione o seguinte código à classe `SurveyResponse`:</span><span class="sxs-lookup"><span data-stu-id="99183-195">Add the following code to your `SurveyResponse` class:</span></span>

[!code-csharp[AnswerSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

<span data-ttu-id="99183-196">O armazenamento das respostas da pesquisa é um `Dictionary<int, string>?`, indicando que ele pode ser um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="99183-196">The storage for the survey answers is a `Dictionary<int, string>?`, indicating that it may be null.</span></span> <span data-ttu-id="99183-197">Você está usando o novo recurso de idioma para declarar sua intenção de design, tanto para o compilador quanto para qualquer pessoa que leia seu código posteriormente.</span><span class="sxs-lookup"><span data-stu-id="99183-197">You're using the new language feature to declare your design intent, both to the compiler and to anyone reading your code later.</span></span> <span data-ttu-id="99183-198">Se você já tiver desconsiderado `surveyResponses` sem verificar o valor nulo primeiro, receberá um aviso do compilador.</span><span class="sxs-lookup"><span data-stu-id="99183-198">If you ever dereference `surveyResponses` without checking for the null value first, you'll get a compiler warning.</span></span> <span data-ttu-id="99183-199">Você não receberá um aviso no método `AnswerSurvey` porque o compilador pode determinar que a variável `surveyResponses` foi definida como um valor não nulo acima.</span><span class="sxs-lookup"><span data-stu-id="99183-199">You don't get a warning in the `AnswerSurvey` method because the compiler can determine the `surveyResponses` variable was set to a non-null value above.</span></span>

<span data-ttu-id="99183-200">O uso de `null` para respostas ausentes destaca um ponto importante para trabalhar com tipos de referência anuláveis: seu objetivo não é remover todos os valores `null` de seu programa.</span><span class="sxs-lookup"><span data-stu-id="99183-200">Using `null` for missing answers highlights a key point for working with nullable reference types: your goal isn't to remove all `null` values from your program.</span></span> <span data-ttu-id="99183-201">Em vez disso, sua meta é garantir que o código escrito expresse a intenção do seu design.</span><span class="sxs-lookup"><span data-stu-id="99183-201">Rather, your goal is to ensure that the code you write expresses the intent of your design.</span></span> <span data-ttu-id="99183-202">Os valores ausentes representam um conceito que precisa ser expresso em seu código.</span><span class="sxs-lookup"><span data-stu-id="99183-202">Missing values are a necessary concept to express in your code.</span></span> <span data-ttu-id="99183-203">O valor `null` é uma forma clara de expressar esses valores ausentes.</span><span class="sxs-lookup"><span data-stu-id="99183-203">The `null` value is a clear way to express those missing values.</span></span> <span data-ttu-id="99183-204">Tentar remover todos os valores `null` leva somente à definição de alguma outra maneira de expressar esses valores ausentes sem `null`.</span><span class="sxs-lookup"><span data-stu-id="99183-204">Trying to remove all `null` values only leads to defining some other way to express those missing values without `null`.</span></span>

<span data-ttu-id="99183-205">Em seguida, é necessário gravar o método `PerformSurvey` na classe `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="99183-205">Next, you need to write the `PerformSurvey` method in the `SurveyRun` class.</span></span> <span data-ttu-id="99183-206">Adicione o seguinte código à classe `SurveyRun`:</span><span class="sxs-lookup"><span data-stu-id="99183-206">Add the following code in the `SurveyRun` class:</span></span>

[!code-csharp[PerformSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

<span data-ttu-id="99183-207">Aqui, novamente, sua opção por uma `List<SurveyResponse>?` que permite valor nulo indica que a resposta pode ser um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="99183-207">Here again, your choice of a nullable `List<SurveyResponse>?` indicates the response may be null.</span></span> <span data-ttu-id="99183-208">Isso indica que a pesquisa ainda não foi entregue a nenhum pesquisado.</span><span class="sxs-lookup"><span data-stu-id="99183-208">That indicates the survey hasn't been given to any respondents yet.</span></span> <span data-ttu-id="99183-209">Observe que os entrevistados são adicionados até que um suficiente de pessoas tiver consentido.</span><span class="sxs-lookup"><span data-stu-id="99183-209">Notice that respondents are added until enough have consented.</span></span>

<span data-ttu-id="99183-210">A última etapa para executar a pesquisa é adicionar uma chamada para executar a pesquisa no final do método `Main`:</span><span class="sxs-lookup"><span data-stu-id="99183-210">The last step to run the survey is to add a call to perform the survey at the end of the `Main` method:</span></span>

[!code-csharp[RunSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a><span data-ttu-id="99183-211">Examinar as respostas da pesquisa</span><span class="sxs-lookup"><span data-stu-id="99183-211">Examine survey responses</span></span>

<span data-ttu-id="99183-212">A última etapa é exibir os resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="99183-212">The last step is to display survey results.</span></span> <span data-ttu-id="99183-213">Você adicionará código a várias classes gravadas.</span><span class="sxs-lookup"><span data-stu-id="99183-213">You'll add code to many of the classes you've written.</span></span> <span data-ttu-id="99183-214">Este código demonstra o valor da distinção dos tipos de referência que permitem valor nulo e tipos de referência que não permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="99183-214">This code demonstrates the value of distinguishing nullable and non-nullable reference types.</span></span> <span data-ttu-id="99183-215">Comece adicionando os dois membros com corpo de expressão à classe `SurveyResponse`:</span><span class="sxs-lookup"><span data-stu-id="99183-215">Start by adding the following two expression-bodied members to the `SurveyResponse` class:</span></span>

[!code-csharp[ReportResponses](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

<span data-ttu-id="99183-216">Como `surveyResponses` é um tipo de referência que não permite valor nulo, nenhuma verificação é necessária antes de desreferenciá-lo.</span><span class="sxs-lookup"><span data-stu-id="99183-216">Because `surveyResponses` is a non-nullable reference type, no checks are necessary before de-referencing it.</span></span> <span data-ttu-id="99183-217">O método `Answer` retorna uma cadeia de caracteres que não permite valor nulo, portanto, escolha a sobrecarga de `GetValueOrDefault` que recebe um segundo argumento para o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="99183-217">The `Answer` method returns a non-nullable string, so choose the overload of `GetValueOrDefault` that takes a second argument for the default value.</span></span>

<span data-ttu-id="99183-218">Em seguida, adicione esses três membros com corpo de expressão à classe `SurveyRun`:</span><span class="sxs-lookup"><span data-stu-id="99183-218">Next, add these three expression-bodied members to the `SurveyRun` class:</span></span>

[!code-csharp[ReportResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

<span data-ttu-id="99183-219">O membro `AllParticipants` deve levar em conta que a variável `respondents` pode ser um valor nulo, mas o valor de retorno não pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="99183-219">The `AllParticipants` member must take into account that the `respondents` variable might be null, but the return value can't be null.</span></span> <span data-ttu-id="99183-220">Se você alterar essa expressão removendo `??` e a sequência vazia que se segue, o compilador avisará que o método poderá retornar `null` e sua assinatura de retorno retornará um tipo que não permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="99183-220">If you change that expression by removing the `??` and the empty sequence that follows, the compiler warns you the method might return `null` and its return signature returns a non-nullable type.</span></span>

<span data-ttu-id="99183-221">Por fim, adicione o seguinte loop à parte inferior do método `Main`:</span><span class="sxs-lookup"><span data-stu-id="99183-221">Finally, add the following loop at the bottom of the `Main` method:</span></span>

[!code-csharp[DisplaySurveyResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

<span data-ttu-id="99183-222">Você não precisa de verificações de `null` neste código porque criou as interfaces subjacentes para que todas elas retornem tipos de referência que não permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="99183-222">You don't need any `null` checks in this code because you've designed the underlying interfaces so that they all return non-nullable reference types.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="99183-223">Obter o código</span><span class="sxs-lookup"><span data-stu-id="99183-223">Get the code</span></span>

<span data-ttu-id="99183-224">Obtenha o código do tutorial concluído em nosso repositório de [amostras](https://github.com/dotnet/samples) na pasta [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction).</span><span class="sxs-lookup"><span data-stu-id="99183-224">You can get the code for the finished tutorial from our [samples](https://github.com/dotnet/samples) repository in the [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) folder.</span></span>

<span data-ttu-id="99183-225">Experimente alterar as declarações de tipo entre os tipos de referência que permitem valor nulo e tipos de referência que não permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="99183-225">Experiment by changing the type declarations between nullable and non-nullable reference types.</span></span> <span data-ttu-id="99183-226">Veja como isso gera avisos diferentes para garantir que um `null` não será acidentalmente cancelado.</span><span class="sxs-lookup"><span data-stu-id="99183-226">See how that generates different warnings to ensure you don't accidentally dereference a `null`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="99183-227">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="99183-227">Next steps</span></span>

<span data-ttu-id="99183-228">Saiba mais migrando um aplicativo existente para usar tipos de referência anuláveis:</span><span class="sxs-lookup"><span data-stu-id="99183-228">Learn more by migrating an existing application to use nullable reference types:</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="99183-229">Atualizar um aplicativo a fim de usar tipos de referência anuláveis</span><span class="sxs-lookup"><span data-stu-id="99183-229">Upgrade an application to use nullable reference types</span></span>](upgrade-to-nullable-references.md)
