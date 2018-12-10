---
title: Criar um aplicativo de lista de campeonato com o Infer.NET e a programação probabilística
description: Descubra como usar a programação probabilística com o Infern.NET para criar um aplicativo de lista de campeonato com base em uma versão simplificada do TrueSkill.
ms.date: 10/04/2018
ms.custom: mvc,how-to
ms.openlocfilehash: ceeb0f43e03c7ce93f105498f44bf243eec86bbf
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152455"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a><span data-ttu-id="d9055-103">Criar um aplicativo de lista de campeonato com o Infer.NET e a programação probabilística</span><span class="sxs-lookup"><span data-stu-id="d9055-103">Create a game match up list app with Infer.NET and probabilistic programming</span></span>

<span data-ttu-id="d9055-104">Este guia de instruções ensina você sobre a programação probabilística usando o Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="d9055-104">This how-to guide teaches you about probabilistic programming using Infer.NET.</span></span> <span data-ttu-id="d9055-105">A programação probabilística é uma abordagem de aprendizado de máquina em que os modelos personalizados são expressados como programas de computador.</span><span class="sxs-lookup"><span data-stu-id="d9055-105">Probabilistic programming is a machine learning approach where custom models are expressed as computer programs.</span></span> <span data-ttu-id="d9055-106">Ela permite a incorporação de conhecimento de domínio aos modelos, além de tornar o sistema de aprendizado de máquina mais interpretável.</span><span class="sxs-lookup"><span data-stu-id="d9055-106">It allows for incorporating domain knowledge in the models and makes the machine learning system more interpretable.</span></span> <span data-ttu-id="d9055-107">Ela também dá suporte à inferência online – o processo de aprender à medida que novos dados são apresentados.</span><span class="sxs-lookup"><span data-stu-id="d9055-107">It also supports online inference – the process of learning as new data arrives.</span></span> <span data-ttu-id="d9055-108">O Infer.NET é usado em vários produtos da Microsoft no Azure, Xbox e Bing.</span><span class="sxs-lookup"><span data-stu-id="d9055-108">Infer.NET is used in various products at Microsoft in Azure, Xbox, and Bing.</span></span>

## <a name="what-is-probabilistic-programming"></a><span data-ttu-id="d9055-109">O que é programação probabilística?</span><span class="sxs-lookup"><span data-stu-id="d9055-109">What is probabilistic programming?</span></span>

<span data-ttu-id="d9055-110">A programação probabilística nos permite criar modelos estatísticos de processos do mundo real.</span><span class="sxs-lookup"><span data-stu-id="d9055-110">Probabilistic programming allows us to create statistical models of real-world processes.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="d9055-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d9055-111">Prerequisites</span></span>

- <span data-ttu-id="d9055-112">Ambiente de desenvolvimento local configurado</span><span class="sxs-lookup"><span data-stu-id="d9055-112">Local development environment setup</span></span>

  <span data-ttu-id="d9055-113">Este guia de instruções supõe que você tenha um computador que possa ser usado para desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="d9055-113">This how-to guide expects you to have a machine you can use for development.</span></span> <span data-ttu-id="d9055-114">O tutorial do .NET [Familiarize-se em 10 minutos](https://www.microsoft.com/net/core) tem instruções para configurar o ambiente de desenvolvimento local no Mac, PC ou Linux.</span><span class="sxs-lookup"><span data-stu-id="d9055-114">The .NET [Get Started in 10 minutes](https://www.microsoft.com/net/core) tutorial has instructions for setting up your local development environment on Mac, PC, or Linux.</span></span>

## <a name="create-your-app"></a><span data-ttu-id="d9055-115">Criar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="d9055-115">Create your app</span></span>

1. <span data-ttu-id="d9055-116">Abra um prompt de comando e execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="d9055-116">Open a new command prompt and run the following commands:</span></span>

```console
dotnet new console -o myApp
cd myApp
```

<span data-ttu-id="d9055-117">O comando `dotnet` cria um aplicativo `new` do tipo `console`.</span><span class="sxs-lookup"><span data-stu-id="d9055-117">The `dotnet` command creates a `new` application of type `console`.</span></span> <span data-ttu-id="d9055-118">O parâmetro `-o` cria um diretório chamado `myApp` onde o seu aplicativo é armazenado e o popula com os arquivos necessários.</span><span class="sxs-lookup"><span data-stu-id="d9055-118">The `-o` parameter creates a directory named `myApp` where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="d9055-119">O comando `cd myApp` coloca você no diretório do aplicativo recém-criado.</span><span class="sxs-lookup"><span data-stu-id="d9055-119">The `cd myApp` command puts you into the newly created app directory.</span></span>

## <a name="install-infernet-package"></a><span data-ttu-id="d9055-120">Instalar o pacote Infer.NET</span><span class="sxs-lookup"><span data-stu-id="d9055-120">Install Infer.NET package</span></span>

<span data-ttu-id="d9055-121">Para usar o Infer.NET, você precisa instalar o pacote `Microsoft.ML.Probabilistic.Compiler`.</span><span class="sxs-lookup"><span data-stu-id="d9055-121">To use Infer.NET, you need to install the `Microsoft.ML.Probabilistic.Compiler` package.</span></span> <span data-ttu-id="d9055-122">No prompt de comando, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="d9055-122">In your command prompt, run the following command:</span></span>

```console
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a><span data-ttu-id="d9055-123">Projetar o modelo</span><span class="sxs-lookup"><span data-stu-id="d9055-123">Design your model</span></span>

<span data-ttu-id="d9055-124">O exemplo a seguir usa partidas de pingue-pongue ou pebolim dentro da empresa.</span><span class="sxs-lookup"><span data-stu-id="d9055-124">The example sample uses table tennis or foosball matches played in the office.</span></span> <span data-ttu-id="d9055-125">Temos os participantes e o resultado de cada jogo.</span><span class="sxs-lookup"><span data-stu-id="d9055-125">We have the participants and outcome of each match.</span></span>  <span data-ttu-id="d9055-126">Queremos inferir habilidades do jogador usando esses dados.</span><span class="sxs-lookup"><span data-stu-id="d9055-126">We want to infer the player's skills from this data.</span></span> <span data-ttu-id="d9055-127">Vamos supor que cada jogador tenha uma habilidade latente distribuída normalmente e que o desempenho em uma determinada partida seja uma versão com ruídos dessa habilidade.</span><span class="sxs-lookup"><span data-stu-id="d9055-127">We’ll assume that each player has a normally distributed latent skill and their performance in a given match is a noisy version of this skill.</span></span> <span data-ttu-id="d9055-128">Os dados forçam o desempenho do vencedor a ser superior ao desempenho do perdedor.</span><span class="sxs-lookup"><span data-stu-id="d9055-128">The data constrains the winner’s performance to be greater than the loser’s performance.</span></span> <span data-ttu-id="d9055-129">Essa é uma versão simplificada do modelo popular do [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/), que também dá suporte a equipes, sorteios e outras extensões.</span><span class="sxs-lookup"><span data-stu-id="d9055-129">This is a simplified version of the popular [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/) model, which also supports teams, draws, and other extensions.</span></span> <span data-ttu-id="d9055-130">Uma [versão avançada](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) desse modelo é usada para organizar partidas em dois jogos muito vendidos, Halo e Gears of War.</span><span class="sxs-lookup"><span data-stu-id="d9055-130">An [advanced version](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) of this model is used for matchmaking in the best-selling game titles Halo and Gears of War.</span></span>

<span data-ttu-id="d9055-131">Precisamos listar as habilidades inferidas do jogador com a respectiva variação – a medição da incerteza em torno das habilidades.</span><span class="sxs-lookup"><span data-stu-id="d9055-131">We need to list the inferred player skills, alongside with their variance – the measure of uncertainty around the skills.</span></span>

<span data-ttu-id="d9055-132">*Dados de exemplo do resultado do jogo*</span><span class="sxs-lookup"><span data-stu-id="d9055-132">*Game result sample data*</span></span>

<span data-ttu-id="d9055-133">Jogo</span><span class="sxs-lookup"><span data-stu-id="d9055-133">Game</span></span> |<span data-ttu-id="d9055-134">Vencedor</span><span class="sxs-lookup"><span data-stu-id="d9055-134">Winner</span></span> | <span data-ttu-id="d9055-135">Perdedor</span><span class="sxs-lookup"><span data-stu-id="d9055-135">Loser</span></span>
---------|----------|---------
 <span data-ttu-id="d9055-136">1</span><span class="sxs-lookup"><span data-stu-id="d9055-136">1</span></span> | <span data-ttu-id="d9055-137">Jogador 0</span><span class="sxs-lookup"><span data-stu-id="d9055-137">Player 0</span></span> | <span data-ttu-id="d9055-138">Jogador 1</span><span class="sxs-lookup"><span data-stu-id="d9055-138">Player 1</span></span>
 <span data-ttu-id="d9055-139">2</span><span class="sxs-lookup"><span data-stu-id="d9055-139">2</span></span> | <span data-ttu-id="d9055-140">Jogador 0</span><span class="sxs-lookup"><span data-stu-id="d9055-140">Player 0</span></span> | <span data-ttu-id="d9055-141">Jogador 3</span><span class="sxs-lookup"><span data-stu-id="d9055-141">Player 3</span></span>
 <span data-ttu-id="d9055-142">3</span><span class="sxs-lookup"><span data-stu-id="d9055-142">3</span></span> | <span data-ttu-id="d9055-143">Jogador 0</span><span class="sxs-lookup"><span data-stu-id="d9055-143">Player 0</span></span> | <span data-ttu-id="d9055-144">Jogador 4</span><span class="sxs-lookup"><span data-stu-id="d9055-144">Player 4</span></span>
 <span data-ttu-id="d9055-145">4</span><span class="sxs-lookup"><span data-stu-id="d9055-145">4</span></span> | <span data-ttu-id="d9055-146">Jogador 1</span><span class="sxs-lookup"><span data-stu-id="d9055-146">Player 1</span></span> | <span data-ttu-id="d9055-147">Jogador 2</span><span class="sxs-lookup"><span data-stu-id="d9055-147">Player 2</span></span>
 <span data-ttu-id="d9055-148">5</span><span class="sxs-lookup"><span data-stu-id="d9055-148">5</span></span> | <span data-ttu-id="d9055-149">Jogador 3</span><span class="sxs-lookup"><span data-stu-id="d9055-149">Player 3</span></span> | <span data-ttu-id="d9055-150">Jogador 1</span><span class="sxs-lookup"><span data-stu-id="d9055-150">Player 1</span></span>
 <span data-ttu-id="d9055-151">6</span><span class="sxs-lookup"><span data-stu-id="d9055-151">6</span></span> | <span data-ttu-id="d9055-152">Jogador 4</span><span class="sxs-lookup"><span data-stu-id="d9055-152">Player 4</span></span> | <span data-ttu-id="d9055-153">Jogador 2</span><span class="sxs-lookup"><span data-stu-id="d9055-153">Player 2</span></span>

<span data-ttu-id="d9055-154">Observando atentamente os dados de exemplo, você perceberá que os jogadores 3 e 4 têm uma vitória e uma derrota.</span><span class="sxs-lookup"><span data-stu-id="d9055-154">With a closer look at the sample data, you’ll notice that players 3 and 4 both have one win and one loss.</span></span> <span data-ttu-id="d9055-155">Vamos ver como ficariam as classificações usando a programação probabilística.</span><span class="sxs-lookup"><span data-stu-id="d9055-155">Let's see what the rankings look like using probabilistic programming.</span></span> <span data-ttu-id="d9055-156">Observe também que há um jogador zero, pois as listas de competição do escritório são baseadas em zero para nós, desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="d9055-156">Notice also there is a player zero because even office match up lists are zero based to us developers.</span></span>

## <a name="write-some-code"></a><span data-ttu-id="d9055-157">Escrever algum código</span><span class="sxs-lookup"><span data-stu-id="d9055-157">Write some code</span></span>

<span data-ttu-id="d9055-158">Tendo projetado o modelo, é hora de expressá-lo como um programa probabilístico usando a API de modelagem do Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="d9055-158">Having designed the model, it’s time to express it as a probabilistic program using the Infer.NET modeling API.</span></span> <span data-ttu-id="d9055-159">Abra `Program.cs` em seu editor de texto de preferência e substitua todo o seu conteúdo pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="d9055-159">Open `Program.cs` in your favorite text editor and replace all of its contents with the following code:</span></span>

```csharp
namespace myApp

{
    using System;
    using System.Linq;
    using Microsoft.ML.Probabilistic;
    using Microsoft.ML.Probabilistic.Distributions;
    using Microsoft.ML.Probabilistic.Models;

    class Program
    {

        static void Main(string[] args)
        {
            // The winner and loser in each of 6 samples games
            var winnerData = new[] { 0, 0, 0, 1, 3, 4 };
            var loserData = new[] { 1, 3, 4, 2, 1, 2 };

            // Define the statistical model as a probabilistic program 
            var game = new Range(winnerData.Length);
            var player = new Range(winnerData.Concat(loserData).Max() + 1);
            var playerSkills = Variable.Array<double>(player);
            playerSkills[player] = Variable.GaussianFromMeanAndVariance(6, 9).ForEach(player);

            var winners = Variable.Array<int>(game);
            var losers = Variable.Array<int>(game);

            using (Variable.ForEach(game))
            {
                // The player performance is a noisy version of their skill
                var winnerPerformance = Variable.GaussianFromMeanAndVariance(playerSkills[winners[game]], 1.0);
                var loserPerformance = Variable.GaussianFromMeanAndVariance(playerSkills[losers[game]], 1.0);

                // The winner performed better in this game
                Variable.ConstrainTrue(winnerPerformance > loserPerformance);
            }

            // Attach the data to the model
            winners.ObservedValue = winnerData;
            losers.ObservedValue = loserData;

            // Run inference
            var inferenceEngine = new InferenceEngine();
            var inferredSkills = inferenceEngine.Infer<Gaussian[]>(playerSkills);

            // The inferred skills are uncertain, which is captured in their variance
            var orderedPlayerSkills = inferredSkills
               .Select((s, i) => new { Player = i, Skill = s })
               .OrderByDescending(ps => ps.Skill.GetMean());

            foreach (var playerSkill in orderedPlayerSkills)
            {
                Console.WriteLine($"Player {playerSkill.Player} skill: {playerSkill.Skill}");
            }
        }
    }
}
```

## <a name="run-your-app"></a><span data-ttu-id="d9055-160">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="d9055-160">Run your app</span></span>

<span data-ttu-id="d9055-161">No prompt de comando, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="d9055-161">In your command prompt, run the following command:</span></span>

```console
dotnet run
```

## <a name="results"></a><span data-ttu-id="d9055-162">Resultados</span><span class="sxs-lookup"><span data-stu-id="d9055-162">Results</span></span>

<span data-ttu-id="d9055-163">Os resultados devem ser semelhantes aos seguintes:</span><span class="sxs-lookup"><span data-stu-id="d9055-163">Your results should be similar to the following:</span></span>

```
Compiling model...done.
Iterating:
.........|.........|.........|.........|.........| 50
Player 0 skill: Gaussian(9.517, 3.926)
Player 3 skill: Gaussian(6.834, 3.892)
Player 4 skill: Gaussian(6.054, 4.731)
Player 1 skill: Gaussian(4.955, 3.503)
Player 2 skill: Gaussian(2.639, 4.288)
```

<span data-ttu-id="d9055-164">Nos resultados, observe que o jogador 3 está classificado ligeiramente acima do jogador 4, de acordo com o nosso modelo.</span><span class="sxs-lookup"><span data-stu-id="d9055-164">In the results, notice that player 3 ranks slightly higher than player 4 according to our model.</span></span> <span data-ttu-id="d9055-165">Isso porque a vitória do jogador 3 sobre o jogador 1 é mais significativa do que a vitória do jogador 4 sobre o jogador 2 – observe que o jogador 1 ganha do jogador 2.</span><span class="sxs-lookup"><span data-stu-id="d9055-165">That’s because the victory of player 3 over player 1 is more significant than the victory of player 4 over player 2 – note that player 1 beats player 2.</span></span> <span data-ttu-id="d9055-166">O jogador 0 é o campeão absoluto!</span><span class="sxs-lookup"><span data-stu-id="d9055-166">Player 0 is the overall champ!</span></span>  

## <a name="keep-learning"></a><span data-ttu-id="d9055-167">Continuar aprendendo</span><span class="sxs-lookup"><span data-stu-id="d9055-167">Keep learning</span></span>

<span data-ttu-id="d9055-168">Projetar modelos estatísticos é uma habilidade por si só.</span><span class="sxs-lookup"><span data-stu-id="d9055-168">Designing statistical models is a skill on its own.</span></span> <span data-ttu-id="d9055-169">A equipe da Microsoft Research Cambridge disponibilizou um [livro online gratuito](http://mbmlbook.com/), que fornece uma breve introdução ao artigo.</span><span class="sxs-lookup"><span data-stu-id="d9055-169">The Microsoft Research Cambridge team has written a [free online book](http://mbmlbook.com/), which gives a gentle introduction to the article.</span></span> <span data-ttu-id="d9055-170">O Capítulo 3 deste livro aborda o modelo do TrueSkill em mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="d9055-170">Chapter 3 of this book covers the TrueSkill model in more detail.</span></span> <span data-ttu-id="d9055-171">Assim que tiver um modelo em mente, você pode transformá-lo em código usando a [extensa documentação](https://dotnet.github.io/infer/) no site do Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="d9055-171">Once you have a model in mind, you can transform it into code using the [extensive documentation](https://dotnet.github.io/infer/) on the Infer.NET website.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d9055-172">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="d9055-172">Next steps</span></span>

<span data-ttu-id="d9055-173">Confira o repositório GitHub do Infer.NET para continuar aprendendo e encontrar mais exemplos.</span><span class="sxs-lookup"><span data-stu-id="d9055-173">Check out the Infer.NET GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="d9055-174">repositório GitHub dotnet/infer</span><span class="sxs-lookup"><span data-stu-id="d9055-174">dotnet/infer GitHub repository</span></span>](https://github.com/dotnet/infer)
