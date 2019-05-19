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
ms.openlocfilehash: 4db6d7e13bfc4a0e2705c210820db511a60e09de
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877348"
---
# <a name="securing-wcf-data-services"></a>Protegendo o WCF Data Services
Este tópico descreve considerações de segurança que são específicas para desenvolver, implantar e executar o WCF Data Services e aplicativos que serviços de acesso que dão suporte a Open Data Protocol (OData). Você também deve seguir as recomendações para criar aplicativos seguros do .NET Framework.  
  
Ao planejar como proteger um serviço OData baseado no WCF Data Services, você deve abordar o processo de detecção e verificar a identidade de uma entidade de segurança, a autenticação e autorização, o processo de determinar se um principal autenticado é permissão para acessar os recursos solicitados. Você também deve considerar a criptografia da mensagem usando o protocolo SSL.  
  
## <a name="authenticating-client-requests"></a>Autenticando solicitações de clientes  
WCF Data Services não implementa nenhum tipo de autenticação próprio, mas depende das previsões de autenticação do host do serviço de dados. Isso significa que o serviço pressupõe que qualquer solicitação recebida já foi autenticada pelo host da rede e que o host identificou corretamente o princípio da solicitação por meio de interfaces fornecidas pelo WCF Data Services. Essas opções de autenticação e as abordagens são detalhadas no multipart [série OData e autenticação](https://devblogs.microsoft.com/odata/?s=%22OData+and+authentication%22).  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>Opções de autenticação para o Serviço de Dados WCF  
 A tabela a seguir lista alguns dos mecanismos de autenticação que estão disponíveis para ajudá-lo a autenticar solicitações a um Serviço de Dados WCF.  
  
|Opções de autenticação|Descrição|  
|----------------------------|-----------------|  
|Autenticação anônima|Quando a autenticação anônima HTTP está habilitada, qualquer princípio pode se conectar ao serviço de dados. Não são necessárias credenciais para o acesso anônimo. Use esta opção somente quando quiser permitir que qualquer pessoa acesse o serviço de dados.|  
|Autenticações básica e digest|As credenciais que consistem em nome de usuário e senha são necessárias para autenticação. Oferecem suporte à autenticação de clientes não Windows. **Observação de segurança:**  As credenciais da autenticação básica (nome de usuário e senha) são enviadas de modo transparente e podem ser interceptadas. A autenticação digest envia um hash baseado nas credenciais fornecidas, o que a torna mais segura do que a autenticação básica. Ambas são suscetíveis a ataques do tipo "man-in-the-middle". Ao usar esses métodos de autenticação, você deve considerar a criptografia da comunicação entre o cliente e o serviço de dados usando o protocolo SSL. <br /><br /> Microsoft Internet Information Services (IIS) fornece uma implementação básica e solicitações de autenticação digest de HTTP em um aplicativo ASP.NET. Essa implementação do provedor de Autenticação do Windows permite que um aplicativo cliente do .NET Framework forneça credenciais do cabeçalho HTTP da solicitação ao serviço de dados para negociar perfeitamente a autenticação de um usuário do Windows. Para obter mais informações, consulte [referência técnica da autenticação Digest](https://go.microsoft.com/fwlink/?LinkId=200408).<br /><br /> Quando você quiser ter seu dados serviço use a autenticação básica com base em algum serviço de autenticação personalizada e não as credenciais do Windows, você deve implementar um módulo HTTP de ADP.NET personalizado para autenticação.<br /><br /> Para obter um exemplo de como usar um esquema de autenticação básica com o WCF Data Services, consulte o postagem no blog [OData e autenticação básica personalizado de autenticação – parte 6 –](https://devblogs.microsoft.com/odata/odata-and-authentication-part-6-custom-basic-authentication/).|  
|Autenticação do Windows|As credenciais baseadas no Windows são trocadas por meio de NTLM ou Kerberos. Esse mecanismo é mais seguro do que a autenticação básica ou digest, mas requer que o cliente seja um aplicativo baseado no Windows. O IIS também fornece uma implementação de autenticação do Windows para solicitações HTTP em um aplicativo ASP.NET. Para obter mais informações, consulte [visão geral de autenticação de formulários do ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/7t6b43z4(v=vs.100)).<br /><br /> Para obter um exemplo de como usar a autenticação do Windows com o WCF Data Services, consulte o postagem no blog [OData e autenticação de Windows autenticação – parte 2 –](https://devblogs.microsoft.com/odata/odata-and-authentication-part-2-windows-authentication/).|  
|Autenticação de formulários do ASP.NET|A autenticação de formulários permite que você autentique usuários usando seu próprio código e, em seguida, mantenha um token de autenticação em um cookie ou na URL da página. Você autentica o nome de usuário e a senha de seus usuários usando um formulário de logon que você cria. As solicitações não autenticadas são redirecionadas para uma página de logon, onde o usuário fornece credenciais e envia o formulário. Se o aplicativo autenticar a solicitação, o sistema emitirá um tíquete contendo uma chave para restabelecer a identidade para solicitações subsequentes. Para obter mais informações, consulte [provedor de autenticação de formulários](https://docs.microsoft.com/previous-versions/aspnet/9wff0kyh(v=vs.100)). **Observação de segurança:**  Por padrão, o cookie que contém o tíquete de autenticação de formulários não é protegido quando você usa a autenticação de formulários em um aplicativo Web ASP.NET. Você deve considerar exigir que o SSL proteja o tíquete de autenticação e as credenciais do logon inicial. <br /><br /> Para um exemplo de como usar autenticação de formulários com o WCF Data Services, consulte o postagem no blog [OData e autenticação de formulários de autenticação – parte 7 –](https://devblogs.microsoft.com/odata/odata-and-authentication-part-7-forms-authentication/).|  
|Autenticação baseada em declarações|Na autenticação baseada em declarações, o serviço de dados se baseia em um serviço de provedor de identidade de "terceiros" confiável para autenticar o usuário. O provedor de identidade positivamente autentica o usuário que está solicitando acesso a recursos do serviço de acesso e emite um token que concede acesso aos recursos solicitados. Esse token é então apresentado ao serviço de dados, que concede acesso ao usuário com base na relação de confiança com o serviço de identidade que emitiu o token de acesso.<br /><br /> A vantagem de usar um provedor de autenticação baseado em declarações é que ele pode ser usado para autenticar vários tipos de clientes em domínios de confiança. Empregando tal provedor de terceiros, um serviço de dados pode descarregar os requisitos de manutenção e autenticação de usuários. OAuth 2.0 é um protocolo de autenticação baseado em declarações que tem o suporte do Microsoft Azure AppFabric Access Control para autorização federada como um serviço. Esse protocolo oferece suporte a serviços baseados em REST. Para obter um exemplo de como usar o OAuth 2.0 com o WCF Data Services, consulte o postagem no blog [OData e autenticação – parte 8 – OAuth WRAP](https://devblogs.microsoft.com/odata/odata-and-authentication-part-8-oauth-wrap/).|  
  
<a name="clientAuthentication"></a>   
### <a name="authentication-in-the-client-library"></a>Autenticação na biblioteca de cliente  
 Por padrão, a biblioteca de cliente do WCF Data Services não fornece credenciais ao fazer uma solicitação para um serviço OData. Quando as credenciais de logon são exigidas pelo serviço de dados para autenticar um usuário, essas credenciais podem ser fornecidas em um <xref:System.Net.NetworkCredential> acessado da propriedade <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> do <xref:System.Data.Services.Client.DataServiceContext>, como no exemplo a seguir:  
  
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
  
 Para obter mais informações, confira [Como: Especifique as credenciais do cliente para uma solicitação de serviço de dados](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md).  
  
 Quando o serviço de dados exige credenciais de logon que não podem ser especificadas com um objeto <xref:System.Net.NetworkCredential>, como um cookie ou um token baseado em declarações, você deve definir manualmente os cabeçalhos na solicitação HTTP, geralmente os cabeçalhos `Authorization` e `Cookie`. Para obter mais informações sobre esse tipo de cenário de autenticação, consulte o postagem no blog [ OData e autenticação – parte 3 – ClientSide Hooks](https://devblogs.microsoft.com/odata/odata-and-authentication-part-3-clientside-hooks/). Para obter um exemplo de como definir cabeçalhos HTTP em uma mensagem de solicitação, consulte [como: Definir os cabeçalhos da solicitação do cliente](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md).  
  
## <a name="impersonation"></a>Representação  
 Em geral, o serviço de dados acessa os recursos necessários, como arquivos no servidor ou em um banco de dados, usando as credenciais do processo de trabalho que está hospedando o serviço de dados. Ao usar a representação, os aplicativos ASP.NET podem ser executados com a identidade do Windows (conta de usuário) do usuário que faz a solicitação. A representação é normalmente usada em aplicativos que dependem do IIS para autenticar o usuário, e as credenciais desse princípio são usadas para acessar os recursos necessários. Para obter mais informações, consulte [personificação do ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)).  
  
## <a name="configuring-data-service-authorization"></a>Configurando a autorização do serviço de dados  
 Autorização é a concessão de acesso a recursos do aplicativo a um princípio ou processo que é identificado com base em uma autenticação anteriormente bem-sucedida. Como uma prática geral, você só deve conceder direitos suficientes para os usuários do serviço de dados executarem as operações exigidas pelos aplicativos cliente.  
  
### <a name="restrict-access-to-data-service-resources"></a>Restringir o acesso a recursos do serviço de dados  
 Por padrão, o WCF Data Services permite que você conceda comuns acesso de leitura e gravação com base nos recursos do serviço de dados (a entidade definida e operações de serviço) para qualquer usuário que seja capaz de acessar o serviço de dados. As regras que definem o acesso de leitura e gravação podem ser definidas separadamente para cada conjunto de entidades exposto pelo serviço de dados, bem como quaisquer operações de serviço. Recomendamos a limitação do acesso de leitura e gravação somente aos recursos exigidos pelo aplicativo cliente. Para obter mais informações, consulte [requisitos de acesso de recursos mínimo](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md#accessRequirements).  
  
### <a name="implement-role-based-interceptors"></a>Implementar interceptores baseados em função  
 Os interceptores permitem que você intercepte solicitações para recursos do serviço de dados antes que elas sejam manipuladas pelo serviço de dados. Para obter mais informações, consulte [interceptores](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md). Os interceptores permitem que você tome decisões de autorização com base no usuário autenticado que está fazendo a solicitação. Para obter um exemplo de como restringir o acesso aos recursos de serviço de dados com base em uma identidade de usuário autenticado, consulte [como: Interceptar mensagens de serviço de dados](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>Restringir o acesso aos recursos locais e do repositório de dados persistente  
 As contas que são usadas para acessar o repositório persistente devem receber somente os direitos suficientes em um banco de dados ou no sistema de arquivos para dar suporte aos requisitos do serviço de dados. Quando a autenticação anônima é usada, essa é a conta usada para executar o aplicativo de hospedagem. Para obter mais informações, confira [Como: Desenvolver um WCF Data Service em execução no IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md). Quando a representação é usada, os usuários autenticados devem receber acesso a esses recursos, normalmente como parte de um grupo do Windows.  
  
## <a name="other-security-considerations"></a>Outras considerações de segurança  
  
### <a name="secure-the-data-in-the-payload"></a>Proteger os dados na carga  
OData é baseado no protocolo HTTP. Em uma mensagem HTTP, o cabeçalho pode conter credenciais de usuário valiosas, dependendo da autenticação implementada pelo serviço de dados. O corpo da mensagem também pode conter dados importantes do cliente que devem ser protegidos. Em ambos os casos, é recomendável que você use o protocolo SSL para proteger essas informações durante a transmissão.  
  
### <a name="ignored-message-headers-and-cookies"></a>Cabeçalhos e cookies de mensagens ignorados  
 Os cabeçalhos de solicitações HTTP, a não ser os que declaram tipos de conteúdo e locais de recursos, são ignorados e nunca são definidos pelo serviço de dados.  
  
 Os cookies podem ser usados como parte de um esquema de autenticação, como com autenticação de formulários do ASP.NET. No entanto, os cookies HTTP definidos em uma solicitação de entrada são ignorados pelos serviços de dados do WCF. O host de um serviço de dados poderá processar o cookie, mas o tempo de execução do WCF Data Services nunca analisará ou retornará cookies. A biblioteca de cliente do WCF Data Services também não processa os cookies enviados na resposta.  
  
### <a name="custom-hosting-requirements"></a>Requisitos de hospedagem personalizada  
 Por padrão, o WCF Data Services é criado como um aplicativo ASP.NET hospedado no IIS. Isso permite que o serviço de dados aproveite os comportamentos seguros da plataforma. Você pode definir o WCF Data Services que são hospedados por um host personalizado. Para obter mais informações, consulte [que hospeda o serviço de dados](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md). Os componentes e a plataforma que hospedam um serviço de dados devem garantir os seguintes comportamentos de segurança para evitar ataques no serviço de dados:  
  
- Limitar o tamanho do URI aceito em uma solicitação do serviço de dados para todas as operações possíveis.  
  
- Limitar o tamanho de mensagens HTTP de entrada e saída.  
  
- Limitar o número total de solicitações pendentes em qualquer momento determinado.  
  
- Limitar o tamanho dos cabeçalhos HTTP e seus valores e fornecer acesso de WCF Data Services para dados de cabeçalho.  
  
- Detectar e deter ataques conhecidos, como ataques de mensagem de repetição e SYN TCP.  
  
### <a name="values-are-not-further-encoded"></a>Os valores não têm codificação adicional  
 Valores de propriedade enviados ao serviço de dados não têm codificação adicional pelo tempo de execução do WCF Data Services. Por exemplo, quando uma propriedade de cadeia de caracteres de uma entidade tem conteúdo HTML formatado, as marcas não são codificadas em HTML pelo serviço de dados. O serviço de dados também não faz a codificação adicional de valores de propriedades na resposta. A biblioteca de cliente também não executa nenhuma codificação adicional.  
  
### <a name="considerations-for-client-applications"></a>Considerações para aplicativos cliente  
 As seguintes considerações de segurança se aplicam a aplicativos que usam o cliente do WCF Data Services para acessar serviços OData:  
  
- A biblioteca de cliente presume que os protocolos usados para acessar o serviço de dados forneçam um nível de segurança adequado.  
  
- A biblioteca de cliente usa todos os valores padrão para tempos limite e opções de análise das pilhas de transporte subjacentes fornecidas pela plataforma.  
  
- A biblioteca de cliente não lê nenhuma configuração de arquivos de configuração de aplicativo.  
  
- A biblioteca de cliente não implementa nenhum mecanismo de acesso entre domínios. Em vez disso, ela depende dos mecanismos fornecidos pela pilha HTTP subjacente.  
  
- A biblioteca de cliente não tem nenhum elemento de interface do usuário, e nunca tenta exibir ou renderizar os dados que recebe ou envia.  
  
- Recomendamos que os aplicativos cliente sempre validem a entrada do usuário, bem como os dados aceitos de serviços não confiáveis.  
  
## <a name="see-also"></a>Consulte também

- [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md) (Definindo o WCF Data Services)
- [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
