---
title: 'Tutorial: Analise o sentimento - classificação binária'
description: Este tutorial mostra como criar um aplicativo Razor Pages que classifica o sentimento a partir de comentários do site e toma as medidas apropriadas. O classificador binário de sentimentos usa Model Builder no Visual Studio.
ms.date: 11/21/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: 3419afb36d73599b8fdb0417a8c0cc4057f60089
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187629"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a>Tutorial: Analise o sentimento dos comentários do site em um aplicativo web usando ML.NET Model Builder

Aprenda a analisar o sentimento a partir de comentários em tempo real dentro de um aplicativo web.

Este tutorial mostra como criar um aplicativo ASP.NET Core Razor Pages que classifica o sentimento dos comentários do site em tempo real.

Neste tutorial, você aprenderá como:

> [!div class="checklist"]
>
> - Crie um aplicativo de páginas de navalha ASP.NET
> - Preparar e compreender os dados
> - Escolha um cenário
> - Carregar os dados
> - Treinar o modelo
> - Avalie o modelo
> - Usar o modelo para previsões

> [!NOTE]
> O Construtor de Modelo está atualmente na Versão Prévia.

Você pode encontrar o código fonte para este tutorial no repositório [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples)

## <a name="pre-requisites"></a>Pré-requisitos

Para obter uma lista de pré-requisitos e instruções de instalação, visite o [guia de instalação do Construtor de Modelo](../how-to-guides/install-model-builder.md).

## <a name="create-a-razor-pages-application"></a>Criar um aplicativo de páginas de barbear

1. Crie um **ASP.NET aplicativo de páginas de navalha do núcleo**.

    1. Abra o Visual Studio e selecione **File > New > Project** na barra de menus.
    1. Na caixa de diálogo Novo projeto, selecione o nó **Visual C#** seguido pelo nó **Web**.
    1. Em seguida, selecione o modelo de projeto **Aplicativo ASP.NET Core Web**.
    1. Na caixa de texto **Nome,** digite "SentimentRazor".
    1. Certifique-se de que **a solução e o projeto place no mesmo diretório** não são **controlados** (VS 2019), ou **Criar diretório para solução** é **verificado** (VS 2017).
    1. Selecione o botão **OK.**
    1. Escolha **a aplicação da Web** na janela que exibe os diferentes tipos de ASP.NET Projetos principais e, em seguida, selecione o botão **OK.**

## <a name="prepare-and-understand-the-data"></a>Preparar e compreender os dados

Baixe [o conjunto de dados desintoxicação da Wikipédia](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv). Quando a página da Web for aberta, clique com o botão direito do mouse na página, **selecione Salvar como** e salve o arquivo em qualquer lugar do computador.

Cada linha no conjunto *de dados wikipedia-detox-250-line.tsv* representa uma revisão diferente deixada por um usuário na Wikipédia. A primeira coluna representa o sentimento do texto (0 não é tóxico, 1 é tóxico), e a segunda coluna representa o comentário deixado pelo usuário. As colunas são separadas por guias. Os dados se parecem com os seguintes:

| Sentimento | SentimentText |
| :---: | :---: |
1 | ==RUDE== Cara, você é rude carregar aquela foto do Carl de volta, ou então.
1 | == OK! == IM VAI VANDALIZAR OS SELVAGENS WIKI ENTÃO!!!
0 | Espero que isso ajude.

## <a name="choose-a-scenario"></a>Escolha um cenário

![Assistente do Construtor de Modelos no Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

Para treinar seu modelo, você precisa selecionar na lista de cenários disponíveis de aprendizado de máquina fornecidos pelo Construtor de Modelo.

1. No **Solution Explorer,** clique com o botão direito do mouse no projeto *SentimentRazor* e selecione **Adicionar** > **aprendizado de máquina**.
1. Para esta amostra, o cenário é a análise de sentimentos. Na etapa de *cenário* da ferramenta Model Builder, selecione o cenário **de Análise de Sentimento.**

## <a name="load-the-data"></a>Carregar os dados

O Model Builder aceita dados de duas fontes, um banco `csv` `tsv` de dados SQL Server ou um arquivo local dentro ou formato.

1. Na etapa de dados da ferramenta do Construtor de Modelo, selecione **Arquivo** na lista suspensa da fonte de dados.
1. Selecione o botão ao lado da **Caixa Selecionar uma** caixa de texto de arquivo e use o File Explorer para navegar e selecionar o arquivo *wikipedia-detox-250-line-data.tsv.*
1. Escolha **Sentimento** na **coluna para prever (rótulo)** dropdown.
1. Deixe os valores padrão para a estada **'Colunas de entrada (Recursos].**
1. Selecione o link **Trem** para passar para a próxima etapa na ferramenta Construtor de modelos.

## <a name="train-the-model"></a>Treinar o modelo

A tarefa de aprendizado de máquina usada para treinar o modelo de análise de sentimento neste tutorial é a classificação binária. Durante o processo de treinamento do modelo, o Model Builder treina modelos separados usando diferentes algoritmos de classificação binária e configurações para encontrar o modelo de melhor desempenho para o seu conjunto de dados.

O tempo necessário para treinar o modelo é proporcional à quantidade de dados. O Model Builder seleciona automaticamente um valor padrão para **tempo de treinar (segundos)** com base no tamanho da fonte de dados.

1. Embora o Model Builder defina o valor do **Tempo para treinar (segundos)** para 10 segundos, aumente-o para 30 segundos. O treinamento por um período maior de tempo permite ao Model Builder explorar um número maior de algoritmos e combinação de parâmetros em busca do melhor modelo.
1. Selecione **Iniciar Treinamento**.

    Durante o processo de treinamento, os dados de progresso são exibidos na seção `Progress` da etapa de treinamento.

    - O status exibe o status de conclusão do processo de treinamento.
    - A melhor precisão exibe a precisão do modelo de melhor desempenho encontrado pelo Construtor do Modelo até o momento. Maior precisão significa que o modelo é previsto mais corretamente nos dados de teste.
    - O melhor algoritmo exibe o nome do algoritmo de melhor desempenho executado encontrado pelo Construtor de Modelo até o momento.
    - O último algoritmo exibe o nome do algoritmo usado mais recentemente pelo Construtor de Modelo para treinar o modelo.

1. Uma vez que o treinamento esteja concluído, selecione o link **de avaliação** para passar para a próxima etapa.

## <a name="evaluate-the-model"></a>Avalie o modelo

O resultado da etapa de treinamento será um modelo que tinha o melhor desempenho. Na etapa de avaliação da ferramenta Model Builder, a seção de saída, conterá o algoritmo usado pelo modelo de melhor desempenho na entrada **do Melhor Modelo,** juntamente com métricas em **Melhor Precisão de Modelo**. Além disso, uma tabela de resumo contém os cinco modelos principais e suas métricas.

Se você não estiver satisfeito com suas métricas de precisão, algumas maneiras fáceis de experimentar e aprimorar a precisão do modelo serão aumentar a quantidade de tempo para treinar o modelo ou usar mais dados. Caso contrário, selecione o link **de código** para passar para a etapa final na ferramenta Construtor de modelos.

## <a name="add-the-code-to-make-predictions"></a>Adicionar o código para fazer previsões

Dois projetos serão criados como resultado do processo de treinamento.

### <a name="reference-the-trained-model"></a>Referência ao modelo treinado

1. Na etapa de *código* da ferramenta Model Builder, **selecione Adicionar projetos** para adicionar os projetos gerados automaticamente à solução.

    Os seguintes projetos devem aparecer no **Solution Explorer**:

    - *SentimentRazorML.ConsoleApp*: Um aplicativo .NET Core Console que contém o código de treinamento e previsão do modelo.
    - *SentimentRazorML.Model*: Uma biblioteca de classe .NET Standard contendo os modelos de dados que definem o esquema de dados do modelo de entrada e saída, bem como a versão salva do modelo de melhor desempenho durante o treinamento.

    Para este tutorial, apenas o projeto *SentimentRazorML.Model* é usado porque as previsões serão feitas no aplicativo web *SentimentRazor* em vez de no console. Embora o *SentimentRazorML.ConsoleApp* não seja usado para marcar, ele pode ser usado para retreinar o modelo usando novos dados posteriormente. O retreinamento está fora do escopo deste tutorial.

### <a name="configure-the-predictionengine-pool"></a>Configure o pool ForecastEngine

Para fazer uma única previsão, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)você tem que criar um . [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)não é seguro para rosca. Além disso, você tem que criar uma instância dele em todos os lugares necessários dentro de sua aplicação. À medida que sua aplicação cresce, esse processo pode se tornar incontrolável. Para melhorar o desempenho e a segurança dos fios, use uma combinação de injeção de dependência e o `PredictionEnginePool` serviço, que cria um de [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objetos para uso em toda a sua aplicação.

1. Instale o pacote *Microsoft.Extensions.ML* NuGet:

    1. No **Gerenciador de Soluções**, clique com o botão direito no projeto e escolha **Gerenciar Pacotes NuGet**.
    1. Escolha "nuget.org" como fonte do Pacote.
    1. Selecione a guia **Procurar** e procurar por **Microsoft.Extensions.ML**.
    1. Selecione o pacote na lista e selecione o botão **Instalar.**
    1. Selecione o botão **OK** na caixa **de diálogo Visualização Alterações**
    1. Selecione o botão **Eu Aceito** na caixa de diálogo **Aceitação de Licença** se você concordar com os termos de licença dos pacotes listados.

1. Abra o arquivo *Startup.cs* no projeto *SentimentRazor.*
1. Adicione as seguintes instruções usando para referenciar o pacote *Microsoft.Extensions.ML* NuGet e o projeto *SentimentRazorML.Model:*

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. Crie uma variável global para armazenar a localização do arquivo de modelo treinado.

    ```csharp
    private readonly string _modelPath;
    ```

1. O arquivo modelo é armazenado no diretório de compilação ao lado dos arquivos de montagem do seu aplicativo. Para facilitar o acesso, crie um `GetAbsolutePath` método `Configure` auxiliar chamado após o método

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }
    ```

1. Use `GetAbsolutePath` o método `Startup` no construtor de `_modelPath`classe para definir o .

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. Configure `PredictionEnginePool` o para sua `ConfigureServices` aplicação no método:

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a>Crie manipulador de análise de sentimentos

As previsões serão feitas dentro da página principal do aplicativo. Portanto, um método que leve a `PredictionEnginePool` entrada do usuário e use o para retornar uma previsão precisa ser adicionado.

1. Abra o *arquivo Index.cshtml.cs* localizado no diretório *Páginas* e adicione as seguintes instruções usando:

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    Para usar o `PredictionEnginePool` configurado `Startup` na classe, você tem que injetá-lo no construtor do modelo onde você deseja usá-lo.

1. Adicione uma variável `PredictionEnginePool` para `IndexModel` referenciar o interior da classe.

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. Crie um construtor `IndexModel` na classe `PredictionEnginePool` e injete o serviço nele.

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }
    ```

1. Crie um manipulador de `PredictionEnginePool` métodos que use o para fazer previsões a partir da entrada do usuário recebida da página da Web.

    1. Abaixo `OnGet` do método, crie um novo método chamado`OnGetAnalyzeSentiment`

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. Dentro `OnGetAnalyzeSentiment` do método, retorne o sentimento *neutro* se a entrada do usuário estiver em branco ou nula.

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. Dada uma entrada válida, `ModelInput`crie uma nova instância de .

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. Use `PredictionEnginePool` o para prever sentimentos.

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. Converta o `bool` valor previsto em tóxico ou não tóxico com o seguinte código.

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. Finalmente, retorne o sentimento para a página web.

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a>Configure a página da Web

Os resultados devolvidos `OnGetAnalyzeSentiment` pelo serão exibidos `Index` dinamicamente na página web.

1. Abra o arquivo *Index.cshtml* no diretório *Páginas* e substitua seu conteúdo pelo seguinte código:

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. Em seguida, adicione o código de estilo css ao final da página *site.css* no diretório *wwwroot\css:*

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. Depois disso, adicione código para enviar entradas `OnGetAnalyzeSentiment` da página web para o manipulador.

    1. No arquivo *site.js* localizado no diretório *wwwroot\js,* crie `getSentiment` uma função chamada para fazer uma `OnGetAnalyzeSentiment` solicitação GET HTTP com a entrada do usuário para o manipulador.

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. Abaixo disso, adicione `updateMarker` outra função chamada para atualizar dinamicamente a posição do marcador na página da Web como o sentimento é previsto.

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. Crie uma função `updateSentiment` manipuladora de eventos chamada para obter `OnGetAnalyzeSentiment` a `getSentiment` entrada do usuário, `updateMarker` envie-a para a função usando a função e atualize o marcador com a função.

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. Finalmente, registre o manipulador de `textarea` eventos e `id=Message` vincule-o ao elemento com o atributo.

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a>Executar o aplicativo

Agora que seu aplicativo está configurado, execute o aplicativo que deve ser lançado no seu navegador.

Quando o aplicativo for lançado, digite *Model Builder é legal!* na área de texto. O sentimento previsto exibido não deve ser *tóxico.*

![Janela de execução com a janela de sentimento prevista](./media/sentiment-analysis-model-builder/web-app.png)

Se você precisar referenciar os projetos gerados pelo Model Builder posteriormente `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` dentro de outra solução, você pode encontrá-los dentro do diretório.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu a:
> [!div class="checklist"]
>
> - Crie um aplicativo de páginas de navalha ASP.NET
> - Preparar e compreender os dados
> - Escolha um cenário
> - Carregar os dados
> - Treinar o modelo
> - Avalie o modelo
> - Usar o modelo para previsões

### <a name="additional-resources"></a>Recursos adicionais

Para saber mais sobre os tópicos mencionados neste tutorial, visite os seguintes recursos:

- [Cenários do Construtor de Modelo](../automate-training-with-model-builder.md#scenarios)
- [Classificação Binária](../resources/glossary.md#binary-classification)
- [Métricas do modelo de classificação binária](../resources/metrics.md#evaluation-metrics-for-binary-classification)
