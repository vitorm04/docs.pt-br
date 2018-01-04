---
title: "Informações de privacidade do Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f66f773551f45f9e4c5978ef09bbe4061a3326bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-communication-foundation-privacy-information"></a><span data-ttu-id="3a1cc-102">Informações de privacidade do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="3a1cc-102">Windows Communication Foundation Privacy Information</span></span>
<span data-ttu-id="3a1cc-103">A Microsoft está comprometida em proteger a privacidade dos usuários finais.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-103">Microsoft is committed to protecting end-users' privacy.</span></span> <span data-ttu-id="3a1cc-104">Quando você cria um aplicativo usando [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], versão 3.0, seu aplicativo pode afetar a privacidade de seus usuários finais.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-104">When you build an application using [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], version 3.0, your application may impact your end-users' privacy.</span></span> <span data-ttu-id="3a1cc-105">Por exemplo, seu aplicativo explicitamente pode coletar informações de contato do usuário, ou pode solicitar ou enviar informações pela Internet para seu site da Web.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-105">For example, your application may explicitly collect user contact information, or it may request or send information over the Internet to your Web site.</span></span> <span data-ttu-id="3a1cc-106">Se você inserir a tecnologia da Microsoft em seu aplicativo, essa tecnologia pode ter seu próprio comportamento que pode afetar a privacidade.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-106">If you embed Microsoft technology in your application, that technology may have its own behavior that might affect privacy.</span></span> [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="3a1cc-107">não enviar informações à Microsoft do seu aplicativo, a menos que você ou o usuário final optar por enviá-lo para nós.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-107"> does not send any information to Microsoft from your application unless you or the end-user choose to send it to us.</span></span>  
  
## <a name="wcf-in-brief"></a><span data-ttu-id="3a1cc-108">WCF no resumo</span><span class="sxs-lookup"><span data-stu-id="3a1cc-108">WCF in Brief</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="3a1cc-109">é uma estrutura de mensagens distribuída usando o Microsoft .NET Framework que permite aos desenvolvedores criar aplicativos distribuídos.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-109"> is a distributed messaging framework using the Microsoft .NET Framework that allows developers to build distributed applications.</span></span> <span data-ttu-id="3a1cc-110">Mensagens trocadas entre os dois aplicativos contêm informações de cabeçalho e corpo.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-110">Messages communicated between two applications contain header and body information.</span></span>  
  
 <span data-ttu-id="3a1cc-111">Cabeçalhos podem conter o roteamento de mensagens, as informações de segurança, transações e muito mais dependendo dos serviços usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-111">Headers may contain message routing, security information, transactions, and more depending on the services used by the application.</span></span> <span data-ttu-id="3a1cc-112">Normalmente, as mensagens são criptografadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-112">Messages are typically encrypted by default.</span></span> <span data-ttu-id="3a1cc-113">A única exceção é quando usando o `BasicHttpBinding`, que foi projetado para uso com os serviços Web herdados, não é seguro.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-113">The one exception is when using the `BasicHttpBinding`, which was designed for use with non-secured, legacy Web services.</span></span> <span data-ttu-id="3a1cc-114">Como criador do aplicativo, você é responsável pelo design final.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-114">As the application designer, you are responsible for the final design.</span></span> <span data-ttu-id="3a1cc-115">Mensagens no corpo de SOAP contêm dados específicos do aplicativo; No entanto, esses dados, como definido pelo aplicativo informações pessoais podem ser protegidos usando [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] recursos de criptografia ou confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-115">Messages in the SOAP body contain application-specific data; however, this data, such as application-defined personal information, can be secured by using [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] encryption or confidentiality features.</span></span> <span data-ttu-id="3a1cc-116">As seções a seguir descrevem os recursos que afetam a privacidade.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-116">The following sections describe the features that potentially impact privacy.</span></span>  
  
## <a name="messaging"></a><span data-ttu-id="3a1cc-117">Mensagens</span><span class="sxs-lookup"><span data-stu-id="3a1cc-117">Messaging</span></span>  
 <span data-ttu-id="3a1cc-118">Cada [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] mensagem tem um cabeçalho de endereço que especifica o destino da mensagem e onde a resposta deve ir.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-118">Each [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] message has an address header that specifies the message destination and where the reply should go.</span></span>  
  
 <span data-ttu-id="3a1cc-119">O componente de endereço de um endereço de ponto de extremidade é um identificador de recurso uniforme (URI) que identifica o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-119">The address component of an endpoint address is a Uniform Resource Identifier (URI) that identifies the endpoint.</span></span> <span data-ttu-id="3a1cc-120">O endereço pode ser um endereço de rede ou um endereço lógico.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-120">The address can be a network address or a logical address.</span></span> <span data-ttu-id="3a1cc-121">O endereço pode incluir o nome do computador (nome de host, o nome de domínio totalmente qualificado) e um endereço IP.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-121">The address may include machine name (hostname, fully qualified domain name) and an IP address.</span></span> <span data-ttu-id="3a1cc-122">O endereço do ponto de extremidade também pode conter um identificador global exclusivo (GUID) ou uma coleção de GUIDs para endereçamento temporário usado para distinguir cada endereço.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-122">The endpoint address may also contain a globally unique identifier (GUID), or a collection of GUIDs for temporary addressing used to discern each address.</span></span> <span data-ttu-id="3a1cc-123">Cada mensagem contém uma ID de mensagem que é um GUID.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-123">Each message contains a message ID that is a GUID.</span></span> <span data-ttu-id="3a1cc-124">Esse recurso segue o padrão de referência do WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-124">This feature follows the WS-Addressing reference standard.</span></span>  
  
 <span data-ttu-id="3a1cc-125">O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] camada de mensagens não gravar informações pessoais no computador local.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-125">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] messaging layer does not write any personal information to the local machine.</span></span> <span data-ttu-id="3a1cc-126">No entanto, ele poderá propagar informações pessoais no nível da rede se um desenvolvedor de serviço tiver criado um serviço que expõe essas informações (por exemplo, por usando o nome de uma pessoa em um nome de ponto de extremidade ou, inclusive informações pessoais na Web do ponto de extremidade Serviços de linguagem de descrição, mas não exigir que os clientes usar https para acessar o WSDL).</span><span class="sxs-lookup"><span data-stu-id="3a1cc-126">However, it might propagate personal information at the network level if a service developer has created a service that exposes such information (for example, by using a person's name in an endpoint name, or including personal information in the endpoint's Web Services Description Language but not requiring clients to use https to access the WSDL).</span></span> <span data-ttu-id="3a1cc-127">Além disso, se um desenvolvedor é executado o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta em relação a um ponto de extremidade que expõe informações pessoais, a saída da ferramenta pode conter essas informações e o arquivo de saída é gravado para o disco rígido local.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-127">Also, if a developer runs the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool against an endpoint that exposes personal information, the tool's output could contain that information, and the output file is written to the local hard disk.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="3a1cc-128">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="3a1cc-128">Hosting</span></span>  
 <span data-ttu-id="3a1cc-129">O recurso de hospedagem no [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] permite que os aplicativos para iniciar sob demanda ou para habilitar o compartilhamento de porta entre vários aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-129">The hosting feature in [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] allows applications to start on demand or to enable port sharing between multiple applications.</span></span> <span data-ttu-id="3a1cc-130">Um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativo pode ser hospedado no Internet Information Services (IIS), semelhante ao [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3a1cc-130">An [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] application can be hosted in Internet Information Services (IIS), similar to [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].</span></span>  
  
 <span data-ttu-id="3a1cc-131">Hospedagem não expõem quaisquer informações específicas da rede e não mantém dados no computador.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-131">Hosting does not expose any specific information on the network and it does not keep data on the machine.</span></span>  
  
## <a name="message-security"></a><span data-ttu-id="3a1cc-132">Segurança de mensagem</span><span class="sxs-lookup"><span data-stu-id="3a1cc-132">Message Security</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="3a1cc-133">segurança fornece os recursos de segurança para aplicativos de mensagens.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-133"> security provides the security capabilities for messaging applications.</span></span> <span data-ttu-id="3a1cc-134">As funções de segurança fornecidas incluem autenticação e autorização.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-134">The security functions provided include authentication and authorization.</span></span>  
  
 <span data-ttu-id="3a1cc-135">Autenticação é realizada pela transmissão de credenciais entre clientes e serviços.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-135">Authentication is performed by passing credentials between the clients and services.</span></span> <span data-ttu-id="3a1cc-136">A autenticação pode ser por meio da segurança de nível de transporte ou por meio de SOAP mensagem de nível de segurança, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="3a1cc-136">Authentication can be either through transport-level security or through SOAP message-level security, as follows:</span></span>  
  
-   <span data-ttu-id="3a1cc-137">Na segurança de mensagem SOAP, a autenticação é realizada por meio de credenciais como nome de usuário/senha, certificados x. 509, tíquetes Kerberos e os tokens SAML que podem conter informações pessoais, dependendo do emissor.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-137">In SOAP message security, authentication is performed through credentials like username/passwords, X.509 certificates, Kerberos tickets, and SAML tokens, all of which might contain personal information, depending on the issuer.</span></span>  
  
-   <span data-ttu-id="3a1cc-138">Usando a segurança de transporte, autenticação é feita por meio de mecanismos de autenticação de transporte tradicionais como esquemas de autenticação HTTP (Basic, Digest, Negotiate, NTLM, None, a autorização integrada do Windows e anônimo) e a autenticação de formulário.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-138">Using transport security, authentication is done through traditional transport authentication mechanisms like HTTP authentication schemes (Basic, Digest, Negotiate, Integrated Windows Authorization, NTLM, None, and Anonymous), and form authentication.</span></span>  
  
 <span data-ttu-id="3a1cc-139">A autenticação pode resultar em uma sessão segura estabelecida entre os pontos de extremidade de comunicação.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-139">Authentication can result in a secure session established between the communicating endpoints.</span></span> <span data-ttu-id="3a1cc-140">A sessão é identificada por um GUID que dura o tempo de vida da sessão de segurança.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-140">The session is identified by a GUID that lasts the lifetime of the security session.</span></span> <span data-ttu-id="3a1cc-141">A tabela a seguir mostra o que é mantido e onde.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-141">The following table shows what is kept and where.</span></span>  
  
|<span data-ttu-id="3a1cc-142">Dados</span><span class="sxs-lookup"><span data-stu-id="3a1cc-142">Data</span></span>|<span data-ttu-id="3a1cc-143">Armazenamento</span><span class="sxs-lookup"><span data-stu-id="3a1cc-143">Storage</span></span>|  
|----------|-------------|  
|<span data-ttu-id="3a1cc-144">Credenciais de apresentação, como nome de usuário, certificados x. 509, tokens Kerberos e as referências às credenciais.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-144">Presentation credentials, such as username, X.509 certificates, Kerberos tokens, and references to credentials.</span></span>|<span data-ttu-id="3a1cc-145">Mecanismos de gerenciamento, como o repositório de certificados do Windows de credencial do Windows padrão.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-145">Standard Windows credential management mechanisms such as the Windows certificate store.</span></span>|  
|<span data-ttu-id="3a1cc-146">Informações de associação de usuário, como nomes de usuário e senhas.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-146">User membership information, such as usernames and passwords.</span></span>|[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]<span data-ttu-id="3a1cc-147">provedores de associação.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-147"> membership providers.</span></span>|  
|<span data-ttu-id="3a1cc-148">Informações de identidade sobre o serviço usado para autenticar o serviço para clientes.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-148">Identity information about the service used to authenticate the service to clients.</span></span>|<span data-ttu-id="3a1cc-149">Endereço de ponto de extremidade do serviço.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-149">Endpoint address of the service.</span></span>|  
|<span data-ttu-id="3a1cc-150">Informações do chamador.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-150">Caller information.</span></span>|<span data-ttu-id="3a1cc-151">Logs de auditoria.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-151">Auditing logs.</span></span>|  
  
## <a name="auditing"></a><span data-ttu-id="3a1cc-152">Auditoria</span><span class="sxs-lookup"><span data-stu-id="3a1cc-152">Auditing</span></span>  
 <span data-ttu-id="3a1cc-153">A auditoria registra o êxito ou falha de eventos de autenticação e autorização.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-153">Auditing records the success and failure of authentication and authorization events.</span></span> <span data-ttu-id="3a1cc-154">Registros de auditoria contêm os seguintes dados: serviço URI, URI de ação e identificação do chamador.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-154">Auditing records contain the following data: service URI, action URI, and the caller's identification.</span></span>  
  
 <span data-ttu-id="3a1cc-155">Auditoria também registra quando o administrador modifica a configuração de log de mensagens (ativar ou desativar), porque o log de mensagem pode registrar dados específicos do aplicativo em cabeçalhos e corpos.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-155">Auditing also records when the administrator modifies the configuration of message logging (turning it on or off), because message logging may log application-specific data in headers and bodies.</span></span> <span data-ttu-id="3a1cc-156">Para [!INCLUDE[wxp](../../../includes/wxp-md.md)], um registro é registrado no log de eventos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-156">For [!INCLUDE[wxp](../../../includes/wxp-md.md)], a record is logged in the application event log.</span></span> <span data-ttu-id="3a1cc-157">Para [!INCLUDE[wv](../../../includes/wv-md.md)] e [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], um registro é registrado no log de eventos de segurança.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-157">For [!INCLUDE[wv](../../../includes/wv-md.md)] and [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], a record is logged in the security event log.</span></span>  
  
## <a name="transactions"></a><span data-ttu-id="3a1cc-158">Transações</span><span class="sxs-lookup"><span data-stu-id="3a1cc-158">Transactions</span></span>  
 <span data-ttu-id="3a1cc-159">O recurso de transações fornece serviços de transação para um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-159">The transactions feature provides transactional services to a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] application.</span></span>  
  
 <span data-ttu-id="3a1cc-160">Cabeçalhos de transação usados na propagação de transação podem conter IDs de transação ou IDs de inscrição, que são GUIDs.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-160">Transaction headers used in transaction propagation may contain Transaction IDs or Enlistment IDs, which are GUIDs.</span></span>  
  
 <span data-ttu-id="3a1cc-161">O recurso de transações usa o Gerenciador de transações Microsoft Distributed Transaction coordenador (MSDTC) (um componente do Windows) para gerenciar o estado de transação.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-161">The Transactions feature uses the Microsoft Distributed Transaction Coordinator (MSDTC) Transaction Manager (a Windows component) to manage transaction state.</span></span> <span data-ttu-id="3a1cc-162">Por padrão, as comunicações entre os gerenciadores de transações são criptografadas.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-162">By default, communications between Transactions Managers are encrypted.</span></span> <span data-ttu-id="3a1cc-163">Gerenciadores de transações podem fazer referências de ponto de extremidade, IDs de transação e IDs de inscrição como parte de seu estado durável.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-163">Transaction Managers may log endpoint references, Transaction IDs, and Enlistment IDs as part of their durable state.</span></span> <span data-ttu-id="3a1cc-164">O tempo de vida deste estado é determinado pelo tempo de vida do Gerenciador de transações do arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-164">The lifetime of this state is determined by the lifetime of the Transaction Manager’s log file.</span></span> <span data-ttu-id="3a1cc-165">O serviço MSDTC possui e mantém esse log.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-165">The MSDTC service owns and maintains this log.</span></span>  
  
 <span data-ttu-id="3a1cc-166">O recurso de transações implementa os padrões de coordenação WS e WS-AT.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-166">The Transactions feature implements the WS-Coordination and WS-Atomic Transaction standards.</span></span>  
  
## <a name="reliable-sessions"></a><span data-ttu-id="3a1cc-167">Sessões confiáveis</span><span class="sxs-lookup"><span data-stu-id="3a1cc-167">Reliable Sessions</span></span>  
 <span data-ttu-id="3a1cc-168">Sessões confiáveis em [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] fornecem a transferência de mensagens quando ocorrerem falhas de transporte ou intermediário.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-168">Reliable sessions in [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] provide the transfer of messages when transport or intermediary failures occur.</span></span> <span data-ttu-id="3a1cc-169">Eles fornecem um exatamente-uma vez transferência de mensagens, mesmo quando o transporte subjacente se desconecta (por exemplo, uma conexão TCP em uma rede sem fio) ou perde uma mensagem (um proxy HTTP descartando uma mensagem de entrada ou saída).</span><span class="sxs-lookup"><span data-stu-id="3a1cc-169">They provide an exactly-once transfer of messages even when the underlying transport disconnects (for example, a TCP connection on a wireless network) or loses a message (an HTTP proxy dropping an outgoing or incoming message).</span></span> <span data-ttu-id="3a1cc-170">Sessões confiáveis também recuperar mensagem reordenação (como pode ocorrer no caso de vários caminhos de roteamento), preservando a ordem na qual as mensagens foram enviadas.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-170">Reliable sessions also recover message reordering (as may happen in the case of multipath routing), preserving the order in which the messages were sent.</span></span>  
  
 <span data-ttu-id="3a1cc-171">Sessões confiáveis são implementadas usando o protocolo WS-ReliableMessaging (WS-RM).</span><span class="sxs-lookup"><span data-stu-id="3a1cc-171">Reliable sessions are implemented using the WS-ReliableMessaging (WS-RM) protocol.</span></span> <span data-ttu-id="3a1cc-172">Eles adicionam cabeçalhos de WS-RM que contêm informações de sessão, que são usadas para identificar todas as mensagens associadas a uma determinada sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-172">They add WS-RM headers that contain session information, which is used to identify all messages associated with a particular reliable session.</span></span> <span data-ttu-id="3a1cc-173">Cada sessão do WS-RM tem um identificador, que é um GUID.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-173">Each WS-RM session has an identifier, which is a GUID.</span></span>  
  
 <span data-ttu-id="3a1cc-174">Nenhuma informação pessoal é mantida no computador do usuário final.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-174">No personal information is retained on the end-user's machine.</span></span>  
  
## <a name="queued-channels"></a><span data-ttu-id="3a1cc-175">Canais em fila</span><span class="sxs-lookup"><span data-stu-id="3a1cc-175">Queued Channels</span></span>  
 <span data-ttu-id="3a1cc-176">Filas de armazenam mensagens em um aplicativo de envio em nome de um aplicativo de recebimento e encaminhá-los posteriormente essas mensagens para o aplicativo receptor.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-176">Queues store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span> <span data-ttu-id="3a1cc-177">Eles ajudam a garantir a transferência de mensagens de envio de aplicativos para aplicativos de recebimento quando, por exemplo, o aplicativo de recebimento é transitório.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-177">They help ensure the transfer of messages from sending applications to receiving applications when, for example, the receiving application is transient.</span></span> [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="3a1cc-178">fornece suporte para enfileiramento de mensagens usando o Microsoft Message Queuing (MSMQ) como um transporte.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-178"> provides support for queuing by using Microsoft Message Queuing (MSMQ) as a transport.</span></span>  
  
 <span data-ttu-id="3a1cc-179">O recurso de canais na fila não adiciona cabeçalhos para uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-179">The queued channels feature does not add headers to a message.</span></span> <span data-ttu-id="3a1cc-180">Em vez disso, ele cria uma mensagem de enfileiramento de mensagens com o conjunto de propriedades de mensagem de enfileiramento de mensagens apropriado e invoca métodos de enfileiramento de mensagens para colocar a mensagem na fila do serviço de enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-180">Instead it creates a Message Queuing message with appropriate Message Queuing message properties set, and invokes Message Queuing methods to put the message in the Message Queuing queue.</span></span> <span data-ttu-id="3a1cc-181">O Message Queuing é um componente opcional que é fornecido com o Windows.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-181">Message Queuing is an optional component that ships with Windows.</span></span>  
  
 <span data-ttu-id="3a1cc-182">Nenhuma informação é mantida no computador do usuário final do recurso de canais em fila, pois ele usa o enfileiramento de mensagens como a infraestrutura de enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-182">No information is retained on the end-user's machine by the queued channels feature, because it uses Message Queuing as the queuing infrastructure.</span></span>  
  
## <a name="com-integration"></a><span data-ttu-id="3a1cc-183">Integração de COM+</span><span class="sxs-lookup"><span data-stu-id="3a1cc-183">COM+ Integration</span></span>  
 <span data-ttu-id="3a1cc-184">Esse recurso encapsula a funcionalidade existente e COM COM+ para criar serviços que são compatíveis com [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviços.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-184">This feature wraps existing COM and COM+ functionality to create services that are compatible with [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services.</span></span> <span data-ttu-id="3a1cc-185">Esse recurso não usa cabeçalhos específicos e ela não retém dados no computador do usuário final.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-185">This feature does not use specific headers and it does not retain data on the end-user's machine.</span></span>  
  
## <a name="com-service-moniker"></a><span data-ttu-id="3a1cc-186">Moniker de serviço COM</span><span class="sxs-lookup"><span data-stu-id="3a1cc-186">COM Service Moniker</span></span>  
 <span data-ttu-id="3a1cc-187">Isso fornece um wrapper gerenciado para um padrão [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] cliente.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-187">This provides an unmanaged wrapper to a standard [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client.</span></span> <span data-ttu-id="3a1cc-188">Este recurso não tem cabeçalhos específicos na conexão nem ele persistir dados no computador.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-188">This feature does not have specific headers on the wire nor does it persist data on the machine.</span></span>  
  
## <a name="peer-channel"></a><span data-ttu-id="3a1cc-189">Canal par</span><span class="sxs-lookup"><span data-stu-id="3a1cc-189">Peer Channel</span></span>  
 <span data-ttu-id="3a1cc-190">Um canal par permite o desenvolvimento de aplicativos com vários participantes usando [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3a1cc-190">A peer channel enables development of multiparty applications using [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="3a1cc-191">Mensagens entre vários participantes ocorre no contexto de uma malha.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-191">Multiparty messaging occurs in the context of a mesh.</span></span> <span data-ttu-id="3a1cc-192">Malhas são identificadas por um nome que podem ingressar em nós.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-192">Meshes are identified by a name that nodes can join.</span></span> <span data-ttu-id="3a1cc-193">Cada nó no canal de ponto a ponto cria um ouvinte TCP em uma porta especificada pelo usuário e estabelece conexões com outros nós da malha para garantir a resiliência.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-193">Each node in the peer channel creates a TCP listener at a user-specified port and establishes connections with other nodes in the mesh to ensure resiliency.</span></span> <span data-ttu-id="3a1cc-194">Para se conectar a outros nós da malha, nós também trocam alguns dados, incluindo o endereço de ouvinte e endereços IP da máquina, com outros nós da malha.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-194">To connect to other nodes in the mesh, nodes also exchange some data, including the listener address and the machine's IP addresses, with other nodes in the mesh.</span></span> <span data-ttu-id="3a1cc-195">As mensagens enviadas ao redor da malha podem conter informações de segurança que pertencem ao remetente para evitar a falsificação de mensagem e a violação.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-195">Messages sent around in the mesh can contain security information that pertains to the sender to prevent message spoofing and tampering.</span></span>  
  
 <span data-ttu-id="3a1cc-196">Nenhuma informação pessoal é armazenada no computador do usuário final.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-196">No personal information is stored on the end-user's machine.</span></span>  
  
## <a name="it-professional-experience"></a><span data-ttu-id="3a1cc-197">Experiência de profissionais de TI</span><span class="sxs-lookup"><span data-stu-id="3a1cc-197">IT Professional Experience</span></span>  
  
### <a name="tracing"></a><span data-ttu-id="3a1cc-198">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="3a1cc-198">Tracing</span></span>  
 <span data-ttu-id="3a1cc-199">O recurso de diagnóstico do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] as mensagens que passam pelas camadas de modelo de serviço e transporte de logs de infraestrutura e as atividades e os eventos associados a essas mensagens.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-199">The diagnostics feature of the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] infrastructure logs messages that pass through the transport and service model layers, and the activities and events associated with these messages.</span></span> <span data-ttu-id="3a1cc-200">Esse recurso é desativado por padrão.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-200">This feature is turned off by default.</span></span> <span data-ttu-id="3a1cc-201">Ele é habilitado usando o arquivo de configuração do aplicativo e o comportamento de rastreamento pode ser modificado usando o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] provedor WMI em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-201">It is enabled using the application’s configuration file and the tracing behavior may be modified using the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] WMI provider at run time.</span></span> <span data-ttu-id="3a1cc-202">Quando habilitada, a infraestrutura de rastreamento emite um rastreamento de diagnóstico que contém as mensagens, atividades e eventos de processamento para ouvintes configurados.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-202">When enabled, the tracing infrastructure emits a diagnostic trace that contains messages, activities, and processing events to configured listeners.</span></span> <span data-ttu-id="3a1cc-203">O formato e o local de saída são determinados por opções de configuração de ouvinte do administrador, mas geralmente é um arquivo XML formatado.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-203">The format and location of the output are determined by the administrator’s listener configuration choices, but is typically an XML formatted file.</span></span> <span data-ttu-id="3a1cc-204">O administrador é responsável por definir a lista de controle de acesso (ACL) nos arquivos de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-204">The administrator is responsible for setting the access control list (ACL) on the trace files.</span></span> <span data-ttu-id="3a1cc-205">Em particular, quando hospedados pelo sistema de ativação do Windows (WAS), o administrador deve assegurar que os arquivos não são atendidos do diretório raiz virtual público se não for desejada.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-205">In particular, when hosted by Windows Activation System (WAS), the administrator should make sure the files are not served from the public virtual root directory if that is not desired.</span></span>  
  
 <span data-ttu-id="3a1cc-206">Há dois tipos de rastreamento: log de mensagens e diagnóstico do modelo de serviço de rastreamento, descrito na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-206">There are two types of tracing: Message logging and Service Model diagnostic tracing, described in the following section.</span></span> <span data-ttu-id="3a1cc-207">Cada tipo é configurado por meio de sua própria fonte de rastreamento: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> e <xref:System.ServiceModel>.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-207">Each type is configured through its own trace source: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> and <xref:System.ServiceModel>.</span></span> <span data-ttu-id="3a1cc-208">Ambas essas fontes de rastreamento de log capturar dados é locais para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-208">Both of these logging trace sources capture data that is local to the application.</span></span>  
  
### <a name="message-logging"></a><span data-ttu-id="3a1cc-209">Registro em log de mensagens</span><span class="sxs-lookup"><span data-stu-id="3a1cc-209">Message Logging</span></span>  
 <span data-ttu-id="3a1cc-210">A mensagem de log de origem de rastreamento (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) permite que um administrador as mensagens de log fluxo por meio do sistema.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-210">The message logging trace source (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) allows an administrator to log the messages that flow through the system.</span></span> <span data-ttu-id="3a1cc-211">Por meio de configuração, o usuário pode optar por registrar mensagens inteiras ou somente os cabeçalhos de mensagem, se deseja registrar nas camadas de modelo de transporte e/ou o serviço e se deseja incluir mensagens malformadas.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-211">Through configuration, the user may decide to log entire messages or message headers only, whether to log at the transport and/or service model layers, and whether to include malformed messages.</span></span> <span data-ttu-id="3a1cc-212">Além disso, o usuário pode configurar a filtragem para restringir quais mensagens são registradas em log.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-212">Also, the user may configure filtering to restrict which messages are logged.</span></span>  
  
 <span data-ttu-id="3a1cc-213">Por padrão, o log de mensagens está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-213">By default, message logging is disabled.</span></span> <span data-ttu-id="3a1cc-214">O administrador do computador local pode impedir que o administrador de nível de aplicativo ativar registro em log de mensagem.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-214">The local machine administrator can prevent the application-level administrator from turning message logging on.</span></span>  
  
#### <a name="encrypted-and-decrypted-message-logging"></a><span data-ttu-id="3a1cc-215">Registro de mensagem criptografados e descriptografados</span><span class="sxs-lookup"><span data-stu-id="3a1cc-215">Encrypted and Decrypted Message Logging</span></span>  
 <span data-ttu-id="3a1cc-216">Mensagens são registradas, criptografadas ou descriptografadas, conforme descrito nos seguintes termos.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-216">Messages are logged, encrypted, or decrypted, as described in the following terms.</span></span>  
  
 <span data-ttu-id="3a1cc-217">Registro de transporte</span><span class="sxs-lookup"><span data-stu-id="3a1cc-217">Transport Logging</span></span>  
 <span data-ttu-id="3a1cc-218">Registra mensagens recebidas e enviadas no nível do transporte.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-218">Logs messages received and sent at the transport level.</span></span> <span data-ttu-id="3a1cc-219">Essas mensagens contêm todos os cabeçalhos e podem ser criptografadas antes de serem enviados na conexão e, quando está sendo recebida.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-219">These messages contain all headers, and may be encrypted before being sent on the wire and when being received.</span></span>  
  
 <span data-ttu-id="3a1cc-220">Se as mensagens são criptografadas antes de serem enviados na conexão e quando elas são recebidas, elas são registradas criptografados.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-220">If messages are encrypted before being sent on the wire and when they are received, they are logged encrypted as well.</span></span> <span data-ttu-id="3a1cc-221">Uma exceção ocorre quando um protocolo de segurança é usado (https): elas são registradas, em seguida, descriptografados antes de serem enviados e depois que está sendo recebida mesmo se forem criptografados durante a transmissão.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-221">An exception is when a security protocol is used (https): they are then logged decrypted before being sent and after being received even if they are encrypted on the wire.</span></span>  
  
 <span data-ttu-id="3a1cc-222">Log de serviço</span><span class="sxs-lookup"><span data-stu-id="3a1cc-222">Service Logging</span></span>  
 <span data-ttu-id="3a1cc-223">Registra mensagens recebidos ou enviados no nível do modelo de serviço, após o processamento de cabeçalho do canal tiver ocorrido, antes e depois de inserir o código do usuário.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-223">Logs messages received or sent at the service model level, after channel header processing has occurred, just before and after entering user code.</span></span>  
  
 <span data-ttu-id="3a1cc-224">Mensagens registradas nesse nível são descriptografadas, mesmo se eles foram protegidos e criptografados na conexão.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-224">Messages logged at this level are decrypted even if they were secured and encrypted on the wire.</span></span>  
  
 <span data-ttu-id="3a1cc-225">Log de mensagem malformada</span><span class="sxs-lookup"><span data-stu-id="3a1cc-225">Malformed Message Logging</span></span>  
 <span data-ttu-id="3a1cc-226">Logs de mensagens que o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] infraestrutura não é possível entender ou processar.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-226">Logs messages that the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] infrastructure cannot understand or process.</span></span>  
  
 <span data-ttu-id="3a1cc-227">As mensagens são registradas como-ou seja, é, criptografada ou não</span><span class="sxs-lookup"><span data-stu-id="3a1cc-227">Messages are logged as-is, that is, encrypted or not</span></span>  
  
 <span data-ttu-id="3a1cc-228">Quando as mensagens são registradas no descriptografado ou sem criptografia, por padrão [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] remove as chaves de segurança e informações pessoais potencialmente as mensagens antes de registrá-los.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-228">When messages are logged in decrypted or unencrypted form, by default [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] removes security keys and potentially personal information from the messages before logging them.</span></span> <span data-ttu-id="3a1cc-229">As próximas seções descrevem quais informações são removidas e quando.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-229">The next sections describe what information is removed, and when.</span></span> <span data-ttu-id="3a1cc-230">O administrador do computador e ambos implantador do aplicativo deve executar determinadas ações de configuração para alterar o comportamento padrão para chaves e as informações pessoais potencialmente de log.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-230">The machine administrator and application deployer must both take certain configuration actions to change the default behavior to log keys and potentially personal information.</span></span>  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="3a1cc-231">Informações removidas dos cabeçalhos de mensagem ao registrar em log mensagens descriptografados/não criptografado</span><span class="sxs-lookup"><span data-stu-id="3a1cc-231">Information Removed from Message Headers When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="3a1cc-232">Quando mensagens são registradas na forma descriptografada/sem criptografia, chaves de segurança e informações pessoais potencialmente são removidos por padrão de cabeçalhos e corpos de mensagens antes que elas são registradas.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-232">When messages are logged in decrypted/unencrypted form, security keys and potentially personal information are removed by default from message headers and message bodies before they are logged.</span></span> <span data-ttu-id="3a1cc-233">A lista a seguir mostra o que [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] considera as chaves e as informações potencialmente pessoais.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-233">The following list shows what [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] considers keys and potentially personal information.</span></span>  
  
 <span data-ttu-id="3a1cc-234">Chaves são removidas:</span><span class="sxs-lookup"><span data-stu-id="3a1cc-234">Keys that are removed:</span></span>  
  
 <span data-ttu-id="3a1cc-235">\-Para xmlns:wst = "http://schemas.xmlsoap.org/ws/2004/04/trust" e xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust"</span><span class="sxs-lookup"><span data-stu-id="3a1cc-235">\- For xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"</span></span>  
  
 <span data-ttu-id="3a1cc-236">WST:BinarySecret</span><span class="sxs-lookup"><span data-stu-id="3a1cc-236">wst:BinarySecret</span></span>  
  
 <span data-ttu-id="3a1cc-237">WST:Entropy</span><span class="sxs-lookup"><span data-stu-id="3a1cc-237">wst:Entropy</span></span>  
  
 <span data-ttu-id="3a1cc-238">\-Para xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" e xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span><span class="sxs-lookup"><span data-stu-id="3a1cc-238">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="3a1cc-239">wsse:password</span><span class="sxs-lookup"><span data-stu-id="3a1cc-239">wsse:Password</span></span>  
  
 <span data-ttu-id="3a1cc-240">wsse:nonce</span><span class="sxs-lookup"><span data-stu-id="3a1cc-240">wsse:Nonce</span></span>  
  
 <span data-ttu-id="3a1cc-241">Informações potencialmente pessoais que são removidas:</span><span class="sxs-lookup"><span data-stu-id="3a1cc-241">Potentially personal information that is removed:</span></span>  
  
 <span data-ttu-id="3a1cc-242">\-Para xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" e xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span><span class="sxs-lookup"><span data-stu-id="3a1cc-242">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="3a1cc-243">wsse:username</span><span class="sxs-lookup"><span data-stu-id="3a1cc-243">wsse:Username</span></span>  
  
 <span data-ttu-id="3a1cc-244">wsse:BinarySecurityToken</span><span class="sxs-lookup"><span data-stu-id="3a1cc-244">wsse:BinarySecurityToken</span></span>  
  
 <span data-ttu-id="3a1cc-245">\-Para xmlns:saml = "urn: oasis: nomes: tc: SAML:1.0:assertion" os itens em negrito (abaixo) são removidos:</span><span class="sxs-lookup"><span data-stu-id="3a1cc-245">\- For xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion" the items in bold (below) are removed:</span></span>  
  
 <span data-ttu-id="3a1cc-246">\<Asserção</span><span class="sxs-lookup"><span data-stu-id="3a1cc-246">\<Assertion</span></span>  
  
 <span data-ttu-id="3a1cc-247">MajorVersion = "1"</span><span class="sxs-lookup"><span data-stu-id="3a1cc-247">MajorVersion="1"</span></span>  
  
 <span data-ttu-id="3a1cc-248">MinorVersion = "1"</span><span class="sxs-lookup"><span data-stu-id="3a1cc-248">MinorVersion="1"</span></span>  
  
 <span data-ttu-id="3a1cc-249">AssertionId = "[ID]"</span><span class="sxs-lookup"><span data-stu-id="3a1cc-249">AssertionId="[ID]"</span></span>  
  
 <span data-ttu-id="3a1cc-250">Emissor = "[string]"</span><span class="sxs-lookup"><span data-stu-id="3a1cc-250">Issuer="[string]"</span></span>  
  
 <span data-ttu-id="3a1cc-251">IssueInstant = "[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="3a1cc-251">IssueInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="3a1cc-252">\<Condições NotBefore = "[dateTime]" NotOnOrAfter = "[dateTime]" ></span><span class="sxs-lookup"><span data-stu-id="3a1cc-252">\<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]"></span></span>  
  
 <span data-ttu-id="3a1cc-253">\<AudienceRestrictionCondition ></span><span class="sxs-lookup"><span data-stu-id="3a1cc-253">\<AudienceRestrictionCondition></span></span>  
  
 <span data-ttu-id="3a1cc-254">\<Público-alvo > [uri]\</Audience > +</span><span class="sxs-lookup"><span data-stu-id="3a1cc-254">\<Audience>[uri]\</Audience>+</span></span>  
  
 <span data-ttu-id="3a1cc-255">\</ AudienceRestrictionCondition > *</span><span class="sxs-lookup"><span data-stu-id="3a1cc-255">\</AudienceRestrictionCondition>*</span></span>  
  
 <span data-ttu-id="3a1cc-256">\<DoNotCacheCondition / > *</span><span class="sxs-lookup"><span data-stu-id="3a1cc-256">\<DoNotCacheCondition />*</span></span>  
  
 <span data-ttu-id="3a1cc-257"><\!– o tipo base abstrato</span><span class="sxs-lookup"><span data-stu-id="3a1cc-257"><\!-- abstract base type</span></span>  
  
 <span data-ttu-id="3a1cc-258">\<Condição / > *</span><span class="sxs-lookup"><span data-stu-id="3a1cc-258">\<Condition />*</span></span>  
  
 -->  
  
 <span data-ttu-id="3a1cc-259">\</ Condições >?</span><span class="sxs-lookup"><span data-stu-id="3a1cc-259">\</Conditions>?</span></span>  
  
 <span data-ttu-id="3a1cc-260">\<Aviso ></span><span class="sxs-lookup"><span data-stu-id="3a1cc-260">\<Advice></span></span>  
  
 <span data-ttu-id="3a1cc-261">\<AssertionIDReference > [ID]\</AssertionIDReference > *</span><span class="sxs-lookup"><span data-stu-id="3a1cc-261">\<AssertionIDReference>[ID]\</AssertionIDReference>*</span></span>  
  
 <span data-ttu-id="3a1cc-262">\<Asserção > [asserção]\</Assertion > *</span><span class="sxs-lookup"><span data-stu-id="3a1cc-262">\<Assertion>[assertion]\</Assertion>*</span></span>  
  
 <span data-ttu-id="3a1cc-263">[Nenhum] *</span><span class="sxs-lookup"><span data-stu-id="3a1cc-263">[any]*</span></span>  
  
 <span data-ttu-id="3a1cc-264">\</ Aviso >?</span><span class="sxs-lookup"><span data-stu-id="3a1cc-264">\</Advice>?</span></span>  
  
 <span data-ttu-id="3a1cc-265"><\!-Tipos de base abstratos</span><span class="sxs-lookup"><span data-stu-id="3a1cc-265"><\!-- Abstract base types</span></span>  
  
 <span data-ttu-id="3a1cc-266">\<Instrução / > *</span><span class="sxs-lookup"><span data-stu-id="3a1cc-266">\<Statement />*</span></span>  
  
 <span data-ttu-id="3a1cc-267">\<SubjectStatement ></span><span class="sxs-lookup"><span data-stu-id="3a1cc-267">\<SubjectStatement></span></span>  
  
 <span data-ttu-id="3a1cc-268">\<Assunto ></span><span class="sxs-lookup"><span data-stu-id="3a1cc-268">\<Subject></span></span>  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 <span data-ttu-id="3a1cc-269">\<SubjectConfirmation ></span><span class="sxs-lookup"><span data-stu-id="3a1cc-269">\<SubjectConfirmation></span></span>  
  
 <span data-ttu-id="3a1cc-270">\<ConfirmationMethod > [anyUri]\</ConfirmationMethod > +</span><span class="sxs-lookup"><span data-stu-id="3a1cc-270">\<ConfirmationMethod>[anyUri]\</ConfirmationMethod>+</span></span>  
  
 <span data-ttu-id="3a1cc-271">\<SubjectConfirmationData > [qualquer]\</SubjectConfirmationData >?</span><span class="sxs-lookup"><span data-stu-id="3a1cc-271">\<SubjectConfirmationData>[any]\</SubjectConfirmationData>?</span></span>  
  
 <span data-ttu-id="3a1cc-272">\<DS:KeyInfo >... \</ds:KeyInfo >?</span><span class="sxs-lookup"><span data-stu-id="3a1cc-272">\<ds:KeyInfo>...\</ds:KeyInfo>?</span></span>  
  
 <span data-ttu-id="3a1cc-273">\</ SubjectConfirmation >?</span><span class="sxs-lookup"><span data-stu-id="3a1cc-273">\</SubjectConfirmation>?</span></span>  
  
 <span data-ttu-id="3a1cc-274">\</ Assunto ></span><span class="sxs-lookup"><span data-stu-id="3a1cc-274">\</Subject></span></span>  
  
 <span data-ttu-id="3a1cc-275">\</ SubjectStatement > *</span><span class="sxs-lookup"><span data-stu-id="3a1cc-275">\</SubjectStatement>*</span></span>  
  
 -->  
  
 <span data-ttu-id="3a1cc-276">\<AuthenticationStatement</span><span class="sxs-lookup"><span data-stu-id="3a1cc-276">\<AuthenticationStatement</span></span>  
  
 <span data-ttu-id="3a1cc-277">AuthenticationMethod = "[uri]"</span><span class="sxs-lookup"><span data-stu-id="3a1cc-277">AuthenticationMethod="[uri]"</span></span>  
  
 <span data-ttu-id="3a1cc-278">AuthenticationInstant = "[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="3a1cc-278">AuthenticationInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="3a1cc-279">[Assunto]</span><span class="sxs-lookup"><span data-stu-id="3a1cc-279">[Subject]</span></span>  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 <span data-ttu-id="3a1cc-280">< AuthorityBinding</span><span class="sxs-lookup"><span data-stu-id="3a1cc-280"><AuthorityBinding</span></span>  
  
 <span data-ttu-id="3a1cc-281">AuthorityKind = "[QName]"</span><span class="sxs-lookup"><span data-stu-id="3a1cc-281">AuthorityKind="[QName]"</span></span>  
  
 <span data-ttu-id="3a1cc-282">Local = "[uri]"</span><span class="sxs-lookup"><span data-stu-id="3a1cc-282">Location="[uri]"</span></span>  
  
 <span data-ttu-id="3a1cc-283">Ligação = "[uri]"</span><span class="sxs-lookup"><span data-stu-id="3a1cc-283">Binding="[uri]"</span></span>  
  
 />*  
  
 <span data-ttu-id="3a1cc-284">\</ AuthenticationStatement > *</span><span class="sxs-lookup"><span data-stu-id="3a1cc-284">\</AuthenticationStatement>*</span></span>  
  
 <span data-ttu-id="3a1cc-285">\<AttributeStatement ></span><span class="sxs-lookup"><span data-stu-id="3a1cc-285">\<AttributeStatement></span></span>  
  
 <span data-ttu-id="3a1cc-286">[Assunto]</span><span class="sxs-lookup"><span data-stu-id="3a1cc-286">[Subject]</span></span>  
  
 <span data-ttu-id="3a1cc-287">\<Atributo</span><span class="sxs-lookup"><span data-stu-id="3a1cc-287">\<Attribute</span></span>  
  
 <span data-ttu-id="3a1cc-288">AttributeName = "[string]"</span><span class="sxs-lookup"><span data-stu-id="3a1cc-288">AttributeName="[string]"</span></span>  
  
 <span data-ttu-id="3a1cc-289">AttributeNamespace = "[uri]"</span><span class="sxs-lookup"><span data-stu-id="3a1cc-289">AttributeNamespace="[uri]"</span></span>  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 <span data-ttu-id="3a1cc-290">\</ Atributo > +</span><span class="sxs-lookup"><span data-stu-id="3a1cc-290">\</Attribute>+</span></span>  
  
 <span data-ttu-id="3a1cc-291">\</ AttributeStatement > *</span><span class="sxs-lookup"><span data-stu-id="3a1cc-291">\</AttributeStatement>*</span></span>  
  
 <span data-ttu-id="3a1cc-292">\<AuthorizationDecisionStatement</span><span class="sxs-lookup"><span data-stu-id="3a1cc-292">\<AuthorizationDecisionStatement</span></span>  
  
 <span data-ttu-id="3a1cc-293">Recurso = "[uri]"</span><span class="sxs-lookup"><span data-stu-id="3a1cc-293">Resource="[uri]"</span></span>  
  
 <span data-ttu-id="3a1cc-294">Decisão = "[permitir &#124; Deny &#124; indeterminado]"</span><span class="sxs-lookup"><span data-stu-id="3a1cc-294">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span></span>  
  
 >  
  
 <span data-ttu-id="3a1cc-295">[Assunto]</span><span class="sxs-lookup"><span data-stu-id="3a1cc-295">[Subject]</span></span>  
  
 <span data-ttu-id="3a1cc-296">\<Ação Namespace = "[uri]" > [string]\</Action > +</span><span class="sxs-lookup"><span data-stu-id="3a1cc-296">\<Action Namespace="[uri]">[string]\</Action>+</span></span>  
  
 <span data-ttu-id="3a1cc-297">\<Evidência ></span><span class="sxs-lookup"><span data-stu-id="3a1cc-297">\<Evidence></span></span>  
  
 <span data-ttu-id="3a1cc-298">\<AssertionIDReference > [ID]\</AssertionIDReference > +</span><span class="sxs-lookup"><span data-stu-id="3a1cc-298">\<AssertionIDReference>[ID]\</AssertionIDReference>+</span></span>  
  
 <span data-ttu-id="3a1cc-299">\<Asserção > [asserção]\</Assertion > +</span><span class="sxs-lookup"><span data-stu-id="3a1cc-299">\<Assertion>[assertion]\</Assertion>+</span></span>  
  
 <span data-ttu-id="3a1cc-300">\</ Evidência >?</span><span class="sxs-lookup"><span data-stu-id="3a1cc-300">\</Evidence>?</span></span>  
  
 <span data-ttu-id="3a1cc-301">\</ AuthorizationDecisionStatement > *</span><span class="sxs-lookup"><span data-stu-id="3a1cc-301">\</AuthorizationDecisionStatement>*</span></span>  
  
 <span data-ttu-id="3a1cc-302">\</ Asserção ></span><span class="sxs-lookup"><span data-stu-id="3a1cc-302">\</Assertion></span></span>  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="3a1cc-303">Informações removidas de corpos de mensagens ao registrar em log mensagens descriptografados/não criptografado</span><span class="sxs-lookup"><span data-stu-id="3a1cc-303">Information Removed from Message Bodies When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="3a1cc-304">Conforme descrito anteriormente, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] remove chaves e informações potencialmente pessoais dos cabeçalhos da mensagem para mensagens registradas descriptografados/sem criptografia.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-304">As previously described, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] removes keys and known potentially personal information from message headers for logged decrypted/unencrypted messages.</span></span> <span data-ttu-id="3a1cc-305">Além disso, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] remove as chaves e informações pessoais potencialmente corpos de mensagens para os elementos do corpo e as ações na lista a seguir, que descrevem as mensagens de segurança envolvidas na troca de chaves.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-305">In addition, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] removes keys and known potentially personal information from message bodies for the body elements and actions in the following list, which describe security messages involved in key exchange.</span></span>  
  
 <span data-ttu-id="3a1cc-306">Para os namespaces a seguir:</span><span class="sxs-lookup"><span data-stu-id="3a1cc-306">For the following namespaces:</span></span>  
  
 <span data-ttu-id="3a1cc-307">xmlns:WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" e xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust" (por exemplo, se nenhuma ação disponível)</span><span class="sxs-lookup"><span data-stu-id="3a1cc-307">xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust" (for example, if no action available)</span></span>  
  
 <span data-ttu-id="3a1cc-308">Informações serão removidas para esses elementos do corpo, que envolve a troca de chaves:</span><span class="sxs-lookup"><span data-stu-id="3a1cc-308">Information is removed for these body elements, which involve key exchange:</span></span>  
  
 <span data-ttu-id="3a1cc-309">WST:RequestSecurityToken</span><span class="sxs-lookup"><span data-stu-id="3a1cc-309">wst:RequestSecurityToken</span></span>  
  
 <span data-ttu-id="3a1cc-310">WST:RequestSecurityTokenResponse</span><span class="sxs-lookup"><span data-stu-id="3a1cc-310">wst:RequestSecurityTokenResponse</span></span>  
  
 <span data-ttu-id="3a1cc-311">WST:RequestSecurityTokenResponseCollection</span><span class="sxs-lookup"><span data-stu-id="3a1cc-311">wst:RequestSecurityTokenResponseCollection</span></span>  
  
 <span data-ttu-id="3a1cc-312">Informações também são removidas para cada uma das seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="3a1cc-312">Information is also removed for each of the following Actions:</span></span>  
  
 <span data-ttu-id="3a1cc-313">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue</span><span class="sxs-lookup"><span data-stu-id="3a1cc-313">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue</span></span>  
  
 <span data-ttu-id="3a1cc-314">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue</span><span class="sxs-lookup"><span data-stu-id="3a1cc-314">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue</span></span>  
  
 <span data-ttu-id="3a1cc-315">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/renew</span><span class="sxs-lookup"><span data-stu-id="3a1cc-315">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew</span></span>  
  
 <span data-ttu-id="3a1cc-316">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/renew</span><span class="sxs-lookup"><span data-stu-id="3a1cc-316">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew</span></span>  
  
 <span data-ttu-id="3a1cc-317">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel</span><span class="sxs-lookup"><span data-stu-id="3a1cc-317">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel</span></span>  
  
 <span data-ttu-id="3a1cc-318">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel</span><span class="sxs-lookup"><span data-stu-id="3a1cc-318">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel</span></span>  
  
 <span data-ttu-id="3a1cc-319">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate</span><span class="sxs-lookup"><span data-stu-id="3a1cc-319">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate</span></span>  
  
 <span data-ttu-id="3a1cc-320">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate</span><span class="sxs-lookup"><span data-stu-id="3a1cc-320">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate</span></span>  
  
 <span data-ttu-id="3a1cc-321">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT</span><span class="sxs-lookup"><span data-stu-id="3a1cc-321">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT</span></span>  
  
 <span data-ttu-id="3a1cc-322">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT</span><span class="sxs-lookup"><span data-stu-id="3a1cc-322">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT</span></span>  
  
 <span data-ttu-id="3a1cc-323">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend</span><span class="sxs-lookup"><span data-stu-id="3a1cc-323">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend</span></span>  
  
 <span data-ttu-id="3a1cc-324">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend</span><span class="sxs-lookup"><span data-stu-id="3a1cc-324">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend</span></span>  
  
 <span data-ttu-id="3a1cc-325">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/renew</span><span class="sxs-lookup"><span data-stu-id="3a1cc-325">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew</span></span>  
  
 <span data-ttu-id="3a1cc-326">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/renew</span><span class="sxs-lookup"><span data-stu-id="3a1cc-326">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew</span></span>  
  
 <span data-ttu-id="3a1cc-327">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel</span><span class="sxs-lookup"><span data-stu-id="3a1cc-327">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel</span></span>  
  
 <span data-ttu-id="3a1cc-328">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel</span><span class="sxs-lookup"><span data-stu-id="3a1cc-328">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel</span></span>  
  
 <span data-ttu-id="3a1cc-329">http://schemas.xmlsoap.org/ws/2004/04/Security/Trust/RST/SCT</span><span class="sxs-lookup"><span data-stu-id="3a1cc-329">http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT</span></span>  
  
 <span data-ttu-id="3a1cc-330">http://schemas.xmlsoap.org/ws/2004/04/Security/Trust/RSTR/SCT</span><span class="sxs-lookup"><span data-stu-id="3a1cc-330">http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT</span></span>  
  
 <span data-ttu-id="3a1cc-331">http://schemas.xmlsoap.org/ws/2004/04/Security/Trust/RST/SCT-Amend</span><span class="sxs-lookup"><span data-stu-id="3a1cc-331">http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend</span></span>  
  
 <span data-ttu-id="3a1cc-332">http://schemas.xmlsoap.org/ws/2004/04/Security/Trust/RSTR/SCT-Amend</span><span class="sxs-lookup"><span data-stu-id="3a1cc-332">http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend</span></span>  
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a><span data-ttu-id="3a1cc-333">Nenhuma informação é removida da cabeçalhos específicos de aplicativos e dados do corpo</span><span class="sxs-lookup"><span data-stu-id="3a1cc-333">No Information Is Removed from Application-specific Headers and Body Data</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="3a1cc-334">não rastreia informações pessoais em cabeçalhos específicos do aplicativo (por exemplo, cadeias de consulta) ou o corpo de dados (por exemplo, o número do cartão de crédito).</span><span class="sxs-lookup"><span data-stu-id="3a1cc-334"> does not track personal information in application-specific headers (for example, query strings) or body data (for example, credit card number).</span></span>  
  
 <span data-ttu-id="3a1cc-335">Quando o log de mensagens estiver ativada, informações pessoais em cabeçalhos específicos do aplicativo e as informações de corpo podem estar visíveis nos logs.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-335">When message logging is on, personal information in application-specific headers and body information may be visible in the logs.</span></span> <span data-ttu-id="3a1cc-336">Novamente, o implantador de aplicativo é responsável por definir as ACLs nos arquivos de configuração e de log.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-336">Again, the application deployer is responsible for setting the ACLs on the configuration and log files.</span></span> <span data-ttu-id="3a1cc-337">Ele também pode desativar registro se ele não quer que essa informação fique visível, ou ele pode filtrar essas informações dos arquivos de log depois que ele está registrado.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-337">He also can turn off logging if he does not want this information to be visible, or he may filter out this information from the log files after it is logged.</span></span>  
  
### <a name="service-model-tracing"></a><span data-ttu-id="3a1cc-338">Rastreamento de modelo de serviço</span><span class="sxs-lookup"><span data-stu-id="3a1cc-338">Service Model Tracing</span></span>  
 <span data-ttu-id="3a1cc-339">A origem de rastreamento de modelo de serviço (<xref:System.ServiceModel>) habilita o rastreamento de eventos e as atividades relacionadas ao processamento de mensagem.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-339">The Service Model trace source (<xref:System.ServiceModel>) enables tracing of activities and events related to message processing.</span></span> <span data-ttu-id="3a1cc-340">Esse recurso usa a funcionalidade de diagnóstico do .NET Framework do <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-340">This feature uses the .NET Framework diagnostic functionality from <xref:System.Diagnostics>.</span></span> <span data-ttu-id="3a1cc-341">Assim como acontece com o <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> propriedade, o local e sua ACL são configuráveis pelo usuário usando arquivos de configuração de aplicativo do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-341">As with the <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> property, the location and its ACL are user-configurable using .NET Framework application configuration files.</span></span> <span data-ttu-id="3a1cc-342">Como com o log de mensagem, o local do arquivo é sempre configurado quando o administrador habilita o rastreamento; Assim, o administrador controla a ACL.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-342">As with message logging, the file location is always configured when the administrator enables tracing; thus, the administrator controls the ACL.</span></span>  
  
 <span data-ttu-id="3a1cc-343">Quando uma mensagem no escopo, os rastreamentos contêm cabeçalhos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-343">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="3a1cc-344">Aplicam as mesmas regras para ocultar informações potencialmente pessoais em cabeçalhos de mensagem na seção anterior: as informações pessoais identificadas anteriormente foram removidas por padrão de cabeçalhos em rastreamentos.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-344">The same rules for hiding potentially personal information in message headers in the previous section apply: the personal information previously identified is removed by default from the headers in traces.</span></span> <span data-ttu-id="3a1cc-345">O administrador da máquina e o implantador de aplicativo devem modificar a configuração para registrar informações potencialmente pessoais.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-345">Both the machine administrator and the application deployer must modify the configuration in order to log potentially personal information.</span></span> <span data-ttu-id="3a1cc-346">No entanto, informações pessoais contidas nos cabeçalhos específicos do aplicativo são registradas em rastreamentos.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-346">However, personal information contained in application-specific headers is logged in traces.</span></span> <span data-ttu-id="3a1cc-347">O implantador de aplicativo é responsável por definir as ACLs nos arquivos de configuração e o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-347">The application deployer is responsible for setting the ACLs on the configuration and trace files.</span></span> <span data-ttu-id="3a1cc-348">Ele também pode desativar o rastreamento se ele não quer que essa informação fique visível, ou ele pode filtrar essas informações dos arquivos de rastreamento depois que ele está registrado.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-348">He also can turn off tracing if he does not want this information to be visible, or he can filter out this information from the trace files after it is logged.</span></span>  
  
 <span data-ttu-id="3a1cc-349">Como parte do rastreamento de ServiceModel, IDs exclusivas (chamado de IDs de atividade e, geralmente um GUID) vincular atividades diferentes juntos como uma mensagem passa pela diferentes partes da infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-349">As part of ServiceModel Tracing, Unique IDs (called Activity IDs, and typically a GUID) link different activities together as a message flows through different parts of the infrastructure.</span></span>  
  
#### <a name="custom-trace-listeners"></a><span data-ttu-id="3a1cc-350">Ouvintes de rastreamento personalizado</span><span class="sxs-lookup"><span data-stu-id="3a1cc-350">Custom Trace Listeners</span></span>  
 <span data-ttu-id="3a1cc-351">Para ambas as mensagens de log e rastreamento, um ouvinte de rastreamento personalizada pode ser configurado, o que pode enviar mensagens e rastreamentos na conexão (por exemplo, para um banco de dados remoto).</span><span class="sxs-lookup"><span data-stu-id="3a1cc-351">For both message logging and tracing, a custom trace listener can be configured, which can send traces and messages on the wire (for example, to a remote database).</span></span> <span data-ttu-id="3a1cc-352">O implantador de aplicativo é responsável por configurar ouvintes personalizados ou permitindo que os usuários fazer isso.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-352">The application deployer is responsible for configuring custom listeners or enabling users to do so.</span></span> <span data-ttu-id="3a1cc-353">Ele também é responsável por quaisquer informações pessoais exposto no local remoto e para aplicar as ACLs adequadamente para esse local.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-353">He is also responsible for any personal information exposed at the remote location, and for properly applying ACLs to this location.</span></span>  
  
### <a name="other-features-for-it-professionals"></a><span data-ttu-id="3a1cc-354">Outros recursos para profissionais de TI</span><span class="sxs-lookup"><span data-stu-id="3a1cc-354">Other features for IT Professionals</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="3a1cc-355">tem um provedor WMI que expõe o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] informações de configuração de infraestrutura por meio do WMI (fornecido com o Windows).</span><span class="sxs-lookup"><span data-stu-id="3a1cc-355"> has a WMI provider that exposes the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] infrastructure configuration information through WMI (shipped with Windows).</span></span> <span data-ttu-id="3a1cc-356">Por padrão, a interface WMI está disponível para administradores.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-356">By default, the WMI interface is available to administrators.</span></span>  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="3a1cc-357">configuração usa o mecanismo de configuração do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-357"> configuration uses the .NET Framework configuration mechanism.</span></span> <span data-ttu-id="3a1cc-358">Os arquivos de configuração são armazenados no computador.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-358">The configuration files are stored on the machine.</span></span> <span data-ttu-id="3a1cc-359">O desenvolvedor do aplicativo e o administrador criam os arquivos de configuração e a ACL para cada um dos requisitos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-359">The application developer and the administrator create the configuration files and ACL for each of the application's requirements.</span></span> <span data-ttu-id="3a1cc-360">Um arquivo de configuração pode conter endereços de ponto de extremidade e links para os certificados no repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-360">A configuration file can contain endpoint addresses and links to certificates in the certificate store.</span></span> <span data-ttu-id="3a1cc-361">Os certificados podem ser usados para fornecer dados de aplicativo para configurar várias propriedades dos recursos usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-361">The certificates can be used to provide application data to configure various properties of the features used by the application.</span></span>  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="3a1cc-362">também usa a funcionalidade de despejo de processo do .NET Framework ao chamar o <xref:System.Environment.FailFast%2A> método.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-362"> also uses the .NET Framework process dump functionality by calling the <xref:System.Environment.FailFast%2A> method.</span></span>  
  
### <a name="it-pro-tools"></a><span data-ttu-id="3a1cc-363">IT Pro ferramentas</span><span class="sxs-lookup"><span data-stu-id="3a1cc-363">IT Pro Tools</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="3a1cc-364">também fornece as ferramentas de profissional seguir IT, fornecidas no SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-364"> also provides the following IT professional tools, which ship in the Windows SDK.</span></span>  
  
#### <a name="svctraceviewerexe"></a><span data-ttu-id="3a1cc-365">SvcTraceViewer.exe</span><span class="sxs-lookup"><span data-stu-id="3a1cc-365">SvcTraceViewer.exe</span></span>  
 <span data-ttu-id="3a1cc-366">O visualizador exibe [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] arquivos de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-366">The viewer displays [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] trace files.</span></span> <span data-ttu-id="3a1cc-367">O visualizador mostra o texto que está contido nos rastreamentos.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-367">The viewer shows whatever information is contained in the traces.</span></span>  
  
#### <a name="svcconfigeditorexe"></a><span data-ttu-id="3a1cc-368">SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="3a1cc-368">SvcConfigEditor.exe</span></span>  
 <span data-ttu-id="3a1cc-369">O editor permite que o usuário criar e editar [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-369">The editor allows the user to create and edit [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration files.</span></span> <span data-ttu-id="3a1cc-370">O editor mostra o texto que está contido nos arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-370">The editor shows whatever information is contained in the configuration files.</span></span> <span data-ttu-id="3a1cc-371">A mesma tarefa pode ser feita com um editor de texto.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-371">The same task can be accomplished with a text editor.</span></span>  
  
#### <a name="servicemodelreg"></a><span data-ttu-id="3a1cc-372">ServiceModel_Reg</span><span class="sxs-lookup"><span data-stu-id="3a1cc-372">ServiceModel_Reg</span></span>  
 <span data-ttu-id="3a1cc-373">Essa ferramenta permite que o usuário gerencie ServiceModel instala em um computador.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-373">This tool allows the user to manage ServiceModel installs on a machine.</span></span> <span data-ttu-id="3a1cc-374">A ferramenta exibe mensagens de status na janela do console quando ele é executado e, no processo, pode exibir informações sobre a configuração do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] instalação.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-374">The tool displays status messages in a console window when it runs and, in the process, may display information about the configuration of the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] installation.</span></span>  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a><span data-ttu-id="3a1cc-375">WSATConfig.exe e WSATUI.dll</span><span class="sxs-lookup"><span data-stu-id="3a1cc-375">WSATConfig.exe and WSATUI.dll</span></span>  
 <span data-ttu-id="3a1cc-376">Essas ferramentas permitem que os profissionais de TI configurar o suporte de rede WS-AtomicTransaction interoperável em [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3a1cc-376">These tools allow IT Professionals to configure interoperable WS-AtomicTransaction network support in [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="3a1cc-377">As ferramentas de exibem e permitir que o usuário altere os valores das configurações do WS-AtomicTransaction mais comumente usadas armazenadas no registro.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-377">The tools display and allow the user to change the values of the most commonly used WS-AtomicTransaction settings stored in the registry.</span></span>  
  
## <a name="cross-cutting-features"></a><span data-ttu-id="3a1cc-378">Recursos abrangentes</span><span class="sxs-lookup"><span data-stu-id="3a1cc-378">Cross-cutting Features</span></span>  
 <span data-ttu-id="3a1cc-379">Os seguintes recursos são abrangentes.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-379">The following features are cross-cutting.</span></span> <span data-ttu-id="3a1cc-380">Ou seja, eles podem ser compostos com qualquer um dos recursos anteriores.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-380">That is, they can be composed with any of the preceding features.</span></span>  
  
### <a name="service-framework"></a><span data-ttu-id="3a1cc-381">Estrutura de serviço</span><span class="sxs-lookup"><span data-stu-id="3a1cc-381">Service Framework</span></span>  
 <span data-ttu-id="3a1cc-382">Cabeçalhos podem conter uma ID de instância, que é um GUID que associa uma mensagem uma instância de uma classe CLR.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-382">Headers can contain an instance ID, which is a GUID that associates a message with an instance of a CLR class.</span></span>  
  
 <span data-ttu-id="3a1cc-383">O WSDL Web Services Description Language () contém uma definição da porta.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-383">The Web Services Description Language (WSDL) contains a definition of the port.</span></span> <span data-ttu-id="3a1cc-384">Cada porta tem um endereço de ponto de extremidade e uma associação que representa os serviços usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-384">Each port has an endpoint address and a binding that represents the services used by the application.</span></span> <span data-ttu-id="3a1cc-385">Expondo WSDL pode ser desativado usando a configuração.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-385">Exposing WSDL can be turned off using configuration.</span></span> <span data-ttu-id="3a1cc-386">Nenhuma informação é mantida no computador.</span><span class="sxs-lookup"><span data-stu-id="3a1cc-386">No information is retained on the machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a1cc-387">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a1cc-387">See Also</span></span>  
 [<span data-ttu-id="3a1cc-388">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="3a1cc-388">Windows Communication Foundation</span></span>](http://msdn.microsoft.com/en-us/fd327ade-0260-4c40-adbe-b74645ba3277)  
 [<span data-ttu-id="3a1cc-389">Segurança</span><span class="sxs-lookup"><span data-stu-id="3a1cc-389">Security</span></span>](../../../docs/framework/wcf/feature-details/security.md)
