---
title: Mecanismos de controle de acesso
ms.date: 03/30/2017
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
ms.openlocfilehash: 53b20e7f11f5accd1436f29063817142681e4f74
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213253"
---
# <a name="access-control-mechanisms"></a>Mecanismos de controle de acesso
Você pode controlar o acesso de vários forma com o Windows Communication Foundation (WCF). Este tópico discute os vários mecanismos rapidamente e fornece sugestões sobre quando usar cada um; Ele destina-se para ajudá-lo a selecionar o mecanismo correto a ser usado. As tecnologias de acesso são listadas em ordem de complexidade. A mais simples é o <xref:System.Security.Permissions.PrincipalPermissionAttribute>; o mais complexo é o modelo de identidade.  
  
 Além desses mecanismos, representação e delegação com o WCF é explicado em [delegação e representação](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 O <xref:System.Security.Permissions.PrincipalPermissionAttribute> é usado para restringir o acesso a um método de serviço. Quando o atributo é aplicado a um método, ele pode ser usado para solicitar um chamador específico identidade ou participação em um grupo do Windows ou [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] função. Se o cliente é autenticado usando um certificado X.509, ele recebe uma identidade primária que consiste o nome da entidade e a impressão digital do certificado.  
  
 Use o <xref:System.Security.Permissions.PrincipalPermissionAttribute> para controlar o acesso aos recursos no computador que o serviço está em execução, e se os usuários do serviço sempre fará parte do mesmo domínio do Windows que o serviço está sendo executado. Você pode facilmente criar grupos do Windows que especificou os níveis de acesso (como none, somente leitura ou leitura e gravação).  
  
 Para obter mais informações sobre como usar o atributo, consulte [como: Restringir o acesso com a classe PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md). Para obter mais informações sobre identidade, consulte [identidade de serviço e autenticação](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="aspnet-membership-provider"></a>Provedor de associação do ASP.NET  
 Um recurso do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] é o provedor de associação. Mesmo que o provedor de associação não seja tecnicamente um mecanismo de controle de acesso, ele permite controlar o acesso ao serviço, limitando o conjunto de identidades possíveis que podem acessar o ponto de extremidade do serviço. O recurso de associação inclui um banco de dados que pode ser populado com combinações de nome/senha de usuário que permitem aos usuários de um site da Web estabelecer contas com o site. Para acessar um serviço que usa o provedor de associação, um usuário faça logon com seu nome de usuário e senha.  
  
> [!NOTE]
>  Você primeiro deve preencher o banco de dados usando o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] para um serviço WCF possa ser usado para fins de autorização de recursos.  
  
 Você também pode usar o recurso de associação, se você já tiver um banco de dados de associação de uma já existente [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] site da Web e você deseja habilitar os mesmos que os usuários usem seu serviço, autorizado com o mesmo nomes de usuário e senhas.  
  
 Para obter mais informações sobre como usar o recurso de associação em um serviço WCF, consulte [como: Usar o provedor de associação ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
## <a name="aspnet-role-provider"></a>Provedor de função ASP.NET  
 Outro recurso do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] é a capacidade de gerenciar a autorização usando funções. O [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função permite que um desenvolvedor para criar funções para usuários e atribuir a cada usuário a uma função ou funções. Como com o provedor de associação, as funções e atribuições são armazenadas em um banco de dados e pode ser preenchidas usando as ferramentas fornecidas por uma implementação específica a [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função. Como com o recurso de associação, os desenvolvedores do WCF podem usar as informações no banco de dados para autorizar os usuários do serviço pelas funções. Eles podem, por exemplo, usar o provedor de função em combinação com o `PrincipalPermissionAttribute` descrito acima de mecanismo de controle de acesso.  
  
 Você também pode usar o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função, se você tiver uma [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] banco de dados de provedor de função e desejar usar o mesmo conjunto de regras e as atribuições de usuário em seu serviço WCF.  
  
 Para obter mais informações sobre como usar o recurso de provedor de função, consulte [como: Usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
## <a name="authorization-manager"></a>Gerenciador de autorização  
 Outro recurso combina o Gerenciador de autorização (AzMan) com o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função para autorizar os clientes. Quando [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hospeda um serviço Web, AzMan pode ser integrado ao aplicativo para que a autorização para o serviço é feita por meio de AzMan. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Gerenciador de funções fornece uma API que permite que você gerencie as funções de aplicativo, adicionar e remover usuários das funções e verificar a associação de função, mas não permite a consulta se um usuário está autorizado a executar uma tarefa nomeada ou a operação. AzMan permite que você defina operações individuais e combiná-los em tarefas. Com o AZMan, além das verificações de função, você também pode verificar se um usuário pode executar uma tarefa. Autorização de tarefa e atribuição de função pode ser configurada fora do aplicativo ou podem ser executada de forma programática dentro do aplicativo. A administração de AzMan snap-in do Console de gerenciamento Microsoft (MMC) permite aos administradores alterar as tarefas de que uma função pode executar no tempo de execução e para gerenciar a associação de cada usuário de funções.  
  
 Você também pode usar o AzMan e o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função, se você já tiver acesso a uma instalação existente do AzMan e deseja autorizar seus usuários de serviço usando os recursos da combinação de provedor de função/AzMan.  
  
 Para obter mais informações sobre o AzMan e o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função, consulte [How To: Usar Gerenciador de autorização (AzMan) com o ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=88951). Para obter mais informações sobre como usar o provedor de função e AzMan para os serviços WCF, consulte [como: Usar o provedor de função do Gerenciador de autorização do ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md).  
  
## <a name="identity-model"></a>Modelo de identidade  
 O modelo de identidade é um conjunto de APIs que permitem que você gerencie as declarações e políticas para autorizar os clientes. Com o modelo de identidade, você pode examinar cada declaração contida em credenciais que o chamador usado para autenticar-se com o serviço, compare as declarações para o conjunto de políticas para o serviço e conceder ou negar acesso com base na comparação.  
  
 Se você precisa de um refinado controle e a capacidade de definir os critérios específicos antes de conceder acesso, use o modelo de identidade. Por exemplo, ao usar o <xref:System.Security.Permissions.PrincipalPermissionAttribute>, o critério é simplesmente que a identidade do usuário é autenticada e que pertence a uma função específica. Em contraste, usando o modelo de identidade, você pode criar uma política que declara o usuário deve ser mais de 18 anos de idade e possui de motorista uma válido carteira antes de terem permissão para exibir um documento.  
  
 Um exemplo em que você pode aproveitar o controle de acesso baseado em declaração de modelo de identidade é ao usar as credenciais de federação no cenário de token emitido. Para obter mais informações sobre a federação e tokens emitidos, consulte [federação e Tokens emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Para obter mais informações sobre o modelo de identidade, consulte [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [Como: Restringir o acesso com a PrincipalPermissionAttribute Class](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [Como: Usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Como: Usar o provedor de função do Gerenciador de autorização do ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)
- [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Delegação e representação](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
