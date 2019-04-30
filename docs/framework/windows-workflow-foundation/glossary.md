---
title: Glossário do Windows Workflow Foundation para o .NET Framework 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Workflow Foundation [WF], glossary
- WF [WF], glossary
ms.assetid: ab682b2f-3779-45ca-b831-b7c03d7dbb3a
ms.openlocfilehash: 61d9acab1161302937e240eb8ebb506ca9f1585c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945620"
---
# <a name="windows-workflow-foundation-glossary-for-net-framework-45"></a>Glossário do Windows Workflow Foundation para o .NET Framework 4.5

Os seguintes termos são usados na documentação do Windows Workflow Foundation.

## <a name="terms"></a>Termos

|Termo|Definição|
|----------|----------------|
|atividade|Uma unidade de comportamento do programa no Windows Workflow Foundation. Atividades únicas podem ser compostas juntos em atividades mais complexas.|
|ação de atividade|Uma estrutura de dados usada para expor retornos de chamada para a execução de fluxo de trabalho e atividades.|
|argumento|Define o fluxo de dados dentro e fora de uma atividade. Cada argumento tem uma direção especificada:, ou na entrada/saída. Eles representam a entrada, saída e parâmetros de entrada/saída da atividade.|
|Indicador|O ponto em que uma atividade pode pausar e esperar para ser retomada.|
|Compensação|Um grupo de ações criadas para desfazer ou diminuir o efeito anteriormente concluído o trabalho.|
|Correlação|O mecanismo para rotear mensagens para uma instância de fluxo de trabalho ou serviço.|
|expressão|Uma construção que usa um ou mais argumentos de entrada, executa uma operação nos argumentos e retorna um único valor. Expressões podem ser usadas em qualquer lugar em que uma atividade pode ser usada.|
|Fluxograma|Um paradigma de modelagem bem conhecido que representa os componentes de programa como símbolos vinculados junto com as setas direcionais.  No .NET Framework 4, os fluxos de trabalho podem ser modelados como fluxogramas, usando a atividade do fluxograma.|
|processo de execução longa|Uma unidade de execução do programa que não retorna imediatamente e pode abranger reinicializações do sistema.|
|persistência|Salvando o estado de um fluxo de trabalho ou o serviço a um meio durável, para que possa ser descarregado da memória ou recuperado após uma falha do sistema.|
|máquina de estado|Um paradigma de modelagem bem conhecido que representa os componentes de programa como cada um dos Estados vinculado junto com as transições de estado controlado por evento.  Fluxos de trabalho podem ser modelados como máquinas de estado usando a atividade de StateMachine.|
|substância|Representa um grupo de indicadores relacionados em um identificador comum e permite que o tempo de execução tomar decisões sobre se uma continuidade de indicador específico é válida ou se tornar válida.|
|conversor de tipo|Um tipo de CLR pode ser associado com um ou mais tipos derivados System.ComponentModel.TypeConverter que permitem converter instâncias do tipo da CLR e instâncias de outros tipos. Um conversor de tipo está associado um tipo CLR usando o atributo System.  Um TypeConverterAttribute pode ser especificado diretamente no tipo de CLR ou propriedade. Um conversor de tipo especificado em uma propriedade sempre tem precedência sobre um conversor de tipo especificado no tipo de CLR de propriedade.|
|variável|Representa o armazenamento de alguns dados que devem ser salvos e acessados posteriormente.|
|fluxo de trabalho|Uma única atividade ou a árvore de atividades, invocado por um processo de host.|
|XAML|extensible application marcação idioma|
