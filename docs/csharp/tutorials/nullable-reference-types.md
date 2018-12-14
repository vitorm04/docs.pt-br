---
title: Criar com tipos de referência que permitem valor nulo
description: Este tutorial avançado fornece uma introdução aos tipos de referência que permitem valor nulo. Você aprenderá a expressar sua intenção de design quando os valores de referência puderem ser nulos e ter o compilador obrigatório quando eles não puderem ser nulos.
ms.date: 12/03/2018
ms.custom: mvc
ms.openlocfilehash: 7e4cb423658287e5260770a680f189c227b9cd01
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53156684"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="2543e-104">Tutorial: Expressar sua intenção de design mais claramente com tipos de referência que permitem valor nulo e tipos que não permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="2543e-104">Tutorial: Express your design intent more clearly with nullable and non-nullable reference types</span></span>

<span data-ttu-id="2543e-105">O C# 8 introduz **tipos de referência que permitem valor nulo** que complementam os tipos de referência da mesma maneira que os tipos de valor que permitem valor nulo complementam os tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="2543e-105">C# 8 introduces **nullable reference types**, which complement reference types the same way nullable value types complement value types.</span></span> <span data-ttu-id="2543e-106">Para declarar que uma variável é um **tipo de referência que permite valor nulo**, anexe um `?` ao tipo.</span><span class="sxs-lookup"><span data-stu-id="2543e-106">You declare a variable to be a **nullable reference type** by appending a `?` to the type.</span></span> <span data-ttu-id="2543e-107">Por exemplo, `string?` representa uma `string` que permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="2543e-107">For example, `string?` represents a nullable `string`.</span></span> <span data-ttu-id="2543e-108">Você pode usar esses novos tipos para expressar mais claramente sua intenção de design: algumas variáveis *devem sempre ter um valor*, outras *podem ter um valor* ausente.</span><span class="sxs-lookup"><span data-stu-id="2543e-108">You can use these new types to more clearly express your design intent: some variables *must always have a value*, others *may be missing a value*.</span></span>

<span data-ttu-id="2543e-109">Neste tutorial, você aprenderá a:</span><span class="sxs-lookup"><span data-stu-id="2543e-109">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="2543e-110">Incorporar tipos de referência que permitem valores nulos e tipos de referência que não permitem valores nulos aos designs</span><span class="sxs-lookup"><span data-stu-id="2543e-110">Incorporate nullable and non-nullable reference types into your designs</span></span>
> * <span data-ttu-id="2543e-111">Habilitar verificações de tipo de referência que permitem valor nulo em todo o código.</span><span class="sxs-lookup"><span data-stu-id="2543e-111">Enable nullable reference type checks throughout your code.</span></span>
> * <span data-ttu-id="2543e-112">Gravar código em locais onde o compilador imponha essas decisões de design.</span><span class="sxs-lookup"><span data-stu-id="2543e-112">Write code where the compiler enforces those design decisions.</span></span>
> * <span data-ttu-id="2543e-113">Usar o recurso de referência que permite valor nulo em seus próprios designs</span><span class="sxs-lookup"><span data-stu-id="2543e-113">Use the nullable reference feature in your own designs</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2543e-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2543e-114">Prerequisites</span></span>

<span data-ttu-id="2543e-115">Você precisará configurar seu computador para executar o .NET Core, incluindo o compilador beta do C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="2543e-115">You’ll need to set up your machine to run .NET Core, including the C# 8.0 beta compiler.</span></span> <span data-ttu-id="2543e-116">O compilador do C# 8 beta está disponível com o [Visual Studio 2019 versão prévia 1](https://visualstudio.microsoft.com/vs/preview/) ou a visualização [.NET Core 3.0 versão prévia 1](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="2543e-116">The C# 8 beta compiler is available with [Visual Studio 2019 preview 1](https://visualstudio.microsoft.com/vs/preview/), or [.NET Core 3.0 preview 1](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="2543e-117">Este tutorial pressupõe que você esteja familiarizado com o C# e .NET, incluindo o Visual Studio ou a CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2543e-117">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="incorporate-nullable-reference-types-into-your-designs"></a><span data-ttu-id="2543e-118">Incorporar tipos de referência que permitem valor nulo aos designs</span><span class="sxs-lookup"><span data-stu-id="2543e-118">Incorporate nullable reference types into your designs</span></span>

<span data-ttu-id="2543e-119">Neste tutorial, você criará uma biblioteca para modelar a executar uma pesquisa.</span><span class="sxs-lookup"><span data-stu-id="2543e-119">In this tutorial, you'll build a library that models running a survey.</span></span> <span data-ttu-id="2543e-120">O código usa tipos de referência que permitem valores nulos e tipos de referência que não permitem valores nulos para representar os conceitos do mundo real.</span><span class="sxs-lookup"><span data-stu-id="2543e-120">The code uses both nullable reference types and non-nullable reference types to represent the real-world concepts.</span></span> <span data-ttu-id="2543e-121">As perguntas da pesquisa nunca podem ser um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="2543e-121">The survey questions can never be null.</span></span> <span data-ttu-id="2543e-122">Um entrevistado pode optar por não responder a uma pergunta.</span><span class="sxs-lookup"><span data-stu-id="2543e-122">A respondent might prefer not to answer a question.</span></span> <span data-ttu-id="2543e-123">As respostas devem ser valores nulos nesse caso.</span><span class="sxs-lookup"><span data-stu-id="2543e-123">The responses might be null in this case.</span></span>

<span data-ttu-id="2543e-124">O código que você gravará para este exemplo expressa essa intenção e o compilador a aplica.</span><span class="sxs-lookup"><span data-stu-id="2543e-124">The code you'll write for this sample expresses that intent, and the compiler enforces that intent.</span></span>

## <a name="create-the-application-and-enable-nullable-reference-types"></a><span data-ttu-id="2543e-125">Criar o aplicativo e habilitar os tipos de referência que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="2543e-125">Create the application and enable nullable reference types</span></span>

<span data-ttu-id="2543e-126">Crie um novo aplicativo de console no Visual Studio ou na linha de comando usando `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="2543e-126">Create a new console application either in Visual Studio or from the command line using `dotnet new console`.</span></span> <span data-ttu-id="2543e-127">Dê o nome `NullableIntroduction` ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2543e-127">Name the application `NullableIntroduction`.</span></span> <span data-ttu-id="2543e-128">Depois de criar o aplicativo, será preciso ativar os recursos beta do C# 8.</span><span class="sxs-lookup"><span data-stu-id="2543e-128">Once you've created the application, you'll need to enable C# 8 beta features.</span></span> <span data-ttu-id="2543e-129">Abra o arquivo `csproj` e adicione um elemento `LangVersion` ao elemento `PropertyGroup`:</span><span class="sxs-lookup"><span data-stu-id="2543e-129">Open the `csproj` file, and add a `LangVersion` element to the `PropertyGroup` element:</span></span>

```xml
<LangVersion>8.0</LangVersion>
```

<span data-ttu-id="2543e-130">Como alternativa, você pode usar as propriedades do projeto do Visual Studio para habilitar o C# 8.</span><span class="sxs-lookup"><span data-stu-id="2543e-130">Alternatively, you can use the Visual Studio project properties to enable C# 8.</span></span> <span data-ttu-id="2543e-131">No Gerenciador de Soluções, clique com o botão direito do mouse no nó do projeto e escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="2543e-131">In Solution Explorer, right click on the project node, select **Properties**.</span></span> <span data-ttu-id="2543e-132">Em seguida, escolha a guia **compilar** e clique em **Avançado...**. Na lista suspensa da versão do idioma, escolha **C# 8.0 (beta)**.</span><span class="sxs-lookup"><span data-stu-id="2543e-132">Then, select the **build** tab, and click **Advanced...**. In the dropdown for language version, select **C# 8.0 (beta)**.</span></span>

<span data-ttu-id="2543e-133">Você deve aceitar o recurso dos **tipos de referência que permitem valor nulo**, mesmo em projetos do C# 8.</span><span class="sxs-lookup"><span data-stu-id="2543e-133">You must opt into the **nullable reference types** feature, even in C# 8 projects.</span></span> <span data-ttu-id="2543e-134">Isso porque, quando o recurso é ativado, as declarações de variáveis de referência existentes tornam-se **tipos de referência que não permitem valor nulo**.</span><span class="sxs-lookup"><span data-stu-id="2543e-134">That's because once the feature is turned on, existing reference variable declarations become **non-nullable reference types**.</span></span> <span data-ttu-id="2543e-135">Embora essa decisão auxilie na localização de problemas nos quais o código existente pode não ter verificações de valores nulos adequadas, ela pode não refletir com precisão a intenção original do design.</span><span class="sxs-lookup"><span data-stu-id="2543e-135">While that decision will help find issues where existing code may not have proper null-checks, it may not accurately reflect your original design intent.</span></span> <span data-ttu-id="2543e-136">Ative o recurso com um novo pragma:</span><span class="sxs-lookup"><span data-stu-id="2543e-136">You turn on the feature with a new pragma:</span></span>

```csharp
#nullable enable
```

<span data-ttu-id="2543e-137">Você pode adicionar o pragma anterior em qualquer ponto de um arquivo de origem e o recurso de tipo de referência que permite valor nulo será ativado a partir desse ponto.</span><span class="sxs-lookup"><span data-stu-id="2543e-137">You can add the preceding pragma anywhere in a source file, and the nullable reference type feature is turned on from that point.</span></span> <span data-ttu-id="2543e-138">O pragma também oferece suporte ao argumento `disable` para desativar o recurso.</span><span class="sxs-lookup"><span data-stu-id="2543e-138">The pragma also supports the `disable` argument to turn off the feature.</span></span>

<span data-ttu-id="2543e-139">Você também pode ativar **tipos de referência que permitem valor nulo** para um projeto inteiro adicionando o seguinte elemento ao arquivo .csproj, por exemplo, imediatamente após o elemento `LangVersion` que ativou o C# 8.0:</span><span class="sxs-lookup"><span data-stu-id="2543e-139">You can also turn on **nullable reference types** for an entire project by adding the following element to your .csproj file, for example, immediately following the `LangVersion` element that enabled C# 8.0:</span></span>

```xml
<NullableReferenceTypes>true</NullableReferenceTypes>
```

### <a name="design-the-types-for-the-application"></a><span data-ttu-id="2543e-140">Criar os tipos para o aplicativo</span><span class="sxs-lookup"><span data-stu-id="2543e-140">Design the types for the application</span></span>

<span data-ttu-id="2543e-141">Este aplicativo de pesquisa requer a criação de várias classes:</span><span class="sxs-lookup"><span data-stu-id="2543e-141">This survey application requires creating a number of classes:</span></span>

- <span data-ttu-id="2543e-142">Uma classe que modela a lista de perguntas.</span><span class="sxs-lookup"><span data-stu-id="2543e-142">A class that models the list of questions.</span></span>
- <span data-ttu-id="2543e-143">Uma classe que modela uma lista de pessoas contatadas para a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="2543e-143">A class that models a list of people contacted for the survey.</span></span>
- <span data-ttu-id="2543e-144">Uma classe que modela as respostas de uma pessoa que participou da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="2543e-144">A class that models the answers from a person that took the survey.</span></span>

<span data-ttu-id="2543e-145">Esses tipos usarão os tipos de referência que permitem valor nulo e tipos de referência que não permitem valor nulo para expressar quais membros são obrigatórios e quais são opcionais.</span><span class="sxs-lookup"><span data-stu-id="2543e-145">These types will make use of both nullable and non-nullable reference types to express which members are required and which members are optional.</span></span> <span data-ttu-id="2543e-146">Os tipos de referência que permitem valor nulo informam claramente essa intenção de design:</span><span class="sxs-lookup"><span data-stu-id="2543e-146">Nullable reference types communicate that design intent clearly:</span></span>

- <span data-ttu-id="2543e-147">As perguntas que fazem parte da pesquisa nunca podem ser valores nulos: não faz sentido fazer uma pergunta vazia.</span><span class="sxs-lookup"><span data-stu-id="2543e-147">The questions that are part of the survey can never be null: It makes no sense to ask an empty question.</span></span>
- <span data-ttu-id="2543e-148">Os entrevistados nunca poderão ser nulos.</span><span class="sxs-lookup"><span data-stu-id="2543e-148">The respondents can never be null.</span></span> <span data-ttu-id="2543e-149">Convém controlar as pessoas contatadas, mesmo os entrevistados que se recusaram a participar.</span><span class="sxs-lookup"><span data-stu-id="2543e-149">You'll want to track people you contacted, even respondents that declined to participate.</span></span>
- <span data-ttu-id="2543e-150">Qualquer resposta a uma pergunta pode ser um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="2543e-150">Any response to a question may be null.</span></span> <span data-ttu-id="2543e-151">Os entrevistados podem se recusar a responder a algumas ou a todas as perguntas.</span><span class="sxs-lookup"><span data-stu-id="2543e-151">Respondents can decline to answer some or all questions.</span></span>

<span data-ttu-id="2543e-152">Se já tiver programado em C#, pode estar tão acostumado a fazer referência a tipos que permitem valor nulo que poderá ter perdido outras oportunidades de declarar instâncias que não permitem valor nulo:</span><span class="sxs-lookup"><span data-stu-id="2543e-152">If you've programmed in C#, you may be so accustomed to reference types that allow null values that you may have missed other opportunities to declare non-nullable instances:</span></span>

- <span data-ttu-id="2543e-153">O conjunto de perguntas não deve permitir um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="2543e-153">The collection of questions should be non-nullable.</span></span>
- <span data-ttu-id="2543e-154">O conjunto de entrevistados não deve permitir um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="2543e-154">The collection of respondents should be non-nullable.</span></span>

<span data-ttu-id="2543e-155">Conforme grava o código, você verá que um tipo de referência que não permite valor nulo como padrão para referências evita erros comuns que podem levar a exceções de referências que permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="2543e-155">As you write the code, you'll see that a non-nullable reference type as the default for references avoids common mistakes that could lead to null reference exceptions.</span></span> <span data-ttu-id="2543e-156">Uma das lições retirada deste tutorial é que você tomou decisões sobre quais variáveis poderiam ou não permitir valor nulo.</span><span class="sxs-lookup"><span data-stu-id="2543e-156">One lesson from this tutorial is that you made decisions about which variables could or could not be null.</span></span> <span data-ttu-id="2543e-157">O idioma não forneceu sintaxe para expressar essas decisões.</span><span class="sxs-lookup"><span data-stu-id="2543e-157">The language didn't provide syntax to express those decisions.</span></span> <span data-ttu-id="2543e-158">Agora ele já fornece.</span><span class="sxs-lookup"><span data-stu-id="2543e-158">Now it does.</span></span>

<span data-ttu-id="2543e-159">O aplicativo que será compilado seguirá as etapas a seguir:</span><span class="sxs-lookup"><span data-stu-id="2543e-159">The app you'll build will do the following steps:</span></span>

1. <span data-ttu-id="2543e-160">Criar uma pesquisa e adicionar perguntas a ela.</span><span class="sxs-lookup"><span data-stu-id="2543e-160">Create a survey and add questions to it.</span></span>
1. <span data-ttu-id="2543e-161">Criar um conjunto pseudoaleatório de entrevistados para a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="2543e-161">Create a pseudo-random set of respondents for the survey.</span></span>
1. <span data-ttu-id="2543e-162">Entre em contato com os entrevistados até que o tamanho da pesquisa preenchida atinja o número da meta.</span><span class="sxs-lookup"><span data-stu-id="2543e-162">Contact respondents until the completed survey size reaches the goal number.</span></span>
1. <span data-ttu-id="2543e-163">Anote estatísticas importantes sobre as respostas da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="2543e-163">Write out important statistics on the survey responses.</span></span>

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a><span data-ttu-id="2543e-164">Criar a pesquisa com tipos que permitem valor nulo e tipos que não permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="2543e-164">Build the survey with nullable and non-nullable types</span></span>

<span data-ttu-id="2543e-165">O primeiro código gravado criará a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="2543e-165">The first code you'll write creates the survey.</span></span> <span data-ttu-id="2543e-166">Você escreverá classes para modelar uma pergunta da pesquisa e uma execução da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="2543e-166">You'll write classes to model a survey question and a survey run.</span></span> <span data-ttu-id="2543e-167">A pesquisa tem três tipos de perguntas, diferenciadas pelo formato da resposta: respostas do tipo Sim/Não, respostas com números e respostas com texto.</span><span class="sxs-lookup"><span data-stu-id="2543e-167">Your survey has three types of questions, distinguished by the format of the answer: Yes/No answers, number answers, and text answers.</span></span> <span data-ttu-id="2543e-168">Criar uma classe `public` `SurveyQuestion`.</span><span class="sxs-lookup"><span data-stu-id="2543e-168">Create a `public` `SurveyQuestion` class.</span></span> <span data-ttu-id="2543e-169">Inclua o pragma `#nullable enable` imediatamente após as instruções `using`:</span><span class="sxs-lookup"><span data-stu-id="2543e-169">Include the `#nullable enable` pragma immediately after the `using` statements:</span></span>

```csharp
#nullable enable
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

<span data-ttu-id="2543e-170">Adicionar o pragma `#nullable enable` significa que o compilador interpretará cada declaração de variável de tipo de referência como um tipo de referência **que não permite valor nulo**.</span><span class="sxs-lookup"><span data-stu-id="2543e-170">Adding the `#nullable enable` pragma means the compiler interprets every reference type variable declaration as a **non-nullable** reference type.</span></span> <span data-ttu-id="2543e-171">Para ver seu primeiro aviso, adicione propriedades ao texto da pergunta e tipo de pergunta, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="2543e-171">You can see your first warning by adding properties for the question text and the type of question, as shown in the following code:</span></span>

```csharp
#nullable enable
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

<span data-ttu-id="2543e-172">Como você não inicializou `QuestionText`, o compilador emitirá um aviso informando que uma propriedade que não permite valor nulo não foi inicializada.</span><span class="sxs-lookup"><span data-stu-id="2543e-172">Because you haven't initialized `QuestionText`, the compiler issues a warning that a non-nullable property hasn't been initialized.</span></span> <span data-ttu-id="2543e-173">Seu design exige que o texto da pergunta não seja um valor nulo, portanto, você inclui um construtor para inicializá-lo e o valor `QuestionType` também.</span><span class="sxs-lookup"><span data-stu-id="2543e-173">Your design requires the question text to be non-null, so you add a constructor to initialize it and the `QuestionType` value as well.</span></span> <span data-ttu-id="2543e-174">A definição da classe concluída se parece com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="2543e-174">The finished class definition looks like the following code:</span></span>

[!code-csharp[DefineQuestion](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

<span data-ttu-id="2543e-175">A adição do construtor removerá o aviso.</span><span class="sxs-lookup"><span data-stu-id="2543e-175">Adding the constructor removes the warning.</span></span> <span data-ttu-id="2543e-176">O argumento do construtor também é um tipo de referência que não permite valor nulo, portanto, o compilador não emite avisos.</span><span class="sxs-lookup"><span data-stu-id="2543e-176">The constructor argument is also a non-nullable reference type, so the compiler doesn't issue any warnings.</span></span>

<span data-ttu-id="2543e-177">Em seguida, crie uma classe `public` chamada `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="2543e-177">Next, create a `public` class named `SurveyRun`.</span></span> <span data-ttu-id="2543e-178">Inclua o pragma `#nullable enable` após as instruções `using`.</span><span class="sxs-lookup"><span data-stu-id="2543e-178">Include the `#nullable enable` pragma following the `using` statements.</span></span> <span data-ttu-id="2543e-179">Esta classe contém uma lista de métodos e objetos `SurveyQuestion` para adicionar perguntas à pesquisa, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="2543e-179">This class contains a list of `SurveyQuestion` objects and methods to add questions to the survey, as shown in the following code:</span></span>

```csharp
using System.Collections.Generic;

#nullable enable
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

<span data-ttu-id="2543e-180">Como foi feito anteriormente, você deve inicializar o objeto de lista com um valor não nulo ou o compilador emitirá um aviso.</span><span class="sxs-lookup"><span data-stu-id="2543e-180">As before, you must initialize the list object to a non-null value or the compiler issues a warning.</span></span> <span data-ttu-id="2543e-181">Não há verificações de valores nulos na segunda sobrecarga de `AddQuestion`, pois elas são desnecessárias: você declarou que a variável não permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="2543e-181">There are no null checks in the second overload of `AddQuestion` because they aren't needed: You've declared that variable to be non-nullable.</span></span> <span data-ttu-id="2543e-182">Seu valor não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="2543e-182">Its value can't be `null`.</span></span>

<span data-ttu-id="2543e-183">Alterne para `Program.cs` no editor e substitua o conteúdo de `Main` pelas seguintes linhas de código:</span><span class="sxs-lookup"><span data-stu-id="2543e-183">Switch to `Program.cs` in your editor and replace the contents of `Main` with the following lines of code:</span></span>

[!code-csharp[AddQuestions](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

<span data-ttu-id="2543e-184">Sem o pragma `#nullable enable` na parte superior do arquivo, o compilador não emitirá um aviso quando você passar `null` como o texto do argumento `AddQuestion`.</span><span class="sxs-lookup"><span data-stu-id="2543e-184">Without the `#nullable enable` pragma at the top of the file, the compiler doesn't issue a warning when you pass `null` as the text for the `AddQuestion` argument.</span></span> <span data-ttu-id="2543e-185">Para corrigir isso, adicione `#nullable enable` após a instrução `using`.</span><span class="sxs-lookup"><span data-stu-id="2543e-185">Fix that by adding `#nullable enable` following the `using` statement.</span></span> <span data-ttu-id="2543e-186">Experimente adicionar a seguinte linha a `Main`:</span><span class="sxs-lookup"><span data-stu-id="2543e-186">Try it by adding the following line to `Main`:</span></span>

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a><span data-ttu-id="2543e-187">Criar entrevistados e obter respostas para a pesquisa</span><span class="sxs-lookup"><span data-stu-id="2543e-187">Create respondents and get answers to the survey</span></span>

<span data-ttu-id="2543e-188">Em seguida, grave o código que gerará respostas para a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="2543e-188">Next, write the code that generates answers to the survey.</span></span> <span data-ttu-id="2543e-189">Isso envolverá várias tarefas de pequeno porte:</span><span class="sxs-lookup"><span data-stu-id="2543e-189">This involves several small tasks:</span></span>

1. <span data-ttu-id="2543e-190">Criar um método para gerar objetos dos entrevistados.</span><span class="sxs-lookup"><span data-stu-id="2543e-190">Build a method that generates respondent objects.</span></span> <span data-ttu-id="2543e-191">Eles representam pessoas solicitadas a preencher a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="2543e-191">These represent people asked to fill out the survey.</span></span>
1. <span data-ttu-id="2543e-192">Criar lógica para simular a realização de perguntas para um pesquisado e coletar respostas ou perceber que um pesquisado não respondeu.</span><span class="sxs-lookup"><span data-stu-id="2543e-192">Build logic to simulate asking the questions to a respondent and collecting answers or noting that a respondent didn't answer.</span></span>
1. <span data-ttu-id="2543e-193">Repetir até que entrevistados suficientes tenham respondido à pesquisa.</span><span class="sxs-lookup"><span data-stu-id="2543e-193">Repeat until enough respondents have answered the survey.</span></span>

<span data-ttu-id="2543e-194">Será necessária uma classe para representar uma resposta da pesquisa. Adicione-a agora.</span><span class="sxs-lookup"><span data-stu-id="2543e-194">You'll need a class to represent a survey response, so add that now.</span></span> <span data-ttu-id="2543e-195">Habilitar o suporte para tipos que permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="2543e-195">Enable nullable support.</span></span> <span data-ttu-id="2543e-196">Adicione uma propriedade `Id` e um construtor para inicializá-la, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="2543e-196">Add an `Id` property and a constructor that initializes it, as shown in the following code:</span></span>

```csharp
#nullable enable
namespace NullableIntroduction
{
    public class SurveyResponse
    {
        public int Id { get; }

        public SurveyResponse(int id) => Id = id;
    }
}
```

<span data-ttu-id="2543e-197">Em seguida, adicione um método `static` para criar novos participantes ao gerar uma ID aleatória:</span><span class="sxs-lookup"><span data-stu-id="2543e-197">Next, add a `static` method to create new participants by generating a random ID:</span></span>

[!code-csharp[GenerateRespondents](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

<span data-ttu-id="2543e-198">A principal responsabilidade dessa classe é gerar as respostas de um participante para as perguntas da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="2543e-198">The main responsibility of this class is to generate the responses for a participant to the questions in the survey.</span></span> <span data-ttu-id="2543e-199">Essa responsabilidade conta com algumas etapas:</span><span class="sxs-lookup"><span data-stu-id="2543e-199">This responsibility has a few steps:</span></span>

1. <span data-ttu-id="2543e-200">Peça para participar da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="2543e-200">Ask for participation in the survey.</span></span> <span data-ttu-id="2543e-201">Se a pessoa não consentir, retorne uma resposta de ausente (ou de valor nulo).</span><span class="sxs-lookup"><span data-stu-id="2543e-201">If the person doesn't consent, return a missing (or null) response.</span></span>
1. <span data-ttu-id="2543e-202">Faça as perguntas e registre a resposta.</span><span class="sxs-lookup"><span data-stu-id="2543e-202">Ask each question and record the answer.</span></span> <span data-ttu-id="2543e-203">As respostas também pode ser ausentes (ou de valor nulo).</span><span class="sxs-lookup"><span data-stu-id="2543e-203">Each answer may also be missing (or null).</span></span>

<span data-ttu-id="2543e-204">Adicione o seguinte código à classe `SurveyRespondent`:</span><span class="sxs-lookup"><span data-stu-id="2543e-204">Add the following code to your `SurveyRespondent` class:</span></span>

[!code-csharp[AnswerSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

<span data-ttu-id="2543e-205">O armazenamento das respostas da pesquisa é um `Dictionary<int, string>?`, indicando que ele pode ser um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="2543e-205">The storage for the survey answers is a `Dictionary<int, string>?`, indicating that it may be null.</span></span> <span data-ttu-id="2543e-206">Você está usando o novo recurso de idioma para declarar sua intenção de design, tanto para o compilador quanto para qualquer pessoa que leia seu código posteriormente.</span><span class="sxs-lookup"><span data-stu-id="2543e-206">You're using the new language feature to declare your design intent, both to the compiler and to anyone reading your code later.</span></span> <span data-ttu-id="2543e-207">Se você já tiver desconsiderado `surveyResponses` sem verificar o valor nulo primeiro, receberá um aviso do compilador.</span><span class="sxs-lookup"><span data-stu-id="2543e-207">If you ever dereference `surveyResponses` without checking for the null value first, you'll get a compiler warning.</span></span> <span data-ttu-id="2543e-208">Você não receberá um aviso no método `AnswerSurvey` porque o compilador pode determinar que a variável `surveyResponses` foi definida como um valor não nulo acima.</span><span class="sxs-lookup"><span data-stu-id="2543e-208">You don't get a warning in the `AnswerSurvey` method because the compiler can determine the `surveyResponses` variable was set to a non-null value above.</span></span>

<span data-ttu-id="2543e-209">Em seguida, é necessário gravar o método `PerformSurvey` na classe `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="2543e-209">Next, you need to write the `PerformSurvey` method in the `SurveyRun` class.</span></span> <span data-ttu-id="2543e-210">Adicione o seguinte código à classe `SurveyRun`:</span><span class="sxs-lookup"><span data-stu-id="2543e-210">Add the following code in the `SurveyRun` class:</span></span>

[!code-csharp[PerformSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

<span data-ttu-id="2543e-211">Aqui, novamente, sua opção por uma `List<SurveyResponse>?` que permite valor nulo indica que a resposta pode ser um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="2543e-211">Here again, your choice of a nullable `List<SurveyResponse>?` indicates the response may be null.</span></span> <span data-ttu-id="2543e-212">Isso indica que a pesquisa ainda não foi entregue a nenhum pesquisado.</span><span class="sxs-lookup"><span data-stu-id="2543e-212">That indicates the survey hasn't been given to any respondents yet.</span></span> <span data-ttu-id="2543e-213">Observe que os entrevistados são adicionados até que um suficiente de pessoas tiver consentido.</span><span class="sxs-lookup"><span data-stu-id="2543e-213">Notice that respondents are added until enough have consented.</span></span>

<span data-ttu-id="2543e-214">A última etapa para executar a pesquisa é adicionar uma chamada para executar a pesquisa no final do método `Main`:</span><span class="sxs-lookup"><span data-stu-id="2543e-214">The last step to run the survey is to add a call to perform the survey at the end of the `Main` method:</span></span>

[!code-csharp[RunSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a><span data-ttu-id="2543e-215">Examinar as respostas da pesquisa</span><span class="sxs-lookup"><span data-stu-id="2543e-215">Examine survey responses</span></span>

<span data-ttu-id="2543e-216">A última etapa é exibir os resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="2543e-216">The last step is to display survey results.</span></span> <span data-ttu-id="2543e-217">Você adicionará código a várias classes gravadas.</span><span class="sxs-lookup"><span data-stu-id="2543e-217">You'll add code to many of the classes you've written.</span></span> <span data-ttu-id="2543e-218">Este código demonstra o valor da distinção dos tipos de referência que permitem valor nulo e tipos de referência que não permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="2543e-218">This code demonstrates the value of distinguishing nullable and non-nullable reference types.</span></span> <span data-ttu-id="2543e-219">Comece adicionando os dois membros com corpo de expressão à classe `SurveyResponse`:</span><span class="sxs-lookup"><span data-stu-id="2543e-219">Start by adding the following two expression-bodied members to the `SurveyResponse` class:</span></span>

[!code-csharp[ReportResponses](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

<span data-ttu-id="2543e-220">Como `surveyResponses` é uma referência que não permite valor nulo, digite que as verificações não são necessárias antes de desconsiderá-la.</span><span class="sxs-lookup"><span data-stu-id="2543e-220">Because `surveyResponses` is a non-nullable reference, type no checks are necessary before de-referencing it.</span></span> <span data-ttu-id="2543e-221">O método `Answer` retorna uma cadeia de caracteres que não permite valor nulo, portanto, escolha a sobrecarga de `GetValueOrDefault` que recebe um segundo argumento para o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="2543e-221">The `Answer` method returns a non-nullable string, so choose the overload of `GetValueOrDefault` that takes a second argument for the default value.</span></span>

<span data-ttu-id="2543e-222">Em seguida, adicione esses três membros com corpo de expressão à classe `SurveyRun`:</span><span class="sxs-lookup"><span data-stu-id="2543e-222">Next, add these three expression-bodied members to the `SurveyRun` class:</span></span>

[!code-csharp[ReportResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

<span data-ttu-id="2543e-223">O membro `AllParticipants` deve levar em conta que a variável `respondents` pode ser um valor nulo, mas o valor de retorno não pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="2543e-223">The `AllParticipants` member must take into account that the `respondents` variable might be null, but the return value can't be null.</span></span> <span data-ttu-id="2543e-224">Se você alterar essa expressão removendo `??` e a sequência vazia que se segue, o compilador avisará que o método poderá retornar `null` e sua assinatura de retorno retornará um tipo que não permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="2543e-224">If you change that expression by removing the `??` and the empty sequence that follows, the compiler warns you the method might return `null` and its return signature returns a non-nullable type.</span></span>

<span data-ttu-id="2543e-225">Por fim, adicione o seguinte loop à parte inferior do método `Main`:</span><span class="sxs-lookup"><span data-stu-id="2543e-225">Finally, add the following loop at the bottom of the `Main` method:</span></span>

[!code-csharp[DisplaySurveyResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

<span data-ttu-id="2543e-226">Você não precisa de verificações de `null` neste código porque criou as interfaces subjacentes para que todas elas retornem tipos de referência que não permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="2543e-226">You don't need any `null` checks in this code because you've designed the underlying interfaces so that they all return non-nullable reference types.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="2543e-227">Obter o código</span><span class="sxs-lookup"><span data-stu-id="2543e-227">Get the code</span></span>

<span data-ttu-id="2543e-228">Obtenha o código do tutorial concluído em nosso repositório de [exemplos](https://github.com/dotnet/samples) na pasta [csharp/IntroToNullables](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction).</span><span class="sxs-lookup"><span data-stu-id="2543e-228">You can get the code for the finished tutorial from our [samples](https://github.com/dotnet/samples) repository in the [csharp/IntroToNullables](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) folder.</span></span>

<span data-ttu-id="2543e-229">Experimente alterar as declarações de tipo entre os tipos de referência que permitem valor nulo e tipos de referência que não permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="2543e-229">Experiment by changing the type declarations between nullable and non-nullable reference types.</span></span> <span data-ttu-id="2543e-230">Veja como isso gera avisos diferentes para garantir que um `null` não será acidentalmente cancelado.</span><span class="sxs-lookup"><span data-stu-id="2543e-230">See how that generates different warnings to ensure you don't accidentally dereference a `null`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2543e-231">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="2543e-231">Next steps</span></span>

<span data-ttu-id="2543e-232">Para saber mais, leia uma visão geral dos tipos de referência que permitem valor nulo...</span><span class="sxs-lookup"><span data-stu-id="2543e-232">Learn more by reading an overview of nullable reference types..</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="2543e-233">Uma visão geral das referências que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="2543e-233">An overview of nullable references</span></span>](../nullable-references.md)
