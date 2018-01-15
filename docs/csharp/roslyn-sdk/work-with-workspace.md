---
title: "Trabalhar com o modelo de espaço de trabalho do SDK do .NET Compiler Platform"
description: "Esta visão geral fornece uma compreensão do tipo usado para consultar e manipular o espaço de trabalho e os projetos para o código."
author: billwagner
ms.author: wiwagn
ms.date: 10/15/2017
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: d0d4e9c012b025b9393ac34f0833795fca9841d5
ms.sourcegitcommit: d095094e942eedf09530ea5636fbaf9029853027
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2017
---
# <a name="work-with-a-workspace"></a>Trabalhar com um espaço de trabalho

A camada **Espaços de Trabalho** contém a API de Espaço de Trabalho para fazer a análise de código e refatoração em soluções inteiras. Nessa camada, a API do Espaço de Trabalho ajudará você a organizar todas as informações sobre os projetos de uma solução em um único modelo de objeto, oferecendo acesso direto aos modelos de objeto da camada do compilador como texto de origem, árvores de sintaxe, modelos semânticos e compilações, sem a necessidade de analisar arquivos, configurar opções ou gerenciar dependências entre projetos. 

Ambientes de host, como um IDE, fornecem um espaço de trabalho para você correspondente à solução aberta. Também é possível usar esse modelo fora de um IDE apenas carregando um arquivo de solução.

## <a name="workspace"></a>Espaço de trabalho

Um espaço de trabalho é uma representação ativa da solução como uma coleção de projetos, cada uma com uma coleção de documentos. Um espaço de trabalho normalmente é vinculado a um ambiente de host que está sendo modificado constantemente conforme um usuário digita ou manipula propriedades. 

O <xref:Microsoft.CodeAnalysis.Workspace> fornece acesso ao modelo atual da solução. Quando ocorre uma alteração no ambiente de host, o espaço de trabalho aciona eventos correspondentes e a propriedade <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> é atualizada. Por exemplo, quando o usuário digita em um editor de texto algo correspondente a um dos documentos de origem, o espaço de trabalho usa um evento para sinalizar que o modelo geral da solução foi alterado e qual documento foi modificado. Em seguida, você pode reagir a essas alterações analisando o novo modelo quanto à exatidão, realçando áreas de significância ou fazendo uma sugestão de alteração de código. 

Também pode criar espaços de trabalho independentes desconectados do ambiente de host ou usados em um aplicativo que não tem nenhum ambiente de host.

## <a name="solutions-projects-documents"></a>Soluções, projetos, documentos

Embora um espaço de trabalho possa ser alterado sempre que uma tecla é pressionada, você pode trabalhar com o modelo da solução de forma isolada. 

Uma solução é um modelo imutável dos projetos e documentos. Isso significa que o modelo pode ser compartilhado sem bloqueio nem duplicação. Depois de obter uma instância da solução da propriedade <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType>, essa instância nunca será alterada. No entanto, assim como árvores de sintaxe e compilações, você pode modificar soluções construindo novas instâncias com base em soluções existentes e alterações específicas. Para fazer com que o espaço de trabalho reflita as alterações, é necessário aplicar explicitamente a solução alterada novamente ao espaço de trabalho.

Um projeto é uma parte do modelo de solução imutável geral. Ele representa todos os documentos do código-fonte, opções de análise e compilação e referências de assembly e projeto a projeto. Em um projeto, você pode acessar a compilação correspondente sem a necessidade de determinar as dependências de projeto nem analisar arquivos de origem.

Um documento também é uma parte do modelo de solução imutável geral. Um documento representa um único arquivo de origem do qual você pode acessar o texto do arquivo, a árvore de sintaxe e o modelo semântico.

O diagrama a seguir é uma representação de como o Espaço de Trabalho se relaciona ao ambiente de host, às ferramentas e ao modo como as edições são feitas.

![as relações entre os diferentes elementos de um espaço de trabalho que contém projetos e arquivos de origem](media/workspace-obj-relations.png)

## <a name="summary"></a>Resumo

O Roslyn expõe um conjunto de APIs do compilador e APIs dos Espaços de Trabalho que fornecem informações detalhadas sobre o código-fonte e que têm fidelidade total com as linguagens C# e Visual Basic.  O SDK do .NET Compiler Platform diminui drasticamente a barreira de entrada para a criação de aplicativos e ferramentas voltadas para o código. Ele cria várias oportunidades para inovação em áreas como metaprogramação, geração e transformação de código, uso interativo das linguagens C# e VB e incorporação de C# e VB a linguagens específicas de domínio.  
