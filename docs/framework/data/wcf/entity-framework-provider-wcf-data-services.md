---
title: Provedor de Entity Framework (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
ms.openlocfilehash: 0b6e76e6c05a091c57f27fc759044d3567cd976a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365022"
---
# <a name="entity-framework-provider-wcf-data-services"></a>Provedor de Entity Framework (WCF Data Services)
Como o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], o ADO.NET Entity Framework é baseado no Modelo de Dados de Entidade, que é um tipo de modelo de relação entre entidades. O Entity Framework converte operações em relação a sua implementação do modelo de dados de entidade, que é chamado de *modelo conceitual*, em operações equivalentes em relação a uma fonte de dados. Isso torna a Entity Framework um provedor ideal para os serviços de dados que são baseados em dados relacionais, e qualquer banco de dados que tem um provedor de dados que dá suporte a Entity Framework pode ser usado com o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Para obter uma lista das fontes de dados que oferecem suporte ao Entity Framework, consulte [provedores de terceiros para o Entity Framework](http://go.microsoft.com/fwlink/?LinkId=143699).  
  
 Em um modelo conceitual, o recipiente de entidade é a raiz do serviço. Você deve definir um modelo conceitual no Entity Framework antes de os dados serem expostos por um serviço de dados. Para obter mais informações, consulte [como: criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] oferece suporte ao modelo de simultaneidade otimista, permitindo que você defina um token de simultaneidade para uma entidade. Este token de simultaneidade, que inclui uma ou mais propriedades da entidade, é usado pelo serviço de dados para determinar se uma alteração ocorreu nos dados que estão sendo solicitados, atualizados ou excluídos. Quando os valores do token obtidos da eTag na solicitação diferem dos valores atuais da entidade, uma exceção é gerada pelo serviço de dados. Para indicar que uma propriedade faz parte do token de simultaneidade, você deverá aplicar o atributo `ConcurrencyMode="Fixed"` no modelo de dados definido pelo provedor do [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]. O token de simultaneidade não pode incluir uma propriedade de chave ou uma propriedade de navegação. Para obter mais informações, consulte [atualizar o serviço de dados](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 Para saber mais sobre o Entity Framework, consulte [visão geral do Entity Framework](../../../../docs/framework/data/adonet/ef/overview.md).  
  
## <a name="see-also"></a>Consulte também  
 [Provedores de Serviços de Dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Provedor de reflexão](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)  
 [Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model.md)
