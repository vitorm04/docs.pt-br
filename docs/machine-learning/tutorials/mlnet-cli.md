---
title: Analisar sentimentos com a CLI do ML.NET
description: Gerar automaticamente um modelo de ML e o código C# relacionado de um conjunto de dados de exemplo
author: cesardl
ms.author: cesardl
ms.date: 04/24/2019
ms.custom: mvc
ms.topic: tutorial
ms.openlocfilehash: 6dbd69c8424227f85d8bf3cdcaf6cf9dbf7e1f4c
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856026"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a>Analisar sentimentos com a CLI do ML.NET

Saiba como usar a CLI do ML.NET para gerar automaticamente um modelo do ML.NET e o código C# subjacente. Você fornece o conjunto de dados e a tarefa de aprendizado de máquina que deseja implementar e a CLI usa o mecanismo de AutoML para criar o código-fonte de implantação e geração de modelo, bem como o modelo binário.

Neste tutorial, você realizará as seguintes etapas:
> [!div class="checklist"]
> - Preparar os dados para a tarefa de aprendizado de máquina selecionada
> - Executar o comando 'mlnet auto-train' da CLI
> - Examinar os resultados de métrica de qualidade
> - Entender o código C# gerado para usar o modelo em seu aplicativo
> - Explorar o código C# gerado que foi usado para treinar o modelo

> [!NOTE]
> Este tópico refere-se à ferramenta de CLI do ML.NET que está atualmente em versão prévia. O material pode estar sujeito a alterações. Para obter mais informações, visite a página [ml.net](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) .

A CLI do ML.NET faz parte do ML.NET e sua meta principal é "democratizar" o ML.NET, durante seu aprendizado, para desenvolvedores do .NET, de modo que você não precise escrever o código do zero para começar a usar.

Você pode executar a CLI do ML.NET em qualquer prompt de comando (Windows, Mac ou Linux) para gerar modelos do ML.NET de boa qualidade e código-fonte com base em conjuntos de dados de treinamento que você fornecer.

## <a name="pre-requisites"></a>Pré-requisitos

- [SDK do .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) ou posterior
- (Opcional) [Visual Studio 2017 ou 2019](https://visualstudio.microsoft.com/vs/)
- [CLI do ML.NET](../how-to-guides/install-ml-net-cli.md)

Você pode executar os projetos de C# gerados do Visual Studio ou com o `dotnet run` (CLI do .NET Core).

## <a name="prepare-your-data"></a>Preparar seus dados

Usaremos um conjunto de dados existente usado para um cenário de 'análise de sentimento ', que é uma tarefa de aprendizado de máquina de classificação binária. Você poderá usar seu próprio conjunto de dados de maneira semelhante, sendo que o modelo e o código serão gerados para você.

1. Baixe [o arquivo zip do conjunto de dados de frases rotuladas por sentimento do UCI (consulte citações na observação abaixo)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) e descompacte-o na pasta que você escolher.

    > [!NOTE]
    > Os conjuntos de dados neste tutorial usam um conjunto de dados de 'From Group to Individual Labels using Deep Features' (de grupo para rótulos individuais usando recursos aprofundados), Kotzias et al., KDD 2015, e hospedados no UCI Machine Learning Repository – Dua, D. e Karra Taniskidou, E. (2017). UCI Machine Learning Repository [http://archive.ics.uci.edu/ml ]. Irvine, CA: University of California, School of Information and Computer Science.

2. Copie o arquivo `yelp_labelled.txt` em qualquer pasta que você criou anteriormente (assim como `/cli-test`).

3. Abra o prompt de comando preferido e mova-o para a pasta em que você copiou o arquivo de conjunto de dados. Por exemplo:

    ```console
    > cd /cli-test
    ```

    Usando qualquer editor de texto, por exemplo, o Visual Studio Code, você pode abrir e explorar o arquivo de conjunto de dados `yelp_labelled.txt`. Você pode ver que a estrutura é:

    - O arquivo não tem cabeçalho. Você usará o índice da coluna.

    - Há apenas duas colunas:

        | Texto (índice de coluna 0) | Rótulo (índice de coluna 1)|
        |--------------------------|-------|
        | Puxa! Adorei esse lugar. | 1 |
        | A torrada não é boa. | 0 |
        | Não é saboroso e a textura é simplesmente horrível. | 0 |
        | ... MUITAS OUTRAS LINHAS DE TEXTO... | ...(1 ou 0)... |

    Feche o arquivo de conjunto de dados do editor.

    Agora, você está pronto para começar a usar a CLI para esse cenário de 'análise de sentimento'.

    > [!NOTE]
    > Depois de concluir este tutorial, você também pode experimentar com seus próprios conjuntos de dados enquanto eles estão prontos para ser usados para qualquer uma das tarefas de ML atualmente compatíveis com a versão prévia da CLI do ML.NET, que são *'Classificação binária', 'Classificação multiclasse' e ' Regressão'* .

## <a name="run-the-mlnet-auto-train-command"></a>Execute o comando 'mlnet auto-train'

1. Execute o comando da CLI do ML.NET a seguir:

    ```console
    > mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    Esse comando executa o **comando `mlnet auto-train`** :
    - para uma **tarefa de ML** do tipo **`binary-classification`**
    - usa o **arquivo de conjunto de dados `yelp_labelled.txt`** como treinamento e teste do conjunto de dados (internamente, a CLI usará a validação cruzada ou será dividida em dois conjuntos de dados, um para treinamento e outro para teste)
    - em que a **coluna de destino/objetivo** que você deseja prever (comumente chamada de **'Rótulo'** ) é a coluna **com o índice 1** (que é a segunda coluna, já que o índice é baseado em zero )
    - **não usa um cabeçalho de arquivo** com nomes de coluna, pois esse arquivo de conjunto de dados específico não tem um cabeçalho
    - o **tempo de exploração de destino** para o experimento é de **10 segundos**

    Você verá a saída da CLI, semelhante a:

    <!-- markdownlint-disable MD023 -->
    # <a name="windowstabwindows"></a>[Windows](#tab/windows)

    ![Treinamento automático da CLI do ML.NET no PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bashtabmacosbash"></a>[Bash do macOS](#tab/macosbash)

    ![Treinamento automático da CLI do ML.NET no PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    Nesse caso específico, em apenas 10 segundos e com um pequeno conjunto de dados fornecido, a ferramenta da CLI foi capaz de executar um número considerável de iterações, o que significa que o treinamento foi realizado várias vezes com base em diferentes combinações de algoritmos/configuração com diferentes transformações de dados internos e hiperparâmetros de algoritmo. 

    Por fim, o modelo de "melhor qualidade" encontrado em 10 segundos é um modelo usando um treinador/algoritmo específico com qualquer configuração específica. Dependendo do tempo de exploração, o comando pode produzir um resultado diferente. A seleção é baseada nas várias métricas mostradas, tais como `Accuracy`.

    **Noções básicas sobre as métricas de qualidade do modelo**

    A primeira e mais fácil métrica para avaliar um modelo de classificação binária é a precisão, o que é simples de entender. "Precisão é a proporção de previsões corretas com um conjunto de dados de teste." Quanto mais próximo de 100% (1,00), melhor.

    No entanto, há casos em que apenas medir com a métrica de precisão não é suficiente, especialmente quando o rótulo (0 e 1 neste caso) é desbalanceado no conjunto de dados de teste.

    Para obter métricas adicionais e muito mais **informações detalhadas sobre as métricas** (tais como precisão, AUC, AUCPR, pontuação F1) usadas para avaliar os modelos diferentes, você pode ler [Noções básicas sobre métricas do ML.NET](../resources/metrics.md)

    > [!NOTE]
    > Você pode experimentar esse mesmo conjunto de dados e especificar alguns minutos para `--max-exploration-time` (por exemplo, três minutos, então você especifica 180 segundos) que encontrará um "melhor modelo" para você com uma configuração de pipeline de treinamento diferente para esse conjunto de dados (que é bem pequeno, 1.000 linhas). 
        
    Para localizar um modelo de "melhor/boa qualidade" que é um "modelo de produção" destinado a conjuntos de dados maiores, você deve fazer experimentos com a CLI, geralmente especificando muito mais tempo de exploração, dependendo do tamanho do conjunto de dados. Na verdade, em muitos casos você poderá exigir várias horas de tempo de exploração, especialmente se o conjunto de dados for grande em linhas e colunas. 

1. A execução do comando anterior gerou os seguintes ativos:

    - Um modelo serializado. zip ("melhor modelo") pronto para uso. 
    - Código C# para a execução/pontuação que gerou o modelo (para fazer previsões em seus aplicativos do usuário final com esse modelo).
    - Código de treinamento C# usado para gerar o modelo (para fins de aprendizado).
    - Um arquivo de log com todas as iterações exploradas, tendo específicas informações detalhadas sobre cada algoritmo tentado com a respectiva combinação de hiperparâmetros e transformações de dados. 

    Os primeiros dois ativos (modelo de arquivo zip e código C# a executar) podem ser usados diretamente em seus aplicativos de usuário final (aplicativo Web ASP.NET Core, serviços, aplicativo da Área de Trabalho etc.) para fazer previsões com esse modelo de ML gerado.

    O terceiro ativo, o código de treinamento, mostra a você que o código de API do ML.NET foi usado pela CLI para treinar o modelo gerado, de modo que você pode investigar qual treinador/algoritmo e parâmetros específicos foram selecionados pela CLI.

Esses ativos enumerados são explicados nas etapas do tutorial a seguir.

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a>Explore o código C# gerado a usar para executar o modelo para fazer previsões

1. No Visual Studio (2017 ou 2019), abra a solução gerada na pasta denominada `SampleBinaryClassification` dentro da pasta de destino original (no tutorial, foi nomeada `/cli-test`). Você deve ver uma solução semelhante a:

    > [!NOTE]
    > No tutorial, sugerimos usar o Visual Studio, mas você também pode explorar o código C# gerado (dois projetos) com qualquer editor de texto e executar o aplicativo de console gerado com o `dotnet CLI` no computador macOS, Linux ou Windows.

    ![Solução de VS gerada pela CLI](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - A **biblioteca de classes** gerada que contém o modelo de ML serializado (arquivo .zip) e as classes de dados (modelos de dados) é algo que você pode usar diretamente em seu aplicativo de usuário final, até mesmo referenciando diretamente essa biblioteca de classes (ou movendo o código, como preferir).
    - O **aplicativo de console** gerado contém o código de execução que você precisa revisar e, em seguida, você geralmente reutiliza o 'código de pontuação' (código que executa o modelo de ML para fazer previsões), movendo o código simples (apenas algumas linhas) para seu aplicativo de usuário final em que você deseja fazer as previsões. 

1. Abra os arquivos de classe **ModelInput.cs** e **ModelOutput.cs** dentro do projeto de biblioteca de classes. Você verá que essas classes são 'classes de dados' ou classes POCO usadas para armazenar dados. Trata-se de "código clichê", mas útil gerá-lo se o seu conjunto de dados tiver dezenas ou até mesmo centenas de colunas. 
    - A classe `ModelInput` é usada ao ler dados do conjunto de dados. 
    - A classe `ModelOutput` é usada para obter o resultado da previsão (dados de previsão).

1. Abra o arquivo Program.cs e explore o código. Em apenas algumas linhas, você pode executar o modelo e fazer uma previsão de exemplo.

    ```csharp
    static void Main(string[] args)
    {
        MLContext mlContext = new MLContext();

        // Training code used by ML.NET CLI and AutoML to generate the model
        //ModelBuilder.CreateModel();

        ITransformer mlModel = mlContext.Model.Load(MODEL_FILEPATH, out DataViewSchema inputSchema);
        var predEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // Create sample data to do a single prediction with it 
        ModelInput sampleData = CreateSingleDataSample(mlContext, DATA_FILEPATH);

        // Try a single prediction
        ModelOutput predictionResult = predEngine.Predict(sampleData);

        Console.WriteLine($"Single Prediction --> Actual value: {sampleData.Label} | Predicted value: {predictionResult.Prediction}");
    }
    ```

- A primeira linha de código simplesmente cria um objeto `MLContext` necessário sempre que você executa o código do ML.NET. 

- A segunda linha de código é comentada porque você não precisa treinar o modelo, já que ele já foi treinado para você pela ferramenta de CLI e salvo no arquivo zip serializado do modelo. Mas se quiser ver *"como o modelo foi treinado"* pela CLI, você poderá remover as marcas de comentários dessa linha e executar/depurar o código de treinamento usado por esse modelo de ML específico.

- Na terceira linha de código, você pode carregar o modelo do arquivo zip do modelo serializado com a API `mlContext.Model.Load()`, fornecendo o caminho para esse arquivo zip de modelo.

- Na quarta linha de código que você carregar, crie o `PredictionEngine` do objeto com a API `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)`. Você precisa do objeto `PredictionEngine` sempre que deseja fazer uma previsão visando um único exemplo de dados (nesse caso, uma única parte do texto para prever seu sentimento).

- É na quinta linha de código que você cria esse *único dado de exemplo* a ser usado para a previsão chamando a função `CreateSingleDataSample()`. Já que a ferramenta da CLI não sabe que tipo de dados de exemplo usar, dentro dessa função, ela está carregando a primeira linha do conjunto de dados. No entanto, para esse caso, você também pode criar seus próprios dados embutidos em código em vez da implementação atual da função `CreateSingleDataSample()`, atualizando esse código mais simples implementando essa função:

    ```csharp
    private static ModelInput CreateSingleDataSample()
    {
        ModelInput sampleForPrediction = new ModelInput() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
        return sampleForPrediction;
    }
    ```

1. Execute o projeto, usando os dados de exemplo originais carregados da primeira linha do conjunto de dados ou fornecendo seus próprios dados de exemplo embutidos em código personalizados. Você deve obter uma previsão comparável a:

    # <a name="windowstabwindows"></a>[Windows](#tab/windows)

    Execute o aplicativo de console do Visual Studio pressionando F5 (botão Reproduzir):

    ![Treinamento automático da CLI do ML.NET no PowerShell](./media/mlnet-cli/sample-cli-prediction-execution.png))

    # <a name="macos-bashtabmacosbash"></a>[Bash do macOS](#tab/macosbash)

    Execute o aplicativo de console do prompt de comando, digitando os seguintes comandos:

     ```
     > cd SampleBinaryClassification
     > cd SampleBinaryClassification.ConsoleApp

     > dotnet run
     ```

    ![Treinamento automático da CLI do ML.NET no PowerShell](./media/mlnet-cli/sample-cli-prediction-execution-bash.png))

    ---

1. Tente alterar os dados de exemplo embutidos em código para outras frases com sentimento diferente e veja como o modelo prevê sentimento positivo ou negativo. 

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a>Introduza previsões do modelo de ML em seus aplicativos de usuário final

Você pode usar um 'código de pontuação de modelo de ML' semelhante para executar o modelo em seu aplicativo de usuário final e fazer previsões. 

Por exemplo, você poderia mover diretamente esse código para qualquer aplicativo da Área de Trabalho do Windows (assim como **WPF** e **WinForms**) e executar o modelo da mesma maneira que isso foi feito no aplicativo de console.

No entanto, a maneira como você implementa essas linhas de código para executar um modelo de ML deverá ser otimizada (isto é, armazenar o arquivo zip de modelo em cache e carregue-o uma vez) e ter objetos singleton em vez de criá-los em cada solicitação, especialmente se seu aplicativo precisar ser escalonável, assim como no caso de um aplicativo Web ou um serviço distribuído, conforme explicado na seção a seguir.

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a>Como executar modelos do ML.NET em aplicativos Web ASP.NET Core e serviços escalonáveis (aplicativos multi-threaded)

A criação do objeto de modelo (`ITransformer` carregado do arquivo zip de um modelo) e do objeto `PredictionEngine` deve ser otimizada, especialmente durante a execução em aplicativos Web escalonáveis e serviços distribuídos. No primeiro caso, a otimização do objeto de modelo (`ITransformer`) é simples. Já que o objeto `ITransformer` é thread-safe, você pode armazenar em cache o objeto como um singleton ou um objeto estático, de modo que você carregue o modelo uma vez.

Para o segundo objeto (`PredictionEngine`), isso não é tão fácil porque o objeto `PredictionEngine` não é thread-safe, portanto, você não pode instanciá-lo como singleton ou como um objeto estático em um aplicativo ASP.NET Core. Esse problema de thread-safe e escalabilidade é discutido em profundidade nesta [postagem no blog](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/). 

No entanto, as coisas ficaram muito mais fáceis para você do que aquilo que é explicado nessa postagem no blog. Trabalhamos em uma abordagem mais simples para você e criamos um ótimo **'Pacote de integração do .NET Core'** , que você pode usar facilmente em seus serviços e aplicativos ASP.NET Core registrando-o nos serviços de DI (injeção de dependência) do aplicativo e, em seguida, usando-o diretamente do seu código. Verifique o tutorial e exemplo a seguir para fazer isso:

- [Tutorial: Executando modelos do ML.NET em aplicativos Web e APIs Web escalonáveis do ASP.NET Core](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Exemplo: Modelo do ML.NET escalonável na API Web do ASP.NET Core](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a>Explore o código C# gerado que foi usado para treinar o modelo de "melhor qualidade" 

Para fins de aprendizado mais avançado, você também pode explorar o código C# gerado que foi usado pela ferramenta da CLI para treinar o modelo gerado.

Esse código de modelo de treinamento é gerado atualmente na classe personalizada gerada chamada `ModelBuilder`, de modo que você pode investigar esse código de treinamento.

Mais importante, para esse cenário específico (modelo de análise de sentimento) também é possível comparar esse código de treinamento gerado com o código explicado no tutorial a seguir:

- Compare: [Tutorial: Use do ML.NET em um cenário de classificação binária de análise de sentimento](sentiment-analysis.md).

É interessante comparar a configuração de pipeline e o algoritmo escolhido no tutorial com o código gerado pela ferramenta de CLI. Dependendo de quanto tempo você gasta em iteração e pesquisa por modelos melhores, o algoritmo escolhido pode ser diferente, juntamente com os respectivos hiperparâmetros e configuração de pipeline específicos.

## <a name="see-also"></a>Consulte também

- [Automatizar o treinamento de modelos com a CLI do ML.NET](../automate-training-with-cli.md)
- [Tutorial: Executando modelos do ML.NET em aplicativos Web e APIs Web escalonáveis do ASP.NET Core](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [Exemplo: Modelo do ML.NET escalonável na API Web do ASP.NET Core](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [Guia de referência de comando auto-train da CLI do ML.NET](../reference/ml-net-cli-reference.md) 
- [Como instalar a ferramenta da CLI (Interface de Linha de Comando) do ML.NET](../how-to-guides/install-ml-net-cli.md)
- [Telemetria na CLI do ML.NET](../resources/ml-net-cli-telemetry.md)

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como:
> [!div class="checklist"]
> - Prepare seus dados para a tarefa de ML selecionada (problema a ser resolvido)
> - Execute o comando 'mlnet auto-train' na ferramenta de CLI
> - Examinar os resultados de métrica de qualidade
> - Entenda o código C# gerado para executar o modelo (o código para usar em seu aplicativo de usuário final)
> - Explore o código C# gerado que foi usado para treinar o modelo de "melhor qualidade" (para fins de aprendizado)

> [!div class="nextstepaction"]
> [Automatizar o treinamento de modelos com a CLI do ML.NET](../automate-training-with-cli.md)
