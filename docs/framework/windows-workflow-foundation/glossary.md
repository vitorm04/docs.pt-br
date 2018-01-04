---
title: "Glossário do Windows Workflow Foundation para o .NET Framework 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Workflow Foundation [WF], glossary
- WF [WF], glossary
ms.assetid: ab682b2f-3779-45ca-b831-b7c03d7dbb3a
caps.latest.revision: "259"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54a0cc6d9a0c922e57bf00b649894f26b42a64f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-workflow-foundation-glossary-for-net-framework-45"></a>Glossário do Windows Workflow Foundation para o .NET Framework 4.5
Os seguintes termos são usados na documentação do Windows Workflow Foundation.  
  
## <a name="terms"></a>Termos  
  
|Termo|Definição|  
|----------|----------------|  
|atividade|Uma unidade de comportamento de programa do Windows Workflow Foundation. Atividades único podem ser compostas juntos em atividades mais complexas.|  
|ação de atividade|Uma estrutura de dados usada para expor os retornos de chamada para execução de fluxo de trabalho e atividades.|  
|Argumento|Define o fluxo de dados dentro e fora de uma atividade. Cada argumento tem uma direção especificada:, ou em entrada/saída. Eles representam a entrada, saída e parâmetros de entrada/saída da atividade.|  
|Indicador|O ponto em que uma atividade pode pausar e aguarde a ser retomado.|  
|compensação|Um grupo de ações criadas para desfazer ou reduzir o efeito de anteriormente concluir o trabalho.|  
|Correlação|O mecanismo de roteamento de mensagens para uma instância de fluxo de trabalho ou serviço.|  
|expressão|Uma construção que entra em um ou mais argumentos, executa uma operação sobre os argumentos e retorna um único valor. Expressões podem ser usadas em qualquer lugar que uma atividade pode ser usada.|  
|fluxograma|Um paradigma de modelagem bem conhecido que representa os componentes de programa como símbolos vinculados junto com as setas direcionais.  No .NET Framework 4, os fluxos de trabalho podem ser modelados como fluxogramas usando a atividade do fluxograma.|  
|processo de execução longa|Uma unidade de execução do programa que não retorna imediatamente e pode abranger reinicializações do sistema.|  
|persistência|Salvar o estado de um fluxo de trabalho ou um serviço em uma mídia durável, para que possa ser descarregado da memória ou recuperado após uma falha do sistema.|  
|máquina de estado|Um paradigma de modelagem bem conhecido que representa os componentes de programa, como cada um dos Estados vinculado junto com as transições de estado controlada por evento.  Fluxos de trabalho podem ser modelados como máquinas de estado usando a atividade de StateMachine.|  
|substância|Representa um grupo de marcadores relacionados em um identificador comum e permite que o tempo de execução tomar decisões sobre se uma continuação de determinado indicador é válida ou se tornem válida.|  
|conversor de tipo|Um tipo de CLR pode ser associado com um ou mais tipos derivados System.ComponentModel.TypeConverter que permitem converter instâncias do tipo da CLR e instâncias de outros tipos. Um converterr de tipo é associado com um tipo de CLR usando o atributo System.ComponentModel.TypeConverterAttribute.  Um TypeConverterAttribute pode ser especificado diretamente no tipo de CLR ou propriedade. Um conversor de tipo especificado em uma propriedade sempre tem precedência sobre um conversor de tipo especificado no tipo de CLR de propriedade.|  
|variável|Representa o armazenamento de alguns dados que devem ser salvos e acessados posteriormente.|  
|fluxo de trabalho|Uma única atividade ou árvore de atividades invocado por um processo de host.|  
|XAML|extensible application marcação idioma|
