---
title: Usar um modelo de Machine Learning em ASP.NET Core Web API
description: Usar um modelo de Machine Learning para Análise de Sentimento com ML.NET pela internet usando o ASP.NET Web API
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 0cc13ec22b3a8805ec4aa17bf10560b2564ccd63
ms.sourcegitcommit: 77854e8704b9689b73103d691db34d71c2bf1dad
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58307909"
---
# <a name="how-to-serve-machine-learning-model-through-aspnet-core-web-api"></a>Como fazer: Usar um modelo de Machine Learning por meio do ASP.NET Web API

Estas instruções mostram como usar um modelo de machine learning com ML.NET, previamente criado, na Web usando um ASP.NET Core Web API. Fazer isso permite que os usuários acessem a API para fins de previsão por meio de métodos HTTP padrão.

> [!NOTE]
> Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações. Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Esta instrução e a amostra relacionada estão usando o **ML.NET versão 0.10** no momento. Saiba mais nas notas de versão no [repositório do github dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

## <a name="prerequisites"></a>Pré-requisitos

- [Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.
- Powershell.
- Modelo previamente treinado.
    - Use o [tutorial de Análise de Sentimento com ML.NET](../tutorials/sentiment-analysis.md) para criar seu próprio modelo.
    - Baixe este [modelo de machine learning previamente treinado para análise de sentimento](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="create-aspnet-core-web-api-project"></a>Criar o projeto do ASP.NET Core Web API

1. Abra o Visual Studio 2017. No menu, selecione **Arquivo > Novo > Projeto**. Na caixa de diálogo Novo projeto, selecione o nó **Visual C#** seguido pelo nó **Web**. Em seguida, selecione o modelo de projeto **Aplicativo ASP.NET Core Web**. Na caixa de texto **Nome**, digite "SentimentAnalysisWebAPI" e, depois, selecione o botão **OK**.
1. Na janela que exibe os diferentes tipos de projetos do ASP.NET Core, selecione **API** e, depois, o botão **OK**.
1. Crie um diretório chamado *MLModels* em seu projeto para salvar os arquivos de modelo de machine learning criados previamente:

    No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione Adicionar > Nova Pasta. Digite "MLModels" e pressione ENTER.

1. Instalar o **Pacote NuGet Microsoft.ML**:

    No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**. Escolha "nuget.org" como a origem do pacote, selecione a guia Procurar, pesquise **Microsoft.ML**, selecione o pacote na lista e selecione o botão Instalar. Selecione o botão **OK** na caixa de diálogo **Visualizar alterações** e, depois, o botão **Aceito** na caixa de diálogo Aceitação da Licença, se concordar com o termos de licença para os pacotes listados.

### <a name="add-model-to-aspnet-core-web-api-project"></a>Adicionar um modelo ao Projeto do ASP.NET Core Web API

1. Copie seu modelo previamente criado para o diretório *MLModels*
1. No Gerenciador de Soluções, clique com o botão direito do mouse no arquivo zip e selecione Propriedades. Em Avançado, altere o valor de Copiar para diretório de saída para Copiar se for mais novo.

## <a name="build-data-models"></a>Criar modelo de dados

Você precisa criar algumas classes para os dados e previsões de entrada. Adicione uma nova classe ao seu projeto:

1. Crie um diretório chamado *DataModels* em seu projeto para salvar os modelos de dados:

    No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione Adicionar > Nova Pasta. Digite "DataModels" e pressione **ENTER**.

2. No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *DataModels* e selecione Adicionar > Novo item.
3. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentData.cs*. Em seguida, selecione o botão **Adicionar**. O arquivo *SentimentData.cs* é aberto no editor de códigos. Adicione a seguinte instrução using na parte superior do *SentimentData.cs*:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.ML.Data;
```

Remova a definição de classe existente e adicione o seguinte código ao arquivo **SentimentData.cs**:

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
5. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentPrediction.cs*. Em seguida, selecione o botão Adicionar. O arquivo *SentimentPrediction.cs* é aberto no editor de códigos. Adicione a seguinte instrução "using" na parte superior do *SentimentPrediction.cs*:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
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

## <a name="register-predictionengine-for-use-in-application"></a>Registrar o PredictionEngine para uso no aplicativo

Para fazer uma única previsão, você pode usar o `PredictionEngine`. Para usar o `PredictionEngine` em seu aplicativo, você precisará criá-lo sempre que necessário. Nesse caso, a prática recomendada é a injeção de dependência do ASP.NET Core.

O link a seguir fornece mais informações sobre a [injeção de dependência](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).

1. Abra a classe *Startup.cs* e adicione a seguinte instrução using à parte superior do arquivo:

```csharp
using System.IO;
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.ML;
using Microsoft.ML.Core.Data;
using SentimentAnalysisWebAPI.DataModels;
```

2. Adicione as seguintes linhas de código ao método *ConfigureServices*:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);

    services.AddScoped<MLContext>();
    services.AddScoped<PredictionEngine<SentimentData, SentimentPrediction>>((ctx) =>
    {
        MLContext mlContext = ctx.GetRequiredService<MLContext>();
        string modelFilePathName = "MLModels/sentiment_model.zip";

        //Load model from file
        ITransformer model;
        using (var stream = File.OpenRead(modelFilePathName))
        {
            model = mlContext.Model.Load(stream);
        }

        // Return prediction engine
        return model.CreatePredictionEngine<SentimentData, SentimentPrediction>(mlContext);
    });
}
```

> [!WARNING]
> `PredictionEngine` não é thread-safe. Uma maneira de limitar o custo da criação do objeto é definir o tempo de vida do serviço *Com escopo*. Os objetos *com escopo* são os mesmos em uma solicitação, mas diferentes entre solicitações. Visite o link a seguir para saber mais sobre [tempos de vida do serviço](/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1#service-lifetimes).

Em um alto nível, esse código inicializa os objetos e serviços automaticamente quando solicitado pelo aplicativo em vez de precisar fazê-lo manualmente.

## <a name="create-predict-controller"></a>Criar o Predict Controller

Para processar as solicitações HTTP de entrada, será necessário criar um controlador.

1. No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *Controladores* e selecione **Adicionar > Controlador**.
1. Na caixa de diálogo **Adicionar Novo Item**, selecione **Controlador de API Vazio** e, então, **Adicionar**.
1. No prompt, altere o campo do **Nome do Controlador** para *PredictController.cs*. Em seguida, selecione o botão Adicionar. O arquivo *PredictController.cs* é aberto no editor de códigos. Adicione a seguinte instrução using na parte superior do *PredictController.cs*:

```csharp
using System;
using Microsoft.AspNetCore.Mvc;
using SentimentAnalysisWebAPI.DataModels;
using Microsoft.ML;
```

Remova a definição de classe existente e adicione o seguinte código ao arquivo *PredictController.cs*:

```csharp
public class PredictController : ControllerBase
{
    
    private readonly PredictionEngine<SentimentData,SentimentPrediction> _predictionEngine;

    public PredictController(PredictionEngine<SentimentData, SentimentPrediction> predictionEngine)
    {
        _predictionEngine = predictionEngine; //Define prediction engine
    }

    [HttpPost]
    public ActionResult<string> Post([FromBody]SentimentData input)
    {
        if(!ModelState.IsValid)
        {
            return BadRequest();
        }

        // Make a prediction
        SentimentPrediction prediction = _predictionEngine.Predict(input);

        //If prediction is true then it is toxic. If it is false, the it is not.
        string isToxic = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";

        return Ok(isToxic);
    }
    
}
```

Isso atribui o `PredictionEngine` passando-o para o construtor do controlador que você obtém por meio da injeção de dependência. Em seguida, no método POST desse controlador, o `PredictionEngine` está sendo usado para fazer previsões e retornar os resultados para o usuário, em caso de êxito.

## <a name="test-web-api-locally"></a>Testar a API Web localmente

Depois que tudo estiver definido, é hora de testar o aplicativo.

1. Execute o aplicativo.
1. Abra o Powershell e digite o seguinte código, em que PORT é a porta em que seu aplicativo está escutando.

```powershell
Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{Text="This is a very rude movie"} | ConvertTo-Json) -ContentType "application/json"
```

Se houver êxito, a saída deverá ser semelhante ao texto abaixo:

```powershell
Toxic
```

Parabéns! Você usou com êxito seu modelo para fazer previsões pela internet usando um ASP.NET Core API.

## <a name="next-steps"></a>Próximas etapas

- [Implantar no Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.1#deploy-the-app-to-azure)