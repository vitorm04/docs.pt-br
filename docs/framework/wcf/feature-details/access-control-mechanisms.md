---
title: Mecanismos de controle de acesso
ms.date: 03/30/2017
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
ms.openlocfilehash: b423dac4d8324069eb1825666419b23b5afdca63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185501"
---
# <a name="access-control-mechanisms"></a>Mecanismos de controle de acesso
Você pode controlar o acesso de várias formas com o Windows Communication Foundation (WCF). Este tópico discute brevemente os diversos mecanismos e fornece sugestões sobre quando usar cada um; destina-se a ajudá-lo a selecionar o mecanismo correto a ser usado. As tecnologias de acesso são listadas por ordem de complexidade. O mais simples <xref:System.Security.Permissions.PrincipalPermissionAttribute>é o; o mais complexo é o Modelo de Identidade.  
  
 Além desses mecanismos, a personificação e delegação com o WCF é explicada em [Delegação e Personificação](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 O <xref:System.Security.Permissions.PrincipalPermissionAttribute> é usado para restringir o acesso a um método de serviço. Quando o atributo é aplicado a um método, ele pode ser usado para exigir a identidade ou a adesão de um chamador específico em um grupo windows ou ASP.NET função. Se o cliente for autenticado usando um certificado X.509, ele recebe uma identidade primária que consiste no nome do assunto mais a impressão digital do certificado.  
  
 Use <xref:System.Security.Permissions.PrincipalPermissionAttribute> o para controlar o acesso aos recursos no computador em que o serviço está sendo executado, e se os usuários do serviço sempre farão parte do mesmo domínio do Windows que o serviço está sendo executado. Você pode facilmente criar grupos do Windows que tenham especificado níveis de acesso (como nenhum, somente leitura ou leitura e gravação).  
  
 Para obter mais informações sobre o uso do atributo, consulte [Como restringir o acesso com a Classe PrincipalPermissionAttribute .](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md) Para obter mais informações sobre identidade, consulte [Identidade de Serviço e Autenticação](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="aspnet-membership-provider"></a>provedor de adesão ASP.NET  
 Uma característica do ASP.NET é o provedor de adesão. Embora o provedor de associação não seja tecnicamente um mecanismo de controle de acesso, ele permite controlar o acesso ao serviço limitando o conjunto de possíveis identidades que podem acessar o ponto final do serviço. O recurso de associação inclui um banco de dados que pode ser preenchido com combinações de nome de usuário/senha que permitem aos usuários de um site estabelecer contas com o site. Para acessar um serviço que usa o provedor de membros, o usuário deve fazer logon com seu nome de usuário e senha.  
  
> [!NOTE]
> Você deve primeiro preencher o banco de dados usando o recurso ASP.NET antes que um serviço WCF possa usá-lo para fins de autorização.  
  
 Você também pode usar o recurso de associação se você já tiver um banco de dados de membros de um site ASP.NET existente e quiser habilitar os mesmos usuários a usar seu serviço, autorizado com os mesmos nomes de usuário e senhas.  
  
 Para obter mais informações sobre como usar o recurso de adesão em um serviço WCF, consulte [Como: Usar o provedor de membros ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
## <a name="aspnet-role-provider"></a>ASP.NET provedor de papéis  
 Outra característica do ASP.NET é a capacidade de gerenciar a autorização usando funções. O provedor de funções ASP.NET permite que um desenvolvedor crie funções para os usuários e designe cada usuário para uma função ou função. Assim como o provedor de membros, as funções e atribuições são armazenadas em um banco de dados e podem ser preenchidas usando ferramentas fornecidas por uma determinada implementação do provedor de função ASP.NET. Assim como no recurso de associação, os desenvolvedores do WCF podem usar as informações no banco de dados para autorizar os usuários do serviço por funções. Eles podem, por exemplo, usar o `PrincipalPermissionAttribute` provedor de função em combinação com o mecanismo de controle de acesso descrito acima.  
  
 Você também pode usar o provedor de ASP.NET função se você tiver um banco de dados de provedor de ASP.NET de função existente e quiser usar o mesmo conjunto de regras e atribuições do usuário em seu serviço WCF.  
  
 Para obter mais informações sobre como usar o recurso do provedor de função, consulte [Como: Usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
## <a name="authorization-manager"></a>Gerenciador de Autorização  
 Outro recurso combina o Gerente de Autorização (AzMan) com o provedor de ASP.NET função para autorizar clientes. Quando ASP.NET hospeda um serviço Web, o AzMan pode ser integrado ao aplicativo para que a autorização para o serviço seja feita através do AzMan. ASP.NET gerenciador de funções fornece uma API que permite gerenciar funções de aplicativos, adicionar e remover usuários de funções e verificar a adesão às funções, mas não permite que você consulte se um usuário está autorizado a executar uma tarefa ou operação nomeada. O AzMan permite definir operações individuais e combiná-las em tarefas. Com o AZMan, além de verificações de função, você também pode verificar se um usuário pode executar uma tarefa. A atribuição de função e a autorização de tarefa podem ser configuradas fora do aplicativo ou executadas de forma programática dentro do aplicativo. O snap-in microsoft management console (MMC) da administração AzMan permite que os administradores alterem as tarefas que uma função pode executar em tempo de execução e gerenciem a adesão de cada usuário às funções.  
  
 Você também pode usar o AzMan e o provedor de função ASP.NET se você já tiver acesso a uma instalação AzMan existente e quiser autorizar seus usuários de serviço usando os recursos da combinação AzMan/provedor de função.  
  
 Para obter mais informações sobre a AzMan e o provedor de ASP.NET função, consulte [Como: Usar o Gerenciador de Autorização (AzMan) com ASP.NET 2.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)). Para obter mais informações sobre como usar o AzMan e o provedor de função para serviços WCF, consulte [Como: Usar o ASP.NET Provedor de Função Gerenciador de Autorização com um Serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md).  
  
## <a name="identity-model"></a>Modelo de Identidade  
 O Modelo de Identidade é um conjunto de APIs que permitem gerenciar sinistros e políticas para autorizar clientes. Com o Modelo de Identidade, você pode examinar todas as reivindicações contidas nas credenciais que o chamador usou para autenticar-se ao serviço, comparar as reivindicações com o conjunto de políticas para o serviço e conceder ou negar acesso com base na comparação.  
  
 Use o Modelo de Identidade se precisar de um controle fino e a capacidade de definir critérios específicos antes de conceder acesso. Por exemplo, ao <xref:System.Security.Permissions.PrincipalPermissionAttribute>usar o , o critério é simplesmente que a identidade do usuário é autenticada e pertence a uma função específica. Em contraste, usando o Modelo de Identidade, você pode criar uma política que afirma que o usuário deve ter mais de 18 anos de idade e possui uma carteira de motorista válida antes de ser autorizado a visualizar um documento.  
  
 Um exemplo em que você pode se beneficiar do controle de acesso baseado em sinistro susceptino de modelo de identidade é usar credenciais da federação no cenário de token emitido. Para obter mais informações sobre a federação e os tokens emitidos, consulte [Federação e Tokens Emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Para obter mais informações sobre o Modelo de Identidade, consulte [Gerenciar sinistros e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [Como restringir o acesso com a classe PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [Como utilizar o provedor de função do ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Como usar o provedor de função do gerenciador de autorização do ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)
- [Gerenciamento de declarações e autorizações com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Delegação e representação](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
