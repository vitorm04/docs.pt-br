---
title: Provedor de Entity Framework (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
ms.openlocfilehash: 5a40eeafafef56902a9ae5037e6bc946b598f752
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854088"
---
# <a name="entity-framework-provider-wcf-data-services"></a>Provedor de Entity Framework (WCF Data Services)
Como o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], o ADO.NET Entity Framework é baseado no Modelo de Dados de Entidade, que é um tipo de modelo de relação entre entidades. O Entity Framework traduz as operações em relação a sua implementação do Modelo de Dados de Entidade, que é chamado de *modelo conceitual*, em operações equivalentes em relação a uma fonte de dados. Isso torna a Entity Framework um provedor ideal para os serviços de dados que são baseados em dados relacionais, e qualquer banco de dados que tem um provedor de dados que dá suporte a Entity Framework pode ser usado com o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Para obter uma lista das fontes de dados que atualmente dão suporte à Entity Framework, consulte [provedores de terceiros para o Entity Framework](https://go.microsoft.com/fwlink/?LinkId=143699).  
  
 Em um modelo conceitual, o recipiente de entidade é a raiz do serviço. Você deve definir um modelo conceitual no Entity Framework antes de os dados serem expostos por um serviço de dados. Para obter mais informações, confira [Como: Crie um serviço de dados usando uma fonte](create-a-data-service-using-an-adonet-ef-data-wcf.md)de dados ADO.NET Entity Framework.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]dá suporte ao modelo de simultaneidade otimista, permitindo que você defina um token de simultaneidade para uma entidade. Este token de simultaneidade, que inclui uma ou mais propriedades da entidade, é usado pelo serviço de dados para determinar se uma alteração ocorreu nos dados que estão sendo solicitados, atualizados ou excluídos. Quando os valores do token obtidos da eTag na solicitação diferem dos valores atuais da entidade, uma exceção é gerada pelo serviço de dados. Para indicar que uma propriedade faz parte do token de simultaneidade, você deve aplicar o `ConcurrencyMode="Fixed"` atributo no modelo de dados definido pelo provedor de Entity Framework. O token de simultaneidade não pode incluir uma propriedade de chave ou uma propriedade de navegação. Para obter mais informações, consulte [atualizando o serviço de dados](updating-the-data-service-wcf-data-services.md).  
  
 Para saber mais sobre o Entity Framework, consulte [Entity Framework visão geral](../adonet/ef/overview.md).  
  
## <a name="see-also"></a>Consulte também

- [Provedores de Serviços de Dados](data-services-providers-wcf-data-services.md)
- [Provedor de reflexão](reflection-provider-wcf-data-services.md)
- [Modelo de Dados de Entidade](../adonet/entity-data-model.md)
