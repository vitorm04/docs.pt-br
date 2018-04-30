---
title: Protocolos de transação versão 1.0
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 60867daa7b8519f745c37371604807c51aa1cbb9
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="transaction-protocols-version-10"></a><span data-ttu-id="803b1-102">Protocolos de transação versão 1.0</span><span class="sxs-lookup"><span data-stu-id="803b1-102">Transaction Protocols version 1.0</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="803b1-103"> versão 1 implementa versão 1.0 dos protocolos WS-AT e coordenação WS.</span><span class="sxs-lookup"><span data-stu-id="803b1-103"> version 1 implements version 1.0 of the WS-Atomic Transaction and WS-Coordination protocols.</span></span> <span data-ttu-id="803b1-104">Para obter mais informações sobre versão 1.1, consulte [protocolos de transação](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="803b1-104">For more information about version 1.1, see [Transaction Protocols](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span></span>  
  
|<span data-ttu-id="803b1-105">Documento de especificação /</span><span class="sxs-lookup"><span data-stu-id="803b1-105">Specification/Document</span></span>|<span data-ttu-id="803b1-106">Link</span><span class="sxs-lookup"><span data-stu-id="803b1-106">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="803b1-107">Coordenação WS</span><span class="sxs-lookup"><span data-stu-id="803b1-107">WS-Coordination</span></span>|http://msdn.microsoft.com/ws/2005/08/ws-coordination/|  
|<span data-ttu-id="803b1-108">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="803b1-108">WS-AtomicTransaction</span></span>|http://msdn.microsoft.com/ws/2005/08/ws-atomictransaction/|  
  
 <span data-ttu-id="803b1-109">Interoperabilidade nessas especificações de protocolo é necessária em dois níveis: entre aplicativos e gerenciadores de transações (consulte a figura a seguir).</span><span class="sxs-lookup"><span data-stu-id="803b1-109">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="803b1-110">Especificações descrevem detalhadamente os formatos de mensagem e a mensagem do exchange para ambos os níveis de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="803b1-110">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="803b1-111">Determinados segurança, confiabilidade e codificações para o aplicativo para exchange se aplicam para troca de aplicativo comum.</span><span class="sxs-lookup"><span data-stu-id="803b1-111">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="803b1-112">No entanto, interoperabilidade com êxito entre gerenciadores de transações exige contrato na associação de determinado, porque geralmente não está configurado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="803b1-112">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="803b1-113">Este tópico descreve uma composição da especificação de transação WS-Atomic (WS-AT) com segurança e descreve a associação de segurança usada para comunicação entre os gerenciadores de transações.</span><span class="sxs-lookup"><span data-stu-id="803b1-113">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="803b1-114">A abordagem descrita neste documento foram testada com êxito com outras implementações do WS-AT e coordenação WS incluindo IBM, IONA, Sun Microsystems e outros.</span><span class="sxs-lookup"><span data-stu-id="803b1-114">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="803b1-115">A figura a seguir ilustra a interoperabilidade entre dois gerenciadores de transações, gerente de transação 1 e 2 do Gerenciador de transações e dois aplicativos, o aplicativo 1 e 2 do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="803b1-115">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2.</span></span>  
  
 <span data-ttu-id="803b1-116">![Protocolos de transação](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span><span class="sxs-lookup"><span data-stu-id="803b1-116">![Transaction Protocols](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span></span>  
  
 <span data-ttu-id="803b1-117">Considere um cenário típico de WS-coordenação/WS-AT com um iniciador (I) e um participante (P).</span><span class="sxs-lookup"><span data-stu-id="803b1-117">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="803b1-118">O iniciador e o participante tem gerenciadores de transações (ITM e PTM, respectivamente).</span><span class="sxs-lookup"><span data-stu-id="803b1-118">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="803b1-119">Confirmação de duas fases é conhecida como 2PC neste tópico.</span><span class="sxs-lookup"><span data-stu-id="803b1-119">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="803b1-120">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="803b1-120">1. CreateCoordinationContext</span></span>|<span data-ttu-id="803b1-121">12. Resposta de mensagem do aplicativo</span><span class="sxs-lookup"><span data-stu-id="803b1-121">12. Application Message Response</span></span>|  
|<span data-ttu-id="803b1-122">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="803b1-122">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="803b1-123">13. Confirmação (preenchimento)</span><span class="sxs-lookup"><span data-stu-id="803b1-123">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="803b1-124">3. Registro (preenchimento)</span><span class="sxs-lookup"><span data-stu-id="803b1-124">3. Register (Completion)</span></span>|<span data-ttu-id="803b1-125">14. Preparar (2PC)</span><span class="sxs-lookup"><span data-stu-id="803b1-125">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="803b1-126">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="803b1-126">4. RegisterResponse</span></span>|<span data-ttu-id="803b1-127">15. Preparar (2PC)</span><span class="sxs-lookup"><span data-stu-id="803b1-127">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="803b1-128">5. Mensagem de aplicativo</span><span class="sxs-lookup"><span data-stu-id="803b1-128">5. Application Message</span></span>|<span data-ttu-id="803b1-129">16. Preparada (2PC)</span><span class="sxs-lookup"><span data-stu-id="803b1-129">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="803b1-130">6. CreateCoordinationContext com contexto</span><span class="sxs-lookup"><span data-stu-id="803b1-130">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="803b1-131">17. Preparada (2PC)</span><span class="sxs-lookup"><span data-stu-id="803b1-131">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="803b1-132">7. Registro (durável)</span><span class="sxs-lookup"><span data-stu-id="803b1-132">7. Register (Durable)</span></span>|<span data-ttu-id="803b1-133">18. Confirmada (preenchimento)</span><span class="sxs-lookup"><span data-stu-id="803b1-133">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="803b1-134">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="803b1-134">8. RegisterResponse</span></span>|<span data-ttu-id="803b1-135">19. 2PC (confirmação)</span><span class="sxs-lookup"><span data-stu-id="803b1-135">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="803b1-136">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="803b1-136">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="803b1-137">20. 2PC (confirmação)</span><span class="sxs-lookup"><span data-stu-id="803b1-137">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="803b1-138">10. Registro (durável)</span><span class="sxs-lookup"><span data-stu-id="803b1-138">10. Register (Durable)</span></span>|<span data-ttu-id="803b1-139">21. Confirmada (2PC)</span><span class="sxs-lookup"><span data-stu-id="803b1-139">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="803b1-140">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="803b1-140">11. RegisterResponse</span></span>|<span data-ttu-id="803b1-141">22. Confirmada (2PC)</span><span class="sxs-lookup"><span data-stu-id="803b1-141">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="803b1-142">Este documento descreve uma composição da especificação WS-AtomicTransaction com segurança e a associação de segurança usada para comunicação entre os gerenciadores de transações.</span><span class="sxs-lookup"><span data-stu-id="803b1-142">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="803b1-143">A abordagem descrita neste documento foram testada com êxito com outras implementações do WS-AT e coordenação WS.</span><span class="sxs-lookup"><span data-stu-id="803b1-143">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="803b1-144">A figura e a tabela ilustram quatro classes de mensagens a partir do ponto de vista de segurança:</span><span class="sxs-lookup"><span data-stu-id="803b1-144">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
-   <span data-ttu-id="803b1-145">Mensagens de ativação (CreateCoordinationContext e CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="803b1-145">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
-   <span data-ttu-id="803b1-146">Mensagens de registro (o registro e RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="803b1-146">Registration messages (Register and RegisterResponse)</span></span>  
  
-   <span data-ttu-id="803b1-147">Mensagens de protocolo (preparar, Rollback, confirmação, Aborted e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="803b1-147">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
-   <span data-ttu-id="803b1-148">Mensagens de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="803b1-148">Application messages.</span></span>  
  
 <span data-ttu-id="803b1-149">Classes de três mensagem primeiro são consideradas mensagens do Gerenciador de transações e sua configuração de associação é descrita em "Aplicativo de troca de mensagens" neste tópico.</span><span class="sxs-lookup"><span data-stu-id="803b1-149">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="803b1-150">A quarta classe da mensagem é mensagens de aplicativo e é descrita na seção "Exemplos de mensagem" neste tópico.</span><span class="sxs-lookup"><span data-stu-id="803b1-150">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="803b1-151">Esta seção descreve as associações de protocolo usadas para cada uma dessas classes por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="803b1-151">This section describes the protocol bindings used for each of these classes by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="803b1-152">Os seguintes Namespaces de XML e prefixos associados são usados em todo este documento.</span><span class="sxs-lookup"><span data-stu-id="803b1-152">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="803b1-153">Prefixo</span><span class="sxs-lookup"><span data-stu-id="803b1-153">Prefix</span></span>|<span data-ttu-id="803b1-154">URI de Namespace</span><span class="sxs-lookup"><span data-stu-id="803b1-154">Namespace URI</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="803b1-155">s11</span><span class="sxs-lookup"><span data-stu-id="803b1-155">s11</span></span>|http://schemas.xmlsoap.org/soap/envelope|  
|<span data-ttu-id="803b1-156">wsa</span><span class="sxs-lookup"><span data-stu-id="803b1-156">wsa</span></span>|http://www.w3.org/2004/08/addressing|  
|<span data-ttu-id="803b1-157">wscoor</span><span class="sxs-lookup"><span data-stu-id="803b1-157">wscoor</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|<span data-ttu-id="803b1-158">WSAT</span><span class="sxs-lookup"><span data-stu-id="803b1-158">wsat</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wsat|  
|<span data-ttu-id="803b1-159">t</span><span class="sxs-lookup"><span data-stu-id="803b1-159">t</span></span>|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|<span data-ttu-id="803b1-160">o</span><span class="sxs-lookup"><span data-stu-id="803b1-160">o</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="803b1-161">XSD</span><span class="sxs-lookup"><span data-stu-id="803b1-161">xsd</span></span>|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="803b1-162">Associações do Gerenciador de transações</span><span class="sxs-lookup"><span data-stu-id="803b1-162">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="803b1-163">R1001: Gerenciadores de transações devem usar os SOAP 1.1 e 08/2004 do WS-Addressing para transações de WS-Atomic e trocas de mensagens de coordenação WS.</span><span class="sxs-lookup"><span data-stu-id="803b1-163">R1001: Transaction Managers must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="803b1-164">As mensagens de aplicativo não são restritos a essas associações e são descritas posteriormente.</span><span class="sxs-lookup"><span data-stu-id="803b1-164">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="803b1-165">Associação de HTTPS de Gerenciador de transações</span><span class="sxs-lookup"><span data-stu-id="803b1-165">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="803b1-166">A associação de HTTPS de Gerenciador de transação depende exclusivamente de segurança de transporte para obter segurança e estabelecer relação de confiança entre cada par de remetente e o receptor na árvore de transação.</span><span class="sxs-lookup"><span data-stu-id="803b1-166">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="803b1-167">Configuração de transporte HTTPS</span><span class="sxs-lookup"><span data-stu-id="803b1-167">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="803b1-168">Certificados x. 509 são usados para estabelecer a identidade do Gerenciador de transações.</span><span class="sxs-lookup"><span data-stu-id="803b1-168">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="803b1-169">Autenticação de cliente/servidor é necessária e autorização do cliente/servidor é mantida como um detalhe de implementação:</span><span class="sxs-lookup"><span data-stu-id="803b1-169">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
-   <span data-ttu-id="803b1-170">R1111: Certificados x. 509 apresentados pela conexão devem ter um nome de assunto que corresponda o nome de domínio totalmente qualificado (FQDN) do computador de origem.</span><span class="sxs-lookup"><span data-stu-id="803b1-170">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
-   <span data-ttu-id="803b1-171">B1112: O DNS deve ser funcional entre cada par de remetente e o receptor do sistema para verificações de nome de assunto de x. 509 seja bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="803b1-171">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="803b1-172">Ativação e registro de configuração de associação</span><span class="sxs-lookup"><span data-stu-id="803b1-172">Activation and Registration Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="803b1-173"> requer a associação de solicitação/resposta duplex com correlação via HTTPS.</span><span class="sxs-lookup"><span data-stu-id="803b1-173"> requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="803b1-174">(Para obter mais informações sobre a correlação e descrições dos padrões de troca de mensagem de solicitação/resposta, consulte transação WS-Atomic, 8 de seção).</span><span class="sxs-lookup"><span data-stu-id="803b1-174">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="803b1-175">Configuração de associação de protocolo 2PC</span><span class="sxs-lookup"><span data-stu-id="803b1-175">2PC Protocol Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="803b1-176"> oferece suporte a mensagens unidirecionais (datagrama) sobre HTTPS.</span><span class="sxs-lookup"><span data-stu-id="803b1-176"> supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="803b1-177">Correlação entre as mensagens será deixada como um detalhe de implementação.</span><span class="sxs-lookup"><span data-stu-id="803b1-177">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="803b1-178">B2131: Implementações devem suportar `wsa:ReferenceParameters` conforme descrito em WS-Addressing para alcançar a correlação de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]do 2PC mensagens.</span><span class="sxs-lookup"><span data-stu-id="803b1-178">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="803b1-179">Gerenciador de transações misto associação de segurança</span><span class="sxs-lookup"><span data-stu-id="803b1-179">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="803b1-180">Esta é uma alternativa (misto) que usa a segurança de transporte combinada com o modelo de Token emitido de coordenação WS para fins de estabelecimento de identidade de associação.</span><span class="sxs-lookup"><span data-stu-id="803b1-180">This is an alternate (mixed mode) binding that uses transport security combined with the  WS-Coordination Issued Token model for identity establishment purposes.</span></span>  <span data-ttu-id="803b1-181">Ativação e registro são os únicos elementos que diferem entre as duas associações.</span><span class="sxs-lookup"><span data-stu-id="803b1-181">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="803b1-182">Configuração de transporte HTTPS</span><span class="sxs-lookup"><span data-stu-id="803b1-182">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="803b1-183">Certificados x. 509 são usados para estabelecer a identidade do Gerenciador de transações.</span><span class="sxs-lookup"><span data-stu-id="803b1-183">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="803b1-184">Autenticação de cliente/servidor é necessária e autorização do cliente/servidor é mantida como um detalhe de implementação.</span><span class="sxs-lookup"><span data-stu-id="803b1-184">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="803b1-185">Configuração de associação de mensagem de ativação</span><span class="sxs-lookup"><span data-stu-id="803b1-185">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="803b1-186">Mensagens de ativação geralmente não participar de interoperabilidade porque eles ocorrem normalmente entre um aplicativo e seu gerente de transação local.</span><span class="sxs-lookup"><span data-stu-id="803b1-186">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="803b1-187">B1221: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa associação de HTTPS duplex (descrito na [protocolos de mensagens](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) para mensagens de ativação.</span><span class="sxs-lookup"><span data-stu-id="803b1-187">B1221: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="803b1-188">Mensagens de resposta e solicitação são correlacionadas usando 08/2004 do WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="803b1-188">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="803b1-189">Especificação WS-AT, 8 de seção, descreve mais detalhes sobre a correlação e os padrões de troca de mensagem.</span><span class="sxs-lookup"><span data-stu-id="803b1-189">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
-   <span data-ttu-id="803b1-190">R1222: após receber uma `CreateCoordinationContext`, o coordenador deve emitir uma `SecurityContextToken` com segredo associado `STx`.</span><span class="sxs-lookup"><span data-stu-id="803b1-190">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="803b1-191">Esse token é retornado em uma `t:IssuedTokens` cabeçalho após a especificação WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="803b1-191">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
-   <span data-ttu-id="803b1-192">R1223: Se a ativação ocorrer dentro de um contexto de coordenação existente, o `t:IssuedTokens` cabeçalho com o `SecurityContextToken` associado existente contexto deve fluir no `CreateCoordinationContext` mensagem.</span><span class="sxs-lookup"><span data-stu-id="803b1-192">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="803b1-193">Um novo `t:IssuedTokens` cabeçalho deve ser gerado para anexar para a saída `wscoor:CreateCoordinationContextResponse` mensagem.</span><span class="sxs-lookup"><span data-stu-id="803b1-193">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="803b1-194">Configuração de associação de mensagem de registro</span><span class="sxs-lookup"><span data-stu-id="803b1-194">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="803b1-195">B1231: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa associação de HTTPS duplex (descrito na [protocolos de mensagens](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="803b1-195">B1231: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="803b1-196">Mensagens de resposta e solicitação são correlacionadas usando 08/2004 do WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="803b1-196">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="803b1-197">WS-AtomicTransaction, 8 de seção descreve mais detalhes sobre a correlação e descrições dos padrões de troca de mensagem.</span><span class="sxs-lookup"><span data-stu-id="803b1-197">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="803b1-198">R1232: Saída `wscoor:Register` mensagens devem usar o `IssuedTokenOverTransport` o modo de autenticação descrito [protocolos de segurança](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="803b1-198">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="803b1-199">O `wsse:Timestamp` elemento deve ser assinado usando o `SecurityContextToken``STx` emitido.</span><span class="sxs-lookup"><span data-stu-id="803b1-199">The `wsse:Timestamp` element must be signed using the `SecurityContextToken``STx` issued.</span></span> <span data-ttu-id="803b1-200">Esta assinatura é uma prova de posse do token associado à transação específica e é usada para autenticar um participante inscrição na transação.</span><span class="sxs-lookup"><span data-stu-id="803b1-200">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="803b1-201">A mensagem RegistrationResponse é enviada novamente por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="803b1-201">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="803b1-202">Configuração de associação de protocolo 2PC</span><span class="sxs-lookup"><span data-stu-id="803b1-202">2PC Protocol Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="803b1-203"> oferece suporte a mensagens unidirecionais (datagrama) sobre HTTPS.</span><span class="sxs-lookup"><span data-stu-id="803b1-203"> supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="803b1-204">Correlação entre as mensagens será deixada como um detalhe de implementação.</span><span class="sxs-lookup"><span data-stu-id="803b1-204">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="803b1-205">B2131: Implementações devem suportar `wsa:ReferenceParameters` conforme descrito em WS-Addressing para alcançar a correlação de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]do 2PC mensagens.</span><span class="sxs-lookup"><span data-stu-id="803b1-205">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="803b1-206">Troca de mensagens de aplicativo</span><span class="sxs-lookup"><span data-stu-id="803b1-206">Application Message Exchange</span></span>  
 <span data-ttu-id="803b1-207">Aplicativos estão livres para usar qualquer associação específica para mensagens de aplicativo, desde que a associação atende aos seguintes requisitos de segurança:</span><span class="sxs-lookup"><span data-stu-id="803b1-207">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
-   <span data-ttu-id="803b1-208">R2001: Mensagens de aplicativo para o aplicativo devem fluir de `t:IssuedTokens` cabeçalho junto com o `CoordinationContext` no cabeçalho da mensagem.</span><span class="sxs-lookup"><span data-stu-id="803b1-208">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
-   <span data-ttu-id="803b1-209">R2002: Integridade e confidencialidade de `t:IssuedToken` deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="803b1-209">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="803b1-210">O `CoordinationContext` cabeçalho contém `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="803b1-210">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="803b1-211">Enquanto a definição de `xsd:AnyURI` permite o uso de absolute e relative URIs, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oferece suporte apenas para `wscoor:Identifiers`, que são URIs absolutos.</span><span class="sxs-lookup"><span data-stu-id="803b1-211">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="803b1-212">Se o `wscoor:Identifier` do `wscoor:CoordinationContext` é um URI relativo, falhas serão retornadas de transacional [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços.</span><span class="sxs-lookup"><span data-stu-id="803b1-212">If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="803b1-213">Exemplos de mensagem</span><span class="sxs-lookup"><span data-stu-id="803b1-213">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="803b1-214">Mensagens de solicitação/resposta CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="803b1-214">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="803b1-215">As seguintes mensagens sigam um padrão de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="803b1-215">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext"></a><span data-ttu-id="803b1-216">CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="803b1-216">CreateCoordinationContext</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wscoor/CreateCoordinationContext</Action>  
    <a:MessageID>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</MessageID>  
    <a:ReplyTo>  
      <Address>https://...</a:Address>  
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security>  
      <u:Timestamp>  
        <wsu:Created>2005-12-15T23:36:09.921Z</u:Created>  
        <wsu:Expires>2005-12-15T23:41:09.921Z</u:Expires>  
      </u:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:CreateCoordinationContext>  
      <wscoor:CoordinationType>...</wscoor:CoordinationType>  
    </wscoor:CreateCoordinationContext>  
  </s:Body>  
</s11:Envelope>  
```  
  
#### <a name="createcoordinationcontextresponse"></a><span data-ttu-id="803b1-217">CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="803b1-217">CreateCoordinationContextResponse</span></span>  
  
```xml  
<s:Envelope>  
  <!-- Data below is shown in the clear for  
       illustration purposes only. -->  
  <s:Header>  
    <a:Action>./ws/2004/10/wscoor/CreateCoordinationContextResponse </a:Action>  
    <a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
    <a:To s:mustUnderstand="1">https://... </a:To>  
    <t:IssuedTokens>  
 <wst:RequestSecurityTokenResponse     
    xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
    xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"   
    xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"  
    xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
    xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
    <wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
    <wst:RequestedSecurityToken>  
      <wsc:SecurityContextToken>  
        <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
        </wssu:Identifier>  
      </wsc:SecurityContextToken>   
    </wst:RequestedSecurityToken>  
    <wsp:AppliesTo>  
        http://fabrikam123.com/CCi  
    </wsp:AppliesTo>    
    <wst:RequestedAttachedReference>  
      <wsse:SecurityTokenReference >  
        <wsse:Reference   
           ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
           URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedAttachedReference>  
    <wst:RequestedUnattachedReference>  
      <wsse:SecurityTokenReference>  
        <wsse:Reference   
          ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
          URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedUnattachedReference>  
    <wst:RequestedProofToken>  
      <wst:BinarySecret   
        Type="http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey">  
        <!-- base64 encoded value -->  
      </wst:BinarySecret>  
    </wst:RequestedProofToken>  
    <wst:Lifetime>  
      <wssu:Created>2005-10-24T20:19:26.526Z</wssu:Created>  
      <wssu:Expires>2005-10-25T06:24:26.526Z</wssu:Expires>  
    </wst:Lifetime>  
    <wst:KeySize>256</wst:KeySize>  
</wst:RequestSecurityTokenResponse>  
    </t:IssuedTokens>  
    <o:Security xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
      <u:Timestamp u:Id="_0">  
        <u:Created>2005-12-15T23:36:12.015Z</u:Created>  
        <u:Expires>2005-12-15T23:41:12.015Z</u:Expires>  
      </u:Timestamp>  
    </o:Security>  
  </s:Header>  
  <s:Body>  
    <wscoor:CreateCoordinationContextResponse>  
      <wscoor:CoordinationContext>  
        <wscoor:Identifier>  
     http://fabrikam123.com/CCi  
      </wscoor:Identifier>  
        <wscoor:Expires>...</wscoor:Expires>  
        <wscoor:CoordinationType>...</wscoor:CoordinationType>  
        <wscoor:RegistrationService>  
          <a:Address>https://...</a:Address>  
          <a:ReferenceParameters>  
             ...  
          </a:ReferenceParameters>  
        </wscoor:RegistrationService>  
      </wscoor:CoordinationContext>  
    </wscoor:CreateCoordinationContextResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="registration-messages"></a><span data-ttu-id="803b1-218">Mensagens de registro</span><span class="sxs-lookup"><span data-stu-id="803b1-218">Registration Messages</span></span>  
 <span data-ttu-id="803b1-219">As seguintes mensagens são mensagens de registro.</span><span class="sxs-lookup"><span data-stu-id="803b1-219">The following messages are registration messages.</span></span>  
  
#### <a name="register"></a><span data-ttu-id="803b1-220">Registro</span><span class="sxs-lookup"><span data-stu-id="803b1-220">Register</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://schemas.xmlsoap.org/ws/2004/10/wscoor/Register</a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>https://...</a:Address>        
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsc:SecurityContextToken>  
      <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
      </wssu:Identifier>  
      </wsc:SecurityContextToken>  
      <!-- supporting signature over the timestamp -->  
      <wsse:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">  
        <ds:SignedInfo>  
          <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
          <ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#hmac-sha1"/>  
          <ds:Reference URI="#_0">  
            <ds:Transforms>  
              <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
            </ds:Transforms>  
            <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>  
            <ds:DigestValue>  
              alRzyhjLgoUOYoh8cx4n75eTcUk=  
            </ds:DigestValue>  
          </ds:Reference>  
        </ds:SignedInfo>  
        <ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=</ds:SignatureValue>  
        <ds:KeyInfo>  
          <wsse:SecurityTokenReference  
            xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
            <wsse:Reference   
              URI="http://fabrikam123.com/SCTi"/>  
          </wsse:SecurityTokenReference>  
        </ds:KeyInfo>  
      </wsse:Signature>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:Register>  
      <wscoor:ProtocolIdentifier>...</wscoor:ProtocolIdentifier>  
      <wscoor:ParticipantProtocolService>  
        <a:Address>https://... </a:Address>  
      </wscoor:ParticipantProtocolService>  
    </wscoor:Register>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="register-response"></a><span data-ttu-id="803b1-221">Resposta de registro</span><span class="sxs-lookup"><span data-stu-id="803b1-221">Register Response</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>  
      http://schemas.xmlsoap.org/ws/2004/10/wscoor/RegisterResponse  
    </a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
    <a:RelatesTo>  
      urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e        
    </a:RelatesTo>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp>  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:RegisterResponse>  
      <wscoor:CoordinatorProtocolService>  
        <a:Address>https://...</a:Address>  
        <a:ReferenceParameters>  
          ...  
        </a:ReferenceParameters>  
      </wscoor:CoordinatorProtocolService>  
    </wscoor:RegisterResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="803b1-222">Duas mensagens de protocolo de confirmação de fase</span><span class="sxs-lookup"><span data-stu-id="803b1-222">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="803b1-223">A seguinte mensagem de erro se relaciona com o protocolo de confirmação de duas fases (2PC).</span><span class="sxs-lookup"><span data-stu-id="803b1-223">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit"></a><span data-ttu-id="803b1-224">Confirmação</span><span class="sxs-lookup"><span data-stu-id="803b1-224">Commit</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wsat/Commit</a:Action>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
   </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wsat:Commit />  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="application-messages"></a><span data-ttu-id="803b1-225">Mensagens de aplicativo</span><span class="sxs-lookup"><span data-stu-id="803b1-225">Application Messages</span></span>  
 <span data-ttu-id="803b1-226">As seguintes mensagens são mensagens do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="803b1-226">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="803b1-227">Solicitação de mensagem do aplicativo</span><span class="sxs-lookup"><span data-stu-id="803b1-227">Application message-Request</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
<!-- Addressing headers, all signed-->  
    <wsse:Security s:mustUnderstand="1">  
      <wssu:Timestamp wssu:Id="timestamp">   
        <wssu:Created>2005-10-25T06:29:18.703Z</wssu:Created>  
        <wssu:Expires>2005-10-25T06:34:18.703Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsse:BinarySecurityToken   
          wssu:Id="IA_Certificate"   
          ValueType="...#X509v3"   
          EncodingType="...#Base64Binary">  
        <!-- IA certificate -->  
      </wsse:BinarySecurityToken>  
      <e:EncryptedKey Id="encrypted_key">  
            <!-- ephemeral key encrypted for PA certificate -->    
        <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
          <e:DataReference URI="#encrypted_body"/>  
          <e:DataReference URI="#encrypted_CCi"/>  
          <e:DataReference URI="#encrypted_issuedtokens"/>  
        </e:ReferenceList>  
      </e:EncryptedKey>  
      <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
        <!-- signature over Addressing headers, Timestamp, and Body -->  
      </Signature>  
    </wsse:Security>  
    <wsse11:EncryptedHeader >  
     <!-- encrypted wscoor:CoordinationContext header containing CCi -->  
    </wsse11:EncryptedHeader>  
    <wsse11:EncryptedHeader   
      <!-- encrypted wst:IssuedTokens header containing SCTi -->  
      <!-- wst:IssuedTokens header is taken verbatim from message #2 above, omitted for brevity -->  
    </wsse11:EncryptedHeader>  
  </s:Header>  
  <s:Body wssu:Id="body">  
    <!-- encrypted content of the Body element of the application message -->      
    <e:EncryptedData Id="encrypted_body"   
           Type="http://www.w3.org/2001/04/xmlenc#Content"   
           xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
...  
    </e:EncryptedData>  
  </s:Body>  
</s:Envelope>  
```
