---
title: Criar um aplicativo de lista de campeonato com o Infer.NET e a programação probabilística
description: Descubra como usar a programação probabilística com o Infern.NET para criar um aplicativo de lista de campeonato com base em uma versão simplificada do TrueSkill.
ms.date: 05/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: f6f91aecfe7fdeffb7e8913309046c7942ecbab7
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71957208"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a>Criar um aplicativo de lista de campeonato com o Infer.NET e a programação probabilística

Este guia de instruções ensina você sobre a programação probabilística usando o Infer.NET. A programação probabilística é uma abordagem de aprendizado de máquina em que os modelos personalizados são expressados como programas de computador. Ela permite a incorporação de conhecimento de domínio aos modelos, além de tornar o sistema de aprendizado de máquina mais interpretável. Ela também dá suporte à inferência online – o processo de aprender à medida que novos dados são apresentados. O Infer.NET é usado em vários produtos da Microsoft no Azure, Xbox e Bing.

## <a name="what-is-probabilistic-programming"></a>O que é programação probabilística?

A programação probabilística nos permite criar modelos estatísticos de processos do mundo real.

## <a name="prerequisites"></a>Pré-requisitos

- Ambiente de desenvolvimento local configurado

  Este guia de instruções supõe que você tenha um computador que possa ser usado para desenvolvimento. O tutorial do .NET [Olá, mundo em 10 minutos](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) tem instruções para configurar seu ambiente de desenvolvimento local no MacOS, Windows ou Linux.

## <a name="create-your-app"></a>Criar seu aplicativo

1. Abra um prompt de comando e execute os seguintes comandos:

```dotnetcli
dotnet new console -o myApp
cd myApp
```

O comando `dotnet` cria um aplicativo `new` do tipo `console`. O parâmetro `-o` cria um diretório chamado `myApp` onde o seu aplicativo é armazenado e o popula com os arquivos necessários. O comando `cd myApp` coloca você no diretório do aplicativo recém-criado.

## <a name="install-infernet-package"></a>Instalar o pacote Infer.NET

Para usar o Infer.NET, você precisa instalar o pacote `Microsoft.ML.Probabilistic.Compiler`. No prompt de comando, execute o seguinte comando:

```dotnetcli
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a>Projetar o modelo

O exemplo a seguir usa partidas de pingue-pongue ou pebolim dentro da empresa. Temos os participantes e o resultado de cada jogo.  Queremos inferir habilidades do jogador usando esses dados. Suponha que cada jogador tenha uma habilidade latente distribuída normalmente e que o desempenho em uma determinada partida seja uma versão com ruídos dessa habilidade. Os dados forçam o desempenho do vencedor a ser superior ao desempenho do perdedor. Essa é uma versão simplificada do modelo popular do [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/), que também dá suporte a equipes, sorteios e outras extensões. Uma [versão avançada](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) desse modelo é usada para organizar partidas em dois jogos muito vendidos, Halo e Gears of War.

Precisamos listar as habilidades inferidas do jogador com a respectiva variação – a medição da incerteza em torno das habilidades.

*Dados de exemplo do resultado do jogo*

Jogo |Vencedor | Perdedor
---------|----------|---------
 1 | Jogador 0 | Jogador 1
 2 | Jogador 0 | Jogador 3
 3 | Jogador 0 | Jogador 4
 4 | Jogador 1 | Jogador 2
 5 | Jogador 3 | Jogador 1
 6 | Jogador 4 | Jogador 2

Observando atentamente os dados de exemplo, você perceberá que os jogadores 3 e 4 têm uma vitória e uma derrota. Vamos ver como ficariam as classificações usando a programação probabilística. Observe também que há um jogador zero, pois as listas de competição do escritório são baseadas em zero para nós, desenvolvedores.

## <a name="write-some-code"></a>Escrever algum código

Tendo projetado o modelo, é hora de expressá-lo como um programa probabilístico usando a API de modelagem do Infer.NET. Abra `Program.cs` em seu editor de texto de preferência e substitua todo o seu conteúdo pelo seguinte código:

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

## <a name="run-your-app"></a>Executar seu aplicativo

No prompt de comando, execute o seguinte comando:

```dotnetcli
dotnet run
```

## <a name="results"></a>Resultados

Os resultados devem ser semelhantes aos seguintes:

```console
Compiling model...done.
Iterating:
.........|.........|.........|.........|.........| 50
Player 0 skill: Gaussian(9.517, 3.926)
Player 3 skill: Gaussian(6.834, 3.892)
Player 4 skill: Gaussian(6.054, 4.731)
Player 1 skill: Gaussian(4.955, 3.503)
Player 2 skill: Gaussian(2.639, 4.288)
```

Nos resultados, observe que o jogador 3 está classificado ligeiramente acima do jogador 4, de acordo com o nosso modelo. Isso porque a vitória do jogador 3 sobre o jogador 1 é mais significativa do que a vitória do jogador 4 sobre o jogador 2 – observe que o jogador 1 ganha do jogador 2. O jogador 0 é o campeão absoluto!

## <a name="keep-learning"></a>Continuar aprendendo

Projetar modelos estatísticos é uma habilidade por si só. A equipe da Microsoft Research Cambridge disponibilizou um [livro online gratuito](http://mbmlbook.com/), que fornece uma breve introdução ao artigo. O Capítulo 3 deste livro aborda o modelo do TrueSkill em mais detalhes. Assim que tiver um modelo em mente, você pode transformá-lo em código usando a [extensa documentação](https://dotnet.github.io/infer/) no site do Infer.NET.

## <a name="next-steps"></a>Próximas etapas

Confira o repositório GitHub do Infer.NET para continuar aprendendo e encontrar mais exemplos.
> [!div class="nextstepaction"]
> [repositório GitHub dotnet/infer](https://github.com/dotnet/infer)
