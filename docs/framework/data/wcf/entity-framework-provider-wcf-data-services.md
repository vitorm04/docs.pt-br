---
title: Provedor de Entity Framework (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
ms.openlocfilehash: 0b75e9645f05e5e83ff76cc138ee37e90600769a
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569261"
---
# <a name="entity-framework-provider-wcf-data-services"></a>Provedor de Entity Framework (WCF Data Services)
Assim como WCF Data Services, o Entity Framework ADO.NET é baseado no Modelo de Dados de Entidade, que é um tipo de modelo de relacionamento de entidade. O Entity Framework traduz as operações em relação a sua implementação do Modelo de Dados de Entidade, que é chamado de *modelo conceitual*, em operações equivalentes em relação a uma fonte de dados. Isso torna o Entity Framework um provedor ideal para serviços de dados que se baseiam em dados relacionais e qualquer banco de dados que tenha um provedor que ofereça suporte a Entity Framework pode ser usado com WCF Data Services. Para obter uma lista das fontes de dados que atualmente dão suporte à Entity Framework, consulte [provedores de terceiros para o Entity Framework](https://go.microsoft.com/fwlink/?LinkId=143699).  
  
 Em um modelo conceitual, o recipiente de entidade é a raiz do serviço. Você deve definir um modelo conceitual no Entity Framework antes de os dados serem expostos por um serviço de dados. Para obter mais informações, consulte [como criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework](create-a-data-service-using-an-adonet-ef-data-wcf.md).  
  
 O WCF Data Services dá suporte ao modelo de simultaneidade otimista, permitindo que você defina um token de simultaneidade para uma entidade. Este token de simultaneidade, que inclui uma ou mais propriedades da entidade, é usado pelo serviço de dados para determinar se uma alteração ocorreu nos dados que estão sendo solicitados, atualizados ou excluídos. Quando os valores do token obtidos da eTag na solicitação diferem dos valores atuais da entidade, uma exceção é gerada pelo serviço de dados. Para indicar que uma propriedade faz parte do token de simultaneidade, você deve aplicar o atributo `ConcurrencyMode="Fixed"` no modelo de dados definido pelo provedor de Entity Framework. O token de simultaneidade não pode incluir uma propriedade de chave ou uma propriedade de navegação. Para obter mais informações, consulte [atualizando o serviço de dados](updating-the-data-service-wcf-data-services.md).  
  
 Para saber mais sobre o Entity Framework, consulte [Entity Framework visão geral](../adonet/ef/overview.md).  
  
## <a name="see-also"></a>Consulte também

- [Provedores de Serviços de Dados](data-services-providers-wcf-data-services.md)
- [Provedor de reflexão](reflection-provider-wcf-data-services.md)
- [Modelo de Dados de Entidade](../adonet/entity-data-model.md)
