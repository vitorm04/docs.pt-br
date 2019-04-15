---
title: Implantar um modelo ML.NET ao Azure Functions
description: Usar um modelo de machine learning para Análise de Sentimento com o ML.NET para previsão pela internet usando o Azure Functions
ms.date: 03/08/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 4681b37da64097dd8e537b4c956917277ecff96b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330630"
---
# <a name="how-to-use-mlnet-model-in-azure-functions"></a>Como fazer: Usar o modelo ML.NET no Azure Functions

Estas instruções mostram como previsões individuais podem ser feitas usando um modelo de machine learning com ML.NET, previamente criado, pela internet em um ambiente sem servidor como o Azure Functions.

> [!NOTE]
> Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações. Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Esta instrução e a amostra relacionada estão usando o **ML.NET versão 0.10** no momento. Saiba mais nas notas de versão no [repositório do github dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

## <a name="prerequisites"></a>Pré-requisitos

- [Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" e “desenvolvimento do Azure” instalados. 
- [Ferramentas do Azure Functions](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- Powershell
- Modelo previamente treinado. 
    - Use o [tutorial de Análise de Sentimento com ML.NET](../tutorials/sentiment-analysis.md) para criar seu próprio modelo.
    - Baixe este [modelo de machine learning previamente treinado para análise de sentimento](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-azure-functions-project"></a>Criar um projeto no Azure Functions

1. Abra o Visual Studio 2017. Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus. Na caixa de diálogo **Novo projeto**, selecione o nó **Visual C#** seguido pelo nó **Nuvem**. Em seguida, selecione o modelo de projeto do **Azure Functions**. Na caixa de texto **Nome**, digite "SentimentAnalysisFunctionsApp" e, em seguida, selecione o botão **OK**.
1. Na caixa de diálogo **Novo Projeto**, abra a lista suspensa acima das opções de projeto e selecione **Azure Functions v2 (.NET Core)**. Depois, selecione o projeto de **Gatilho de HTTP** e, em seguida, o botão **OK**.
1. Crie um diretório chamado *MLModels* em seu projeto para salvar o modelo:

    No **Gerenciador de Soluções**, clique com o botão direito do mouse no seu projeto e selecione **Adicionar** > **Nova Pasta**. Digite "MLModels" e pressione ENTER.

1. Instalar o **Pacote NuGet Microsoft.ML**:

    No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**. Escolha "nuget.org" como a Origem do pacote, selecione a guia Procurar, pesquise por **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**. Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.

## <a name="add-pre-built-model-to-project"></a>Adicionar o modelo previamente criado ao projeto

1. Copie o modelo previamente criado para o diretório *MLModels*.
1. No Gerenciador de Soluções, clique com o botão direito do mouse no arquivo do modelo criado previamente e selecione **Propriedades**. Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.

## <a name="create-function-to-analyze-sentiment"></a>Criar a função para analisar o sentimento

Crie uma classe para prever o sentimento. Adicione uma nova classe ao seu projeto:

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.

1. Na caixa de diálogo **Adicionar novo item**, selecione **Função do Azure** e altere o campo **Nome** para *AnalyzeSentiment.cs*. Em seguida, selecione o botão **Adicionar**.

1. Na caixa de diálogo **Nova Função do Azure**, selecione **Gatilho de HTTP**. Depois, selecione o botão **OK**.

    O arquivo *AnalyzeSentiment.cs* é aberto no editor de códigos. Adicione a seguinte instrução `using` acima de *GitHubIssueData.cs*:

```csharp
using System;
using System.IO;
using System.Threading.Tasks;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Azure.WebJobs;
using Microsoft.Azure.WebJobs.Extensions.Http;
using Microsoft.AspNetCore.Http;
using Microsoft.Extensions.Logging;
using Newtonsoft.Json;
using Microsoft.ML;
using Microsoft.ML.Core.Data;
using Microsoft.ML.Data;
using MLNETServerless.DataModels;
```

### <a name="create-data-models"></a>Criar modelo de dados

Você precisa criar algumas classes para os dados e previsões de entrada. Adicione uma nova classe ao seu projeto:

1. Crie um diretório chamado *DataModels* em seu projeto para salvar os modelos de dados: No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **Adicionar > Nova pasta**. Digite "DataModels" e pressione ENTER.
2. No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *DataModels* e selecione **Adicionar > Novo Item**.
3. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentData.cs*. Em seguida, selecione o botão **Adicionar**. O arquivo *SentimentData.cs* é aberto no editor de códigos. Adicione a seguinte instrução using na parte superior do *SentimentData.cs*:

```csharp
using Microsoft.ML.Data;
```

Remova a definição de classe existente e adicione o seguinte código ao arquivo SentimentData.cs:

```csharp
public class SentimentData
{
    [LoadColumn(0)]
    public bool Label { get; set; }
    [LoadColumn(1)]
    public string Text { get; set; }
}
```

4. No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *DataModels* e selecione **Adicionar > Novo Item**.
5. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentPrediction.cs*. Em seguida, selecione o botão **Adicionar**. O arquivo *SentimentPrediction.cs* é aberto no editor de códigos. Adicione a seguinte instrução "using" na parte superior do *SentimentPrediction.cs*:

```csharp
using Microsoft.ML.Data;
```

Remova a definição de classe existente e adicione o seguinte código ao arquivo *SentimentPrediction.cs*:

```csharp
public class SentimentPrediction
{
    [ColumnName("PredictedLabel")]
    public bool Prediction { get; set; }
}
```

### <a name="add-prediction-logic"></a>Adicionar lógica de previsão

Substitua a implementação existente do método *Run* na classe *AnalyzeSentiment* pelo código a seguir:

```csharp
    public static async Task<IActionResult> Run(
        [HttpTrigger(AuthorizationLevel.Function,"post", Route = null)] HttpRequest req,
        ILogger log)
    {
        log.LogInformation("C# HTTP trigger function processed a request.");

        //Create Context
        MLContext mlContext = new MLContext();

        //Load Model
        using (var fs = File.OpenRead("MLModels/sentiment_model.zip"))
        {
            model = mlContext.Model.Load(fs);
        }

        //Parse HTTP Request Body
        string requestBody = await new StreamReader(req.Body).ReadToEndAsync();
        SentimentData data = JsonConvert.DeserializeObject<SentimentData>(requestBody);

        //Create Prediction Engine
        PredictionEngine<SentimentData, SentimentPrediction> predictionEngine = model.CreatePredictionEngine<SentimentData, SentimentPrediction>(mlContext);

        //Make Prediction
        SentimentPrediction prediction = predictionEngine.Predict(data);

        //Convert prediction to string
        string isToxic = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";

        //Return Prediction
        return (ActionResult)new OkObjectResult(isToxic);
    }
}
```

## <a name="test-locally"></a>Testar localmente

Agora que está tudo definido, é hora de testar o aplicativo:

1. Executar o aplicativo
1. Abra o PowerShell e digite o seguinte código no prompt, em que PORT é a porta em que seu aplicativo está sendo executado. Normalmente, a porta é a 7071. 

```powershell
Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{Text="This is a very rude movie"} | ConvertTo-Json) -ContentType "application/json"
```

Se houver êxito, a saída deverá ser semelhante ao texto abaixo:

```powershell
Toxic
```

Parabéns! Você usou com êxito o modelo para fazer previsões pela internet usando uma função do Azure.

## <a name="next-steps"></a>Próximas etapas

- [Implantar no Azure](/azure/azure-functions/functions-develop-vs#publish-to-azure)