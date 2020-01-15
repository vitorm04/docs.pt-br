---
title: Adicionando uma referência de serviço em uma solução de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: 7197ae991207efd60ea398794c7c23f427f6b0cc
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964211"
---
# <a name="adding-a-service-reference-in-a-workflow-solution"></a>Adicionando uma referência de serviço em uma solução de fluxo de trabalho

Adicionar uma referência de serviço em um aplicativo de fluxo de trabalho funciona um pouco diferente do que um aplicativo WCF regular. Quando você seleciona **adicionar > referência de serviço** e especifica a URL para o serviço, os metadados são baixados e as atividades personalizadas são geradas que permitem chamar o serviço WCF ou o serviço de fluxo de trabalho WCF que você adicionou uma referência a. Depois de adicionar uma referência de serviço, recompile a solução para que as atividades geradas sejam criadas. Eles serão exibidos na caixa de ferramentas do designer de fluxo de trabalho. No entanto, observe que isso só funcionará se você estiver adicionando uma referência de serviço dentro de uma solução de fluxo de trabalho. A seguinte conversão da Web mostra como adicionar uma referência de serviço em outros tipos de projetos: [chamar um serviço WCF de um fluxo de trabalho em um projeto Web](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow).

Adicionar duas ou mais referências de serviço a serviços que contêm o mesmo nome de operação causará um problema. As atividades geradas chamarão apenas a primeira operação de serviço. Para contornar esse problema, renomeie as operações de serviço para que elas sejam diferentes ou altere o nome de configuração do ponto de extremidade dentro de cada atividade gerada.

## <a name="see-also"></a>Veja também

- [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Chamando um serviço WCF de um fluxo de trabalho em um projeto Web](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
