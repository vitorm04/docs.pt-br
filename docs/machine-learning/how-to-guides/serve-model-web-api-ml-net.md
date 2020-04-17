---
title: Implantar um modelo em uma API Web do ASP.NET Core
description: Usar um modelo de Machine Learning para Análise de Sentimento com ML.NET pela internet usando o ASP.NET Web API
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 3f1ca48ab29b04931961b52743bb6c7fab70b06d
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608069"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a>Implantar um modelo em uma API Web do ASP.NET Core

Saiba como fornecer um modelo de machine Learning do ML.NET previamente treinado na Web usando uma API Web do ASP.NET Core. Veicular um modelo por uma API Web habilita previsões por meio de métodos HTTP padrão.

## <a name="prerequisites"></a>Pré-requisitos

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou posterior ou Visual Studio 2017 versão 15.6 ou posterior com a carga de trabalho ".NET Core cross-platform development" instalada.
- Powershell.
- Modelo previamente treinado. Use o [tutorial de Análise de Sentimento do ML.NET](../tutorials/sentiment-analysis.md) para criar seu próprio modelo ou baixe este [modelo de machine learning de análise de sentimento pré-treinado](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-aspnet-core-web-api-project"></a>Criar o projeto da API Web do ASP.NET Core

1. Abra o Visual Studio 2017. No menu, selecione **Arquivo > Novo > Projeto**. Na caixa de diálogo Novo projeto, selecione o nó **Visual C#** seguido pelo nó **Web**. Em seguida, selecione o modelo de projeto **Aplicativo ASP.NET Core Web**. Na caixa de texto **Nome**, digite "SentimentAnalysisWebAPI" e, depois, selecione o botão **OK**.

1. Na janela que exibe os diferentes tipos de projetos do ASP.NET Core, selecione **API** e, depois, o botão **OK**.

1. Crie um diretório chamado *MLModels* em seu projeto para salvar os arquivos de modelo de machine learning criados previamente:

    No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione Adicionar > Nova Pasta. Digite "MLModels" e pressione ENTER.

1. Instalar o **Pacote NuGet Microsoft.ML**:

    No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**. Escolha "nuget.org" como a Origem do pacote, selecione a guia Procurar, pesquise por **Microsoft.ML**, selecione o pacote na lista e escolha o botão Instalar. Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo Aceitação da Licença, se concordar com o termos de licença para os pacotes listados.

1. Instalar o **Pacote do Nuget Microsoft.Extensions.ML**:

    No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**. Escolha "nuget.org" como a origem do pacote, selecione a guia Procurar, pesquise **Microsoft.Extensions.ML**, selecione o pacote na lista e selecione o botão Instalar. Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo Aceitação da Licença, se concordar com o termos de licença para os pacotes listados.

### <a name="add-model-to-aspnet-core-web-api-project"></a>Adicionar um modelo ao projeto da API Web do ASP.NET Core

1. Copie seu modelo previamente criado para o diretório *MLModels*
1. No Gerenciador de Soluções, clique com o botão direito do mouse no arquivo zip e selecione Propriedades. Em Avançado, altere o valor de Copiar para diretório de saída para Copiar se for mais novo.

## <a name="create-data-models"></a>Criar modelo de dados

Você precisa criar algumas classes para os dados e previsões de entrada. Adicione uma nova classe ao seu projeto:

1. Crie um diretório chamado *DataModels* em seu projeto para salvar os modelos de dados:

    No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione Adicionar > Nova Pasta. Digite "DataModels" e aperte **Enter**.

2. No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *DataModels* e selecione Adicionar > Novo item.
3. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentData.cs*. Em seguida, selecione o botão **Adicionar**. O arquivo *SentimentData.cs* é aberto no editor de códigos. Adicione a seguinte instrução using na parte superior do *SentimentData.cs*:

    ```csharp
    using Microsoft.ML.Data;
    ```

    Remova a definição de classe existente e adicione o seguinte código ao arquivo **SentimentData.cs:**

    ```csharp
    public class SentimentData
    {
        [LoadColumn(0)]
        public string SentimentText;

        [LoadColumn(1)]
        [ColumnName("Label")]
        public bool Sentiment;
    }
    ```

4. No Solution Explorer, clique com o botão direito do mouse no diretório *DataModels* e, em seguida, **selecione Adicionar > Novo Item**.
5. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentPrediction.cs*. Em seguida, selecione o botão Adicionar. O arquivo *SentimentPrediction.cs* é aberto no editor de códigos. Adicione a seguinte instrução "using" na parte superior do *SentimentPrediction.cs*:

    ```csharp
    using Microsoft.ML.Data;
    ```

    Remova a definição de classe existente e adicione o seguinte código ao arquivo *SentimentPrediction.cs*:

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    `SentimentPrediction` herda de `SentimentData`. Isso torna mais fácil ver os dados originais na propriedade `SentimentText` junto com a saída gerada pelo modelo.

## <a name="register-predictionenginepool-for-use-in-the-application"></a>Registrar PredictionEnginePool para uso no aplicativo

Para fazer uma única previsão, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)você tem que criar um . [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)não é seguro para rosca. Além disso, você tem que criar uma instância dele em todos os lugares necessários dentro de sua aplicação. À medida que sua aplicação cresce, esse processo pode se tornar incontrolável. Para melhorar o desempenho e a segurança dos fios, use uma combinação de injeção de dependência e o `PredictionEnginePool` serviço, que cria um de [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objetos para uso em toda a sua aplicação.

O link a seguir fornece mais informações se você quiser saber mais sobre [injeção de dependência no ASP.NET Core](/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).

1. Abra a classe *Startup.cs* e adicione a seguinte instrução using à parte superior do arquivo:

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. Adicione o seguinte código ao método *ConfigureServices*:

    ```csharp
    services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
        .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
    ```

Em um alto nível, esse código inicializa os objetos e serviços automaticamente para uso posterior quando solicitado pelo aplicativo, em vez de ter que fazê-lo manualmente.

Modelos de aprendizado de máquina não são estáticos. À medida que novos dados de treinamento se tornam disponíveis, o modelo é retreinado e reimplantado. Uma maneira de colocar a versão mais recente do modelo em seu aplicativo é reimplantar todo o aplicativo. No entanto, isso introduz o tempo de inatividade do aplicativo. O `PredictionEnginePool` serviço fornece um mecanismo para recarregar um modelo atualizado sem retirar seu aplicativo.

Defina `watchForChanges` o `true`parâmetro para `PredictionEnginePool` , [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) e as iniciações a que ouve o sistema de arquivos alterar notificações e levanta eventos quando há uma alteração no arquivo. Isso solicita `PredictionEnginePool` a recarga automática do modelo.

O modelo é `modelName` identificado pelo parâmetro para que mais de um modelo por aplicativo possa ser recarregado após a alteração.

> [!TIP]
> Alternativamente, você pode `FromUri` usar o método ao trabalhar com modelos armazenados remotamente. Em vez de assistir `FromUri` a eventos alterados por arquivos, pesquisa o local remoto para alterações. O intervalo de votação é de 5 minutos. Você pode aumentar ou diminuir o intervalo de votação com base nos requisitos do seu aplicativo. Na amostra de código `PredictionEnginePool` abaixo, as pesquisas o modelo armazenado no URI especificado a cada minuto.
>
>```csharp
>services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="create-predict-controller"></a>Criar o Controlador de Previsão

Para processar as solicitações HTTP de entrada, crie um controlador.

1. No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *Controladores* e selecione **Adicionar > Controlador**.
1. Na caixa de diálogo **Adicionar Novo Item**, selecione **Controlador de API Vazio** e, então, **Adicionar**.
1. No prompt, altere o campo do **Nome do Controlador** para *PredictController.cs*. Em seguida, selecione o botão Adicionar. O arquivo *PredictController.cs* é aberto no editor de códigos. Adicione a seguinte instrução using na parte superior do *PredictController.cs*:

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    Remova a definição de classe existente e adicione o seguinte código ao arquivo *PredictController.cs*:

    ```csharp
    public class PredictController : ControllerBase
    {
        private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

        public PredictController(PredictionEnginePool<SentimentData,SentimentPrediction> predictionEnginePool)
        {
            _predictionEnginePool = predictionEnginePool;
        }

        [HttpPost]
        public ActionResult<string> Post([FromBody] SentimentData input)
        {
            if(!ModelState.IsValid)
            {
                return BadRequest();
            }

            SentimentPrediction prediction = _predictionEnginePool.Predict(modelName: "SentimentAnalysisModel", example: input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

Esse código atribui o `PredictionEnginePool` passando-o para o construtor do controlador que você obtém por meio da injeção de dependência. Em seguida, `Predict` o `Post` método `PredictionEnginePool` do controlador usa `SentimentAnalysisModel` o para `Startup` fazer previsões usando o registrado na classe e retorna os resultados de volta ao usuário se for bem sucedido.

## <a name="test-web-api-locally"></a>Testar a API Web localmente

Depois que tudo estiver definido, é hora de testar o aplicativo.

1. Execute o aplicativo.
1. Abra o Powershell e digite o seguinte código, em que PORT é a porta em que seu aplicativo está escutando.

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    Se houver êxito, a saída deverá ser semelhante ao texto abaixo:

    ```powershell
    Negative
    ```

Parabéns! Você usou com êxito seu modelo para fazer previsões pela internet usando um ASP.NET Core API Web.

## <a name="next-steps"></a>Próximas etapas

- [Implantar no Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
