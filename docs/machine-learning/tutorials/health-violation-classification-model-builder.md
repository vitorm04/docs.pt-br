---
title: 'Tutorial: Classificar violações de saúde com Model Builder'
description: Este tutorial ilustra como construir um modelo de classificação multiclasse usando ML.NET Model Builder para classificar a gravidade da violação da saúde do restaurante em São Francisco.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: 6a36989f9453208e436ef8a4db2d4440aa0a1382
ms.sourcegitcommit: 2ff49dcf9ddf107d139b4055534681052febad62
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2020
ms.locfileid: "80438186"
---
# <a name="tutorial-classify-the-severity-of-restaurant-health-violations-with-model-builder"></a>Tutorial: Classifique a gravidade das violações à saúde do restaurante com o Model Builder

Aprenda a construir um modelo de classificação multiclasse usando o Model Builder para categorizar o nível de risco de violações de restaurantes encontrados durante inspeções de saúde.

Neste tutorial, você aprenderá como:

> [!div class="checklist"]
>
> - Preparar e compreender os dados
> - Escolha um cenário
> - Carregar dados de um banco de dados
> - Treinar o modelo
> - Avalie o modelo
> - Usar o modelo para previsões

> [!NOTE]
> O Construtor de Modelo está atualmente na Versão Prévia.

## <a name="prerequisites"></a>Pré-requisitos

Para obter uma lista de pré-requisitos e instruções de instalação, visite o [guia de instalação do Model Builder](../how-to-guides/install-model-builder.md).

## <a name="model-builder-multiclass-classification-overview"></a>Visão geral da classificação multiclasse do Model Builder

Esta amostra cria um aplicativo de console C# .NET Core que categoriza o risco de violações à saúde usando um modelo de aprendizado de máquina construído com o Model Builder. Você pode encontrar o código fonte para este tutorial no repositório GitHub [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations)

## <a name="create-a-console-application"></a>Criar um aplicativo de console

1. Crie um **aplicativo de console C# .NET Core** chamado "RestaurantViolations". Certifique-se de que **a solução e o projeto place no mesmo diretório** não são **controlados** (VS 2019), ou **Criar diretório para solução** é **verificado** (VS 2017).

## <a name="prepare-and-understand-the-data"></a>Preparar e compreender os dados

> O conjunto de dados usado para treinar e avaliar o modelo de aprendizagem de máquina é originalmente do [Departamento de Saúde Pública de São Francisco.](https://www.sfdph.org/dph/EH/Food/score/default.asp) Por conveniência, o conjunto de dados foi condensado para incluir apenas as colunas relevantes para treinar o modelo e fazer previsões. Visite o site a seguir para saber mais sobre o [conjunto de dados](https://data.sfgov.org/Health-and-Social-Services/Restaurant-Scores-LIVES-Standard/pyih-qa8i?row_index=0).

[Baixe o conjunto de dados Restaurant Safety Scores](https://github.com/luisquintanilla/machinelearning-samples/raw/AB1608219/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantScores.zip) e descompacte-o.

Cada linha do conjunto de dados contém informações sobre violações observadas durante uma inspeção do Departamento de Saúde e uma avaliação de risco da ameaça que essas violações apresentam à saúde e segurança pública.

| Tipo de inspeção | ViolaçãoDescriçãoDescrição | Categoria de Risco |
| --- | --- | --- |
| Rotina - Não programada | Superfícies de contato com alimentos inadequadamente limpos ou higienizados | Risco Moderado |
| Nova Propriedade | Infestação de vermes de alto risco | Alto Risco |
| Rotina - Não programada | Enxugando panos não limpos ou armazenados corretamente ou desinfetante inadequado | Baixo Risco |

- **Tipo de inspeção**: o tipo de inspeção. Isso pode ser uma inspeção pela primeira vez para um novo estabelecimento, uma inspeção de rotina, uma inspeção de reclamações e muitos outros tipos.
- **Descrição da violação:** uma descrição da violação encontrada durante a inspeção.
- **Categoria de Risco**: a gravidade do risco que uma violação representa para a saúde pública e a segurança.

O `label` é a coluna que você deseja prever. Ao executar uma tarefa de classificação, o objetivo é atribuir uma categoria (texto ou numérico). Nesse cenário de classificação, a gravidade da violação é atribuída ao valor de baixo, moderado ou alto risco. Portanto, a **Categoria de Risco** é o rótulo. São `features` as entradas que você dá `label`ao modelo para prever o . Neste caso, o **InspectionType** e **o ViolationDescription** são usados como recursos ou entradas para prever a **Categoria de Risco**.

## <a name="choose-a-scenario"></a>Escolha um cenário

![Assistente do Construtor de Modelos no Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

Para treinar seu modelo, selecione na lista de cenários de aprendizado de máquina disponíveis fornecidos pelo Model Builder. Neste caso, o cenário é *Classificação de Problemas*.

1. No **Solution Explorer,** clique com o botão direito do mouse no projeto *RestaurantViolações* e selecione **Adicionar** > **aprendizado de máquina**.
1. Para esta amostra, o cenário é a classificação multiclasse. Na etapa *de cenário* do Model Builder, selecione o cenário **classificação de** problemas.

## <a name="load-the-data"></a>Carregar os dados

O Model Builder aceita dados de um banco de `csv` `tsv` dados SQL Server ou de um arquivo local dentro ou em formato.

1. Na etapa de dados da ferramenta Model Builder, selecione **SQL Server** a partir da gota de origem de dados.
1. Selecione o botão ao lado da caixa de texto **do banco de dados Connect to SQL Server.**
    1. Na caixa de diálogo **Escolher dados,** selecione **O arquivo de banco de dados do Microsoft SQL Server**.
    1. Desmarque o Use sempre esta caixa **de seleção** e selecione **Continuar**.
    1. Na caixa de diálogo Propriedades de **conexão,** **selecione Procurar** e selecione o arquivo *RestaurantScores.mdf* baixado.
    1. Selecione **OK**.
1. Escolha **Violações** na estada **nome da tabela.**
1. Escolha **RiscoCategoria** na **coluna para prever (rótulo)** a gota.
1. Deixe as seleções de coluna padrão, **InspectionType** e **ViolationDescription**, verificadas na parada **Colunas de entrada (Recursos).**
1. Selecione o link **Trem** para passar para a próxima etapa do Model Builder.

## <a name="train-the-model"></a>Treinar o modelo

A tarefa de aprendizado de máquina usada para treinar o modelo de classificação de problemas neste tutorial é a classificação multiclasse. Durante o processo de treinamento do modelo, o Model Builder treina modelos separados usando diferentes algoritmos de classificação multiclasse e configurações para encontrar o modelo de melhor desempenho para o seu conjunto de dados.

O tempo necessário para o modelo treinar é proporcional à quantidade de dados. O Model Builder seleciona automaticamente um valor padrão para **tempo de treinar (segundos)** com base no tamanho da fonte de dados.

1. Embora o Model Builder defina o valor do **Tempo para treinar (segundos)** para 10 segundos, aumente-o para 30 segundos. O treinamento por um período maior de tempo permite ao Model Builder explorar um número maior de algoritmos e combinação de parâmetros em busca do melhor modelo.
1. Selecione **Iniciar Treinamento**.

    Durante o processo de treinamento, os dados de progresso são exibidos na seção `Progress` da etapa de treinamento.

    - **O status** exibe o status de conclusão do processo de treinamento.
    - **A melhor precisão** mostra a precisão do modelo de melhor desempenho encontrado pelo Model Builder até agora. Maior precisão significa que o modelo é previsto mais corretamente nos dados de teste.
    - **O melhor algoritmo** exibe o nome do algoritmo de melhor desempenho encontrado pelo Model Builder até agora.
    - **O último algoritmo** exibe o nome do algoritmo mais recentemente usado pelo Model Builder para treinar o modelo.

1. Uma vez que o treinamento esteja concluído, selecione o link **Avaliar** para passar para a próxima etapa.

## <a name="evaluate-the-model"></a>Avalie o modelo

O resultado da etapa de treinamento é o modelo que teve o melhor desempenho. Na etapa de avaliação do Model Builder, a seção de saída contém o algoritmo usado pelo modelo de melhor desempenho na entrada **Do Melhor Modelo,** juntamente com as métricas em **Melhor Precisão de Modelo**. Além disso, uma tabela de resumo contendo até cinco modelos que foram explorados e suas métricas é exibida.

Se você não está satisfeito com suas métricas de precisão, algumas maneiras fáceis de tentar melhorar a precisão do modelo são aumentar o tempo para treinar o modelo ou usar mais dados. Caso contrário, selecione o link **de código** para passar para a etapa final do Model Builder.

## <a name="add-the-code-to-make-predictions"></a>Adicionar o código para fazer previsões

Dois projetos são criados como resultado do processo de treinamento.

- RestaurantViolaçõesML.ConsoleApp: Um aplicativo C# .NET Core Console que contém o código de treinamento do modelo e o código de consumo de amostras.
- RestaurantViolationsML.Model: Uma biblioteca de classe .NET Standard contendo os modelos de dados que definem o esquema de dados do modelo `ConsumeModel` de entrada e saída, a versão salva do modelo de melhor desempenho durante o treinamento e uma classe auxiliar chamada para fazer previsões.

1. Na etapa de código do Model Builder, selecione **Adicionar projetos** para adicionar os projetos gerados automaticamente à solução.
1. Abra o arquivo *Program.cs* no projeto *RestaurantViolations.*
1. Adicione a seguinte declaração usando para referenciar o projeto *RestaurantViolationsML.Model:*

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L2)]

1. Para fazer uma previsão sobre novos dados usando o `ModelInput` modelo, `Main` crie uma nova instância da classe dentro do método de sua aplicação. Observe que a categoria de risco não faz parte da entrada. Isso porque o modelo gera a previsão para ele.

    [!code-csharp [TestData](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L11-L15)]

1. Use `Predict` o método `ConsumeModel` da classe. O `Predict` método carrega o modelo [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) treinado, cria um para o modelo e o usa para fazer previsões sobre novos dados.

    [!code-csharp [Prediction](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L17-L24)]

1. Execute o aplicativo.

    A saída gerada pelo programa deve ser semelhante ao snippet a seguir:

    ```bash
    Inspection Type: Complaint
    Violation Description: Inadequate sewage or wastewater disposal
    Risk Category: Moderate Risk
    ```

Se precisar fazer referência aos projetos gerados em um momento posterior dentro de outra solução, você poderá encontrá-los no diretório `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.

Parabéns! Você construiu com sucesso um modelo de aprendizado de máquina para categorizar o risco de violações à saúde usando o Model Builder. Você pode encontrar o código fonte para este tutorial no repositório GitHub [dotnet/machinelearning-samples.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations)

## <a name="additional-resources"></a>Recursos adicionais

Para saber mais sobre os tópicos mencionados neste tutorial, visite os seguintes recursos:

- [Cenários do Construtor de Modelo](../automate-training-with-model-builder.md#scenario)
- [Classificação multiclasse](../resources/glossary.md#multiclass-classification)
- [Métricas do modelo de classificação multiclasse](../resources/metrics.md#evaluation-metrics-for-multi-class-classification)
