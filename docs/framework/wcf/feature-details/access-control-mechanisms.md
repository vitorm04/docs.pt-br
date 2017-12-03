---
title: Mecanismos de controle de acesso
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5cb3afec00fea5432329bd30fc993ac0cafd8b10
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="access-control-mechanisms"></a>Mecanismos de controle de acesso
Você pode controlar o acesso de forma várias com [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Este tópico discute os vários mecanismos rapidamente e fornece sugestões sobre quando usar cada uma delas; destina-se a ajudá-lo a selecionar o mecanismo correto a ser usado. As tecnologias de acesso são listadas em ordem de complexidade. É mais simples de <xref:System.Security.Permissions.PrincipalPermissionAttribute>; as mais complexas são o modelo de identidade.  
  
 Além desses mecanismos, representação e delegação com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é explicado em [delegação e representação](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 O <xref:System.Security.Permissions.PrincipalPermissionAttribute> é usado para restringir o acesso a um método de serviço. Quando o atributo é aplicado a um método, ele pode ser usado para solicitar a identidade de um chamador específico ou associação em um grupo do Windows ou [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] função. Se o cliente é autenticado usando um certificado x. 509, ele recebe uma identidade primária consiste do nome da entidade e a impressão digital do certificado.  
  
 Use o <xref:System.Security.Permissions.PrincipalPermissionAttribute> para controlar o acesso aos recursos no computador em que o serviço está em execução, e se os usuários do serviço sempre fará parte do mesmo domínio do Windows que o serviço está em execução. Você pode facilmente criar grupos do Windows que especificou níveis de acesso (como none, somente leitura ou leitura e gravação).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]usando o atributo, consulte [como: restringir o acesso com a PrincipalPermissionAttribute Class](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]identidade, consulte [autenticação e identidade de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="aspnet-membership-provider"></a>Provedor de associação ASP.NET  
 Um recurso do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] é o provedor de associação. Mesmo que o provedor de associação não seja tecnicamente um mecanismo de controle de acesso, ele permite controlar o acesso ao serviço, limitando o conjunto de identidades possíveis que podem acessar o ponto de extremidade do serviço. O recurso de associação inclui um banco de dados que pode ser preenchido com combinações de nome e senha do usuário que permitem aos usuários de um site da Web estabelecer contas com o site. Para acessar um serviço que usa o provedor de associação, um usuário faça logon com seu nome de usuário e senha.  
  
> [!NOTE]
>  Você primeiro deve preencher o banco de dados usando o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] recurso antes de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço pode usá-lo para fins de autorização.  
  
 Você também pode usar o recurso de associação, se você já tiver um banco de dados de associação de uma já existente [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] site da Web e você deseja habilitar os mesmos usuários usar o serviço autorizado com os mesmos nomes de usuário e senhas.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]usando o recurso de associação em um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de serviço, consulte [como: usar o provedor de associação ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
## <a name="aspnet-role-provider"></a>Provedor de função do ASP.NET  
 Outro recurso do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] é a capacidade de gerenciar o uso de funções de autorização. O [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função permite que um desenvolvedor para criar funções para usuários e atribua a cada usuário a uma função ou funções. Como com o provedor de associação, as funções e atribuições são armazenadas em um banco de dados e pode ser preenchidas usando as ferramentas fornecidas por uma implementação específica do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função. Assim como acontece com o recurso de associação, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] os desenvolvedores podem usar as informações no banco de dados para autorizar usuários do serviço de funções. Por exemplo, eles podem usar o provedor de função em combinação com o `PrincipalPermissionAttribute` descrito acima do mecanismo de controle de acesso.  
  
 Você também pode usar o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função, se você tiver uma [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] banco de dados de provedor de função e desejar usar o mesmo conjunto de regras e as atribuições de usuário no seu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]usando o recurso de provedor de função, consulte [como: usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
## <a name="authorization-manager"></a>Gerenciador de autorização  
 Outro recurso combina o Gerenciador de autorização (AzMan) com o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função para autorizar clientes. Quando [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hospeda um serviço Web, AzMan pode ser integrado no aplicativo para que a autorização para o serviço é feita por meio do AzMan. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Gerenciador de função fornece uma API que permite gerenciar funções de aplicativo, adicionar e remover usuários das funções e verificar a associação de função, mas não permite consultar se um usuário está autorizado a executar uma tarefa nomeada ou a operação. AzMan permite definir as operações individuais e combiná-los em tarefas. Com o AZMan, além de verificações de função, você também pode verificar se um usuário pode executar uma tarefa. Autorização de atribuição e tarefa de função pode ser configurada fora do aplicativo ou por meio de programação executada dentro do aplicativo. A administração de AzMan snap-in do Console de gerenciamento Microsoft (MMC) permite que os administradores para alterar as tarefas que pode executar uma função em tempo de execução e para gerenciar a associação de cada usuário de funções.  
  
 Você também pode usar o AzMan e [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função, se você já tiver acesso a uma instalação existente do AzMan e deseja autorizar seus usuários de serviço usando os recursos da combinação de provedor AzMan/função.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]AzMan e [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função, consulte [como: Use o Gerenciador de autorização (AzMan) com o ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=88951). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]usando o provedor de função para e de AzMan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços, consulte [como: usar o provedor de função do Gerenciador de autorização ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md).  
  
## <a name="identity-model"></a>Modelo de identidade  
 O modelo de identidade é um conjunto de APIs que permitem gerenciar políticas e declarações para autorizar clientes. Com o modelo de identidade, você pode examinar cada declaração contida nas credenciais que o chamador usado para autenticar para o serviço, compare as declarações para o conjunto de políticas para o serviço e conceder ou negar acesso com base na comparação.  
  
 Use o modelo de identidade se você precisa excelente controle e a capacidade de definir os critérios específicos antes de conceder acesso. Por exemplo, ao usar o <xref:System.Security.Permissions.PrincipalPermissionAttribute>, o critério é que a identidade do usuário é autenticada e pertence a uma função específica. Por outro lado, usando o modelo de identidade, você pode criar uma diretiva que informa o usuário deve ser mais de 18 anos de idade e possui de motorista uma válido carteira antes de terem permissão para exibir um documento.  
  
 Um exemplo onde você pode aproveitar o controle de acesso baseado em declaração de modelo de identidade é ao usar credenciais de federação no cenário do token emitido. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Federação e tokens emitidos, consulte [federação e Tokens emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]o modelo de identidade, consulte [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md) (Como restringir o acesso com a classe PrincipalPermissionAttribute)  
 [Como: usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [Como: usar o provedor de função do Gerenciador de autorização ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Delegação e representação](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
