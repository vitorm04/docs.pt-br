---
title: Adicionando uma referência de serviço em uma solução de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: 8f1fa4604f1a1873c7063ec3c9dccf08bd0aa0ee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669661"
---
# <a name="adding-a-service-reference-in-a-workflow-solution"></a>Adicionando uma referência de serviço em uma solução de fluxo de trabalho

Adicionando uma referência de serviço em um aplicativo de fluxo de trabalho funciona um pouco diferente que um aplicativo WCF regular. Quando você seleciona **Add > Referência de serviço** e especifique a URL para o serviço, os metadados é baixado e atividades personalizados são geradas que permitem que você chame o serviço WCF ou serviço de fluxo de trabalho WCF adicionou uma referência ao. Depois de adicionar uma referência de serviço, recompile a solução para que as atividades geradas são criadas. Em seguida, eles serão exibidos na caixa de ferramentas de designer de fluxo de trabalho. No entanto, observe que isso só funcionará se você estiver adicionando uma referência de serviço dentro de uma solução de fluxo de trabalho. A conversão de web a seguir mostra como adicionar uma referência de serviço em outros tipos de projetos: [Chamando um serviço WCF de um fluxo de trabalho em um projeto Web](https://go.microsoft.com/fwlink/?LinkId=207725).

Adição de dois ou mais referências de serviço para serviços que contêm o mesmo nome de operação fará com que um problema. As atividades geradas chamará somente a primeira operação de serviço. Para contornar esse problema renomear as operações de serviço para que eles são diferentes ou alterar o nome da configuração de ponto de extremidade dentro de cada atividade gerada.

## <a name="see-also"></a>Consulte também

- [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Chamando um serviço WCF de um fluxo de trabalho em um projeto Web](https://go.microsoft.com/fwlink/?LinkId=207725)
