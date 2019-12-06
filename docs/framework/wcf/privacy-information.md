---
title: Informações de privacidade do Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: c5500b8fd8b35081e83e2e9279dc4f236ef3c7b0
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837929"
---
# <a name="windows-communication-foundation-privacy-information"></a><span data-ttu-id="fa8f0-102">Informações de privacidade do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="fa8f0-102">Windows Communication Foundation Privacy Information</span></span>
<span data-ttu-id="fa8f0-103">A Microsoft está comprometida em proteger a privacidade dos usuários finais.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-103">Microsoft is committed to protecting end-users' privacy.</span></span> <span data-ttu-id="fa8f0-104">Quando você cria um aplicativo usando Windows Communication Foundation (WCF), versão 3,0, seu aplicativo pode afetar a privacidade dos usuários finais.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-104">When you build an application using Windows Communication Foundation (WCF), version 3.0, your application may impact your end-users' privacy.</span></span> <span data-ttu-id="fa8f0-105">Por exemplo, seu aplicativo pode coletar explicitamente as informações de contato do usuário ou pode solicitar ou enviar informações pela Internet para seu site.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-105">For example, your application may explicitly collect user contact information, or it may request or send information over the Internet to your Web site.</span></span> <span data-ttu-id="fa8f0-106">Se você inserir a tecnologia da Microsoft em seu aplicativo, essa tecnologia poderá ter seu próprio comportamento que pode afetar a privacidade.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-106">If you embed Microsoft technology in your application, that technology may have its own behavior that might affect privacy.</span></span> <span data-ttu-id="fa8f0-107">O WCF não envia nenhuma informação à Microsoft do seu aplicativo, a menos que você ou o usuário final opte por enviá-lo para nós.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-107">WCF does not send any information to Microsoft from your application unless you or the end-user choose to send it to us.</span></span>  
  
## <a name="wcf-in-brief"></a><span data-ttu-id="fa8f0-108">WCF em resumo</span><span class="sxs-lookup"><span data-stu-id="fa8f0-108">WCF in Brief</span></span>  
 <span data-ttu-id="fa8f0-109">O WCF é uma estrutura de mensagens distribuídas usando o Microsoft .NET Framework que permite aos desenvolvedores criar aplicativos distribuídos.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-109">WCF is a distributed messaging framework using the Microsoft .NET Framework that allows developers to build distributed applications.</span></span> <span data-ttu-id="fa8f0-110">As mensagens comunicadas entre dois aplicativos contêm informações de cabeçalho e corpo.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-110">Messages communicated between two applications contain header and body information.</span></span>  
  
 <span data-ttu-id="fa8f0-111">Os cabeçalhos podem conter roteamento de mensagens, informações de segurança, transações e muito mais, dependendo dos serviços usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-111">Headers may contain message routing, security information, transactions, and more depending on the services used by the application.</span></span> <span data-ttu-id="fa8f0-112">Normalmente, as mensagens são criptografadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-112">Messages are typically encrypted by default.</span></span> <span data-ttu-id="fa8f0-113">A única exceção é ao usar o `BasicHttpBinding`, que foi projetado para uso com serviços Web herdados e não protegidos.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-113">The one exception is when using the `BasicHttpBinding`, which was designed for use with non-secured, legacy Web services.</span></span> <span data-ttu-id="fa8f0-114">Como o designer de aplicativos, você é responsável pelo design final.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-114">As the application designer, you are responsible for the final design.</span></span> <span data-ttu-id="fa8f0-115">As mensagens no corpo SOAP contêm dados específicos do aplicativo; no entanto, esses dados, como informações pessoais definidas pelo aplicativo, podem ser protegidos usando recursos de confidencialidade ou criptografia do WCF.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-115">Messages in the SOAP body contain application-specific data; however, this data, such as application-defined personal information, can be secured by using WCF encryption or confidentiality features.</span></span> <span data-ttu-id="fa8f0-116">As seções a seguir descrevem os recursos que potencialmente afetam a privacidade.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-116">The following sections describe the features that potentially impact privacy.</span></span>  
  
## <a name="messaging"></a><span data-ttu-id="fa8f0-117">Mensagens</span><span class="sxs-lookup"><span data-stu-id="fa8f0-117">Messaging</span></span>  
 <span data-ttu-id="fa8f0-118">Cada mensagem do WCF tem um cabeçalho de endereço que especifica o destino da mensagem e onde a resposta deve ir.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-118">Each WCF message has an address header that specifies the message destination and where the reply should go.</span></span>  
  
 <span data-ttu-id="fa8f0-119">O componente de endereço de um endereço de ponto de extremidade é um Uniform Resource Identifier (URI) que identifica o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-119">The address component of an endpoint address is a Uniform Resource Identifier (URI) that identifies the endpoint.</span></span> <span data-ttu-id="fa8f0-120">O endereço pode ser um endereço de rede ou um endereço lógico.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-120">The address can be a network address or a logical address.</span></span> <span data-ttu-id="fa8f0-121">O endereço pode incluir o nome do computador (hostname, nome de domínio totalmente qualificado) e um endereço IP.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-121">The address may include machine name (hostname, fully qualified domain name) and an IP address.</span></span> <span data-ttu-id="fa8f0-122">O endereço do ponto de extremidade também pode conter um GUID (identificador global exclusivo) ou uma coleção de GUIDs para endereçamento temporário usado para discernir cada endereço.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-122">The endpoint address may also contain a globally unique identifier (GUID), or a collection of GUIDs for temporary addressing used to discern each address.</span></span> <span data-ttu-id="fa8f0-123">Cada mensagem contém uma ID de mensagem que é um GUID.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-123">Each message contains a message ID that is a GUID.</span></span> <span data-ttu-id="fa8f0-124">Esse recurso segue o padrão de referência do WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-124">This feature follows the WS-Addressing reference standard.</span></span>  
  
 <span data-ttu-id="fa8f0-125">A camada de mensagens do WCF não grava nenhuma informação pessoal no computador local.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-125">The WCF messaging layer does not write any personal information to the local machine.</span></span> <span data-ttu-id="fa8f0-126">No entanto, ele poderá propagar informações pessoais no nível da rede se um desenvolvedor de serviço tiver criado um serviço que expõe essas informações (por exemplo, usando o nome de uma pessoa em um nome de ponto de extremidade ou incluindo informações pessoais na Web do ponto de extremidade Linguagem de descrição de serviços, mas não requer que os clientes usem HTTPS para acessar o WSDL).</span><span class="sxs-lookup"><span data-stu-id="fa8f0-126">However, it might propagate personal information at the network level if a service developer has created a service that exposes such information (for example, by using a person's name in an endpoint name, or including personal information in the endpoint's Web Services Description Language but not requiring clients to use https to access the WSDL).</span></span> <span data-ttu-id="fa8f0-127">Além disso, se um desenvolvedor executar a ferramenta de [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) em um ponto de extremidade que expõe informações pessoais, a saída da ferramenta poderá conter essas informações e o arquivo de saída será gravado no disco rígido local.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-127">Also, if a developer runs the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) tool against an endpoint that exposes personal information, the tool's output could contain that information, and the output file is written to the local hard disk.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="fa8f0-128">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="fa8f0-128">Hosting</span></span>  
 <span data-ttu-id="fa8f0-129">O recurso de hospedagem no WCF permite que os aplicativos iniciem sob demanda ou habilitem o compartilhamento de porta entre vários aplicativos.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-129">The hosting feature in WCF allows applications to start on demand or to enable port sharing between multiple applications.</span></span> <span data-ttu-id="fa8f0-130">Um aplicativo WCF pode ser hospedado em Serviços de Informações da Internet (IIS), semelhante ao ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-130">An WCF application can be hosted in Internet Information Services (IIS), similar to ASP.NET.</span></span>  
  
 <span data-ttu-id="fa8f0-131">A hospedagem não expõe nenhuma informação específica na rede e não mantém os dados no computador.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-131">Hosting does not expose any specific information on the network and it does not keep data on the machine.</span></span>  
  
## <a name="message-security"></a><span data-ttu-id="fa8f0-132">Segurança de mensagem</span><span class="sxs-lookup"><span data-stu-id="fa8f0-132">Message Security</span></span>  
 <span data-ttu-id="fa8f0-133">A segurança do WCF fornece os recursos de segurança para aplicativos de mensagens.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-133">WCF security provides the security capabilities for messaging applications.</span></span> <span data-ttu-id="fa8f0-134">As funções de segurança fornecidas incluem autenticação e autorização.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-134">The security functions provided include authentication and authorization.</span></span>  
  
 <span data-ttu-id="fa8f0-135">A autenticação é realizada passando credenciais entre os clientes e os serviços.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-135">Authentication is performed by passing credentials between the clients and services.</span></span> <span data-ttu-id="fa8f0-136">A autenticação pode ser por meio de segurança em nível de transporte ou por meio de segurança em nível de mensagem SOAP, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="fa8f0-136">Authentication can be either through transport-level security or through SOAP message-level security, as follows:</span></span>  
  
- <span data-ttu-id="fa8f0-137">Na segurança de mensagem SOAP, a autenticação é executada por meio de credenciais como nome de usuário/senhas, certificados X. 509, tíquetes Kerberos e tokens SAML, que podem conter informações pessoais, dependendo do emissor.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-137">In SOAP message security, authentication is performed through credentials like username/passwords, X.509 certificates, Kerberos tickets, and SAML tokens, all of which might contain personal information, depending on the issuer.</span></span>  
  
- <span data-ttu-id="fa8f0-138">Usando a segurança de transporte, a autenticação é feita por meio de mecanismos de autenticação de transporte tradicionais, como esquemas de autenticação HTTP (básico, Digest, negociação, autorização integrada do Windows, NTLM, nenhum e anônimo) e autenticação de formulário.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-138">Using transport security, authentication is done through traditional transport authentication mechanisms like HTTP authentication schemes (Basic, Digest, Negotiate, Integrated Windows Authorization, NTLM, None, and Anonymous), and form authentication.</span></span>  
  
 <span data-ttu-id="fa8f0-139">A autenticação pode resultar em uma sessão segura estabelecida entre os pontos de extremidade de comunicação.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-139">Authentication can result in a secure session established between the communicating endpoints.</span></span> <span data-ttu-id="fa8f0-140">A sessão é identificada por um GUID que dura o tempo de vida da sessão de segurança.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-140">The session is identified by a GUID that lasts the lifetime of the security session.</span></span> <span data-ttu-id="fa8f0-141">A tabela a seguir mostra o que é mantido e onde.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-141">The following table shows what is kept and where.</span></span>  
  
|<span data-ttu-id="fa8f0-142">Dados</span><span class="sxs-lookup"><span data-stu-id="fa8f0-142">Data</span></span>|<span data-ttu-id="fa8f0-143">Armazenamento</span><span class="sxs-lookup"><span data-stu-id="fa8f0-143">Storage</span></span>|  
|----------|-------------|  
|<span data-ttu-id="fa8f0-144">As credenciais de apresentação, como nome de usuário, certificados X. 509, tokens Kerberos e referências a credenciais.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-144">Presentation credentials, such as username, X.509 certificates, Kerberos tokens, and references to credentials.</span></span>|<span data-ttu-id="fa8f0-145">Mecanismos padrão de gerenciamento de credenciais do Windows, como o repositório de certificados do Windows.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-145">Standard Windows credential management mechanisms such as the Windows certificate store.</span></span>|  
|<span data-ttu-id="fa8f0-146">Informações de associação de usuários, como nomes de usuário e senhas.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-146">User membership information, such as usernames and passwords.</span></span>|<span data-ttu-id="fa8f0-147">Provedores de associação do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-147">ASP.NET membership providers.</span></span>|  
|<span data-ttu-id="fa8f0-148">Informações de identidade sobre o serviço usado para autenticar o serviço para clientes.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-148">Identity information about the service used to authenticate the service to clients.</span></span>|<span data-ttu-id="fa8f0-149">Endereço do ponto de extremidade do serviço.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-149">Endpoint address of the service.</span></span>|  
|<span data-ttu-id="fa8f0-150">Informações do chamador.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-150">Caller information.</span></span>|<span data-ttu-id="fa8f0-151">Logs de auditoria.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-151">Auditing logs.</span></span>|  
  
## <a name="auditing"></a><span data-ttu-id="fa8f0-152">Auditoria do</span><span class="sxs-lookup"><span data-stu-id="fa8f0-152">Auditing</span></span>  
 <span data-ttu-id="fa8f0-153">A auditoria registra o êxito e a falha de eventos de autenticação e autorização.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-153">Auditing records the success and failure of authentication and authorization events.</span></span> <span data-ttu-id="fa8f0-154">Os registros de auditoria contêm os seguintes dados: URI de serviço, URI de ação e identificação do chamador.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-154">Auditing records contain the following data: service URI, action URI, and the caller's identification.</span></span>  
  
 <span data-ttu-id="fa8f0-155">A auditoria também registra quando o administrador modifica a configuração do log de mensagens (ativando ou desligando), pois o log de mensagens pode registrar dados específicos do aplicativo em cabeçalhos e corpos.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-155">Auditing also records when the administrator modifies the configuration of message logging (turning it on or off), because message logging may log application-specific data in headers and bodies.</span></span> <span data-ttu-id="fa8f0-156">Por [!INCLUDE[wxp](../../../includes/wxp-md.md)], um registro é registrado no log de eventos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-156">For [!INCLUDE[wxp](../../../includes/wxp-md.md)], a record is logged in the application event log.</span></span> <span data-ttu-id="fa8f0-157">Para o Windows Vista e o [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], um registro é registrado no log de eventos de segurança.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-157">For Windows Vista and [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], a record is logged in the security event log.</span></span>  
  
## <a name="transactions"></a><span data-ttu-id="fa8f0-158">Transações</span><span class="sxs-lookup"><span data-stu-id="fa8f0-158">Transactions</span></span>  
 <span data-ttu-id="fa8f0-159">O recurso de transações fornece serviços transacionais para um aplicativo WCF.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-159">The transactions feature provides transactional services to a WCF application.</span></span>  
  
 <span data-ttu-id="fa8f0-160">Os cabeçalhos de transação usados na propagação da transação podem conter IDs de transação ou IDs de inscrição, que são GUIDs.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-160">Transaction headers used in transaction propagation may contain Transaction IDs or Enlistment IDs, which are GUIDs.</span></span>  
  
 <span data-ttu-id="fa8f0-161">O recurso de transações usa o Gerenciador de transações do Microsoft Coordenador de Transações Distribuídas (MSDTC) (um componente do Windows) para gerenciar o estado da transação.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-161">The Transactions feature uses the Microsoft Distributed Transaction Coordinator (MSDTC) Transaction Manager (a Windows component) to manage transaction state.</span></span> <span data-ttu-id="fa8f0-162">Por padrão, as comunicações entre os gerenciadores de transações são criptografadas.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-162">By default, communications between Transactions Managers are encrypted.</span></span> <span data-ttu-id="fa8f0-163">Os gerenciadores de transações podem registrar referências de ponto de extremidade, IDs de transação e IDs de inscrição como parte de seu estado durável.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-163">Transaction Managers may log endpoint references, Transaction IDs, and Enlistment IDs as part of their durable state.</span></span> <span data-ttu-id="fa8f0-164">O tempo de vida desse Estado é determinado pelo tempo de vida do arquivo de log do Gerenciador de transações.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-164">The lifetime of this state is determined by the lifetime of the Transaction Manager’s log file.</span></span> <span data-ttu-id="fa8f0-165">O serviço MSDTC possui e mantém esse log.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-165">The MSDTC service owns and maintains this log.</span></span>  
  
 <span data-ttu-id="fa8f0-166">O recurso de transações implementa os padrões de transação WS-Coordination e WS-Atomic.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-166">The Transactions feature implements the WS-Coordination and WS-Atomic Transaction standards.</span></span>  
  
## <a name="reliable-sessions"></a><span data-ttu-id="fa8f0-167">Sessões confiáveis</span><span class="sxs-lookup"><span data-stu-id="fa8f0-167">Reliable Sessions</span></span>  
 <span data-ttu-id="fa8f0-168">As sessões confiáveis no WCF fornecem a transferência de mensagens quando ocorrem falhas de transporte ou intermediárias.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-168">Reliable sessions in WCF provide the transfer of messages when transport or intermediary failures occur.</span></span> <span data-ttu-id="fa8f0-169">Eles fornecem uma transferência de mensagens exatamente uma vez, mesmo quando o transporte subjacente se desconecta (por exemplo, uma conexão TCP em uma rede sem fio) ou perde uma mensagem (um proxy HTTP descartando uma mensagem de saída ou de entrada).</span><span class="sxs-lookup"><span data-stu-id="fa8f0-169">They provide an exactly-once transfer of messages even when the underlying transport disconnects (for example, a TCP connection on a wireless network) or loses a message (an HTTP proxy dropping an outgoing or incoming message).</span></span> <span data-ttu-id="fa8f0-170">As sessões confiáveis também recuperam a reordenação de mensagens (como pode acontecer no caso de roteamento de vários caminhos), preservando a ordem na qual as mensagens foram enviadas.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-170">Reliable sessions also recover message reordering (as may happen in the case of multipath routing), preserving the order in which the messages were sent.</span></span>  
  
 <span data-ttu-id="fa8f0-171">As sessões confiáveis são implementadas usando o protocolo WS-ReliableMessaging (WS-RM).</span><span class="sxs-lookup"><span data-stu-id="fa8f0-171">Reliable sessions are implemented using the WS-ReliableMessaging (WS-RM) protocol.</span></span> <span data-ttu-id="fa8f0-172">Eles adicionam cabeçalhos WS-RM que contêm informações de sessão, que são usadas para identificar todas as mensagens associadas a uma sessão confiável específica.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-172">They add WS-RM headers that contain session information, which is used to identify all messages associated with a particular reliable session.</span></span> <span data-ttu-id="fa8f0-173">Cada sessão WS-RM tem um identificador, que é um GUID.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-173">Each WS-RM session has an identifier, which is a GUID.</span></span>  
  
 <span data-ttu-id="fa8f0-174">Nenhuma informação pessoal é mantida no computador do usuário final.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-174">No personal information is retained on the end-user's machine.</span></span>  
  
## <a name="queued-channels"></a><span data-ttu-id="fa8f0-175">Canais em fila</span><span class="sxs-lookup"><span data-stu-id="fa8f0-175">Queued Channels</span></span>  
 <span data-ttu-id="fa8f0-176">As filas armazenam mensagens de um aplicativo de envio em nome de um aplicativo de recebimento e encaminham essas mensagens posteriormente para o aplicativo de recebimento.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-176">Queues store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span> <span data-ttu-id="fa8f0-177">Eles ajudam a garantir que a transferência de mensagens envie aplicativos para o recebimento de aplicativos quando, por exemplo, o aplicativo receptor é transitório.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-177">They help ensure the transfer of messages from sending applications to receiving applications when, for example, the receiving application is transient.</span></span> <span data-ttu-id="fa8f0-178">O WCF dá suporte para enfileiramento usando o MSMQ (enfileiramento de mensagens da Microsoft) como um transporte.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-178">WCF provides support for queuing by using Microsoft Message Queuing (MSMQ) as a transport.</span></span>  
  
 <span data-ttu-id="fa8f0-179">O recurso de canais em fila não adiciona cabeçalhos a uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-179">The queued channels feature does not add headers to a message.</span></span> <span data-ttu-id="fa8f0-180">Em vez disso, ele cria uma mensagem de enfileiramento de mensagens com as propriedades de mensagem do enfileiramento de mensagens apropriadas definidas e invoca métodos de enfileiramento de mensagens para colocar a mensagem na fila do enfileiramento</span><span class="sxs-lookup"><span data-stu-id="fa8f0-180">Instead it creates a Message Queuing message with appropriate Message Queuing message properties set, and invokes Message Queuing methods to put the message in the Message Queuing queue.</span></span> <span data-ttu-id="fa8f0-181">O enfileiramento de mensagens é um componente opcional fornecido com o Windows.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-181">Message Queuing is an optional component that ships with Windows.</span></span>  
  
 <span data-ttu-id="fa8f0-182">Nenhuma informação é mantida no computador do usuário final pelo recurso de canais em fila, pois usa o enfileiramento de mensagens como a infraestrutura de enfileiramento.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-182">No information is retained on the end-user's machine by the queued channels feature, because it uses Message Queuing as the queuing infrastructure.</span></span>  
  
## <a name="com-integration"></a><span data-ttu-id="fa8f0-183">Integração de COM+</span><span class="sxs-lookup"><span data-stu-id="fa8f0-183">COM+ Integration</span></span>  
 <span data-ttu-id="fa8f0-184">Esse recurso encapsula a funcionalidade COM e COM+ existente para criar serviços que são compatíveis com os serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-184">This feature wraps existing COM and COM+ functionality to create services that are compatible with WCF services.</span></span> <span data-ttu-id="fa8f0-185">Esse recurso não usa cabeçalhos específicos e não retém dados no computador do usuário final.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-185">This feature does not use specific headers and it does not retain data on the end-user's machine.</span></span>  
  
## <a name="com-service-moniker"></a><span data-ttu-id="fa8f0-186">Moniker do serviço COM</span><span class="sxs-lookup"><span data-stu-id="fa8f0-186">COM Service Moniker</span></span>  
 <span data-ttu-id="fa8f0-187">Isso fornece um wrapper não gerenciado para um cliente padrão do WCF.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-187">This provides an unmanaged wrapper to a standard WCF client.</span></span> <span data-ttu-id="fa8f0-188">Esse recurso não tem cabeçalhos específicos na conexão, nem mantém os dados no computador.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-188">This feature does not have specific headers on the wire nor does it persist data on the machine.</span></span>  
  
## <a name="peer-channel"></a><span data-ttu-id="fa8f0-189">Canal par</span><span class="sxs-lookup"><span data-stu-id="fa8f0-189">Peer Channel</span></span>  
 <span data-ttu-id="fa8f0-190">Um canal de mesmo nível permite o desenvolvimento de aplicativos com multipartes usando o WCF.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-190">A peer channel enables development of multiparty applications using WCF.</span></span> <span data-ttu-id="fa8f0-191">As mensagens multipartes ocorrem no contexto de uma malha.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-191">Multiparty messaging occurs in the context of a mesh.</span></span> <span data-ttu-id="fa8f0-192">As malhas são identificadas por um nome que os nós podem unir.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-192">Meshes are identified by a name that nodes can join.</span></span> <span data-ttu-id="fa8f0-193">Cada nó no canal de mesmo nível cria um ouvinte TCP em uma porta especificada pelo usuário e estabelece conexões com outros nós na malha para garantir a resiliência.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-193">Each node in the peer channel creates a TCP listener at a user-specified port and establishes connections with other nodes in the mesh to ensure resiliency.</span></span> <span data-ttu-id="fa8f0-194">Para se conectar a outros nós na malha, os nós também trocam alguns dados, incluindo o endereço do ouvinte e os endereços IP do computador, com outros nós na malha.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-194">To connect to other nodes in the mesh, nodes also exchange some data, including the listener address and the machine's IP addresses, with other nodes in the mesh.</span></span> <span data-ttu-id="fa8f0-195">As mensagens enviadas na malha podem conter informações de segurança relacionadas ao remetente para evitar falsificação e adulteração de mensagens.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-195">Messages sent around in the mesh can contain security information that pertains to the sender to prevent message spoofing and tampering.</span></span>  
  
 <span data-ttu-id="fa8f0-196">Nenhuma informação pessoal é armazenada no computador do usuário final.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-196">No personal information is stored on the end-user's machine.</span></span>  
  
## <a name="it-professional-experience"></a><span data-ttu-id="fa8f0-197">Experiência profissional de ti</span><span class="sxs-lookup"><span data-stu-id="fa8f0-197">IT Professional Experience</span></span>  
  
### <a name="tracing"></a><span data-ttu-id="fa8f0-198">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="fa8f0-198">Tracing</span></span>  
 <span data-ttu-id="fa8f0-199">O recurso de diagnóstico da infraestrutura do WCF registra as mensagens que passam pelas camadas de modelo de serviço e transporte, bem como as atividades e os eventos associados a essas mensagens.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-199">The diagnostics feature of the WCF infrastructure logs messages that pass through the transport and service model layers, and the activities and events associated with these messages.</span></span> <span data-ttu-id="fa8f0-200">Este recurso permanece desativado por padrão.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-200">This feature is turned off by default.</span></span> <span data-ttu-id="fa8f0-201">Ele é habilitado usando o arquivo de configuração do aplicativo e o comportamento de rastreamento pode ser modificado usando o provedor WMI WCF em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-201">It is enabled using the application’s configuration file and the tracing behavior may be modified using the WCF WMI provider at run time.</span></span> <span data-ttu-id="fa8f0-202">Quando habilitada, a infraestrutura de rastreamento emite um rastreamento de diagnóstico que contém mensagens, atividades e eventos de processamento para os ouvintes configurados.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-202">When enabled, the tracing infrastructure emits a diagnostic trace that contains messages, activities, and processing events to configured listeners.</span></span> <span data-ttu-id="fa8f0-203">O formato e o local da saída são determinados pelas opções de configuração de ouvinte do administrador, mas normalmente é um arquivo formatado XML.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-203">The format and location of the output are determined by the administrator’s listener configuration choices, but is typically an XML formatted file.</span></span> <span data-ttu-id="fa8f0-204">O administrador é responsável por definir a ACL (lista de controle de acesso) nos arquivos de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-204">The administrator is responsible for setting the access control list (ACL) on the trace files.</span></span> <span data-ttu-id="fa8f0-205">Em particular, quando hospedado pelo WAS (sistema de ativação do Windows), o administrador deve verificar se os arquivos não são atendidos do diretório raiz virtual público, se isso não for desejado.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-205">In particular, when hosted by Windows Activation System (WAS), the administrator should make sure the files are not served from the public virtual root directory if that is not desired.</span></span>  
  
 <span data-ttu-id="fa8f0-206">Há dois tipos de rastreamento: log de mensagens e rastreamento de diagnóstico do modelo de serviço, descritos na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-206">There are two types of tracing: Message logging and Service Model diagnostic tracing, described in the following section.</span></span> <span data-ttu-id="fa8f0-207">Cada tipo é configurado por meio de sua própria origem de rastreamento: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> e <xref:System.ServiceModel>.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-207">Each type is configured through its own trace source: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> and <xref:System.ServiceModel>.</span></span> <span data-ttu-id="fa8f0-208">Ambas as fontes de rastreamento de log capturam dados que são locais para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-208">Both of these logging trace sources capture data that is local to the application.</span></span>  
  
### <a name="message-logging"></a><span data-ttu-id="fa8f0-209">Registro em log de mensagens</span><span class="sxs-lookup"><span data-stu-id="fa8f0-209">Message Logging</span></span>  
 <span data-ttu-id="fa8f0-210">A fonte de rastreamento de log de mensagens (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) permite que um administrador Registre as mensagens que fluem pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-210">The message logging trace source (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) allows an administrator to log the messages that flow through the system.</span></span> <span data-ttu-id="fa8f0-211">Por meio da configuração, o usuário pode decidir registrar somente mensagens inteiras ou cabeçalhos de mensagem, se deseja registrar nas camadas de modelo de transporte e/ou serviço e se deseja incluir mensagens malformadas.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-211">Through configuration, the user may decide to log entire messages or message headers only, whether to log at the transport and/or service model layers, and whether to include malformed messages.</span></span> <span data-ttu-id="fa8f0-212">Além disso, o usuário pode configurar a filtragem para restringir quais mensagens são registradas.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-212">Also, the user may configure filtering to restrict which messages are logged.</span></span>  
  
 <span data-ttu-id="fa8f0-213">Por padrão, o log de mensagens está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-213">By default, message logging is disabled.</span></span> <span data-ttu-id="fa8f0-214">O administrador do computador local pode impedir que o administrador de nível de aplicativo ative o log de mensagens.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-214">The local machine administrator can prevent the application-level administrator from turning message logging on.</span></span>  
  
#### <a name="encrypted-and-decrypted-message-logging"></a><span data-ttu-id="fa8f0-215">Registro em log de mensagens criptografadas e descriptografadas</span><span class="sxs-lookup"><span data-stu-id="fa8f0-215">Encrypted and Decrypted Message Logging</span></span>  
 <span data-ttu-id="fa8f0-216">As mensagens são registradas, criptografadas ou descriptografadas, conforme descrito nos termos a seguir.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-216">Messages are logged, encrypted, or decrypted, as described in the following terms.</span></span>  
  
 <span data-ttu-id="fa8f0-217">Registro em log de transporte</span><span class="sxs-lookup"><span data-stu-id="fa8f0-217">Transport Logging</span></span>  
 <span data-ttu-id="fa8f0-218">Registra as mensagens recebidas e enviadas no nível de transporte.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-218">Logs messages received and sent at the transport level.</span></span> <span data-ttu-id="fa8f0-219">Essas mensagens contêm todos os cabeçalhos e podem ser criptografadas antes de serem enviadas na conexão e quando forem recebidas.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-219">These messages contain all headers, and may be encrypted before being sent on the wire and when being received.</span></span>  
  
 <span data-ttu-id="fa8f0-220">Se as mensagens forem criptografadas antes de serem enviadas na conexão e quando forem recebidas, elas também serão criptografadas em log.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-220">If messages are encrypted before being sent on the wire and when they are received, they are logged encrypted as well.</span></span> <span data-ttu-id="fa8f0-221">Uma exceção é quando um protocolo de segurança é usado (https): em seguida, eles são descriptografados em log antes de serem enviados e depois de serem recebidos, mesmo que sejam criptografados na conexão.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-221">An exception is when a security protocol is used (https): they are then logged decrypted before being sent and after being received even if they are encrypted on the wire.</span></span>  
  
 <span data-ttu-id="fa8f0-222">Registro em log do serviço</span><span class="sxs-lookup"><span data-stu-id="fa8f0-222">Service Logging</span></span>  
 <span data-ttu-id="fa8f0-223">Registra as mensagens recebidas ou enviadas no nível do modelo de serviço, após a ocorrência do processamento do cabeçalho do canal, logo antes e depois da inserção do código do usuário.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-223">Logs messages received or sent at the service model level, after channel header processing has occurred, just before and after entering user code.</span></span>  
  
 <span data-ttu-id="fa8f0-224">As mensagens registradas nesse nível são descriptografadas mesmo que elas tenham sido protegidas e criptografadas na conexão.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-224">Messages logged at this level are decrypted even if they were secured and encrypted on the wire.</span></span>  
  
 <span data-ttu-id="fa8f0-225">Log de mensagens malformados</span><span class="sxs-lookup"><span data-stu-id="fa8f0-225">Malformed Message Logging</span></span>  
 <span data-ttu-id="fa8f0-226">Registra mensagens que a infraestrutura do WCF não pode entender ou processar.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-226">Logs messages that the WCF infrastructure cannot understand or process.</span></span>  
  
 <span data-ttu-id="fa8f0-227">As mensagens são registradas como estão, ou seja, criptografadas ou não</span><span class="sxs-lookup"><span data-stu-id="fa8f0-227">Messages are logged as-is, that is, encrypted or not</span></span>  
  
 <span data-ttu-id="fa8f0-228">Quando as mensagens são registradas em formato descriptografado ou não criptografado, por padrão, o WCF remove as chaves de segurança e as informações potencialmente pessoais das mensagens antes de fazer logon.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-228">When messages are logged in decrypted or unencrypted form, by default WCF removes security keys and potentially personal information from the messages before logging them.</span></span> <span data-ttu-id="fa8f0-229">As seções a seguir descrevem quais informações são removidas e quando.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-229">The next sections describe what information is removed, and when.</span></span> <span data-ttu-id="fa8f0-230">O administrador do computador e o implantador de aplicativos devem executar certas ações de configuração para alterar o comportamento padrão para chaves de log e informações potencialmente pessoais.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-230">The machine administrator and application deployer must both take certain configuration actions to change the default behavior to log keys and potentially personal information.</span></span>  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="fa8f0-231">Informações removidas dos cabeçalhos de mensagem ao registrar em log as mensagens descriptografadas/não criptografadas</span><span class="sxs-lookup"><span data-stu-id="fa8f0-231">Information Removed from Message Headers When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="fa8f0-232">Quando as mensagens são registradas em formato descriptografado/não criptografado, as chaves de segurança e as informações potencialmente pessoais são removidas por padrão dos cabeçalhos e corpos das mensagens antes de serem registradas.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-232">When messages are logged in decrypted/unencrypted form, security keys and potentially personal information are removed by default from message headers and message bodies before they are logged.</span></span> <span data-ttu-id="fa8f0-233">A lista a seguir mostra o que o WCF considera as chaves e as informações potencialmente pessoais.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-233">The following list shows what WCF considers keys and potentially personal information.</span></span>  
  
 <span data-ttu-id="fa8f0-234">Chaves que são removidas:</span><span class="sxs-lookup"><span data-stu-id="fa8f0-234">Keys that are removed:</span></span>  
  
 <span data-ttu-id="fa8f0-235">\- para xmlns: WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" e xmlns: WST = "http://schemas.xmlsoap.org/ws/2005/02/trust"</span><span class="sxs-lookup"><span data-stu-id="fa8f0-235">\- For xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"</span></span>  
  
 <span data-ttu-id="fa8f0-236">wst:BinarySecret</span><span class="sxs-lookup"><span data-stu-id="fa8f0-236">wst:BinarySecret</span></span>  
  
 <span data-ttu-id="fa8f0-237">wst:Entropy</span><span class="sxs-lookup"><span data-stu-id="fa8f0-237">wst:Entropy</span></span>  
  
 <span data-ttu-id="fa8f0-238">\- para xmlns: wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" e xmlns: wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span><span class="sxs-lookup"><span data-stu-id="fa8f0-238">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="fa8f0-239">wsse: senha</span><span class="sxs-lookup"><span data-stu-id="fa8f0-239">wsse:Password</span></span>  
  
 <span data-ttu-id="fa8f0-240">wsse: nonce</span><span class="sxs-lookup"><span data-stu-id="fa8f0-240">wsse:Nonce</span></span>  
  
 <span data-ttu-id="fa8f0-241">Informações potencialmente pessoais que são removidas:</span><span class="sxs-lookup"><span data-stu-id="fa8f0-241">Potentially personal information that is removed:</span></span>  
  
 <span data-ttu-id="fa8f0-242">\- para xmlns: wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" e xmlns: wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span><span class="sxs-lookup"><span data-stu-id="fa8f0-242">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="fa8f0-243">wsse: nome de usuário</span><span class="sxs-lookup"><span data-stu-id="fa8f0-243">wsse:Username</span></span>  
  
 <span data-ttu-id="fa8f0-244">wsse:BinarySecurityToken</span><span class="sxs-lookup"><span data-stu-id="fa8f0-244">wsse:BinarySecurityToken</span></span>  
  
 <span data-ttu-id="fa8f0-245">\- para xmlns: SAML = "urn: Oasis: names: TC: SAML: 1.0: Assertion" os itens em negrito (abaixo) são removidos:</span><span class="sxs-lookup"><span data-stu-id="fa8f0-245">\- For xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion" the items in bold (below) are removed:</span></span>  
  
 <span data-ttu-id="fa8f0-246">Asserção de \<</span><span class="sxs-lookup"><span data-stu-id="fa8f0-246">\<Assertion</span></span>  
  
 <span data-ttu-id="fa8f0-247">MajorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="fa8f0-247">MajorVersion="1"</span></span>  
  
 <span data-ttu-id="fa8f0-248">MinorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="fa8f0-248">MinorVersion="1"</span></span>  
  
 <span data-ttu-id="fa8f0-249">AssertionId="[ID]"</span><span class="sxs-lookup"><span data-stu-id="fa8f0-249">AssertionId="[ID]"</span></span>  
  
 <span data-ttu-id="fa8f0-250">Issuer="[string]"</span><span class="sxs-lookup"><span data-stu-id="fa8f0-250">Issuer="[string]"</span></span>  
  
 <span data-ttu-id="fa8f0-251">IssueInstant="[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="fa8f0-251">IssueInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="fa8f0-252">\<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]"></span><span class="sxs-lookup"><span data-stu-id="fa8f0-252">\<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]"></span></span>  
  
 <span data-ttu-id="fa8f0-253">\<AudienceRestrictionCondition></span><span class="sxs-lookup"><span data-stu-id="fa8f0-253">\<AudienceRestrictionCondition></span></span>  
  
 <span data-ttu-id="fa8f0-254">\<público > [URI]\</Audience > +</span><span class="sxs-lookup"><span data-stu-id="fa8f0-254">\<Audience>[uri]\</Audience>+</span></span>  
  
 <span data-ttu-id="fa8f0-255">\</AudienceRestrictionCondition>\*</span><span class="sxs-lookup"><span data-stu-id="fa8f0-255">\</AudienceRestrictionCondition>\*</span></span>  
  
 <span data-ttu-id="fa8f0-256">\<DoNotCacheCondition/> \*</span><span class="sxs-lookup"><span data-stu-id="fa8f0-256">\<DoNotCacheCondition />\*</span></span>  
  
 <span data-ttu-id="fa8f0-257"><\!--tipo base abstrato</span><span class="sxs-lookup"><span data-stu-id="fa8f0-257"><\!-- abstract base type</span></span>  
  
 <span data-ttu-id="fa8f0-258">Condição de \</> \*</span><span class="sxs-lookup"><span data-stu-id="fa8f0-258">\<Condition />\*</span></span>  
  
 -->  
  
 <span data-ttu-id="fa8f0-259">\</Conditions >?</span><span class="sxs-lookup"><span data-stu-id="fa8f0-259">\</Conditions>?</span></span>  
  
 <span data-ttu-id="fa8f0-260">\<conselhos ></span><span class="sxs-lookup"><span data-stu-id="fa8f0-260">\<Advice></span></span>  
  
 <span data-ttu-id="fa8f0-261">\<AssertionIDReference>[ID]\</AssertionIDReference>\*</span><span class="sxs-lookup"><span data-stu-id="fa8f0-261">\<AssertionIDReference>[ID]\</AssertionIDReference>\*</span></span>  
  
 <span data-ttu-id="fa8f0-262">\<asserção > [asserção]\</Assertion > \*</span><span class="sxs-lookup"><span data-stu-id="fa8f0-262">\<Assertion>[assertion]\</Assertion>\*</span></span>  
  
 <span data-ttu-id="fa8f0-263">[qualquer] \*</span><span class="sxs-lookup"><span data-stu-id="fa8f0-263">[any]\*</span></span>  
  
 <span data-ttu-id="fa8f0-264">\</Advice >?</span><span class="sxs-lookup"><span data-stu-id="fa8f0-264">\</Advice>?</span></span>  
  
 <span data-ttu-id="fa8f0-265"><\!--tipos base abstratos</span><span class="sxs-lookup"><span data-stu-id="fa8f0-265"><\!-- Abstract base types</span></span>  
  
 <span data-ttu-id="fa8f0-266">Instrução \</> \*</span><span class="sxs-lookup"><span data-stu-id="fa8f0-266">\<Statement />\*</span></span>  
  
 <span data-ttu-id="fa8f0-267">\<SubjectStatement ></span><span class="sxs-lookup"><span data-stu-id="fa8f0-267">\<SubjectStatement></span></span>  
  
 <span data-ttu-id="fa8f0-268">\<assunto ></span><span class="sxs-lookup"><span data-stu-id="fa8f0-268">\<Subject></span></span>  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 <span data-ttu-id="fa8f0-269">\<SubjectConfirmation></span><span class="sxs-lookup"><span data-stu-id="fa8f0-269">\<SubjectConfirmation></span></span>  
  
 <span data-ttu-id="fa8f0-270">\<ConfirmationMethod > [anyURI]\</ConfirmationMethod > +</span><span class="sxs-lookup"><span data-stu-id="fa8f0-270">\<ConfirmationMethod>[anyUri]\</ConfirmationMethod>+</span></span>  
  
 <span data-ttu-id="fa8f0-271">\<SubjectConfirmationData > [any]\</SubjectConfirmationData >?</span><span class="sxs-lookup"><span data-stu-id="fa8f0-271">\<SubjectConfirmationData>[any]\</SubjectConfirmationData>?</span></span>  
  
 <span data-ttu-id="fa8f0-272">\<ds:KeyInfo>...\</ds:KeyInfo>?</span><span class="sxs-lookup"><span data-stu-id="fa8f0-272">\<ds:KeyInfo>...\</ds:KeyInfo>?</span></span>  
  
 <span data-ttu-id="fa8f0-273">\</SubjectConfirmation>?</span><span class="sxs-lookup"><span data-stu-id="fa8f0-273">\</SubjectConfirmation>?</span></span>  
  
 <span data-ttu-id="fa8f0-274">\</Subject></span><span class="sxs-lookup"><span data-stu-id="fa8f0-274">\</Subject></span></span>  
  
 <span data-ttu-id="fa8f0-275">\</SubjectStatement > \*</span><span class="sxs-lookup"><span data-stu-id="fa8f0-275">\</SubjectStatement>\*</span></span>  
  
 -->  
  
 <span data-ttu-id="fa8f0-276">\<AuthenticationStatement</span><span class="sxs-lookup"><span data-stu-id="fa8f0-276">\<AuthenticationStatement</span></span>  
  
 <span data-ttu-id="fa8f0-277">AuthenticationMethod = "[URI]"</span><span class="sxs-lookup"><span data-stu-id="fa8f0-277">AuthenticationMethod="[uri]"</span></span>  
  
 <span data-ttu-id="fa8f0-278">AuthenticationInstant="[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="fa8f0-278">AuthenticationInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="fa8f0-279">Subjetiva</span><span class="sxs-lookup"><span data-stu-id="fa8f0-279">[Subject]</span></span>  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 <span data-ttu-id="fa8f0-280">< Authoritybinding</span><span class="sxs-lookup"><span data-stu-id="fa8f0-280"><AuthorityBinding</span></span>  
  
 <span data-ttu-id="fa8f0-281">AuthorityKind="[QName]"</span><span class="sxs-lookup"><span data-stu-id="fa8f0-281">AuthorityKind="[QName]"</span></span>  
  
 <span data-ttu-id="fa8f0-282">Location="[uri]"</span><span class="sxs-lookup"><span data-stu-id="fa8f0-282">Location="[uri]"</span></span>  
  
 <span data-ttu-id="fa8f0-283">Binding="[uri]"</span><span class="sxs-lookup"><span data-stu-id="fa8f0-283">Binding="[uri]"</span></span>  
  
 />*  
  
 <span data-ttu-id="fa8f0-284">\</AuthenticationStatement>\*</span><span class="sxs-lookup"><span data-stu-id="fa8f0-284">\</AuthenticationStatement>\*</span></span>  
  
 <span data-ttu-id="fa8f0-285">\<AttributeStatement ></span><span class="sxs-lookup"><span data-stu-id="fa8f0-285">\<AttributeStatement></span></span>  
  
 <span data-ttu-id="fa8f0-286">Subjetiva</span><span class="sxs-lookup"><span data-stu-id="fa8f0-286">[Subject]</span></span>  
  
 <span data-ttu-id="fa8f0-287">\<atributo</span><span class="sxs-lookup"><span data-stu-id="fa8f0-287">\<Attribute</span></span>  
  
 <span data-ttu-id="fa8f0-288">AttributeName="[string]"</span><span class="sxs-lookup"><span data-stu-id="fa8f0-288">AttributeName="[string]"</span></span>  
  
 <span data-ttu-id="fa8f0-289">AttributeNamespace="[uri]"</span><span class="sxs-lookup"><span data-stu-id="fa8f0-289">AttributeNamespace="[uri]"</span></span>  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 <span data-ttu-id="fa8f0-290">\</attribute > +</span><span class="sxs-lookup"><span data-stu-id="fa8f0-290">\</Attribute>+</span></span>  
  
 <span data-ttu-id="fa8f0-291">\</AttributeStatement>\*</span><span class="sxs-lookup"><span data-stu-id="fa8f0-291">\</AttributeStatement>\*</span></span>  
  
 <span data-ttu-id="fa8f0-292">\<AuthorizationDecisionStatement</span><span class="sxs-lookup"><span data-stu-id="fa8f0-292">\<AuthorizationDecisionStatement</span></span>  
  
 <span data-ttu-id="fa8f0-293">Resource="[uri]"</span><span class="sxs-lookup"><span data-stu-id="fa8f0-293">Resource="[uri]"</span></span>  
  
 <span data-ttu-id="fa8f0-294">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span><span class="sxs-lookup"><span data-stu-id="fa8f0-294">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span></span>  
  
 >  
  
 <span data-ttu-id="fa8f0-295">Subjetiva</span><span class="sxs-lookup"><span data-stu-id="fa8f0-295">[Subject]</span></span>  
  
 <span data-ttu-id="fa8f0-296">\<Action Namespace="[uri]">[string]\</Action>+</span><span class="sxs-lookup"><span data-stu-id="fa8f0-296">\<Action Namespace="[uri]">[string]\</Action>+</span></span>  
  
 <span data-ttu-id="fa8f0-297">Evidência de \<</span><span class="sxs-lookup"><span data-stu-id="fa8f0-297">\<Evidence></span></span>  
  
 <span data-ttu-id="fa8f0-298">\<AssertionIDReference>[ID]\</AssertionIDReference>+</span><span class="sxs-lookup"><span data-stu-id="fa8f0-298">\<AssertionIDReference>[ID]\</AssertionIDReference>+</span></span>  
  
 <span data-ttu-id="fa8f0-299">\<asserção > [asserção]\</Assertion > +</span><span class="sxs-lookup"><span data-stu-id="fa8f0-299">\<Assertion>[assertion]\</Assertion>+</span></span>  
  
 <span data-ttu-id="fa8f0-300">\</Evidence >?</span><span class="sxs-lookup"><span data-stu-id="fa8f0-300">\</Evidence>?</span></span>  
  
 <span data-ttu-id="fa8f0-301">\</AuthorizationDecisionStatement>\*</span><span class="sxs-lookup"><span data-stu-id="fa8f0-301">\</AuthorizationDecisionStatement>\*</span></span>  
  
 <span data-ttu-id="fa8f0-302">\</Assertion></span><span class="sxs-lookup"><span data-stu-id="fa8f0-302">\</Assertion></span></span>  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="fa8f0-303">Informações removidas de corpos de mensagens ao registrar em log mensagens descriptografadas/sem criptografia</span><span class="sxs-lookup"><span data-stu-id="fa8f0-303">Information Removed from Message Bodies When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="fa8f0-304">Conforme descrito anteriormente, o WCF remove as chaves e as informações potencialmente pessoais conhecidas dos cabeçalhos de mensagem para mensagens descriptografadas/descriptografadas registradas.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-304">As previously described, WCF removes keys and known potentially personal information from message headers for logged decrypted/unencrypted messages.</span></span> <span data-ttu-id="fa8f0-305">Além disso, o WCF remove as chaves e as informações potencialmente pessoais conhecidas dos corpos de mensagens para os elementos e ações do corpo na lista a seguir, que descrevem as mensagens de segurança envolvidas na troca de chaves.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-305">In addition, WCF removes keys and known potentially personal information from message bodies for the body elements and actions in the following list, which describe security messages involved in key exchange.</span></span>  
  
 <span data-ttu-id="fa8f0-306">Para os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="fa8f0-306">For the following namespaces:</span></span>  
  
 <span data-ttu-id="fa8f0-307">xmlns: WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" e xmlns: WST = "http://schemas.xmlsoap.org/ws/2005/02/trust" (por exemplo, se nenhuma ação estiver disponível)</span><span class="sxs-lookup"><span data-stu-id="fa8f0-307">xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust" (for example, if no action available)</span></span>  
  
 <span data-ttu-id="fa8f0-308">As informações são removidas para esses elementos do corpo, que envolvem a troca de chaves:</span><span class="sxs-lookup"><span data-stu-id="fa8f0-308">Information is removed for these body elements, which involve key exchange:</span></span>  
  
 <span data-ttu-id="fa8f0-309">wst:RequestSecurityToken</span><span class="sxs-lookup"><span data-stu-id="fa8f0-309">wst:RequestSecurityToken</span></span>  
  
 <span data-ttu-id="fa8f0-310">wst:RequestSecurityTokenResponse</span><span class="sxs-lookup"><span data-stu-id="fa8f0-310">wst:RequestSecurityTokenResponse</span></span>  
  
 <span data-ttu-id="fa8f0-311">wst:RequestSecurityTokenResponseCollection</span><span class="sxs-lookup"><span data-stu-id="fa8f0-311">wst:RequestSecurityTokenResponseCollection</span></span>  
  
 <span data-ttu-id="fa8f0-312">As informações também são removidas para cada uma das seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="fa8f0-312">Information is also removed for each of the following Actions:</span></span>  
  
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
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a><span data-ttu-id="fa8f0-313">Nenhuma informação é removida dos cabeçalhos e dos dados de corpo específicos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="fa8f0-313">No Information Is Removed from Application-specific Headers and Body Data</span></span>  
 <span data-ttu-id="fa8f0-314">O WCF não rastreia informações pessoais em cabeçalhos específicos do aplicativo (por exemplo, cadeias de caracteres de consulta) ou dados de corpo (por exemplo, número de cartão de crédito).</span><span class="sxs-lookup"><span data-stu-id="fa8f0-314">WCF does not track personal information in application-specific headers (for example, query strings) or body data (for example, credit card number).</span></span>  
  
 <span data-ttu-id="fa8f0-315">Quando o log de mensagens está ativado, informações pessoais em cabeçalhos específicos do aplicativo e informações de corpo podem estar visíveis nos logs.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-315">When message logging is on, personal information in application-specific headers and body information may be visible in the logs.</span></span> <span data-ttu-id="fa8f0-316">Novamente, o implantador de aplicativos é responsável por definir as ACLs nos arquivos de configuração e de log.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-316">Again, the application deployer is responsible for setting the ACLs on the configuration and log files.</span></span> <span data-ttu-id="fa8f0-317">Ele também pode desativar o registro em log se ele não quiser que essas informações fiquem visíveis ou se ele puder filtrar essas informações dos arquivos de log depois que ele for registrado.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-317">He also can turn off logging if he does not want this information to be visible, or he may filter out this information from the log files after it is logged.</span></span>  
  
### <a name="service-model-tracing"></a><span data-ttu-id="fa8f0-318">Rastreamento do modelo de serviço</span><span class="sxs-lookup"><span data-stu-id="fa8f0-318">Service Model Tracing</span></span>  
 <span data-ttu-id="fa8f0-319">A fonte de rastreamento do modelo de serviço (<xref:System.ServiceModel>) permite o rastreamento de atividades e eventos relacionados ao processamento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-319">The Service Model trace source (<xref:System.ServiceModel>) enables tracing of activities and events related to message processing.</span></span> <span data-ttu-id="fa8f0-320">Esse recurso usa a funcionalidade de diagnóstico .NET Framework da <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-320">This feature uses the .NET Framework diagnostic functionality from <xref:System.Diagnostics>.</span></span> <span data-ttu-id="fa8f0-321">Assim como com a propriedade <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>, o local e sua ACL são configuráveis pelo usuário usando .NET Framework arquivos de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-321">As with the <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> property, the location and its ACL are user-configurable using .NET Framework application configuration files.</span></span> <span data-ttu-id="fa8f0-322">Assim como ocorre com o log de mensagens, o local do arquivo é sempre configurado quando o administrador habilita o rastreamento; Portanto, o administrador controla a ACL.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-322">As with message logging, the file location is always configured when the administrator enables tracing; thus, the administrator controls the ACL.</span></span>  
  
 <span data-ttu-id="fa8f0-323">Os rastreamentos contêm cabeçalhos de mensagem quando uma mensagem está no escopo.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-323">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="fa8f0-324">As mesmas regras para ocultar informações potencialmente pessoais em cabeçalhos de mensagens na seção anterior se aplicam: as informações pessoais identificadas anteriormente são removidas por padrão dos cabeçalhos em rastreamentos.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-324">The same rules for hiding potentially personal information in message headers in the previous section apply: the personal information previously identified is removed by default from the headers in traces.</span></span> <span data-ttu-id="fa8f0-325">Tanto o administrador do computador quanto o implantador de aplicativos devem modificar a configuração para registrar informações potencialmente pessoais.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-325">Both the machine administrator and the application deployer must modify the configuration in order to log potentially personal information.</span></span> <span data-ttu-id="fa8f0-326">No entanto, as informações pessoais contidas em cabeçalhos específicos do aplicativo são registradas em rastreamentos.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-326">However, personal information contained in application-specific headers is logged in traces.</span></span> <span data-ttu-id="fa8f0-327">O implantador de aplicativos é responsável por definir as ACLs nos arquivos de configuração e de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-327">The application deployer is responsible for setting the ACLs on the configuration and trace files.</span></span> <span data-ttu-id="fa8f0-328">Ele também poderá desativar o rastreamento se ele não quiser que essas informações fiquem visíveis ou se ele puder filtrar essas informações dos arquivos de rastreamento depois que ele for registrado.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-328">He also can turn off tracing if he does not want this information to be visible, or he can filter out this information from the trace files after it is logged.</span></span>  
  
 <span data-ttu-id="fa8f0-329">Como parte do rastreamento de ServiceModel, as IDs exclusivas (chamadas de IDs de atividade e, normalmente, um GUID) vinculam diferentes atividades em conjunto como uma mensagem fluindo por diferentes partes da infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-329">As part of ServiceModel Tracing, Unique IDs (called Activity IDs, and typically a GUID) link different activities together as a message flows through different parts of the infrastructure.</span></span>  
  
#### <a name="custom-trace-listeners"></a><span data-ttu-id="fa8f0-330">Ouvintes de rastreamento personalizados</span><span class="sxs-lookup"><span data-stu-id="fa8f0-330">Custom Trace Listeners</span></span>  
 <span data-ttu-id="fa8f0-331">Para o log de mensagens e o rastreamento, um ouvinte de rastreamento personalizado pode ser configurado, o que pode enviar rastreamentos e mensagens na transmissão (por exemplo, para um banco de dados remoto).</span><span class="sxs-lookup"><span data-stu-id="fa8f0-331">For both message logging and tracing, a custom trace listener can be configured, which can send traces and messages on the wire (for example, to a remote database).</span></span> <span data-ttu-id="fa8f0-332">O implantador de aplicativos é responsável por configurar ouvintes personalizados ou permitir que os usuários façam isso.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-332">The application deployer is responsible for configuring custom listeners or enabling users to do so.</span></span> <span data-ttu-id="fa8f0-333">Ele também é responsável por qualquer informação pessoal exposta no local remoto e para aplicar ACLs adequadamente a esse local.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-333">He is also responsible for any personal information exposed at the remote location, and for properly applying ACLs to this location.</span></span>  
  
### <a name="other-features-for-it-professionals"></a><span data-ttu-id="fa8f0-334">Outros recursos para profissionais de ti</span><span class="sxs-lookup"><span data-stu-id="fa8f0-334">Other features for IT Professionals</span></span>  
 <span data-ttu-id="fa8f0-335">O WCF tem um provedor WMI que expõe as informações de configuração de infraestrutura do WCF por meio do WMI (fornecido com o Windows).</span><span class="sxs-lookup"><span data-stu-id="fa8f0-335">WCF has a WMI provider that exposes the WCF infrastructure configuration information through WMI (shipped with Windows).</span></span> <span data-ttu-id="fa8f0-336">Por padrão, a interface WMI está disponível para administradores.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-336">By default, the WMI interface is available to administrators.</span></span>  
  
 <span data-ttu-id="fa8f0-337">A configuração do WCF usa o mecanismo de configuração do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-337">WCF configuration uses the .NET Framework configuration mechanism.</span></span> <span data-ttu-id="fa8f0-338">Os arquivos de configuração são armazenados no computador.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-338">The configuration files are stored on the machine.</span></span> <span data-ttu-id="fa8f0-339">O desenvolvedor de aplicativos e o administrador criam os arquivos de configuração e a ACL para cada um dos requisitos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-339">The application developer and the administrator create the configuration files and ACL for each of the application's requirements.</span></span> <span data-ttu-id="fa8f0-340">Um arquivo de configuração pode conter endereços de ponto de extremidade e links para certificados no repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-340">A configuration file can contain endpoint addresses and links to certificates in the certificate store.</span></span> <span data-ttu-id="fa8f0-341">Os certificados podem ser usados para fornecer dados de aplicativo para configurar várias propriedades dos recursos usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-341">The certificates can be used to provide application data to configure various properties of the features used by the application.</span></span>  
  
 <span data-ttu-id="fa8f0-342">O WCF também usa a funcionalidade de despejo de .NET Framework processo chamando o método <xref:System.Environment.FailFast%2A>.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-342">WCF also uses the .NET Framework process dump functionality by calling the <xref:System.Environment.FailFast%2A> method.</span></span>  
  
### <a name="it-pro-tools"></a><span data-ttu-id="fa8f0-343">Ferramentas de profissionais de ti</span><span class="sxs-lookup"><span data-stu-id="fa8f0-343">IT Pro Tools</span></span>  
 <span data-ttu-id="fa8f0-344">O WCF também fornece as seguintes ferramentas profissionais de ti, que são fornecidas na SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-344">WCF also provides the following IT professional tools, which ship in the Windows SDK.</span></span>  
  
#### <a name="svctraceviewerexe"></a><span data-ttu-id="fa8f0-345">SvcTraceViewer.exe</span><span class="sxs-lookup"><span data-stu-id="fa8f0-345">SvcTraceViewer.exe</span></span>  
 <span data-ttu-id="fa8f0-346">O visualizador exibe os arquivos de rastreamento do WCF.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-346">The viewer displays WCF trace files.</span></span> <span data-ttu-id="fa8f0-347">O visualizador mostra qualquer informação contida nos rastreamentos.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-347">The viewer shows whatever information is contained in the traces.</span></span>  
  
#### <a name="svcconfigeditorexe"></a><span data-ttu-id="fa8f0-348">SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="fa8f0-348">SvcConfigEditor.exe</span></span>  
 <span data-ttu-id="fa8f0-349">O editor permite que o usuário crie e edite arquivos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-349">The editor allows the user to create and edit WCF configuration files.</span></span> <span data-ttu-id="fa8f0-350">O editor mostra qualquer informação contida nos arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-350">The editor shows whatever information is contained in the configuration files.</span></span> <span data-ttu-id="fa8f0-351">A mesma tarefa pode ser realizada com um editor de texto.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-351">The same task can be accomplished with a text editor.</span></span>  
  
#### <a name="servicemodel_reg"></a><span data-ttu-id="fa8f0-352">ServiceModel_Reg</span><span class="sxs-lookup"><span data-stu-id="fa8f0-352">ServiceModel_Reg</span></span>  
 <span data-ttu-id="fa8f0-353">Essa ferramenta permite que o usuário gerencie instalações de ServiceModel em um computador.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-353">This tool allows the user to manage ServiceModel installs on a machine.</span></span> <span data-ttu-id="fa8f0-354">A ferramenta exibe mensagens de status em uma janela de console quando ela é executada e, no processo, pode exibir informações sobre a configuração da instalação do WCF.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-354">The tool displays status messages in a console window when it runs and, in the process, may display information about the configuration of the WCF installation.</span></span>  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a><span data-ttu-id="fa8f0-355">WSATConfig. exe e WSATUI. dll</span><span class="sxs-lookup"><span data-stu-id="fa8f0-355">WSATConfig.exe and WSATUI.dll</span></span>  
 <span data-ttu-id="fa8f0-356">Essas ferramentas permitem que os profissionais de ti configurem o suporte de rede WS-AtomicTransaction interoperável no WCF.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-356">These tools allow IT Professionals to configure interoperable WS-AtomicTransaction network support in WCF.</span></span> <span data-ttu-id="fa8f0-357">As ferramentas exibem e permitem que o usuário altere os valores das configurações WS-AtomicTransaction mais usadas armazenadas no registro.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-357">The tools display and allow the user to change the values of the most commonly used WS-AtomicTransaction settings stored in the registry.</span></span>  
  
## <a name="cross-cutting-features"></a><span data-ttu-id="fa8f0-358">Recursos de corte cruzado</span><span class="sxs-lookup"><span data-stu-id="fa8f0-358">Cross-cutting Features</span></span>  
 <span data-ttu-id="fa8f0-359">Os recursos a seguir são de corte cruzado.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-359">The following features are cross-cutting.</span></span> <span data-ttu-id="fa8f0-360">Ou seja, eles podem ser compostos com qualquer um dos recursos anteriores.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-360">That is, they can be composed with any of the preceding features.</span></span>  
  
### <a name="service-framework"></a><span data-ttu-id="fa8f0-361">Estrutura de serviço</span><span class="sxs-lookup"><span data-stu-id="fa8f0-361">Service Framework</span></span>  
 <span data-ttu-id="fa8f0-362">Os cabeçalhos podem conter uma ID de instância, que é um GUID que associa uma mensagem a uma instância de uma classe CLR.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-362">Headers can contain an instance ID, which is a GUID that associates a message with an instance of a CLR class.</span></span>  
  
 <span data-ttu-id="fa8f0-363">O WSDL (Web Services Description Language) contém uma definição da porta.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-363">The Web Services Description Language (WSDL) contains a definition of the port.</span></span> <span data-ttu-id="fa8f0-364">Cada porta tem um endereço de ponto de extremidade e uma associação que representa os serviços usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-364">Each port has an endpoint address and a binding that represents the services used by the application.</span></span> <span data-ttu-id="fa8f0-365">Expor o WSDL pode ser desativado usando a configuração.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-365">Exposing WSDL can be turned off using configuration.</span></span> <span data-ttu-id="fa8f0-366">Nenhuma informação é mantida no computador.</span><span class="sxs-lookup"><span data-stu-id="fa8f0-366">No information is retained on the machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa8f0-367">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa8f0-367">See also</span></span>

- [<span data-ttu-id="fa8f0-368">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="fa8f0-368">Windows Communication Foundation</span></span>](index.md)
- [<span data-ttu-id="fa8f0-369">Security</span><span class="sxs-lookup"><span data-stu-id="fa8f0-369">Security</span></span>](./feature-details/security.md)
