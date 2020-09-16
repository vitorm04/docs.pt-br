---
title: Adicionando uma referência de serviço em uma solução de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: 1b4cc16d3bd85c28ac7267e88ae0a714620c9861
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557052"
---
# <a name="add-a-service-reference-in-a-workflow-solution"></a>Adicionar uma referência de serviço em uma solução de fluxo de trabalho

Adicionar uma referência de serviço em um aplicativo de fluxo de trabalho funciona um pouco diferente do que um aplicativo WCF regular. Quando você seleciona **Adicionar**  >  **referência de serviço** e especifica a URL para o serviço, os metadados são baixados e as atividades personalizadas são geradas que permitem chamar esse serviço WCF ou o serviço de fluxo de trabalho WCF. Depois de adicionar uma referência de serviço, recompile a solução para que as atividades geradas sejam criadas. Eles serão exibidos na caixa de ferramentas do designer de fluxo de trabalho. Isso só funcionará se você estiver adicionando uma referência de serviço dentro de uma solução de fluxo de trabalho. A seguinte conversão da Web mostra como adicionar uma referência de serviço em outros tipos de projetos: [chamar um serviço WCF de um fluxo de trabalho em um projeto Web](/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow).

Adicionar duas ou mais referências de serviço a serviços que contêm o mesmo nome de operação causará um problema. As atividades geradas chamarão apenas a primeira operação de serviço. Para contornar esse problema, renomeie as operações de serviço para que elas sejam diferentes ou altere o nome de configuração do ponto de extremidade dentro de cada atividade gerada.

## <a name="see-also"></a>Confira também

- [Serviços de fluxo de trabalho](workflow-services.md)
- [Chamando um serviço WCF de um fluxo de trabalho em um projeto Web](/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
