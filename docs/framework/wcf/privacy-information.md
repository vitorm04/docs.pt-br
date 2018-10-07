---
title: Informações de privacidade do Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: 717e38b15767b744816c0a57c97827a1a35c95b3
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847809"
---
# <a name="windows-communication-foundation-privacy-information"></a><span data-ttu-id="dd662-102">Informações de privacidade do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="dd662-102">Windows Communication Foundation Privacy Information</span></span>
<span data-ttu-id="dd662-103">A Microsoft está comprometida em proteger a privacidade dos usuários finais.</span><span class="sxs-lookup"><span data-stu-id="dd662-103">Microsoft is committed to protecting end-users' privacy.</span></span> <span data-ttu-id="dd662-104">Quando você compila um aplicativo usando o Windows Communication Foundation (WCF), versão 3.0, seu aplicativo pode afetar a privacidade de seus usuários finais.</span><span class="sxs-lookup"><span data-stu-id="dd662-104">When you build an application using Windows Communication Foundation (WCF), version 3.0, your application may impact your end-users' privacy.</span></span> <span data-ttu-id="dd662-105">Por exemplo, seu aplicativo explicitamente poderá coletar informações de contato do usuário, ou ele pode solicitar ou enviar informações pela Internet para seu site da Web.</span><span class="sxs-lookup"><span data-stu-id="dd662-105">For example, your application may explicitly collect user contact information, or it may request or send information over the Internet to your Web site.</span></span> <span data-ttu-id="dd662-106">Se você incorporar tecnologia da Microsoft em seu aplicativo, o que a tecnologia pode ter seu próprio comportamento que pode afetar a privacidade.</span><span class="sxs-lookup"><span data-stu-id="dd662-106">If you embed Microsoft technology in your application, that technology may have its own behavior that might affect privacy.</span></span> <span data-ttu-id="dd662-107">WCF não enviar todas as informações à Microsoft do seu aplicativo, a menos que você ou o usuário final optar por enviá-los para nós.</span><span class="sxs-lookup"><span data-stu-id="dd662-107">WCF does not send any information to Microsoft from your application unless you or the end-user choose to send it to us.</span></span>  
  
## <a name="wcf-in-brief"></a><span data-ttu-id="dd662-108">WCF no resumo</span><span class="sxs-lookup"><span data-stu-id="dd662-108">WCF in Brief</span></span>  
 <span data-ttu-id="dd662-109">O WCF é uma estrutura de mensagens distribuída usando o Microsoft .NET Framework que permite aos desenvolvedores criar aplicativos distribuídos.</span><span class="sxs-lookup"><span data-stu-id="dd662-109">WCF is a distributed messaging framework using the Microsoft .NET Framework that allows developers to build distributed applications.</span></span> <span data-ttu-id="dd662-110">Mensagens de comunicado entre dois aplicativos contêm informações de cabeçalho e corpo.</span><span class="sxs-lookup"><span data-stu-id="dd662-110">Messages communicated between two applications contain header and body information.</span></span>  
  
 <span data-ttu-id="dd662-111">Cabeçalhos podem conter o roteamento de mensagens, informações de segurança, transações e muito mais, dependendo dos serviços usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd662-111">Headers may contain message routing, security information, transactions, and more depending on the services used by the application.</span></span> <span data-ttu-id="dd662-112">Normalmente, as mensagens são criptografadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="dd662-112">Messages are typically encrypted by default.</span></span> <span data-ttu-id="dd662-113">A única exceção é ao usar o `BasicHttpBinding`, que foi projetado para uso com os serviços da Web herdados, não é seguro.</span><span class="sxs-lookup"><span data-stu-id="dd662-113">The one exception is when using the `BasicHttpBinding`, which was designed for use with non-secured, legacy Web services.</span></span> <span data-ttu-id="dd662-114">Como criador do aplicativo, você é responsável pelo design final.</span><span class="sxs-lookup"><span data-stu-id="dd662-114">As the application designer, you are responsible for the final design.</span></span> <span data-ttu-id="dd662-115">Mensagens no corpo SOAP contêm dados específicos do aplicativo; No entanto, esses dados, como definido pelo aplicativo informações pessoais podem ser protegidos usando recursos de criptografia ou a confidencialidade do WCF.</span><span class="sxs-lookup"><span data-stu-id="dd662-115">Messages in the SOAP body contain application-specific data; however, this data, such as application-defined personal information, can be secured by using WCF encryption or confidentiality features.</span></span> <span data-ttu-id="dd662-116">As seções a seguir descrevem os recursos que potencialmente afetam a privacidade.</span><span class="sxs-lookup"><span data-stu-id="dd662-116">The following sections describe the features that potentially impact privacy.</span></span>  
  
## <a name="messaging"></a><span data-ttu-id="dd662-117">Mensagens</span><span class="sxs-lookup"><span data-stu-id="dd662-117">Messaging</span></span>  
 <span data-ttu-id="dd662-118">Cada mensagem do WCF tem um cabeçalho de endereço que especifica o destino da mensagem e, em que a resposta deve ir.</span><span class="sxs-lookup"><span data-stu-id="dd662-118">Each WCF message has an address header that specifies the message destination and where the reply should go.</span></span>  
  
 <span data-ttu-id="dd662-119">O componente de endereço de um endereço de ponto de extremidade é um identificador de URI (Uniform Resource) que identifica o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="dd662-119">The address component of an endpoint address is a Uniform Resource Identifier (URI) that identifies the endpoint.</span></span> <span data-ttu-id="dd662-120">O endereço pode ser um endereço de rede ou um endereço lógico.</span><span class="sxs-lookup"><span data-stu-id="dd662-120">The address can be a network address or a logical address.</span></span> <span data-ttu-id="dd662-121">O endereço pode incluir o nome do computador (nome de host, nome de domínio totalmente qualificado) e um endereço IP.</span><span class="sxs-lookup"><span data-stu-id="dd662-121">The address may include machine name (hostname, fully qualified domain name) and an IP address.</span></span> <span data-ttu-id="dd662-122">O endereço do ponto de extremidade também pode conter um identificador global exclusivo (GUID) ou uma coleção de GUIDs para endereçamento temporário usado para distinguir cada endereço.</span><span class="sxs-lookup"><span data-stu-id="dd662-122">The endpoint address may also contain a globally unique identifier (GUID), or a collection of GUIDs for temporary addressing used to discern each address.</span></span> <span data-ttu-id="dd662-123">Cada mensagem contém uma ID de mensagem que é um GUID.</span><span class="sxs-lookup"><span data-stu-id="dd662-123">Each message contains a message ID that is a GUID.</span></span> <span data-ttu-id="dd662-124">Esse recurso segue o padrão de referência do WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="dd662-124">This feature follows the WS-Addressing reference standard.</span></span>  
  
 <span data-ttu-id="dd662-125">A camada de mensagens do WCF não grava nenhuma informação pessoal para o computador local.</span><span class="sxs-lookup"><span data-stu-id="dd662-125">The WCF messaging layer does not write any personal information to the local machine.</span></span> <span data-ttu-id="dd662-126">No entanto, ele poderá propagar as informações pessoais no nível da rede se um desenvolvedor de serviços criou um serviço que expõe essas informações (por exemplo, por usando o nome de uma pessoa em um nome de ponto de extremidade, ou incluir informações pessoais na Web do ponto de extremidade Serviços de linguagem de descrição, mas não exigir que os clientes usar https para acessar o WSDL).</span><span class="sxs-lookup"><span data-stu-id="dd662-126">However, it might propagate personal information at the network level if a service developer has created a service that exposes such information (for example, by using a person's name in an endpoint name, or including personal information in the endpoint's Web Services Description Language but not requiring clients to use https to access the WSDL).</span></span> <span data-ttu-id="dd662-127">Além disso, se um desenvolvedor executa o [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta em relação a um ponto de extremidade que expõe informações pessoais, a saída da ferramenta poderia conter essas informações e o arquivo de saída é gravado para o disco rígido local.</span><span class="sxs-lookup"><span data-stu-id="dd662-127">Also, if a developer runs the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool against an endpoint that exposes personal information, the tool's output could contain that information, and the output file is written to the local hard disk.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="dd662-128">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="dd662-128">Hosting</span></span>  
 <span data-ttu-id="dd662-129">O recurso de hospedagem do WCF permite que os aplicativos para iniciar por demanda ou para habilitar o compartilhamento de porta entre vários aplicativos.</span><span class="sxs-lookup"><span data-stu-id="dd662-129">The hosting feature in WCF allows applications to start on demand or to enable port sharing between multiple applications.</span></span> <span data-ttu-id="dd662-130">Um aplicativo WCF pode ser hospedado no Internet Information Services (IIS), semelhante ao [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dd662-130">An WCF application can be hosted in Internet Information Services (IIS), similar to [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].</span></span>  
  
 <span data-ttu-id="dd662-131">Hospedagem não expõem quaisquer informações específicas sobre a rede e não mantém dados na máquina.</span><span class="sxs-lookup"><span data-stu-id="dd662-131">Hosting does not expose any specific information on the network and it does not keep data on the machine.</span></span>  
  
## <a name="message-security"></a><span data-ttu-id="dd662-132">Segurança de mensagem</span><span class="sxs-lookup"><span data-stu-id="dd662-132">Message Security</span></span>  
 <span data-ttu-id="dd662-133">Segurança do WCF fornece os recursos de segurança para aplicativos de mensagens.</span><span class="sxs-lookup"><span data-stu-id="dd662-133">WCF security provides the security capabilities for messaging applications.</span></span> <span data-ttu-id="dd662-134">As funções de segurança fornecidas incluem autenticação e autorização.</span><span class="sxs-lookup"><span data-stu-id="dd662-134">The security functions provided include authentication and authorization.</span></span>  
  
 <span data-ttu-id="dd662-135">Autenticação é realizada pela transmissão de credenciais entre os clientes e serviços.</span><span class="sxs-lookup"><span data-stu-id="dd662-135">Authentication is performed by passing credentials between the clients and services.</span></span> <span data-ttu-id="dd662-136">A autenticação pode ser por meio da segurança de nível de transporte ou por meio de SOAP mensagem de nível de segurança, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="dd662-136">Authentication can be either through transport-level security or through SOAP message-level security, as follows:</span></span>  
  
-   <span data-ttu-id="dd662-137">Na segurança de mensagem SOAP, a autenticação é realizada por meio de credenciais, como nome de usuário/senhas, certificados x. 509, tíquetes Kerberos e os tokens SAML, que podem conter informações pessoais, dependendo do emissor.</span><span class="sxs-lookup"><span data-stu-id="dd662-137">In SOAP message security, authentication is performed through credentials like username/passwords, X.509 certificates, Kerberos tickets, and SAML tokens, all of which might contain personal information, depending on the issuer.</span></span>  
  
-   <span data-ttu-id="dd662-138">Usando a segurança de transporte, a autenticação é feita por meio de mecanismos de autenticação do transporte tradicionais, como esquemas de autenticação HTTP (básica, Digest, Negotiate, NTLM, None, a autorização integrada do Windows e anônima) e a autenticação de formulário.</span><span class="sxs-lookup"><span data-stu-id="dd662-138">Using transport security, authentication is done through traditional transport authentication mechanisms like HTTP authentication schemes (Basic, Digest, Negotiate, Integrated Windows Authorization, NTLM, None, and Anonymous), and form authentication.</span></span>  
  
 <span data-ttu-id="dd662-139">A autenticação pode resultar em uma sessão segura estabelecida entre os pontos de extremidade de comunicação.</span><span class="sxs-lookup"><span data-stu-id="dd662-139">Authentication can result in a secure session established between the communicating endpoints.</span></span> <span data-ttu-id="dd662-140">A sessão é identificada por um GUID que dura o tempo de vida da sessão de segurança.</span><span class="sxs-lookup"><span data-stu-id="dd662-140">The session is identified by a GUID that lasts the lifetime of the security session.</span></span> <span data-ttu-id="dd662-141">A tabela a seguir mostra o que é mantido e onde.</span><span class="sxs-lookup"><span data-stu-id="dd662-141">The following table shows what is kept and where.</span></span>  
  
|<span data-ttu-id="dd662-142">Dados</span><span class="sxs-lookup"><span data-stu-id="dd662-142">Data</span></span>|<span data-ttu-id="dd662-143">Armazenamento</span><span class="sxs-lookup"><span data-stu-id="dd662-143">Storage</span></span>|  
|----------|-------------|  
|<span data-ttu-id="dd662-144">Credenciais de apresentação, como nome de usuário, certificados X.509, tokens Kerberos e as referências às credenciais.</span><span class="sxs-lookup"><span data-stu-id="dd662-144">Presentation credentials, such as username, X.509 certificates, Kerberos tokens, and references to credentials.</span></span>|<span data-ttu-id="dd662-145">Mecanismos de gerenciamento, como o repositório de certificados do Windows de credenciais do Windows padrão.</span><span class="sxs-lookup"><span data-stu-id="dd662-145">Standard Windows credential management mechanisms such as the Windows certificate store.</span></span>|  
|<span data-ttu-id="dd662-146">Informações de associação de usuário, como nomes de usuário e senhas.</span><span class="sxs-lookup"><span data-stu-id="dd662-146">User membership information, such as usernames and passwords.</span></span>|[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] <span data-ttu-id="dd662-147">provedores de associação.</span><span class="sxs-lookup"><span data-stu-id="dd662-147"> membership providers.</span></span>|  
|<span data-ttu-id="dd662-148">Informações de identidade sobre o serviço usado para autenticar o serviço aos clientes.</span><span class="sxs-lookup"><span data-stu-id="dd662-148">Identity information about the service used to authenticate the service to clients.</span></span>|<span data-ttu-id="dd662-149">Endereço do ponto de extremidade do serviço.</span><span class="sxs-lookup"><span data-stu-id="dd662-149">Endpoint address of the service.</span></span>|  
|<span data-ttu-id="dd662-150">Informações do chamador.</span><span class="sxs-lookup"><span data-stu-id="dd662-150">Caller information.</span></span>|<span data-ttu-id="dd662-151">Os logs de auditoria.</span><span class="sxs-lookup"><span data-stu-id="dd662-151">Auditing logs.</span></span>|  
  
## <a name="auditing"></a><span data-ttu-id="dd662-152">Auditoria</span><span class="sxs-lookup"><span data-stu-id="dd662-152">Auditing</span></span>  
 <span data-ttu-id="dd662-153">A auditoria registra o êxito ou falha de eventos de autenticação e autorização.</span><span class="sxs-lookup"><span data-stu-id="dd662-153">Auditing records the success and failure of authentication and authorization events.</span></span> <span data-ttu-id="dd662-154">Registros de auditoria contêm os seguintes dados: identificação do chamador, o URI da ação e o URI de serviço.</span><span class="sxs-lookup"><span data-stu-id="dd662-154">Auditing records contain the following data: service URI, action URI, and the caller's identification.</span></span>  
  
 <span data-ttu-id="dd662-155">A auditoria também registra quando o administrador modifica a configuração de log de mensagens (ativando ou desativando), porque o log de mensagens pode registrar dados específicos do aplicativo em cabeçalhos e corpos.</span><span class="sxs-lookup"><span data-stu-id="dd662-155">Auditing also records when the administrator modifies the configuration of message logging (turning it on or off), because message logging may log application-specific data in headers and bodies.</span></span> <span data-ttu-id="dd662-156">Para [!INCLUDE[wxp](../../../includes/wxp-md.md)], um registro é registrado no log de eventos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd662-156">For [!INCLUDE[wxp](../../../includes/wxp-md.md)], a record is logged in the application event log.</span></span> <span data-ttu-id="dd662-157">Para [!INCLUDE[wv](../../../includes/wv-md.md)] e [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], um registro é registrado no log de eventos de segurança.</span><span class="sxs-lookup"><span data-stu-id="dd662-157">For [!INCLUDE[wv](../../../includes/wv-md.md)] and [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], a record is logged in the security event log.</span></span>  
  
## <a name="transactions"></a><span data-ttu-id="dd662-158">Transações</span><span class="sxs-lookup"><span data-stu-id="dd662-158">Transactions</span></span>  
 <span data-ttu-id="dd662-159">O recurso de transações fornece serviços transacionais para um aplicativo WCF.</span><span class="sxs-lookup"><span data-stu-id="dd662-159">The transactions feature provides transactional services to a WCF application.</span></span>  
  
 <span data-ttu-id="dd662-160">Cabeçalhos de transação usados na propagação de transações podem conter IDs de transação ou IDs de inscrição, que são GUIDs.</span><span class="sxs-lookup"><span data-stu-id="dd662-160">Transaction headers used in transaction propagation may contain Transaction IDs or Enlistment IDs, which are GUIDs.</span></span>  
  
 <span data-ttu-id="dd662-161">A funcionalidade de transações usa o Gerenciador de transações (um componente do Windows) do Microsoft Distributed Transaction coordenador (MSDTC) para gerenciar o estado da transação.</span><span class="sxs-lookup"><span data-stu-id="dd662-161">The Transactions feature uses the Microsoft Distributed Transaction Coordinator (MSDTC) Transaction Manager (a Windows component) to manage transaction state.</span></span> <span data-ttu-id="dd662-162">Por padrão, as comunicações entre os gerenciadores de transações são criptografadas.</span><span class="sxs-lookup"><span data-stu-id="dd662-162">By default, communications between Transactions Managers are encrypted.</span></span> <span data-ttu-id="dd662-163">Gerenciadores de transações podem registrar IDs de inscrição, IDs de transação e referências de ponto de extremidade como parte de seu estado durável.</span><span class="sxs-lookup"><span data-stu-id="dd662-163">Transaction Managers may log endpoint references, Transaction IDs, and Enlistment IDs as part of their durable state.</span></span> <span data-ttu-id="dd662-164">O tempo de vida esse estado é determinado pelo tempo de vida do arquivo de log do Gerenciador de transações.</span><span class="sxs-lookup"><span data-stu-id="dd662-164">The lifetime of this state is determined by the lifetime of the Transaction Manager’s log file.</span></span> <span data-ttu-id="dd662-165">O serviço MSDTC possui e mantém esse log.</span><span class="sxs-lookup"><span data-stu-id="dd662-165">The MSDTC service owns and maintains this log.</span></span>  
  
 <span data-ttu-id="dd662-166">O recurso de transações implementa os padrões WS-Coordination e transações de WS-Atomic.</span><span class="sxs-lookup"><span data-stu-id="dd662-166">The Transactions feature implements the WS-Coordination and WS-Atomic Transaction standards.</span></span>  
  
## <a name="reliable-sessions"></a><span data-ttu-id="dd662-167">Sessões confiáveis</span><span class="sxs-lookup"><span data-stu-id="dd662-167">Reliable Sessions</span></span>  
 <span data-ttu-id="dd662-168">Sessões confiáveis no WCF fornecem a transferência de mensagens quando ocorrem falhas intermediárias ou transporte.</span><span class="sxs-lookup"><span data-stu-id="dd662-168">Reliable sessions in WCF provide the transfer of messages when transport or intermediary failures occur.</span></span> <span data-ttu-id="dd662-169">Eles fornecem um exatamente-uma vez de transferência de mensagens, mesmo quando o transporte subjacente se desconecta (por exemplo, uma conexão TCP em uma rede sem fio) ou perde uma mensagem (um proxy HTTP descartando uma mensagem de entrada ou de saída).</span><span class="sxs-lookup"><span data-stu-id="dd662-169">They provide an exactly-once transfer of messages even when the underlying transport disconnects (for example, a TCP connection on a wireless network) or loses a message (an HTTP proxy dropping an outgoing or incoming message).</span></span> <span data-ttu-id="dd662-170">Sessões confiáveis também recuperar a mensagem reordenação (como pode acontecer no caso de roteamento de vários caminhos), preservando a ordem na qual as mensagens foram enviadas.</span><span class="sxs-lookup"><span data-stu-id="dd662-170">Reliable sessions also recover message reordering (as may happen in the case of multipath routing), preserving the order in which the messages were sent.</span></span>  
  
 <span data-ttu-id="dd662-171">Sessões confiáveis são implementadas usando o protocolo WS-ReliableMessaging (WS-RM).</span><span class="sxs-lookup"><span data-stu-id="dd662-171">Reliable sessions are implemented using the WS-ReliableMessaging (WS-RM) protocol.</span></span> <span data-ttu-id="dd662-172">Eles adicionam cabeçalhos WS-RM que contêm informações de sessão, que são usadas para identificar todas as mensagens associadas a uma determinada sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="dd662-172">They add WS-RM headers that contain session information, which is used to identify all messages associated with a particular reliable session.</span></span> <span data-ttu-id="dd662-173">Cada sessão WS-RM tem um identificador, que é um GUID.</span><span class="sxs-lookup"><span data-stu-id="dd662-173">Each WS-RM session has an identifier, which is a GUID.</span></span>  
  
 <span data-ttu-id="dd662-174">Nenhuma informação pessoal é mantida no computador do usuário final.</span><span class="sxs-lookup"><span data-stu-id="dd662-174">No personal information is retained on the end-user's machine.</span></span>  
  
## <a name="queued-channels"></a><span data-ttu-id="dd662-175">Canais na fila</span><span class="sxs-lookup"><span data-stu-id="dd662-175">Queued Channels</span></span>  
 <span data-ttu-id="dd662-176">As filas armazenam mensagens de um aplicativo de envio em nome de um aplicativo de recebimento e posteriormente, encaminham essas mensagens para o aplicativo de recebimento.</span><span class="sxs-lookup"><span data-stu-id="dd662-176">Queues store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span> <span data-ttu-id="dd662-177">Eles ajudam a garantir a transferência de mensagens dos aplicativos de envio para aplicativos de recebimento, quando, por exemplo, o aplicativo de recebimento é transitório.</span><span class="sxs-lookup"><span data-stu-id="dd662-177">They help ensure the transfer of messages from sending applications to receiving applications when, for example, the receiving application is transient.</span></span> <span data-ttu-id="dd662-178">O WCF oferece suporte para enfileiramento de mensagens usando o Microsoft Message Queuing (MSMQ) como um transporte.</span><span class="sxs-lookup"><span data-stu-id="dd662-178">WCF provides support for queuing by using Microsoft Message Queuing (MSMQ) as a transport.</span></span>  
  
 <span data-ttu-id="dd662-179">O recurso de canais na fila não adiciona cabeçalhos de uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="dd662-179">The queued channels feature does not add headers to a message.</span></span> <span data-ttu-id="dd662-180">Em vez disso, ele cria uma mensagem de enfileiramento de mensagens com o conjunto de propriedades de mensagem de enfileiramento de mensagens apropriado e invoca métodos de enfileiramento de mensagens para colocar a mensagem na fila de enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="dd662-180">Instead it creates a Message Queuing message with appropriate Message Queuing message properties set, and invokes Message Queuing methods to put the message in the Message Queuing queue.</span></span> <span data-ttu-id="dd662-181">O enfileiramento é um componente opcional que acompanha o Windows.</span><span class="sxs-lookup"><span data-stu-id="dd662-181">Message Queuing is an optional component that ships with Windows.</span></span>  
  
 <span data-ttu-id="dd662-182">Nenhuma informação é mantida no computador do usuário final pelo recurso de canais na fila, pois ela usa o enfileiramento de mensagens como a infraestrutura de enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="dd662-182">No information is retained on the end-user's machine by the queued channels feature, because it uses Message Queuing as the queuing infrastructure.</span></span>  
  
## <a name="com-integration"></a><span data-ttu-id="dd662-183">Integração de COM+</span><span class="sxs-lookup"><span data-stu-id="dd662-183">COM+ Integration</span></span>  
 <span data-ttu-id="dd662-184">Esse recurso encapsula a funcionalidade e COM+ existente para criar serviços que são compatíveis com os serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="dd662-184">This feature wraps existing COM and COM+ functionality to create services that are compatible with WCF services.</span></span> <span data-ttu-id="dd662-185">Esse recurso não usa cabeçalhos específicos e ela não retém os dados na máquina do usuário final.</span><span class="sxs-lookup"><span data-stu-id="dd662-185">This feature does not use specific headers and it does not retain data on the end-user's machine.</span></span>  
  
## <a name="com-service-moniker"></a><span data-ttu-id="dd662-186">Moniker de serviço COM</span><span class="sxs-lookup"><span data-stu-id="dd662-186">COM Service Moniker</span></span>  
 <span data-ttu-id="dd662-187">Isso fornece um invólucro não gerenciado para um cliente WCF padrão.</span><span class="sxs-lookup"><span data-stu-id="dd662-187">This provides an unmanaged wrapper to a standard WCF client.</span></span> <span data-ttu-id="dd662-188">Esse recurso não tem cabeçalhos específicos durante a transmissão nem manter a dados no computador.</span><span class="sxs-lookup"><span data-stu-id="dd662-188">This feature does not have specific headers on the wire nor does it persist data on the machine.</span></span>  
  
## <a name="peer-channel"></a><span data-ttu-id="dd662-189">Canal par</span><span class="sxs-lookup"><span data-stu-id="dd662-189">Peer Channel</span></span>  
 <span data-ttu-id="dd662-190">Um canal par permite o desenvolvimento de aplicativos com vários participantes usando o WCF.</span><span class="sxs-lookup"><span data-stu-id="dd662-190">A peer channel enables development of multiparty applications using WCF.</span></span> <span data-ttu-id="dd662-191">Mensagens entre vários participantes ocorre no contexto de uma malha.</span><span class="sxs-lookup"><span data-stu-id="dd662-191">Multiparty messaging occurs in the context of a mesh.</span></span> <span data-ttu-id="dd662-192">Malhas são identificadas por um nome que podem juntar a nós.</span><span class="sxs-lookup"><span data-stu-id="dd662-192">Meshes are identified by a name that nodes can join.</span></span> <span data-ttu-id="dd662-193">Cada nó no canal par cria um ouvinte TCP em uma porta especificada pelo usuário e estabelece conexões com outros nós na malha para garantir a resiliência.</span><span class="sxs-lookup"><span data-stu-id="dd662-193">Each node in the peer channel creates a TCP listener at a user-specified port and establishes connections with other nodes in the mesh to ensure resiliency.</span></span> <span data-ttu-id="dd662-194">Para se conectar a outros nós na malha, nós também trocam alguns dados, incluindo o endereço de escuta e endereços IP da máquina, com outros nós na malha.</span><span class="sxs-lookup"><span data-stu-id="dd662-194">To connect to other nodes in the mesh, nodes also exchange some data, including the listener address and the machine's IP addresses, with other nodes in the mesh.</span></span> <span data-ttu-id="dd662-195">As mensagens enviadas em torno da malha podem conter informações de segurança que pertencem ao remetente para evitar falsificação de mensagens e a violação.</span><span class="sxs-lookup"><span data-stu-id="dd662-195">Messages sent around in the mesh can contain security information that pertains to the sender to prevent message spoofing and tampering.</span></span>  
  
 <span data-ttu-id="dd662-196">Nenhuma informação pessoal é armazenada no computador do usuário final.</span><span class="sxs-lookup"><span data-stu-id="dd662-196">No personal information is stored on the end-user's machine.</span></span>  
  
## <a name="it-professional-experience"></a><span data-ttu-id="dd662-197">Experiência do profissional de TI</span><span class="sxs-lookup"><span data-stu-id="dd662-197">IT Professional Experience</span></span>  
  
### <a name="tracing"></a><span data-ttu-id="dd662-198">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="dd662-198">Tracing</span></span>  
 <span data-ttu-id="dd662-199">O recurso de diagnóstico da infraestrutura do WCF registra em log as mensagens que passam por meio de transporte e camadas do modelo de serviço e as atividades e eventos associados a essas mensagens.</span><span class="sxs-lookup"><span data-stu-id="dd662-199">The diagnostics feature of the WCF infrastructure logs messages that pass through the transport and service model layers, and the activities and events associated with these messages.</span></span> <span data-ttu-id="dd662-200">Esse recurso é desativado por padrão.</span><span class="sxs-lookup"><span data-stu-id="dd662-200">This feature is turned off by default.</span></span> <span data-ttu-id="dd662-201">Ele é habilitado usando o arquivo de configuração do aplicativo e o comportamento de rastreamento pode ser modificado usando o provedor de WMI do WCF em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="dd662-201">It is enabled using the application’s configuration file and the tracing behavior may be modified using the WCF WMI provider at run time.</span></span> <span data-ttu-id="dd662-202">Quando habilitada, a infra-estrutura de rastreamento emite um rastreamento de diagnóstico que contém as mensagens, atividades e eventos de processamento para ouvintes configurados.</span><span class="sxs-lookup"><span data-stu-id="dd662-202">When enabled, the tracing infrastructure emits a diagnostic trace that contains messages, activities, and processing events to configured listeners.</span></span> <span data-ttu-id="dd662-203">O formato e o local de saída são determinados por opções de configuração de ouvinte do administrador, mas normalmente é um arquivo XML formatado.</span><span class="sxs-lookup"><span data-stu-id="dd662-203">The format and location of the output are determined by the administrator’s listener configuration choices, but is typically an XML formatted file.</span></span> <span data-ttu-id="dd662-204">O administrador é responsável por definir a lista de controle de acesso (ACL) nos arquivos de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="dd662-204">The administrator is responsible for setting the access control list (ACL) on the trace files.</span></span> <span data-ttu-id="dd662-205">Em particular, quando hospedado pelo sistema de ativação do Windows (WAS), o administrador deve se certificar que de arquivos não são servidos do diretório raiz virtual pública se não for desejado.</span><span class="sxs-lookup"><span data-stu-id="dd662-205">In particular, when hosted by Windows Activation System (WAS), the administrator should make sure the files are not served from the public virtual root directory if that is not desired.</span></span>  
  
 <span data-ttu-id="dd662-206">Há dois tipos de rastreamento: log de mensagens e o modelo de serviço de diagnóstico, rastreamento, descrito na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="dd662-206">There are two types of tracing: Message logging and Service Model diagnostic tracing, described in the following section.</span></span> <span data-ttu-id="dd662-207">Cada tipo é configurado por meio de sua própria origem de rastreamento: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> e <xref:System.ServiceModel>.</span><span class="sxs-lookup"><span data-stu-id="dd662-207">Each type is configured through its own trace source: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> and <xref:System.ServiceModel>.</span></span> <span data-ttu-id="dd662-208">Ambas essas fontes de rastreamento de registro em log capturam dados que são locais para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd662-208">Both of these logging trace sources capture data that is local to the application.</span></span>  
  
### <a name="message-logging"></a><span data-ttu-id="dd662-209">Registro em log de mensagens</span><span class="sxs-lookup"><span data-stu-id="dd662-209">Message Logging</span></span>  
 <span data-ttu-id="dd662-210">A mensagem de log de origem de rastreamento (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) permite que um administrador registrar em log as mensagens desse fluxo por meio do sistema.</span><span class="sxs-lookup"><span data-stu-id="dd662-210">The message logging trace source (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) allows an administrator to log the messages that flow through the system.</span></span> <span data-ttu-id="dd662-211">Por meio da configuração, o usuário pode decidir registrar mensagens inteiras ou somente os cabeçalhos de mensagem, se é preciso registrar nas camadas de modelo de transporte e/ou serviço e se é necessário incluir mensagens malformadas.</span><span class="sxs-lookup"><span data-stu-id="dd662-211">Through configuration, the user may decide to log entire messages or message headers only, whether to log at the transport and/or service model layers, and whether to include malformed messages.</span></span> <span data-ttu-id="dd662-212">Além disso, o usuário pode configurar a filtragem para restringir quais mensagens são registradas.</span><span class="sxs-lookup"><span data-stu-id="dd662-212">Also, the user may configure filtering to restrict which messages are logged.</span></span>  
  
 <span data-ttu-id="dd662-213">Por padrão, o log de mensagens está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="dd662-213">By default, message logging is disabled.</span></span> <span data-ttu-id="dd662-214">O administrador do computador local pode impedir que o administrador de nível de aplicativo transformar a mensagem de logon.</span><span class="sxs-lookup"><span data-stu-id="dd662-214">The local machine administrator can prevent the application-level administrator from turning message logging on.</span></span>  
  
#### <a name="encrypted-and-decrypted-message-logging"></a><span data-ttu-id="dd662-215">Registro de mensagem criptografada e descriptografada</span><span class="sxs-lookup"><span data-stu-id="dd662-215">Encrypted and Decrypted Message Logging</span></span>  
 <span data-ttu-id="dd662-216">Mensagens são registradas, criptografadas ou descriptografadas, conforme descrito nos seguintes termos.</span><span class="sxs-lookup"><span data-stu-id="dd662-216">Messages are logged, encrypted, or decrypted, as described in the following terms.</span></span>  
  
 <span data-ttu-id="dd662-217">Registro de transporte</span><span class="sxs-lookup"><span data-stu-id="dd662-217">Transport Logging</span></span>  
 <span data-ttu-id="dd662-218">Registra mensagens recebidas e enviadas no nível do transporte.</span><span class="sxs-lookup"><span data-stu-id="dd662-218">Logs messages received and sent at the transport level.</span></span> <span data-ttu-id="dd662-219">Essas mensagens contêm todos os cabeçalhos e podem ser criptografadas antes de serem enviados durante a transmissão e ao que está sendo recebido.</span><span class="sxs-lookup"><span data-stu-id="dd662-219">These messages contain all headers, and may be encrypted before being sent on the wire and when being received.</span></span>  
  
 <span data-ttu-id="dd662-220">Se as mensagens são criptografadas antes de serem enviados durante a transmissão e quando elas são recebidas, elas são registradas criptografados também.</span><span class="sxs-lookup"><span data-stu-id="dd662-220">If messages are encrypted before being sent on the wire and when they are received, they are logged encrypted as well.</span></span> <span data-ttu-id="dd662-221">Uma exceção é quando um protocolo de segurança é usado (https): estiverem conectados, em seguida, descriptografados antes de serem enviados e depois que está sendo recebido mesmo se eles são criptografados durante a transmissão.</span><span class="sxs-lookup"><span data-stu-id="dd662-221">An exception is when a security protocol is used (https): they are then logged decrypted before being sent and after being received even if they are encrypted on the wire.</span></span>  
  
 <span data-ttu-id="dd662-222">Log de serviço</span><span class="sxs-lookup"><span data-stu-id="dd662-222">Service Logging</span></span>  
 <span data-ttu-id="dd662-223">Registra mensagens recebidas ou enviadas no nível do modelo de serviço, após a realização processamento do cabeçalho de canal, pouco antes e depois de inserir o código do usuário.</span><span class="sxs-lookup"><span data-stu-id="dd662-223">Logs messages received or sent at the service model level, after channel header processing has occurred, just before and after entering user code.</span></span>  
  
 <span data-ttu-id="dd662-224">As mensagens registradas nesse nível são descriptografadas, mesmo se elas foram protegidas e criptografadas durante a transmissão.</span><span class="sxs-lookup"><span data-stu-id="dd662-224">Messages logged at this level are decrypted even if they were secured and encrypted on the wire.</span></span>  
  
 <span data-ttu-id="dd662-225">Registro em log de mensagem malformada</span><span class="sxs-lookup"><span data-stu-id="dd662-225">Malformed Message Logging</span></span>  
 <span data-ttu-id="dd662-226">Registra mensagens que a infraestrutura do WCF não é possível entender ou processar.</span><span class="sxs-lookup"><span data-stu-id="dd662-226">Logs messages that the WCF infrastructure cannot understand or process.</span></span>  
  
 <span data-ttu-id="dd662-227">As mensagens são registradas como-está, ou seja, criptografado ou não</span><span class="sxs-lookup"><span data-stu-id="dd662-227">Messages are logged as-is, that is, encrypted or not</span></span>  
  
 <span data-ttu-id="dd662-228">Quando mensagens são registradas no formulário não criptografado ou descriptografado, por padrão, o WCF remove as chaves de segurança e potencialmente informações pessoais das mensagens de antes de registrá-los.</span><span class="sxs-lookup"><span data-stu-id="dd662-228">When messages are logged in decrypted or unencrypted form, by default WCF removes security keys and potentially personal information from the messages before logging them.</span></span> <span data-ttu-id="dd662-229">As seções a seguir descrevem quais informações são removidas e quando.</span><span class="sxs-lookup"><span data-stu-id="dd662-229">The next sections describe what information is removed, and when.</span></span> <span data-ttu-id="dd662-230">O administrador do computador e ambos implantador de aplicativo deve tomar determinadas ações de configuração para alterar o comportamento padrão para registrar em log as chaves e informações potencialmente particulares.</span><span class="sxs-lookup"><span data-stu-id="dd662-230">The machine administrator and application deployer must both take certain configuration actions to change the default behavior to log keys and potentially personal information.</span></span>  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="dd662-231">Informações removidas dos cabeçalhos de mensagem quando o registro em log mensagens/não criptografado descriptografado</span><span class="sxs-lookup"><span data-stu-id="dd662-231">Information Removed from Message Headers When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="dd662-232">Quando mensagens são registradas na forma descriptografada/sem criptografia, chaves de segurança e informações potencialmente particulares são removidos por padrão com base em cabeçalhos de mensagens e corpos de mensagens antes que elas são registradas.</span><span class="sxs-lookup"><span data-stu-id="dd662-232">When messages are logged in decrypted/unencrypted form, security keys and potentially personal information are removed by default from message headers and message bodies before they are logged.</span></span> <span data-ttu-id="dd662-233">A lista a seguir mostra o que o WCF considera as chaves e informações potencialmente particulares.</span><span class="sxs-lookup"><span data-stu-id="dd662-233">The following list shows what WCF considers keys and potentially personal information.</span></span>  
  
 <span data-ttu-id="dd662-234">Chaves são removidas:</span><span class="sxs-lookup"><span data-stu-id="dd662-234">Keys that are removed:</span></span>  
  
 <span data-ttu-id="dd662-235">\- Para xmlns:wst = "http://schemas.xmlsoap.org/ws/2004/04/trust" e xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust"</span><span class="sxs-lookup"><span data-stu-id="dd662-235">\- For xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"</span></span>  
  
 <span data-ttu-id="dd662-236">wst:BinarySecret</span><span class="sxs-lookup"><span data-stu-id="dd662-236">wst:BinarySecret</span></span>  
  
 <span data-ttu-id="dd662-237">wst:Entropy</span><span class="sxs-lookup"><span data-stu-id="dd662-237">wst:Entropy</span></span>  
  
 <span data-ttu-id="dd662-238">\- Para xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" e xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span><span class="sxs-lookup"><span data-stu-id="dd662-238">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="dd662-239">wsse:password</span><span class="sxs-lookup"><span data-stu-id="dd662-239">wsse:Password</span></span>  
  
 <span data-ttu-id="dd662-240">wsse:nonce</span><span class="sxs-lookup"><span data-stu-id="dd662-240">wsse:Nonce</span></span>  
  
 <span data-ttu-id="dd662-241">Informações potencialmente particulares que são removidas:</span><span class="sxs-lookup"><span data-stu-id="dd662-241">Potentially personal information that is removed:</span></span>  
  
 <span data-ttu-id="dd662-242">\- Para xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" e xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span><span class="sxs-lookup"><span data-stu-id="dd662-242">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="dd662-243">wsse:username</span><span class="sxs-lookup"><span data-stu-id="dd662-243">wsse:Username</span></span>  
  
 <span data-ttu-id="dd662-244">wsse:BinarySecurityToken</span><span class="sxs-lookup"><span data-stu-id="dd662-244">wsse:BinarySecurityToken</span></span>  
  
 <span data-ttu-id="dd662-245">\- Para xmlns:saml = "urn: oasis: nomes: tc: SAML:1.0:assertion" os itens em negrito (abaixo) serão removidos:</span><span class="sxs-lookup"><span data-stu-id="dd662-245">\- For xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion" the items in bold (below) are removed:</span></span>  
  
 <span data-ttu-id="dd662-246">\<Asserção</span><span class="sxs-lookup"><span data-stu-id="dd662-246">\<Assertion</span></span>  
  
 <span data-ttu-id="dd662-247">MajorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="dd662-247">MajorVersion="1"</span></span>  
  
 <span data-ttu-id="dd662-248">MinorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="dd662-248">MinorVersion="1"</span></span>  
  
 <span data-ttu-id="dd662-249">AssertionId="[ID]"</span><span class="sxs-lookup"><span data-stu-id="dd662-249">AssertionId="[ID]"</span></span>  
  
 <span data-ttu-id="dd662-250">Issuer="[string]"</span><span class="sxs-lookup"><span data-stu-id="dd662-250">Issuer="[string]"</span></span>  
  
 <span data-ttu-id="dd662-251">IssueInstant="[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="dd662-251">IssueInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="dd662-252">\<Condições NotBefore = "[data e hora]" NotOnOrAfter = "[data e hora]" ></span><span class="sxs-lookup"><span data-stu-id="dd662-252">\<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]"></span></span>  
  
 <span data-ttu-id="dd662-253">\<AudienceRestrictionCondition></span><span class="sxs-lookup"><span data-stu-id="dd662-253">\<AudienceRestrictionCondition></span></span>  
  
 <span data-ttu-id="dd662-254">\<Público-alvo > [uri]\</Audience > +</span><span class="sxs-lookup"><span data-stu-id="dd662-254">\<Audience>[uri]\</Audience>+</span></span>  
  
 <span data-ttu-id="dd662-255">\</AudienceRestrictionCondition>\*</span><span class="sxs-lookup"><span data-stu-id="dd662-255">\</AudienceRestrictionCondition>\*</span></span>  
  
 <span data-ttu-id="dd662-256">\<DoNotCacheCondition / > \*</span><span class="sxs-lookup"><span data-stu-id="dd662-256">\<DoNotCacheCondition />\*</span></span>  
  
 <span data-ttu-id="dd662-257"><\!– o tipo base abstrato</span><span class="sxs-lookup"><span data-stu-id="dd662-257"><\!-- abstract base type</span></span>  
  
 <span data-ttu-id="dd662-258">\<Condição / > \*</span><span class="sxs-lookup"><span data-stu-id="dd662-258">\<Condition />\*</span></span>  
  
 -->  
  
 <span data-ttu-id="dd662-259">\</ Condições >?</span><span class="sxs-lookup"><span data-stu-id="dd662-259">\</Conditions>?</span></span>  
  
 <span data-ttu-id="dd662-260">\<Conselhos ></span><span class="sxs-lookup"><span data-stu-id="dd662-260">\<Advice></span></span>  
  
 <span data-ttu-id="dd662-261">\<AssertionIDReference>[ID]\</AssertionIDReference>\*</span><span class="sxs-lookup"><span data-stu-id="dd662-261">\<AssertionIDReference>[ID]\</AssertionIDReference>\*</span></span>  
  
 <span data-ttu-id="dd662-262">\<Asserção > [asserção]\</Assertion > \*</span><span class="sxs-lookup"><span data-stu-id="dd662-262">\<Assertion>[assertion]\</Assertion>\*</span></span>  
  
 <span data-ttu-id="dd662-263">[qualquer] \*</span><span class="sxs-lookup"><span data-stu-id="dd662-263">[any]\*</span></span>  
  
 <span data-ttu-id="dd662-264">\</ Conselhos >?</span><span class="sxs-lookup"><span data-stu-id="dd662-264">\</Advice>?</span></span>  
  
 <span data-ttu-id="dd662-265"><\!– Tipos de base abstratos</span><span class="sxs-lookup"><span data-stu-id="dd662-265"><\!-- Abstract base types</span></span>  
  
 <span data-ttu-id="dd662-266">\<Instrução / > \*</span><span class="sxs-lookup"><span data-stu-id="dd662-266">\<Statement />\*</span></span>  
  
 <span data-ttu-id="dd662-267">\<SubjectStatement ></span><span class="sxs-lookup"><span data-stu-id="dd662-267">\<SubjectStatement></span></span>  
  
 <span data-ttu-id="dd662-268">\<Assunto ></span><span class="sxs-lookup"><span data-stu-id="dd662-268">\<Subject></span></span>  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 <span data-ttu-id="dd662-269">\<SubjectConfirmation></span><span class="sxs-lookup"><span data-stu-id="dd662-269">\<SubjectConfirmation></span></span>  
  
 <span data-ttu-id="dd662-270">\<ConfirmationMethod > [anyUri]\</ConfirmationMethod > +</span><span class="sxs-lookup"><span data-stu-id="dd662-270">\<ConfirmationMethod>[anyUri]\</ConfirmationMethod>+</span></span>  
  
 <span data-ttu-id="dd662-271">\<SubjectConfirmationData > [qualquer]\</SubjectConfirmationData >?</span><span class="sxs-lookup"><span data-stu-id="dd662-271">\<SubjectConfirmationData>[any]\</SubjectConfirmationData>?</span></span>  
  
 <span data-ttu-id="dd662-272">\<ds:KeyInfo>...\</ds:KeyInfo>?</span><span class="sxs-lookup"><span data-stu-id="dd662-272">\<ds:KeyInfo>...\</ds:KeyInfo>?</span></span>  
  
 <span data-ttu-id="dd662-273">\</SubjectConfirmation>?</span><span class="sxs-lookup"><span data-stu-id="dd662-273">\</SubjectConfirmation>?</span></span>  
  
 <span data-ttu-id="dd662-274">\</Subject></span><span class="sxs-lookup"><span data-stu-id="dd662-274">\</Subject></span></span>  
  
 <span data-ttu-id="dd662-275">\</ SubjectStatement > \*</span><span class="sxs-lookup"><span data-stu-id="dd662-275">\</SubjectStatement>\*</span></span>  
  
 -->  
  
 <span data-ttu-id="dd662-276">\<AuthenticationStatement</span><span class="sxs-lookup"><span data-stu-id="dd662-276">\<AuthenticationStatement</span></span>  
  
 <span data-ttu-id="dd662-277">AuthenticationMethod = "[uri]"</span><span class="sxs-lookup"><span data-stu-id="dd662-277">AuthenticationMethod="[uri]"</span></span>  
  
 <span data-ttu-id="dd662-278">AuthenticationInstant="[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="dd662-278">AuthenticationInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="dd662-279">[Assunto]</span><span class="sxs-lookup"><span data-stu-id="dd662-279">[Subject]</span></span>  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 <span data-ttu-id="dd662-280">< AuthorityBinding</span><span class="sxs-lookup"><span data-stu-id="dd662-280"><AuthorityBinding</span></span>  
  
 <span data-ttu-id="dd662-281">AuthorityKind="[QName]"</span><span class="sxs-lookup"><span data-stu-id="dd662-281">AuthorityKind="[QName]"</span></span>  
  
 <span data-ttu-id="dd662-282">Location="[uri]"</span><span class="sxs-lookup"><span data-stu-id="dd662-282">Location="[uri]"</span></span>  
  
 <span data-ttu-id="dd662-283">Binding="[uri]"</span><span class="sxs-lookup"><span data-stu-id="dd662-283">Binding="[uri]"</span></span>  
  
 />*  
  
 <span data-ttu-id="dd662-284">\</AuthenticationStatement>\*</span><span class="sxs-lookup"><span data-stu-id="dd662-284">\</AuthenticationStatement>\*</span></span>  
  
 <span data-ttu-id="dd662-285">\<AttributeStatement ></span><span class="sxs-lookup"><span data-stu-id="dd662-285">\<AttributeStatement></span></span>  
  
 <span data-ttu-id="dd662-286">[Assunto]</span><span class="sxs-lookup"><span data-stu-id="dd662-286">[Subject]</span></span>  
  
 <span data-ttu-id="dd662-287">\<Atributo</span><span class="sxs-lookup"><span data-stu-id="dd662-287">\<Attribute</span></span>  
  
 <span data-ttu-id="dd662-288">AttributeName="[string]"</span><span class="sxs-lookup"><span data-stu-id="dd662-288">AttributeName="[string]"</span></span>  
  
 <span data-ttu-id="dd662-289">AttributeNamespace="[uri]"</span><span class="sxs-lookup"><span data-stu-id="dd662-289">AttributeNamespace="[uri]"</span></span>  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 <span data-ttu-id="dd662-290">\</ Atributo > +</span><span class="sxs-lookup"><span data-stu-id="dd662-290">\</Attribute>+</span></span>  
  
 <span data-ttu-id="dd662-291">\</ AttributeStatement > \*</span><span class="sxs-lookup"><span data-stu-id="dd662-291">\</AttributeStatement>\*</span></span>  
  
 <span data-ttu-id="dd662-292">\<AuthorizationDecisionStatement</span><span class="sxs-lookup"><span data-stu-id="dd662-292">\<AuthorizationDecisionStatement</span></span>  
  
 <span data-ttu-id="dd662-293">Recurso = "[uri]"</span><span class="sxs-lookup"><span data-stu-id="dd662-293">Resource="[uri]"</span></span>  
  
 <span data-ttu-id="dd662-294">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span><span class="sxs-lookup"><span data-stu-id="dd662-294">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span></span>  
  
 >  
  
 <span data-ttu-id="dd662-295">[Assunto]</span><span class="sxs-lookup"><span data-stu-id="dd662-295">[Subject]</span></span>  
  
 <span data-ttu-id="dd662-296">\<Namespace de ação = "[uri]" > [string]\</Action > +</span><span class="sxs-lookup"><span data-stu-id="dd662-296">\<Action Namespace="[uri]">[string]\</Action>+</span></span>  
  
 <span data-ttu-id="dd662-297">\<Evidência ></span><span class="sxs-lookup"><span data-stu-id="dd662-297">\<Evidence></span></span>  
  
 <span data-ttu-id="dd662-298">\<AssertionIDReference>[ID]\</AssertionIDReference>+</span><span class="sxs-lookup"><span data-stu-id="dd662-298">\<AssertionIDReference>[ID]\</AssertionIDReference>+</span></span>  
  
 <span data-ttu-id="dd662-299">\<Asserção > [asserção]\</Assertion > +</span><span class="sxs-lookup"><span data-stu-id="dd662-299">\<Assertion>[assertion]\</Assertion>+</span></span>  
  
 <span data-ttu-id="dd662-300">\</ Evidência >?</span><span class="sxs-lookup"><span data-stu-id="dd662-300">\</Evidence>?</span></span>  
  
 <span data-ttu-id="dd662-301">\</AuthorizationDecisionStatement>\*</span><span class="sxs-lookup"><span data-stu-id="dd662-301">\</AuthorizationDecisionStatement>\*</span></span>  
  
 <span data-ttu-id="dd662-302">\</Assertion></span><span class="sxs-lookup"><span data-stu-id="dd662-302">\</Assertion></span></span>  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="dd662-303">Removido do corpos de mensagem quando o registro em log mensagens/não criptografado descriptografado de informações</span><span class="sxs-lookup"><span data-stu-id="dd662-303">Information Removed from Message Bodies When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="dd662-304">Conforme descrito anteriormente, WCF remove chaves e conhecidas informações potencialmente pessoais de cabeçalhos de mensagem para mensagens registradas/não criptografado descriptografado.</span><span class="sxs-lookup"><span data-stu-id="dd662-304">As previously described, WCF removes keys and known potentially personal information from message headers for logged decrypted/unencrypted messages.</span></span> <span data-ttu-id="dd662-305">Além disso, o WCF remove chaves e informações potencialmente particulares conhecidas de corpos de mensagem para os elementos do corpo e ações na lista a seguir, que descrevem as mensagens de segurança envolvidas na troca de chaves.</span><span class="sxs-lookup"><span data-stu-id="dd662-305">In addition, WCF removes keys and known potentially personal information from message bodies for the body elements and actions in the following list, which describe security messages involved in key exchange.</span></span>  
  
 <span data-ttu-id="dd662-306">Para os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="dd662-306">For the following namespaces:</span></span>  
  
 <span data-ttu-id="dd662-307">xmlns:WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" e xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust" (por exemplo, se nenhuma ação disponível)</span><span class="sxs-lookup"><span data-stu-id="dd662-307">xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust" (for example, if no action available)</span></span>  
  
 <span data-ttu-id="dd662-308">Informações são removidas para esses elementos de corpo, que envolvem a troca de chaves:</span><span class="sxs-lookup"><span data-stu-id="dd662-308">Information is removed for these body elements, which involve key exchange:</span></span>  
  
 <span data-ttu-id="dd662-309">wst:RequestSecurityToken</span><span class="sxs-lookup"><span data-stu-id="dd662-309">wst:RequestSecurityToken</span></span>  
  
 <span data-ttu-id="dd662-310">wst:RequestSecurityTokenResponse</span><span class="sxs-lookup"><span data-stu-id="dd662-310">wst:RequestSecurityTokenResponse</span></span>  
  
 <span data-ttu-id="dd662-311">wst:RequestSecurityTokenResponseCollection</span><span class="sxs-lookup"><span data-stu-id="dd662-311">wst:RequestSecurityTokenResponseCollection</span></span>  
  
 <span data-ttu-id="dd662-312">Informações também são removidas para cada uma das seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="dd662-312">Information is also removed for each of the following Actions:</span></span>  
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend`
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a><span data-ttu-id="dd662-313">Nenhuma informação é removida do cabeçalhos específicos de aplicativo e o corpo de dados</span><span class="sxs-lookup"><span data-stu-id="dd662-313">No Information Is Removed from Application-specific Headers and Body Data</span></span>  
 <span data-ttu-id="dd662-314">O WCF não rastreia informações pessoais em cabeçalhos específicos do aplicativo (por exemplo, cadeias de consulta) ou o corpo de dados (por exemplo, o número de cartão de crédito).</span><span class="sxs-lookup"><span data-stu-id="dd662-314">WCF does not track personal information in application-specific headers (for example, query strings) or body data (for example, credit card number).</span></span>  
  
 <span data-ttu-id="dd662-315">Quando o log de mensagens estiver ativada, informações pessoais em cabeçalhos específicos de aplicativo e informações do corpo podem ser visíveis nos logs.</span><span class="sxs-lookup"><span data-stu-id="dd662-315">When message logging is on, personal information in application-specific headers and body information may be visible in the logs.</span></span> <span data-ttu-id="dd662-316">Novamente, o implantador de aplicativo é responsável por definir as ACLs nos arquivos de configuração e de log.</span><span class="sxs-lookup"><span data-stu-id="dd662-316">Again, the application deployer is responsible for setting the ACLs on the configuration and log files.</span></span> <span data-ttu-id="dd662-317">Ele também pode desativar registro em log se ele não quer que essa informação fique visível, ou ele pode filtrar essas informações dos arquivos de log depois que ele é registrado.</span><span class="sxs-lookup"><span data-stu-id="dd662-317">He also can turn off logging if he does not want this information to be visible, or he may filter out this information from the log files after it is logged.</span></span>  
  
### <a name="service-model-tracing"></a><span data-ttu-id="dd662-318">Rastreamento de modelo de serviço</span><span class="sxs-lookup"><span data-stu-id="dd662-318">Service Model Tracing</span></span>  
 <span data-ttu-id="dd662-319">A origem de rastreamento do modelo de serviço (<xref:System.ServiceModel>) habilita o rastreamento de atividades e eventos relacionados ao processamento de mensagem.</span><span class="sxs-lookup"><span data-stu-id="dd662-319">The Service Model trace source (<xref:System.ServiceModel>) enables tracing of activities and events related to message processing.</span></span> <span data-ttu-id="dd662-320">Esse recurso usa a funcionalidade de diagnóstico do .NET Framework do <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="dd662-320">This feature uses the .NET Framework diagnostic functionality from <xref:System.Diagnostics>.</span></span> <span data-ttu-id="dd662-321">Assim como acontece com o <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> propriedade, o local e sua ACL são configuráveis pelo usuário usando arquivos de configuração de aplicativo do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dd662-321">As with the <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> property, the location and its ACL are user-configurable using .NET Framework application configuration files.</span></span> <span data-ttu-id="dd662-322">Assim como acontece com o log de mensagens, o local do arquivo é sempre configurado quando o administrador habilita o rastreamento; Portanto, o administrador controla a ACL.</span><span class="sxs-lookup"><span data-stu-id="dd662-322">As with message logging, the file location is always configured when the administrator enables tracing; thus, the administrator controls the ACL.</span></span>  
  
 <span data-ttu-id="dd662-323">Quando uma mensagem está no escopo os rastreamentos contêm cabeçalhos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="dd662-323">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="dd662-324">Aplicam as mesmas regras para ocultar informações potencialmente pessoais nos cabeçalhos de mensagem na seção anterior: as informações pessoais identificadas anteriormente foram removidas por padrão, dos cabeçalhos em rastreamentos.</span><span class="sxs-lookup"><span data-stu-id="dd662-324">The same rules for hiding potentially personal information in message headers in the previous section apply: the personal information previously identified is removed by default from the headers in traces.</span></span> <span data-ttu-id="dd662-325">O administrador da máquina e o implantador de aplicativo deverá modificar a configuração para registrar informações potencialmente particulares.</span><span class="sxs-lookup"><span data-stu-id="dd662-325">Both the machine administrator and the application deployer must modify the configuration in order to log potentially personal information.</span></span> <span data-ttu-id="dd662-326">No entanto, as informações pessoais contidas em cabeçalhos específicos de aplicativo são registradas em rastreamentos.</span><span class="sxs-lookup"><span data-stu-id="dd662-326">However, personal information contained in application-specific headers is logged in traces.</span></span> <span data-ttu-id="dd662-327">O implantador de aplicativo é responsável por definir as ACLs nos arquivos de configuração e o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="dd662-327">The application deployer is responsible for setting the ACLs on the configuration and trace files.</span></span> <span data-ttu-id="dd662-328">Ele também pode desativar o rastreamento se ele não quer que essa informação fique visível, ou ele pode filtrar essas informações dos arquivos de rastreamento depois que ele é registrado.</span><span class="sxs-lookup"><span data-stu-id="dd662-328">He also can turn off tracing if he does not want this information to be visible, or he can filter out this information from the trace files after it is logged.</span></span>  
  
 <span data-ttu-id="dd662-329">Como parte do rastreamento de ServiceModel, IDs exclusivas (chamado de IDs de atividade e, geralmente um GUID) vincular atividades diferentes juntos como uma mensagem flui por meio de diferentes partes da infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="dd662-329">As part of ServiceModel Tracing, Unique IDs (called Activity IDs, and typically a GUID) link different activities together as a message flows through different parts of the infrastructure.</span></span>  
  
#### <a name="custom-trace-listeners"></a><span data-ttu-id="dd662-330">Ouvintes de rastreamento personalizado</span><span class="sxs-lookup"><span data-stu-id="dd662-330">Custom Trace Listeners</span></span>  
 <span data-ttu-id="dd662-331">Para ambas as mensagens de log e rastreamento, um ouvinte de rastreamento personalizado pode ser configurado, o que pode enviar mensagens e rastreamentos durante a transmissão (por exemplo, para um banco de dados remoto).</span><span class="sxs-lookup"><span data-stu-id="dd662-331">For both message logging and tracing, a custom trace listener can be configured, which can send traces and messages on the wire (for example, to a remote database).</span></span> <span data-ttu-id="dd662-332">O implantador de aplicativo é responsável por configurar ouvintes personalizados ou permitindo que os usuários fazer isso.</span><span class="sxs-lookup"><span data-stu-id="dd662-332">The application deployer is responsible for configuring custom listeners or enabling users to do so.</span></span> <span data-ttu-id="dd662-333">Ele também é responsável por quaisquer informações pessoais exposto no local remoto e corretamente aplicando as ACLs para este local.</span><span class="sxs-lookup"><span data-stu-id="dd662-333">He is also responsible for any personal information exposed at the remote location, and for properly applying ACLs to this location.</span></span>  
  
### <a name="other-features-for-it-professionals"></a><span data-ttu-id="dd662-334">Outros recursos para profissionais de TI</span><span class="sxs-lookup"><span data-stu-id="dd662-334">Other features for IT Professionals</span></span>  
 <span data-ttu-id="dd662-335">O WCF possui um provedor WMI que expõe as informações de configuração de infraestrutura do WCF por meio do WMI (fornecido com o Windows).</span><span class="sxs-lookup"><span data-stu-id="dd662-335">WCF has a WMI provider that exposes the WCF infrastructure configuration information through WMI (shipped with Windows).</span></span> <span data-ttu-id="dd662-336">Por padrão, a interface WMI está disponível para administradores.</span><span class="sxs-lookup"><span data-stu-id="dd662-336">By default, the WMI interface is available to administrators.</span></span>  
  
 <span data-ttu-id="dd662-337">Configuração do WCF usa o mecanismo de configuração do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dd662-337">WCF configuration uses the .NET Framework configuration mechanism.</span></span> <span data-ttu-id="dd662-338">Os arquivos de configuração são armazenados no computador.</span><span class="sxs-lookup"><span data-stu-id="dd662-338">The configuration files are stored on the machine.</span></span> <span data-ttu-id="dd662-339">O desenvolvedor do aplicativo e o administrador criam os arquivos de configuração e a ACL para cada um dos requisitos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd662-339">The application developer and the administrator create the configuration files and ACL for each of the application's requirements.</span></span> <span data-ttu-id="dd662-340">Um arquivo de configuração pode conter endereços de ponto de extremidade e links para os certificados no repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="dd662-340">A configuration file can contain endpoint addresses and links to certificates in the certificate store.</span></span> <span data-ttu-id="dd662-341">Os certificados podem ser usados para fornecer dados de aplicativo para configurar várias propriedades dos recursos usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd662-341">The certificates can be used to provide application data to configure various properties of the features used by the application.</span></span>  
  
 <span data-ttu-id="dd662-342">O WCF também usa a funcionalidade de despejo de processo do .NET Framework ao chamar o <xref:System.Environment.FailFast%2A> método.</span><span class="sxs-lookup"><span data-stu-id="dd662-342">WCF also uses the .NET Framework process dump functionality by calling the <xref:System.Environment.FailFast%2A> method.</span></span>  
  
### <a name="it-pro-tools"></a><span data-ttu-id="dd662-343">IT Pro ferramentas</span><span class="sxs-lookup"><span data-stu-id="dd662-343">IT Pro Tools</span></span>  
 <span data-ttu-id="dd662-344">O WCF também fornece as seguintes IT professional ferramentas, fornecidos no SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="dd662-344">WCF also provides the following IT professional tools, which ship in the Windows SDK.</span></span>  
  
#### <a name="svctraceviewerexe"></a><span data-ttu-id="dd662-345">SvcTraceViewer.exe</span><span class="sxs-lookup"><span data-stu-id="dd662-345">SvcTraceViewer.exe</span></span>  
 <span data-ttu-id="dd662-346">O visualizador exibe os arquivos de rastreamento do WCF.</span><span class="sxs-lookup"><span data-stu-id="dd662-346">The viewer displays WCF trace files.</span></span> <span data-ttu-id="dd662-347">O visualizador mostra o texto que está contido nos rastreamentos.</span><span class="sxs-lookup"><span data-stu-id="dd662-347">The viewer shows whatever information is contained in the traces.</span></span>  
  
#### <a name="svcconfigeditorexe"></a><span data-ttu-id="dd662-348">SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="dd662-348">SvcConfigEditor.exe</span></span>  
 <span data-ttu-id="dd662-349">O editor permite que o usuário criar e editar arquivos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="dd662-349">The editor allows the user to create and edit WCF configuration files.</span></span> <span data-ttu-id="dd662-350">O editor mostra o texto que está contido nos arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="dd662-350">The editor shows whatever information is contained in the configuration files.</span></span> <span data-ttu-id="dd662-351">A mesma tarefa pode ser feita com um editor de texto.</span><span class="sxs-lookup"><span data-stu-id="dd662-351">The same task can be accomplished with a text editor.</span></span>  
  
#### <a name="servicemodelreg"></a><span data-ttu-id="dd662-352">ServiceModel_Reg</span><span class="sxs-lookup"><span data-stu-id="dd662-352">ServiceModel_Reg</span></span>  
 <span data-ttu-id="dd662-353">Essa ferramenta permite que o usuário gerencie ServiceModel instala em um computador.</span><span class="sxs-lookup"><span data-stu-id="dd662-353">This tool allows the user to manage ServiceModel installs on a machine.</span></span> <span data-ttu-id="dd662-354">A ferramenta exibe mensagens de status na janela do console quando ele é executado e, no processo, poderá exibir informações sobre a configuração da instalação do WCF.</span><span class="sxs-lookup"><span data-stu-id="dd662-354">The tool displays status messages in a console window when it runs and, in the process, may display information about the configuration of the WCF installation.</span></span>  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a><span data-ttu-id="dd662-355">WSATConfig.exe e WSATUI.dll</span><span class="sxs-lookup"><span data-stu-id="dd662-355">WSATConfig.exe and WSATUI.dll</span></span>  
 <span data-ttu-id="dd662-356">Essas ferramentas permitem que os profissionais de TI configurar o suporte de rede de WS-AtomicTransaction interoperável no WCF.</span><span class="sxs-lookup"><span data-stu-id="dd662-356">These tools allow IT Professionals to configure interoperable WS-AtomicTransaction network support in WCF.</span></span> <span data-ttu-id="dd662-357">As ferramentas de exibam e permitir que o usuário altere os valores das configurações de WS-AtomicTransaction mais comumente usadas, armazenadas no registro.</span><span class="sxs-lookup"><span data-stu-id="dd662-357">The tools display and allow the user to change the values of the most commonly used WS-AtomicTransaction settings stored in the registry.</span></span>  
  
## <a name="cross-cutting-features"></a><span data-ttu-id="dd662-358">Recursos abrangentes</span><span class="sxs-lookup"><span data-stu-id="dd662-358">Cross-cutting Features</span></span>  
 <span data-ttu-id="dd662-359">Os seguintes recursos são abrangentes.</span><span class="sxs-lookup"><span data-stu-id="dd662-359">The following features are cross-cutting.</span></span> <span data-ttu-id="dd662-360">Ou seja, eles podem ser compostos com qualquer um dos recursos anteriores.</span><span class="sxs-lookup"><span data-stu-id="dd662-360">That is, they can be composed with any of the preceding features.</span></span>  
  
### <a name="service-framework"></a><span data-ttu-id="dd662-361">Estrutura de serviço</span><span class="sxs-lookup"><span data-stu-id="dd662-361">Service Framework</span></span>  
 <span data-ttu-id="dd662-362">Cabeçalhos podem conter uma ID de instância, que é um GUID que associa uma mensagem uma instância de uma classe CLR.</span><span class="sxs-lookup"><span data-stu-id="dd662-362">Headers can contain an instance ID, which is a GUID that associates a message with an instance of a CLR class.</span></span>  
  
 <span data-ttu-id="dd662-363">A descrição de linguagem WSDL (Web Services) contém uma definição da porta.</span><span class="sxs-lookup"><span data-stu-id="dd662-363">The Web Services Description Language (WSDL) contains a definition of the port.</span></span> <span data-ttu-id="dd662-364">Cada porta tem um endereço de ponto de extremidade e uma associação que representa os serviços usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd662-364">Each port has an endpoint address and a binding that represents the services used by the application.</span></span> <span data-ttu-id="dd662-365">Expondo a WSDL pode ser desativado usando a configuração.</span><span class="sxs-lookup"><span data-stu-id="dd662-365">Exposing WSDL can be turned off using configuration.</span></span> <span data-ttu-id="dd662-366">Nenhuma informação é mantida no computador.</span><span class="sxs-lookup"><span data-stu-id="dd662-366">No information is retained on the machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd662-367">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd662-367">See Also</span></span>  
 [<span data-ttu-id="dd662-368">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="dd662-368">Windows Communication Foundation</span></span>](https://msdn.microsoft.com/library/fd327ade-0260-4c40-adbe-b74645ba3277)  
 [<span data-ttu-id="dd662-369">Segurança</span><span class="sxs-lookup"><span data-stu-id="dd662-369">Security</span></span>](../../../docs/framework/wcf/feature-details/security.md)
