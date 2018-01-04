---
title: "Protocolos de transação versão 1.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e616f989416fcee77caa9b9a5d87cfa6812eab32
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-protocols-version-10"></a><span data-ttu-id="bb781-102">Protocolos de transação versão 1.0</span><span class="sxs-lookup"><span data-stu-id="bb781-102">Transaction Protocols version 1.0</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="bb781-103">versão 1 implementa versão 1.0 dos protocolos WS-AT e coordenação WS.</span><span class="sxs-lookup"><span data-stu-id="bb781-103"> version 1 implements version 1.0 of the WS-Atomic Transaction and WS-Coordination protocols.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="bb781-104">versão 1.1, consulte [protocolos de transação](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="bb781-104"> version 1.1, see [Transaction Protocols](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span></span>  
  
|<span data-ttu-id="bb781-105">Documento de especificação /</span><span class="sxs-lookup"><span data-stu-id="bb781-105">Specification/Document</span></span>|<span data-ttu-id="bb781-106">Link</span><span class="sxs-lookup"><span data-stu-id="bb781-106">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="bb781-107">Coordenação WS</span><span class="sxs-lookup"><span data-stu-id="bb781-107">WS-Coordination</span></span>|<span data-ttu-id="bb781-108">http://msdn.microsoft.com/ws/2005/08/WS-Coordination/</span><span class="sxs-lookup"><span data-stu-id="bb781-108">http://msdn.microsoft.com/ws/2005/08/ws-coordination/</span></span>|  
|<span data-ttu-id="bb781-109">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="bb781-109">WS-AtomicTransaction</span></span>|<span data-ttu-id="bb781-110">http://msdn.microsoft.com/ws/2005/08/WS-AtomicTransaction/</span><span class="sxs-lookup"><span data-stu-id="bb781-110">http://msdn.microsoft.com/ws/2005/08/ws-atomictransaction/</span></span>|  
  
 <span data-ttu-id="bb781-111">Interoperabilidade nessas especificações de protocolo é necessária em dois níveis: entre aplicativos e gerenciadores de transações (consulte a figura a seguir).</span><span class="sxs-lookup"><span data-stu-id="bb781-111">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="bb781-112">Especificações descrevem detalhadamente os formatos de mensagem e a mensagem do exchange para ambos os níveis de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="bb781-112">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="bb781-113">Determinados segurança, confiabilidade e codificações para o aplicativo para exchange se aplicam para troca de aplicativo comum.</span><span class="sxs-lookup"><span data-stu-id="bb781-113">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="bb781-114">No entanto, interoperabilidade com êxito entre gerenciadores de transações exige contrato na associação de determinado, porque geralmente não está configurado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="bb781-114">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="bb781-115">Este tópico descreve uma composição da especificação de transação WS-Atomic (WS-AT) com segurança e descreve a associação de segurança usada para comunicação entre os gerenciadores de transações.</span><span class="sxs-lookup"><span data-stu-id="bb781-115">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="bb781-116">A abordagem descrita neste documento foram testada com êxito com outras implementações do WS-AT e coordenação WS incluindo IBM, IONA, Sun Microsystems e outros.</span><span class="sxs-lookup"><span data-stu-id="bb781-116">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="bb781-117">A figura a seguir ilustra a interoperabilidade entre dois gerenciadores de transações, gerente de transação 1 e 2 do Gerenciador de transações e dois aplicativos, o aplicativo 1 e 2 do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bb781-117">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2.</span></span>  
  
 <span data-ttu-id="bb781-118">![Protocolos de transação](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span><span class="sxs-lookup"><span data-stu-id="bb781-118">![Transaction Protocols](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span></span>  
  
 <span data-ttu-id="bb781-119">Considere um cenário típico de WS-coordenação/WS-AT com um iniciador (I) e um participante (P).</span><span class="sxs-lookup"><span data-stu-id="bb781-119">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="bb781-120">O iniciador e o participante tem gerenciadores de transações (ITM e PTM, respectivamente).</span><span class="sxs-lookup"><span data-stu-id="bb781-120">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="bb781-121">Confirmação de duas fases é conhecida como 2PC neste tópico.</span><span class="sxs-lookup"><span data-stu-id="bb781-121">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bb781-122">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="bb781-122">1. CreateCoordinationContext</span></span>|<span data-ttu-id="bb781-123">12. Resposta de mensagem do aplicativo</span><span class="sxs-lookup"><span data-stu-id="bb781-123">12. Application Message Response</span></span>|  
|<span data-ttu-id="bb781-124">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="bb781-124">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="bb781-125">13. Confirmação (preenchimento)</span><span class="sxs-lookup"><span data-stu-id="bb781-125">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="bb781-126">3. Registro (preenchimento)</span><span class="sxs-lookup"><span data-stu-id="bb781-126">3. Register (Completion)</span></span>|<span data-ttu-id="bb781-127">14. Preparar (2PC)</span><span class="sxs-lookup"><span data-stu-id="bb781-127">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="bb781-128">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="bb781-128">4. RegisterResponse</span></span>|<span data-ttu-id="bb781-129">15. Preparar (2PC)</span><span class="sxs-lookup"><span data-stu-id="bb781-129">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="bb781-130">5. Mensagem de aplicativo</span><span class="sxs-lookup"><span data-stu-id="bb781-130">5. Application Message</span></span>|<span data-ttu-id="bb781-131">16. Preparada (2PC)</span><span class="sxs-lookup"><span data-stu-id="bb781-131">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="bb781-132">6. CreateCoordinationContext com contexto</span><span class="sxs-lookup"><span data-stu-id="bb781-132">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="bb781-133">17. Preparada (2PC)</span><span class="sxs-lookup"><span data-stu-id="bb781-133">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="bb781-134">7. Registro (durável)</span><span class="sxs-lookup"><span data-stu-id="bb781-134">7. Register (Durable)</span></span>|<span data-ttu-id="bb781-135">18. Confirmada (preenchimento)</span><span class="sxs-lookup"><span data-stu-id="bb781-135">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="bb781-136">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="bb781-136">8. RegisterResponse</span></span>|<span data-ttu-id="bb781-137">19. 2PC (confirmação)</span><span class="sxs-lookup"><span data-stu-id="bb781-137">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="bb781-138">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="bb781-138">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="bb781-139">20. 2PC (confirmação)</span><span class="sxs-lookup"><span data-stu-id="bb781-139">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="bb781-140">10. Registro (durável)</span><span class="sxs-lookup"><span data-stu-id="bb781-140">10. Register (Durable)</span></span>|<span data-ttu-id="bb781-141">21. Confirmada (2PC)</span><span class="sxs-lookup"><span data-stu-id="bb781-141">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="bb781-142">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="bb781-142">11. RegisterResponse</span></span>|<span data-ttu-id="bb781-143">22. Confirmada (2PC)</span><span class="sxs-lookup"><span data-stu-id="bb781-143">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="bb781-144">Este documento descreve uma composição da especificação WS-AtomicTransaction com segurança e a associação de segurança usada para comunicação entre os gerenciadores de transações.</span><span class="sxs-lookup"><span data-stu-id="bb781-144">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="bb781-145">A abordagem descrita neste documento foram testada com êxito com outras implementações do WS-AT e coordenação WS.</span><span class="sxs-lookup"><span data-stu-id="bb781-145">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="bb781-146">A figura e a tabela ilustram quatro classes de mensagens a partir do ponto de vista de segurança:</span><span class="sxs-lookup"><span data-stu-id="bb781-146">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
-   <span data-ttu-id="bb781-147">Mensagens de ativação (CreateCoordinationContext e CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="bb781-147">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
-   <span data-ttu-id="bb781-148">Mensagens de registro (o registro e RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="bb781-148">Registration messages (Register and RegisterResponse)</span></span>  
  
-   <span data-ttu-id="bb781-149">Mensagens de protocolo (preparar, Rollback, confirmação, Aborted e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="bb781-149">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
-   <span data-ttu-id="bb781-150">Mensagens de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bb781-150">Application messages.</span></span>  
  
 <span data-ttu-id="bb781-151">Classes de três mensagem primeiro são consideradas mensagens do Gerenciador de transações e sua configuração de associação é descrita em "Aplicativo de troca de mensagens" neste tópico.</span><span class="sxs-lookup"><span data-stu-id="bb781-151">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="bb781-152">A quarta classe da mensagem é mensagens de aplicativo e é descrita na seção "Exemplos de mensagem" neste tópico.</span><span class="sxs-lookup"><span data-stu-id="bb781-152">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="bb781-153">Esta seção descreve as associações de protocolo usadas para cada uma dessas classes por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb781-153">This section describes the protocol bindings used for each of these classes by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="bb781-154">Os seguintes Namespaces de XML e prefixos associados são usados em todo este documento.</span><span class="sxs-lookup"><span data-stu-id="bb781-154">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="bb781-155">Prefixo</span><span class="sxs-lookup"><span data-stu-id="bb781-155">Prefix</span></span>|<span data-ttu-id="bb781-156">URI de Namespace</span><span class="sxs-lookup"><span data-stu-id="bb781-156">Namespace URI</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="bb781-157">S11</span><span class="sxs-lookup"><span data-stu-id="bb781-157">s11</span></span>|<span data-ttu-id="bb781-158">http://schemas.xmlsoap.org/SOAP/envelope</span><span class="sxs-lookup"><span data-stu-id="bb781-158">http://schemas.xmlsoap.org/soap/envelope</span></span>|  
|<span data-ttu-id="bb781-159">wsa</span><span class="sxs-lookup"><span data-stu-id="bb781-159">wsa</span></span>|<span data-ttu-id="bb781-160">http://www.w3.org/2004/08/Addressing</span><span class="sxs-lookup"><span data-stu-id="bb781-160">http://www.w3.org/2004/08/addressing</span></span>|  
|<span data-ttu-id="bb781-161">wscoor</span><span class="sxs-lookup"><span data-stu-id="bb781-161">wscoor</span></span>|<span data-ttu-id="bb781-162">http://schemas.xmlsoap.org/ws/2004/10/wscoor</span><span class="sxs-lookup"><span data-stu-id="bb781-162">http://schemas.xmlsoap.org/ws/2004/10/wscoor</span></span>|  
|<span data-ttu-id="bb781-163">WSAT</span><span class="sxs-lookup"><span data-stu-id="bb781-163">wsat</span></span>|<span data-ttu-id="bb781-164">http://schemas.xmlsoap.org/ws/2004/10/WSAT</span><span class="sxs-lookup"><span data-stu-id="bb781-164">http://schemas.xmlsoap.org/ws/2004/10/wsat</span></span>|  
|<span data-ttu-id="bb781-165">t</span><span class="sxs-lookup"><span data-stu-id="bb781-165">t</span></span>|<span data-ttu-id="bb781-166">http://schemas.xmlsoap.org/ws/2005/02/trust</span><span class="sxs-lookup"><span data-stu-id="bb781-166">http://schemas.xmlsoap.org/ws/2005/02/trust</span></span>|  
|<span data-ttu-id="bb781-167">o</span><span class="sxs-lookup"><span data-stu-id="bb781-167">o</span></span>|<span data-ttu-id="bb781-168">http://docs.oasis-open.org/WSS/2004/01/OASIS-200401-WSS-wssecurity-secext-1.0.xsd</span><span class="sxs-lookup"><span data-stu-id="bb781-168">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd</span></span>|  
|<span data-ttu-id="bb781-169">XSD</span><span class="sxs-lookup"><span data-stu-id="bb781-169">xsd</span></span>|<span data-ttu-id="bb781-170">http://www.w3.org/2001/XMLSchema</span><span class="sxs-lookup"><span data-stu-id="bb781-170">http://www.w3.org/2001/XMLSchema</span></span>|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="bb781-171">Associações do Gerenciador de transações</span><span class="sxs-lookup"><span data-stu-id="bb781-171">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="bb781-172">R1001: Gerenciadores de transações devem usar os SOAP 1.1 e 08/2004 do WS-Addressing para transações de WS-Atomic e trocas de mensagens de coordenação WS.</span><span class="sxs-lookup"><span data-stu-id="bb781-172">R1001: Transaction Managers must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="bb781-173">As mensagens de aplicativo não são restritos a essas associações e são descritas posteriormente.</span><span class="sxs-lookup"><span data-stu-id="bb781-173">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="bb781-174">Associação de HTTPS de Gerenciador de transações</span><span class="sxs-lookup"><span data-stu-id="bb781-174">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="bb781-175">A associação de HTTPS de Gerenciador de transação depende exclusivamente de segurança de transporte para obter segurança e estabelecer relação de confiança entre cada par de remetente e o receptor na árvore de transação.</span><span class="sxs-lookup"><span data-stu-id="bb781-175">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="bb781-176">Configuração de transporte HTTPS</span><span class="sxs-lookup"><span data-stu-id="bb781-176">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="bb781-177">Certificados x. 509 são usados para estabelecer a identidade do Gerenciador de transações.</span><span class="sxs-lookup"><span data-stu-id="bb781-177">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="bb781-178">Autenticação de cliente/servidor é necessária e autorização do cliente/servidor é mantida como um detalhe de implementação:</span><span class="sxs-lookup"><span data-stu-id="bb781-178">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
-   <span data-ttu-id="bb781-179">R1111: Certificados x. 509 apresentados pela conexão devem ter um nome de assunto que corresponda o nome de domínio totalmente qualificado (FQDN) do computador de origem.</span><span class="sxs-lookup"><span data-stu-id="bb781-179">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
-   <span data-ttu-id="bb781-180">B1112: O DNS deve ser funcional entre cada par de remetente e o receptor do sistema para verificações de nome de assunto de x. 509 seja bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="bb781-180">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="bb781-181">Ativação e registro de configuração de associação</span><span class="sxs-lookup"><span data-stu-id="bb781-181">Activation and Registration Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="bb781-182">requer a associação de solicitação/resposta duplex com correlação via HTTPS.</span><span class="sxs-lookup"><span data-stu-id="bb781-182"> requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="bb781-183">(Para obter mais informações sobre a correlação e descrições dos padrões de troca de mensagem de solicitação/resposta, consulte transação WS-Atomic, 8 de seção).</span><span class="sxs-lookup"><span data-stu-id="bb781-183">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="bb781-184">Configuração de associação de protocolo 2PC</span><span class="sxs-lookup"><span data-stu-id="bb781-184">2PC Protocol Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="bb781-185">oferece suporte a mensagens unidirecionais (datagrama) sobre HTTPS.</span><span class="sxs-lookup"><span data-stu-id="bb781-185"> supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="bb781-186">Correlação entre as mensagens será deixada como um detalhe de implementação.</span><span class="sxs-lookup"><span data-stu-id="bb781-186">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="bb781-187">B2131: Implementações devem suportar `wsa:ReferenceParameters` conforme descrito em WS-Addressing para alcançar a correlação de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]do 2PC mensagens.</span><span class="sxs-lookup"><span data-stu-id="bb781-187">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="bb781-188">Gerenciador de transações misto associação de segurança</span><span class="sxs-lookup"><span data-stu-id="bb781-188">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="bb781-189">Esta é uma alternativa (misto) que usa a segurança de transporte combinada com o modelo de Token emitido de coordenação WS para fins de estabelecimento de identidade de associação.</span><span class="sxs-lookup"><span data-stu-id="bb781-189">This is an alternate (mixed mode) binding that uses transport security combined with the  WS-Coordination Issued Token model for identity establishment purposes.</span></span>  <span data-ttu-id="bb781-190">Ativação e registro são os únicos elementos que diferem entre as duas associações.</span><span class="sxs-lookup"><span data-stu-id="bb781-190">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="bb781-191">Configuração de transporte HTTPS</span><span class="sxs-lookup"><span data-stu-id="bb781-191">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="bb781-192">Certificados x. 509 são usados para estabelecer a identidade do Gerenciador de transações.</span><span class="sxs-lookup"><span data-stu-id="bb781-192">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="bb781-193">Autenticação de cliente/servidor é necessária e autorização do cliente/servidor é mantida como um detalhe de implementação.</span><span class="sxs-lookup"><span data-stu-id="bb781-193">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="bb781-194">Configuração de associação de mensagem de ativação</span><span class="sxs-lookup"><span data-stu-id="bb781-194">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="bb781-195">Mensagens de ativação geralmente não participar de interoperabilidade porque eles ocorrem normalmente entre um aplicativo e seu gerente de transação local.</span><span class="sxs-lookup"><span data-stu-id="bb781-195">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="bb781-196">B1221: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa associação de HTTPS duplex (descrito na [protocolos de mensagens](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) para mensagens de ativação.</span><span class="sxs-lookup"><span data-stu-id="bb781-196">B1221: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="bb781-197">Mensagens de resposta e solicitação são correlacionadas usando 08/2004 do WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="bb781-197">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="bb781-198">Especificação WS-AT, 8 de seção, descreve mais detalhes sobre a correlação e os padrões de troca de mensagem.</span><span class="sxs-lookup"><span data-stu-id="bb781-198">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
-   <span data-ttu-id="bb781-199">R1222: após receber uma `CreateCoordinationContext`, o coordenador deve emitir uma `SecurityContextToken` com segredo associado `STx`.</span><span class="sxs-lookup"><span data-stu-id="bb781-199">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="bb781-200">Esse token é retornado em uma `t:IssuedTokens` cabeçalho após a especificação WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="bb781-200">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
-   <span data-ttu-id="bb781-201">R1223: Se a ativação ocorrer dentro de um contexto de coordenação existente, o `t:IssuedTokens` cabeçalho com o `SecurityContextToken` associado existente contexto deve fluir no `CreateCoordinationContext` mensagem.</span><span class="sxs-lookup"><span data-stu-id="bb781-201">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="bb781-202">Um novo `t:IssuedTokens` cabeçalho deve ser gerado para anexar para a saída `wscoor:CreateCoordinationContextResponse` mensagem.</span><span class="sxs-lookup"><span data-stu-id="bb781-202">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="bb781-203">Configuração de associação de mensagem de registro</span><span class="sxs-lookup"><span data-stu-id="bb781-203">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="bb781-204">B1231: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa associação de HTTPS duplex (descrito na [protocolos de mensagens](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="bb781-204">B1231: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="bb781-205">Mensagens de resposta e solicitação são correlacionadas usando 08/2004 do WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="bb781-205">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="bb781-206">WS-AtomicTransaction, 8 de seção descreve mais detalhes sobre a correlação e descrições dos padrões de troca de mensagem.</span><span class="sxs-lookup"><span data-stu-id="bb781-206">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="bb781-207">R1232: Saída `wscoor:Register` mensagens devem usar o `IssuedTokenOverTransport` o modo de autenticação descrito [protocolos de segurança](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="bb781-207">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="bb781-208">O `wsse:Timestamp` elemento deve ser assinado usando o `SecurityContextToken``STx` emitido.</span><span class="sxs-lookup"><span data-stu-id="bb781-208">The `wsse:Timestamp` element must be signed using the `SecurityContextToken``STx` issued.</span></span> <span data-ttu-id="bb781-209">Esta assinatura é uma prova de posse do token associado à transação específica e é usada para autenticar um participante inscrição na transação.</span><span class="sxs-lookup"><span data-stu-id="bb781-209">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="bb781-210">A mensagem RegistrationResponse é enviada novamente por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="bb781-210">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="bb781-211">Configuração de associação de protocolo 2PC</span><span class="sxs-lookup"><span data-stu-id="bb781-211">2PC Protocol Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="bb781-212">oferece suporte a mensagens unidirecionais (datagrama) sobre HTTPS.</span><span class="sxs-lookup"><span data-stu-id="bb781-212"> supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="bb781-213">Correlação entre as mensagens será deixada como um detalhe de implementação.</span><span class="sxs-lookup"><span data-stu-id="bb781-213">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="bb781-214">B2131: Implementações devem suportar `wsa:ReferenceParameters` conforme descrito em WS-Addressing para alcançar a correlação de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]do 2PC mensagens.</span><span class="sxs-lookup"><span data-stu-id="bb781-214">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="bb781-215">Troca de mensagens de aplicativo</span><span class="sxs-lookup"><span data-stu-id="bb781-215">Application Message Exchange</span></span>  
 <span data-ttu-id="bb781-216">Aplicativos estão livres para usar qualquer associação específica para mensagens de aplicativo, desde que a associação atende aos seguintes requisitos de segurança:</span><span class="sxs-lookup"><span data-stu-id="bb781-216">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
-   <span data-ttu-id="bb781-217">R2001: Mensagens de aplicativo para o aplicativo devem fluir de `t:IssuedTokens` cabeçalho junto com o `CoordinationContext` no cabeçalho da mensagem.</span><span class="sxs-lookup"><span data-stu-id="bb781-217">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
-   <span data-ttu-id="bb781-218">R2002: Integridade e confidencialidade de `t:IssuedToken` deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="bb781-218">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="bb781-219">O `CoordinationContext` cabeçalho contém `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="bb781-219">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="bb781-220">Enquanto a definição de `xsd:AnyURI` permite o uso de absolute e relative URIs, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oferece suporte apenas para `wscoor:Identifiers`, que são URIs absolutos.</span><span class="sxs-lookup"><span data-stu-id="bb781-220">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="bb781-221">Se o `wscoor:Identifier` do `wscoor:CoordinationContext` é um URI relativo, falhas serão retornadas de transacional [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços.</span><span class="sxs-lookup"><span data-stu-id="bb781-221">If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="bb781-222">Exemplos de mensagem</span><span class="sxs-lookup"><span data-stu-id="bb781-222">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="bb781-223">Mensagens de solicitação/resposta CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="bb781-223">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="bb781-224">As seguintes mensagens sigam um padrão de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="bb781-224">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext"></a><span data-ttu-id="bb781-225">CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="bb781-225">CreateCoordinationContext</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse"></a><span data-ttu-id="bb781-226">CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="bb781-226">CreateCoordinationContextResponse</span></span>  
  
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
  
### <a name="registration-messages"></a><span data-ttu-id="bb781-227">Mensagens de registro</span><span class="sxs-lookup"><span data-stu-id="bb781-227">Registration Messages</span></span>  
 <span data-ttu-id="bb781-228">As seguintes mensagens são mensagens de registro.</span><span class="sxs-lookup"><span data-stu-id="bb781-228">The following messages are registration messages.</span></span>  
  
#### <a name="register"></a><span data-ttu-id="bb781-229">Registro</span><span class="sxs-lookup"><span data-stu-id="bb781-229">Register</span></span>  
  
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
  
#### <a name="register-response"></a><span data-ttu-id="bb781-230">Resposta de registro</span><span class="sxs-lookup"><span data-stu-id="bb781-230">Register Response</span></span>  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="bb781-231">Duas mensagens de protocolo de confirmação de fase</span><span class="sxs-lookup"><span data-stu-id="bb781-231">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="bb781-232">A seguinte mensagem de erro se relaciona com o protocolo de confirmação de duas fases (2PC).</span><span class="sxs-lookup"><span data-stu-id="bb781-232">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit"></a><span data-ttu-id="bb781-233">Confirmação</span><span class="sxs-lookup"><span data-stu-id="bb781-233">Commit</span></span>  
  
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
  
### <a name="application-messages"></a><span data-ttu-id="bb781-234">Mensagens de aplicativo</span><span class="sxs-lookup"><span data-stu-id="bb781-234">Application Messages</span></span>  
 <span data-ttu-id="bb781-235">As seguintes mensagens são mensagens do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bb781-235">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="bb781-236">Solicitação de mensagem do aplicativo</span><span class="sxs-lookup"><span data-stu-id="bb781-236">Application message-Request</span></span>  
  
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
