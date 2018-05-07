---
title: Protegendo o WCF Data Services
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- securing application [WCF Data Services]
- WCF Data Services, security
ms.assetid: 99fc2baa-a040-4549-bc4d-f683d60298af
ms.openlocfilehash: 468353d0cd4cc36507fe5f10a702450d2b516ed8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="securing-wcf-data-services"></a>Protegendo o WCF Data Services
Este tópico descreve as considerações de segurança que são específicas para desenvolver, implantar e executar o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] e os aplicativos que acessam serviços que oferecem suporte ao [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. Você também deve seguir as recomendações para criar aplicativos seguros do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
 Ao planejar como proteger um serviço [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] baseado em [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], você deve considerar a autenticação, o processo de descobrir e verificar a identidade de uma entidade de segurança, e a autorização, o processo de determinar se uma entidade de segurança autenticada está autorizada a acessar os recursos solicitados. Você também deve considerar a criptografia da mensagem usando o protocolo SSL.  
  
## <a name="authenticating-client-requests"></a>Autenticando solicitações de clientes  
 O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] não implementa nenhum tipo de autenticação própria, mas, em vez disso, depende das previsões de autenticação do host do serviço de dados. Isso significa que o serviço presume que qualquer solicitação recebida já foi autenticada pelo host da rede e que o host identificou corretamente o princípio da solicitação por meio das interfaces fornecidas pelo [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Essas opções de autenticação e as abordagens são detalhadas no [série OData e autenticação](http://go.microsoft.com/fwlink/?LinkId=200381).  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>Opções de autenticação para o Serviço de Dados WCF  
 A tabela a seguir lista alguns dos mecanismos de autenticação que estão disponíveis para ajudá-lo a autenticar solicitações a um Serviço de Dados WCF.  
  
|Opções de autenticação|Descrição|  
|----------------------------|-----------------|  
|Autenticação anônima|Quando a autenticação anônima HTTP está habilitada, qualquer princípio pode se conectar ao serviço de dados. Não são necessárias credenciais para o acesso anônimo. Use esta opção somente quando quiser permitir que qualquer pessoa acesse o serviço de dados.|  
|Autenticações básica e digest|As credenciais que consistem em nome de usuário e senha são necessárias para autenticação. Oferecem suporte à autenticação de clientes não Windows. **Observação de segurança:** credenciais de autenticação básica (nome de usuário e senha) são enviadas sem e podem ser interceptadas. A autenticação digest envia um hash baseado nas credenciais fornecidas, o que a torna mais segura do que a autenticação básica. Ambas são suscetíveis a ataques do tipo "man-in-the-middle". Ao usar esses métodos de autenticação, você deve considerar a criptografia da comunicação entre o cliente e o serviço de dados usando o protocolo SSL. <br /><br /> Os Serviços de Informações da Internet da Microsoft (IIS) fornecem uma implementação de autenticações básica e digest para solicitações HTTP em um aplicativo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Essa implementação do provedor de Autenticação do Windows permite que um aplicativo cliente do .NET Framework forneça credenciais do cabeçalho HTTP da solicitação ao serviço de dados para negociar perfeitamente a autenticação de um usuário do Windows. Para obter mais informações, consulte [referência técnica da autenticação Digest](http://go.microsoft.com/fwlink/?LinkId=200408).<br /><br /> Quando você quiser que seu serviço de dados use a autenticação básica com base em algum serviço de autenticação personalizada e não em credenciais do Windows, deverá implementar um módulo HTTP [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] personalizado para autenticação.<br /><br /> Para obter um exemplo de como usar um esquema de autenticação básica com [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], consulte a postagem no [autenticação básica](http://go.microsoft.com/fwlink/?LinkID=200388) no [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] e a série de autenticação.|  
|Autenticação do Windows|As credenciais baseadas no Windows são trocadas por meio de NTLM ou Kerberos. Esse mecanismo é mais seguro do que a autenticação básica ou digest, mas requer que o cliente seja um aplicativo baseado no Windows. O IIS também fornece uma implementação da autenticação do Windows para solicitações HTTP em um aplicativo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Para obter mais informações, consulte [visão geral de autenticação de formulários do ASP.NET](http://msdn.microsoft.com/library/099c1587-6934-476e-ac95-28f534bc9708).<br /><br /> Para obter um exemplo de como usar a autenticação do Windows com [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], consulte a postagem no [autenticação do Windows](http://go.microsoft.com/fwlink/?LinkID=200384) no [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] e a série de autenticação.|  
|Autenticação de formulários [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]|A autenticação de formulários permite que você autentique usuários usando seu próprio código e, em seguida, mantenha um token de autenticação em um cookie ou na URL da página. Você autentica o nome de usuário e a senha de seus usuários usando um formulário de logon que você cria. As solicitações não autenticadas são redirecionadas para uma página de logon, onde o usuário fornece credenciais e envia o formulário. Se o aplicativo autenticar a solicitação, o sistema emitirá um tíquete contendo uma chave para restabelecer a identidade para solicitações subsequentes. Para obter mais informações, consulte [provedor de autenticação de formulários](http://msdn.microsoft.com/library/77e21ba2-bad1-4967-a8ec-74942dea7e47). **Observação de segurança:** por padrão, o cookie que contém o tíquete de autenticação de formulários não está protegido quando você usar a autenticação de formulários em um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo Web. Você deve considerar exigir que o SSL proteja o tíquete de autenticação e as credenciais do logon inicial. <br /><br /> Para um exemplo de como usar a autenticação com de formulários [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], consulte a postagem no [autenticação de formulários](http://go.microsoft.com/fwlink/?LinkID=200389) no [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] e a série de autenticação.|  
|Autenticação baseada em declarações|Na autenticação baseada em declarações, o serviço de dados depende de um serviço de provedor de identidade "de terceiros" confiável para autenticar o usuário. O provedor de identidade positivamente autentica o usuário que está solicitando acesso a recursos do serviço de acesso e emite um token que concede acesso aos recursos solicitados. Esse token é então apresentado ao serviço de dados, que concede acesso ao usuário com base na relação de confiança com o serviço de identidade que emitiu o token de acesso.<br /><br /> A vantagem de usar um provedor de autenticação baseado em declarações é que ele pode ser usado para autenticar vários tipos de clientes em domínios de confiança. Empregando tal provedor de terceiros, um serviço de dados pode descarregar os requisitos de manutenção e autenticação de usuários. OAuth 2.0 é um protocolo de autenticação baseado em declarações que tem o suporte do Microsoft Azure AppFabric Access Control para autorização federada como um serviço. Esse protocolo oferece suporte a serviços baseados em REST. Para obter um exemplo de como usar o OAuth 2.0 com [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], consulte a postagem no [OData and OAuth](http://go.microsoft.com/fwlink/?LinkId=200514) no [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] e a série de autenticação.|  
  
<a name="clientAuthentication"></a>   
### <a name="authentication-in-the-client-library"></a>Autenticação na biblioteca de cliente  
 Por padrão, a biblioteca de cliente do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] não fornece credenciais ao fazer uma solicitação a um serviço [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Quando as credenciais de logon são exigidas pelo serviço de dados para autenticar um usuário, essas credenciais podem ser fornecidas em um <xref:System.Net.NetworkCredential> acessado da propriedade <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> do <xref:System.Data.Services.Client.DataServiceContext>, como no exemplo a seguir:  
  
```csharp  
// Set the client authentication credentials.  
context.Credentials =  
    new NetworkCredential(userName, password, domain);  
```  
  
```vb  
' Set the client authentication credentials.  
context.Credentials = _  
    New NetworkCredential(userName, password, domain)  
```  
  
 Para obter mais informações, consulte [como: especificar as credenciais do cliente para uma solicitação de serviço de dados](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md).  
  
 Quando o serviço de dados exige credenciais de logon que não podem ser especificadas com um objeto <xref:System.Net.NetworkCredential>, como um cookie ou um token baseado em declarações, você deve definir manualmente os cabeçalhos na solicitação HTTP, geralmente os cabeçalhos `Authorization` e `Cookie`. Para obter mais informações sobre esse tipo de cenário de autenticação, consulte a postagem [OData e autenticação: cliente conecta](http://go.microsoft.com/fwlink/?LinkID=200385). Para obter um exemplo de como configurar os cabeçalhos HTTP em uma mensagem de solicitação, consulte [como: definir cabeçalhos da solicitação do cliente](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md).  
  
## <a name="impersonation"></a>Representação  
 Em geral, o serviço de dados acessa os recursos necessários, como arquivos no servidor ou em um banco de dados, usando as credenciais do processo de trabalho que está hospedando o serviço de dados. Ao usar a representação, os aplicativos [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] podem ser executados com a identidade do Windows (conta de usuário) do usuário que faz a solicitação. A representação é normalmente usada em aplicativos que dependem do IIS para autenticar o usuário, e as credenciais desse princípio são usadas para acessar os recursos necessários. Para obter mais informações, consulte [representação do ASP.NET](http://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d).  
  
## <a name="configuring-data-service-authorization"></a>Configurando a autorização do serviço de dados  
 Autorização é a concessão de acesso a recursos do aplicativo a um princípio ou processo que é identificado com base em uma autenticação anteriormente bem-sucedida. Como uma prática geral, você só deve conceder direitos suficientes para os usuários do serviço de dados executarem as operações exigidas pelos aplicativos cliente.  
  
### <a name="restrict-access-to-data-service-resources"></a>Restringir o acesso a recursos do serviço de dados  
 Por padrão, o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] permite que você conceda acesso comum de leitura e gravação para recursos do serviço de dados (operações de conjunto de entidades e serviço) a qualquer usuário que tenha acesso ao serviço de dados. As regras que definem o acesso de leitura e gravação podem ser definidas separadamente para cada conjunto de entidades exposto pelo serviço de dados, bem como quaisquer operações de serviço. Recomendamos a limitação do acesso de leitura e gravação somente aos recursos exigidos pelo aplicativo cliente. Para obter mais informações, consulte [os requisitos mínimos de acesso de recurso](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md#accessRequirements).  
  
### <a name="implement-role-based-interceptors"></a>Implementar interceptores baseados em função  
 Os interceptores permitem que você intercepte solicitações para recursos do serviço de dados antes que elas sejam manipuladas pelo serviço de dados. Para obter mais informações, consulte [interceptores](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md). Os interceptores permitem que você tome decisões de autorização com base no usuário autenticado que está fazendo a solicitação. Para obter um exemplo de como restringir o acesso a recursos de serviço de dados com base em uma identidade de usuário autenticado, consulte [como: interceptar mensagens do serviço de dados](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>Restringir o acesso aos recursos locais e do repositório de dados persistente  
 As contas que são usadas para acessar o repositório persistente devem receber somente os direitos suficientes em um banco de dados ou no sistema de arquivos para dar suporte aos requisitos do serviço de dados. Quando a autenticação anônima é usada, essa é a conta usada para executar o aplicativo de hospedagem. Para obter mais informações, consulte [como: desenvolver um WCF Data Service em execução no IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md). Quando a representação é usada, os usuários autenticados devem receber acesso a esses recursos, normalmente como parte de um grupo do Windows.  
  
## <a name="other-security-considerations"></a>Outras considerações de segurança  
  
### <a name="secure-the-data-in-the-payload"></a>Proteger os dados na carga  
 O [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] é baseado no protocolo HTTP. Em uma mensagem HTTP, o cabeçalho pode conter credenciais de usuário valiosas, dependendo da autenticação implementada pelo serviço de dados. O corpo da mensagem também pode conter dados importantes do cliente que devem ser protegidos. Em ambos os casos, é recomendável que você use o protocolo SSL para proteger essas informações durante a transmissão.  
  
### <a name="ignored-message-headers-and-cookies"></a>Cabeçalhos e cookies de mensagens ignorados  
 Os cabeçalhos de solicitações HTTP, a não ser os que declaram tipos de conteúdo e locais de recursos, são ignorados e nunca são definidos pelo serviço de dados.  
  
 Os cookies podem ser usados como parte de um esquema de autenticação, por exemplo, com a autenticação de formulários [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Entretanto, os cookies HTTP definidos em uma solicitação de entrada são ignorados pelo [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. O host de um serviço de dados poderá processar o cookie, mas o tempo de execução do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] nunca analisará ou retornará cookies. A biblioteca de cliente do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] também não processa os cookies enviados na resposta.  
  
### <a name="custom-hosting-requirements"></a>Requisitos de hospedagem personalizada  
 Por padrão, o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] é criado como um aplicativo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hospedado no IIS. Isso permite que o serviço de dados aproveite os comportamentos seguros da plataforma. Você pode definir o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] que é hospedado por um host personalizado. Para obter mais informações, consulte [hospeda o serviço de dados](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md). Os componentes e a plataforma que hospedam um serviço de dados devem garantir os seguintes comportamentos de segurança para evitar ataques no serviço de dados:  
  
-   Limitar o tamanho do URI aceito em uma solicitação do serviço de dados para todas as operações possíveis.  
  
-   Limitar o tamanho de mensagens HTTP de entrada e saída.  
  
-   Limitar o número total de solicitações pendentes em qualquer momento determinado.  
  
-   Limitar o tamanho de cabeçalhos HTTP e seus valores, e fornecer ao [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] acesso a dados do cabeçalho.  
  
-   Detectar e deter ataques conhecidos, como ataques de mensagem de repetição e SYN TCP.  
  
### <a name="values-are-not-further-encoded"></a>Os valores não têm codificação adicional  
 Os valores de propriedade enviados ao serviço de dados não têm codificação adicional do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] em tempo de execução. Por exemplo, quando uma propriedade de cadeia de caracteres de uma entidade tem conteúdo HTML formatado, as marcas não são codificadas em HTML pelo serviço de dados. O serviço de dados também não faz a codificação adicional de valores de propriedades na resposta. A biblioteca de cliente também não executa nenhuma codificação adicional.  
  
### <a name="considerations-for-client-applications"></a>Considerações para aplicativos cliente  
 As seguintes considerações de segurança se aplicam aos aplicativos que usam o cliente do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] para acessar serviços [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]:  
  
-   A biblioteca de cliente presume que os protocolos usados para acessar o serviço de dados forneçam um nível de segurança adequado.  
  
-   A biblioteca de cliente usa todos os valores padrão para tempos limite e opções de análise das pilhas de transporte subjacentes fornecidas pela plataforma.  
  
-   A biblioteca de cliente não lê nenhuma configuração de arquivos de configuração de aplicativo.  
  
-   A biblioteca de cliente não implementa nenhum mecanismo de acesso entre domínios. Em vez disso, ela depende dos mecanismos fornecidos pela pilha HTTP subjacente.  
  
-   A biblioteca de cliente não tem nenhum elemento de interface do usuário, e nunca tenta exibir ou renderizar os dados que recebe ou envia.  
  
-   Recomendamos que os aplicativos cliente sempre validem a entrada do usuário, bem como os dados aceitos de serviços não confiáveis.  
  
## <a name="see-also"></a>Consulte também  
 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md) (Definindo o WCF Data Services)  
 [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
