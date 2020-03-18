---
title: Implantar um modelo no Azure Functions
description: Usar um modelo de machine learning para Análise de Sentimento com o ML.NET para previsão pela internet usando o Azure Functions
ms.date: 02/21/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 33afd568bb12b855a3888bec31f2e9bbc3c720da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628664"
---
# <a name="deploy-a-model-to-azure-functions"></a>Implantar um modelo no Azure Functions

Saiba como implantar um modelo de machine learning do ML.NET pré-treinado para previsões por HTTP por meio de um ambiente sem servidor do Azure Functions.

> [!NOTE]
> Esta amostra executa uma `PredictionEnginePool` versão de pré-visualização do serviço.

## <a name="prerequisites"></a>Pré-requisitos

- [Visual Studio 2017 versão 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho ".NET Core cross-platform development" e "Desenvolvimento Azure" instalado.
- [Ferramentas de funções do Azure](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- Powershell
- Modelo previamente treinado. Use o [tutorial de Análise de Sentimento do ML.NET](../tutorials/sentiment-analysis.md) para criar seu próprio modelo ou baixe este [modelo de machine learning de análise de sentimento pré-treinado](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="azure-functions-sample-overview"></a>Visão geral da amostra de funções do Azure

Esta amostra é um **aplicativo C# HTTP Trigger Azure Functions** que usa um modelo de classificação binária pré-treinado para categorizar o sentimento do texto como positivo ou negativo. O Azure Functions fornece uma maneira fácil de executar pequenos pedaços de código em escala em um ambiente sem servidor gerenciado na nuvem. O código para esta amostra pode ser encontrado no repositório [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) no GitHub.

## <a name="create-azure-functions-project"></a>Criar um projeto do Azure Functions

1. Abra o Visual Studio 2017. Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus. Na caixa de diálogo **Novo projeto**, selecione o nó **Visual C#** seguido pelo nó **Nuvem**. Em seguida, selecione o modelo de projeto do **Azure Functions**. Na caixa de texto **Nome**, digite "SentimentAnalysisFunctionsApp" e, em seguida, selecione o botão **OK**.
1. Na caixa de diálogo **Novo Projeto**, abra a lista suspensa acima das opções de projeto e selecione **Azure Functions v2 (.NET Core)**. Depois, selecione o projeto de **Gatilho de HTTP** e, em seguida, o botão **OK**.
1. Crie um diretório chamado *MLModels* em seu projeto para salvar o modelo:

    No **Gerenciador de Soluções**, clique com o botão direito do mouse no seu projeto e selecione **Adicionar** > **Nova Pasta**. Digite "MLModels" e pressione ENTER.

1. Instale o **Microsoft.ML NuGet Package** versão **1.3.1**:

    No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**. Escolha "nuget.org" como a Origem do pacote, selecione a guia Procurar, pesquise por **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**. Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.

1. Instale o **Pacote NuGet Microsoft.Azure.Functions.Extensions**:

    No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**. Escolha "nuget.org" como a origem do pacote, selecione a guia Procurar, procure por **Microsoft.Azure.Functions.Extensions**, selecione o pacote na lista e selecione o botão **Instalar**. Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.

1. Instale o **Microsoft.Extensions.ML nuget package** versão **0.15.1**:

    No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**. Escolha "nuget.org" como a origem do pacote, selecione a guia Procurar, procure **Microsoft.Extensions.ML,** selecione esse pacote na lista e selecione o botão **Instalar.** Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.

1. Instale o **Pacote Microsoft.NET.Sdk.Funções NuGet Versão** **1.0.31**:

    No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**. Escolha "nuget.org" como a origem do pacote, selecione a guia Instalado, procure **por Funções Microsoft.NET.Sdk.,** selecione esse pacote na lista, selecione **1.0.31** na versão suspensa e selecione o botão **Atualizar.** Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.

## <a name="add-pre-trained-model-to-project"></a>Adicionar modelo pré-treinado ao projeto

1. Copie o modelo previamente criado para o diretório *MLModels*.
1. No Gerenciador de Soluções, clique com o botão direito do mouse no arquivo do modelo criado previamente e selecione **Propriedades**. Em **Avançado,** altere o valor de **Copiar para Diretório de Saída** para Copiar se mais **novo**.

## <a name="create-azure-function-to-analyze-sentiment"></a>Criar Função do Azure para analisar o sentimento

Crie uma classe para prever o sentimento. Adicione uma nova classe ao seu projeto:

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.

1. Na caixa de diálogo **Adicionar novo item**, selecione **Função do Azure** e altere o campo **Nome** para *AnalyzeSentiment.cs*. Em seguida, selecione o botão **Adicionar**.

1. Na caixa de diálogo **Nova Função do Azure**, selecione **Gatilho de HTTP**. Depois, selecione o botão **OK**.

    O arquivo *AnalyzeSentiment.cs* é aberto no editor de códigos. Adicione a seguinte instrução `using` acima de *AnalyzeSentiment.cs*:

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    Por padrão, a classe `AnalyzeSentiment` é `static`. Remova a palavra-chave `static` da definição da classe.

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a>Criar modelo de dados

Você precisa criar algumas classes para os dados e previsões de entrada. Adicione uma nova classe ao seu projeto:

1. Crie um diretório chamado *DataModels* em seu projeto para salvar seus modelos de dados: No Solution Explorer, clique com o botão direito do mouse no seu projeto e **selecione Adicionar > Nova Pasta**. Digite "DataModels" e pressione ENTER.
2. No Solution Explorer, clique com o botão direito do mouse no diretório *DataModels* e, em seguida, **selecione Adicionar > Novo Item**.
3. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentData.cs*. Em seguida, selecione o botão **Adicionar**.

    O arquivo *SentimentData.cs* é aberto no editor de códigos. Adicione a seguinte instrução using na parte superior do *SentimentData.cs*:

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    Remova a definição de classe existente e adicione o seguinte código ao arquivo *SentimentData.cs:*

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. No Solution Explorer, clique com o botão direito do mouse no diretório *DataModels* e, em seguida, **selecione Adicionar > Novo Item**.
5. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentPrediction.cs*. Em seguida, selecione o botão **Adicionar**. O arquivo *SentimentPrediction.cs* é aberto no editor de códigos. Adicione a seguinte instrução "using" na parte superior do *SentimentPrediction.cs*:

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    Remova a definição de classe existente e adicione o seguinte código ao arquivo *SentimentPrediction.cs*:

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    `SentimentPrediction` herda de `SentimentData`, que dá acesso aos dados originais na propriedade `SentimentText`, bem como a saída gerada pelo modelo.

## <a name="register-predictionenginepool-service"></a>Registrar serviço PredictionEnginePool

Para fazer uma única previsão, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)você tem que criar um . [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)não é seguro para rosca. Além disso, você tem que criar uma instância dele em todos os lugares necessários dentro de sua aplicação. À medida que sua aplicação cresce, esse processo pode se tornar incontrolável. Para melhorar o desempenho e a segurança dos fios, use uma combinação de injeção de dependência e o `PredictionEnginePool` serviço, que cria um de [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objetos para uso em toda a sua aplicação.

O link a seguir fornece mais informações se você quiser saber mais sobre [injeção de dependência](https://en.wikipedia.org/wiki/Dependency_injection).

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.
1. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *Startup.cs*. Em seguida, selecione o botão **Adicionar**.
1. Adicione as seguintes instruções usando a parte superior do *Startup.cs:*

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L1-L6)]

1. Remova o código existente abaixo das instruções de uso e adicione o seguinte código:

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {

        }
    }
    ```

1. Defina variáveis para armazenar o ambiente em que o aplicativo está sendo `Startup` executado e o caminho do arquivo onde o modelo está localizado dentro da classe

    [!code-csharp [DefineStartupVars](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L13-L14)]

1. Abaixo disso, crie um construtor para `_environment` definir `_modelPath` os valores das variáveis. Quando o aplicativo está sendo executado localmente, o ambiente padrão é *Desenvolvimento*.

    [!code-csharp [StartupCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L16-L29)]

1. Em seguida, adicione `Configure` um novo `PredictionEnginePool` método chamado para registrar o serviço abaixo do construtor.

    [!code-csharp [ConfigureServices](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L31-L35)]

Em um alto nível, esse código inicializa os objetos e serviços automaticamente para uso posterior quando solicitado pelo aplicativo, em vez de ter que fazê-lo manualmente.

Modelos de aprendizado de máquina não são estáticos. À medida que novos dados de treinamento se tornam disponíveis, o modelo é retreinado e reimplantado. Uma maneira de colocar a versão mais recente do modelo em seu aplicativo é reimplantar todo o aplicativo. No entanto, isso introduz o tempo de inatividade do aplicativo. O `PredictionEnginePool` serviço fornece um mecanismo para recarregar um modelo atualizado sem retirar seu aplicativo.

Defina `watchForChanges` o `true`parâmetro para `PredictionEnginePool` , [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) e as iniciações a que ouve o sistema de arquivos alterar notificações e levanta eventos quando há uma alteração no arquivo. Isso solicita `PredictionEnginePool` a recarga automática do modelo.

O modelo é `modelName` identificado pelo parâmetro para que mais de um modelo por aplicativo possa ser recarregado após a alteração.

> [!TIP]
> Alternativamente, você pode `FromUri` usar o método ao trabalhar com modelos armazenados remotamente. Em vez de assistir `FromUri` a eventos alterados por arquivos, pesquisa o local remoto para alterações. O intervalo de votação é de 5 minutos. Você pode aumentar ou diminuir o intervalo de votação com base nos requisitos do seu aplicativo. Na amostra de código `PredictionEnginePool` abaixo, as pesquisas o modelo armazenado no URI especificado a cada minuto.
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a>Carregar o modelo na função

Insira o seguinte código dentro da classe *AnalyzeSentiment*:

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

Esse código atribui o `PredictionEnginePool` passando-o para o construtor da função que você obtém por meio da injeção de dependência.

## <a name="use-the-model-to-make-predictions"></a>Usar o modelo para fazer previsões

Substitua a implementação existente do método *Run* na classe *AnalyzeSentiment* pelo código a seguir:

[!code-csharp [AnalyzeRunMethod](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L26-L45)]

Quando o método `Run` é executado, os dados de entrada da solicitação HTTP são desserializados e usados como entrada para o `PredictionEnginePool`. O `Predict` método é então chamado `SentimentAnalysisModel` para fazer `Startup` previsões usando o registrado na classe e retorna os resultados ao usuário se for bem sucedido.

## <a name="test-locally"></a>Testar localmente

Agora que está tudo definido, é hora de testar o aplicativo:

1. Executar o aplicativo
1. Abra o PowerShell e digite o seguinte código no prompt, em que PORT é a porta em que seu aplicativo está sendo executado. Normalmente, a porta é a 7071.

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    Se houver êxito, a saída deverá ser semelhante ao texto abaixo:

    ```powershell
    Negative
    ```

Parabéns! Você usou com êxito o modelo para fazer previsões pela internet usando uma função do Azure.

## <a name="next-steps"></a>Próximas etapas

- [Implantar no Azure](/azure/azure-functions/functions-develop-vs#publish-to-azure)
