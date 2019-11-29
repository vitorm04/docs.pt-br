---
title: 'Tutorial: classificar violações de integridade com o construtor de modelos'
description: Este tutorial ilustra como criar um modelo de classificação multiclasse usando o ML.NET Model Builder para classificar a severidade de violação de integridade de restaurante em São Francisco.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 07729e1667f8aa3aba74576943d79eaa3bcd14d8
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552893"
---
# <a name="tutorial-classify-the-severity-of-restaurant-health-violations-with-model-builder"></a>Tutorial: classificar a gravidade das violações de integridade do restaurante com o construtor de modelos

Saiba como criar um modelo de classificação multiclasse usando o construtor de modelos para categorizar o nível de risco de violações de restaurante encontradas durante as inspeções de integridade.

Neste tutorial, você aprenderá como:

> [!div class="checklist"]
>
> - Preparar e compreender os dados
> - Escolha um cenário
> - Carregar dados de um banco
> - Treinar o modelo
> - Avaliar o modelo
> - Usar o modelo para previsões

> [!NOTE]
> O Construtor de Modelo está atualmente na Versão Prévia.

## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}

Para obter uma lista de pré-requisitos e instruções de instalação, visite o [Guia de instalação do Model Builder](../how-to-guides/install-model-builder.md).

## <a name="model-builder-multiclass-classification-overview"></a>Visão geral da classificação multiclasse do construtor de modelos

Este exemplo cria um C# aplicativo de console .NET Core que categoriza o risco de violações de integridade usando um modelo de aprendizado de máquina criado com o construtor de modelos. Você pode encontrar o código-fonte deste tutorial no repositório do GitHub [dotnet/MachineLearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations) .

## <a name="create-a-console-application"></a>Criar um aplicativo de console

1. Crie um  **C# aplicativo de console do .NET Core** chamado "RestaurantViolations". Verifique se a opção **Colocar solução e projeto no mesmo diretório** está **desmarcada** (vs 2019) ou **criar diretório para solução** está **marcado** (vs 2017).

## <a name="prepare-and-understand-the-data"></a>Preparar e compreender os dados

> O conjunto de dados usado para treinar e avaliar o modelo de aprendizado de máquina é originalmente da [Pontuação de segurança de restaurantes do departamento de saúde pública de San Francisco](https://www.sfdph.org/dph/EH/Food/score/default.asp). Para sua conveniência, o conjunto de linhas foi condensado para incluir apenas as colunas relevantes para treinar o modelo e fazer previsões. Visite o site a seguir para saber mais sobre o [conjunto](https://data.sfgov.org/Health-and-Social-Services/Restaurant-Scores-LIVES-Standard/pyih-qa8i?row_index=0)de informações.

[Baixe o conjunto de resultados de pontos de segurança do restaurante](https://github.com/luisquintanilla/machinelearning-samples/raw/AB1608219/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantScores.zip) e descompacte-o.

Cada linha no conjunto de dados contém informações sobre violações observadas durante uma inspeção do departamento de integridade e uma avaliação de risco da ameaça que essas violações apresentam à integridade pública e à segurança.

| De inspeção | ViolationDescription | RiskCategory |
| --- | --- | --- |
| Rotina-não agendada | Superfícies de contato de alimentos desfeitas ou limpas inadequadamente | Risco moderado |
| Nova Propriedade | Infestação Vermin de alto risco | Alto risco |
| Rotina-não agendada | Limpando os panons não limpos ou corretamente armazenados ou inadequados | Baixo risco |

- **Inspeçãotype**: o tipo de inspeção. Isso pode ser uma inspeção pela primeira vez para um novo estabelecimento, uma inspeção de rotina, uma inspeção de reclamação e muitos outros tipos.
- **ViolationDescription**: uma descrição da violação encontrada durante a inspeção.
- **RiskCategory**: a severidade de risco uma violação representa a integridade pública e a segurança.

O `label` é a coluna que você deseja prever. Ao executar uma tarefa de classificação, o objetivo é atribuir uma categoria (texto ou numérico). Nesse cenário de classificação, a severidade da violação é atribuída ao valor baixo, moderado ou alto risco. Portanto, o **RiskCategory** é o rótulo. As `features` são as entradas que você fornece ao modelo para prever o `label`. Nesse caso, o **inspeções de inspeção** e **ViolationDescription** são usados como recursos ou entradas para prever o **RiskCategory**.

## <a name="choose-a-scenario"></a>Escolha um cenário

![Assistente do construtor de modelos no Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

Para treinar seu modelo, selecione na lista de cenários de aprendizado de máquina disponíveis fornecidos pelo construtor de modelos. Nesse caso, o cenário é a *classificação do problema*.

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto *RestaurantViolations* e selecione **Adicionar** > **Machine Learning**.
1. Para este exemplo, o cenário é classificação multiclasse. Na etapa *cenário* do construtor de modelos, selecione o cenário de **classificação do problema** .

## <a name="load-the-data"></a>Carregar os dados

O construtor de modelos aceita dados de um banco de SQL Server ou de um arquivo local no formato `csv` ou `tsv`.

1. Na etapa dados da ferramenta Construtor de modelos, selecione **SQL Server** na lista suspensa fonte de dados.
1. Selecione o botão ao lado da caixa de texto **conectar ao SQL Server banco de dados** .
    1. Na caixa de diálogo **escolher dados** , selecione **Microsoft SQL Server arquivo de banco**.
    1. Desmarque a caixa de seleção **sempre usar esta seleção** e selecione **continuar**.
    1. Na caixa de diálogo **Propriedades da conexão** , selecione **procurar** e selecione o arquivo *RestaurantScores. MDF* baixado.
    1. Selecione **OK**.
1. Escolha **violações** na lista suspensa **nome da tabela** .
1. Escolha **RiskCategory** na **coluna para prever (rótulo)** DropDown.
1. Deixe as seleções de coluna padrão, **inspeções de inspeção** e **ViolationDescription**, marcadas na lista suspensa **colunas de entrada (recursos)** .
1. Selecione o link **treinar** para mover para a próxima etapa no construtor de modelos.

## <a name="train-the-model"></a>Treinar o modelo

A tarefa de aprendizado de máquina usada para treinar o modelo de classificação de problemas neste tutorial é classificação multiclasse. Durante o processo de treinamento do modelo, o construtor de modelos treina modelos separados usando diferentes algoritmos de classificação multiclasse e configurações para encontrar o melhor modelo de desempenho para seu conjunto de seus.

O tempo necessário para o modelo treinar é proporcional à quantidade de dados. O construtor de modelos seleciona automaticamente um valor padrão para o **tempo de treinamento (segundos)** com base no tamanho da fonte de dados.

1. Embora o construtor de modelos defina o valor de **tempo para treinar (segundos)** como 10 segundos, aumente-o para 30 segundos. O treinamento para um período de tempo maior permite que o construtor de modelos Explore um número maior de algoritmos e uma combinação de parâmetros na pesquisa do melhor modelo.
1. Selecione **Iniciar Treinamento**.

    Durante o processo de treinamento, os dados de progresso são exibidos na seção `Progress` da etapa de treinamento.

    - **Status** exibe o status de conclusão do processo de treinamento.
    - A **melhor precisão** exibe a precisão do melhor modelo de desempenho encontrado pelo construtor de modelos até o momento. Maior precisão significa que o modelo é previsto mais corretamente nos dados de teste.
    - **Melhor algoritmo** exibe o nome do algoritmo de melhor desempenho encontrado pelo construtor de modelos até o momento.
    - **Último algoritmo** exibe o nome do algoritmo usado mais recentemente pelo construtor de modelos para treinar o modelo.

1. Quando o treinamento estiver concluído, selecione o link **avaliar** para passar para a próxima etapa.

## <a name="evaluate-the-model"></a>Avaliar o modelo

O resultado da etapa de treinamento é um modelo que tinha o melhor desempenho. Na etapa avaliar do construtor de modelos, a seção saída contém o algoritmo usado pelo melhor modelo de desempenho na melhor entrada de **modelo** , juntamente com as métricas na **melhor precisão do modelo**. Além disso, uma tabela de resumo que contém até cinco modelos que foram explorados e suas métricas são exibidas.

Se você não estiver satisfeito com suas métricas de precisão, algumas maneiras fáceis de tentar melhorar a precisão do modelo são aumentar a quantidade de tempo para treinar o modelo ou usar mais dados. Caso contrário, selecione o link de **código** para mover para a etapa final no construtor de modelos.

## <a name="add-the-code-to-make-predictions"></a>Adicionar o código para fazer previsões

Dois projetos são criados como resultado do processo de treinamento.

- RestaurantViolationsML. ConsoleApp: um C# aplicativo de console do .NET Core que contém o treinamento do modelo e o código de consumo de exemplo.
- RestaurantViolationsML. Model: um .NET Standard biblioteca de classes que contém os modelos de dados que definem o esquema de dados de modelo de entrada e saída, a versão salva do modelo de melhor desempenho durante o treinamento e uma classe auxiliar chamada `ConsumeModel` para fazer previsões.

1. Na etapa de código do construtor de modelos, selecione **adicionar projetos** para adicionar os projetos gerados automaticamente à solução.
1. Abra o arquivo *Program.cs* no projeto *RestaurantViolations* .
1. Adicione a seguinte instrução using para fazer referência ao projeto *RestaurantViolationsML. Model* :

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L2)]

1. Para fazer uma previsão sobre novos dados usando o modelo, crie uma nova instância da classe `ModelInput` dentro do método `Main` do seu aplicativo. Observe que a categoria de risco não faz parte da entrada. Isso ocorre porque o modelo gera a previsão para ela.

    [!code-csharp [TestData](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L11-L15)]

1. Use o método `Predict` da classe `ConsumeModel`. O método `Predict` carrega o modelo treinado, cria um [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) para o modelo e o usa para fazer previsões sobre novos dados.

    [!code-csharp [Prediction](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L17-L24)]

1. Execute o aplicativo.

    A saída gerada pelo programa deve ser semelhante ao snippet a seguir:

    ```bash
    Inspection Type: Complaint
    Violation Description: Inadequate sewage or wastewater disposal
    Risk Category: Moderate Risk
    ```

Se precisar fazer referência aos projetos gerados em um momento posterior dentro de outra solução, você poderá encontrá-los no diretório `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.

Parabéns! Você criou com êxito um modelo de aprendizado de máquina para categorizar o risco de violações de integridade usando o construtor de modelos. Você pode encontrar o código-fonte deste tutorial no repositório do GitHub [dotnet/MachineLearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations) .

## <a name="additional-resources"></a>Recursos adicionais

Para saber mais sobre os tópicos mencionados neste tutorial, visite os seguintes recursos:

- [Cenários do Construtor de Modelo](../automate-training-with-model-builder.md#scenarios)
- [Classificação Multiclasse](../resources/glossary.md#multiclass-classification)
- [Métricas do modelo de classificação multiclasse](../resources/metrics.md#metrics-for-multi-class-classification)
