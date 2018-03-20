---
title: Conceitos e modelo de objeto do SDK do .NET Compiler Platform
description: "Esta visão geral fornece o contexto necessário para trabalhar efetivamente com o SDK do .NET Compiler. Você aprenderá sobre as camadas de API, os principais tipos envolvidos e o modelo de objeto geral."
author: billwagner
ms.author: wiwagn
ms.date: 10/10/2017
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: d230d334eba4e438635a4c70e8c1b5fc5075b065
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="understand-the-net-compiler-platform-sdk-model"></a>Entender o modelo do SDK do .NET Compiler Platform

Os compiladores processam o código escrito seguindo regras estruturadas que geralmente diferem da forma como os humanos leem e entendem um código. Uma compreensão básica do modelo usado pelos compiladores é essencial para compreender as APIs usadas ao criar ferramentas baseadas no Roslyn. 

## <a name="compiler-pipeline-functional-areas"></a>Áreas funcionais do pipeline do compilador

O SDK do .NET Compiler Platform expõe a análise de código dos compiladores C# e Visual Basic para você como um consumidor, fornecendo uma camada de API que espelha um pipeline de compilador tradicional.

![etapas de processamento do pipeline do compilador do código-fonte para o código de objeto](media/compiler-pipeline.png)

Cada fase desse pipeline é um componente separado. Primeiro, a fase de análise cria tokens do texto de origem e o analisa na sintaxe que segue a gramática da linguagem. Depois, a fase de declaração analisa os metadados de origem e importados para formar símbolos nomeados. Em seguida, a fase de associação corresponde os identificadores no código aos símbolos. Por fim, a fase de emissão emite um assembly com todas as informações criadas pelo compilador.

![API do pipeline do compilador fornece acesso a cada etapa que faz parte do pipeline do compilador](media/compiler-pipeline-api.png)

Correspondente a cada uma dessas fases, o SDK do .NET Compiler Platform expõe um modelo de objeto que permite o acesso às informações da fase. A fase de análise expõe uma árvore de sintaxe, a fase de declaração expõe uma tabela de símbolos hierárquica, a fase de associação expõe o resultado da análise semântica do compilador e a fase de emissão é uma API que gera códigos de bytes de IL.

![os serviço de linguagem disponíveis na API do compilador em cada etapa do pipeline do compilador](media/compiler-pipeline-lang-svc.png)

Cada compilador combina esses componentes como um único inteiro de ponta a ponta.

Essas APIs são as mesmas usadas pelo Visual Studio. Por exemplo, os recursos de formatação e estrutura de tópicos do código usam as árvores de sintaxe, o Pesquisador de Objetos e os recursos de navegação usam a tabela de símbolos, as refatorações e o recurso Ir para Definição usam o modelo semântico e o recurso Editar e Continuar usa todos eles, incluindo a API de Emissão. 

## <a name="api-layers"></a>Camadas de API

O SDK do .NET Compiler consiste em duas camadas principais de APIs: APIs do compilador e APIs dos espaços de trabalho.

![as camadas de API representadas pelas APIs do pipeline do compilador](media/api-layers.png)

### <a name="compiler-apis"></a>APIs do compilador

A camada do compilador contém os modelos de objeto que correspondem às informações expostas em cada fase do pipeline do compilador, tanto sintáticas quanto semânticas. A camada do compilador também contém um instantâneo imutável de uma única invocação de um compilador, incluindo referências de assembly, opções do compilador e arquivos de código-fonte. Há duas APIs distintas que representam a linguagem C# e a linguagem Visual Basic. Essas duas APIs são semelhantes na forma, mas adaptadas para alta fidelidade a cada linguagem individual. Essa camada não tem dependências em componentes do Visual Studio.

### <a name="diagnostic-apis"></a>APIs de diagnóstico

Como parte de sua análise, o compilador pode produzir um conjunto de diagnósticos que abrangem tudo, desde a sintaxe, semântica e erros de atribuição definitiva a vários diagnósticos de avisos e informativos. A camada de API do Compilador expõe o diagnóstico por meio de uma API extensível que permite que os analisadores definidos pelo usuário sejam conectados ao processo de compilação. Ela possibilita que o diagnóstico definido pelo usuário, como aqueles gerados por ferramentas como o StyleCop ou FxCop, seja produzido junto com o diagnóstico definido pelo compilador. A produção de diagnóstico dessa maneira tem o benefício da integração natural a ferramentas como o MSBuild e Visual Studio, que dependem do diagnóstico para experiências como interrupção de um build com base na política, exibição de rabiscos em tempo real no editor e sugestão de correções de código.

### <a name="scripting-apis"></a>APIs de script

APIs de hospedagem e script fazem parte da camada do compilador. Você pode usá-las para execução de trechos de código e acúmulo de um contexto de execução em tempo de execução.
O REPL (Loop de Leitura-Avaliação-Impressão) interativo do C# usa essas APIs. O REPL permite usar o C# como a linguagem de scripts, executando o código de forma interativa à medida que ele é escrito.

### <a name="workspaces-apis"></a>APIs dos espaços de trabalho

A camada Espaços de Trabalho contém a API de Espaço de Trabalho, que é o ponto de partida para fazer a análise de código e refatoração em soluções inteiras. Ela ajuda você a organizar todas as informações sobre os projetos de uma solução em um único modelo de objeto, oferecendo acesso direto aos modelos de objeto da camada do compilador, sem a necessidade de analisar arquivos, configurar opções ou gerenciar dependências de projeto a projeto.

Além disso, a camada Espaços de Trabalho expõe um conjunto de APIs usado ao implementar ferramentas de análise de código e refatoração que funcionam em um ambiente de host como o IDE do Visual Studio. Exemplos incluem as APIs Localizar Todas as Referências, Formatação e Geração de Código.

Essa camada não tem dependências em componentes do Visual Studio.
