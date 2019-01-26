---
title: Protocolos de transação versão 1.0
ms.date: 03/30/2017
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
ms.openlocfilehash: d2a50e798af47dd4f80f149362f2afffbab007f6
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066353"
---
# <a name="transaction-protocols-version-10"></a><span data-ttu-id="6c3ee-102">Protocolos de transação versão 1.0</span><span class="sxs-lookup"><span data-stu-id="6c3ee-102">Transaction Protocols version 1.0</span></span>
<span data-ttu-id="6c3ee-103">Versão 1 do Windows Communication Foundation (WCF) implementa a versão 1.0 dos protocolos WS-Coordination e de transações de WS-Atomic.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-103">Windows Communication Foundation (WCF) version 1 implements version 1.0 of the WS-Atomic Transaction and WS-Coordination protocols.</span></span> <span data-ttu-id="6c3ee-104">Para obter mais informações sobre a versão 1.1, consulte [protocolos de transação](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="6c3ee-104">For more information about version 1.1, see [Transaction Protocols](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span></span>  
  
|<span data-ttu-id="6c3ee-105">Especificação/documento</span><span class="sxs-lookup"><span data-stu-id="6c3ee-105">Specification/Document</span></span>|<span data-ttu-id="6c3ee-106">Link</span><span class="sxs-lookup"><span data-stu-id="6c3ee-106">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="6c3ee-107">WS-Coordination</span><span class="sxs-lookup"><span data-stu-id="6c3ee-107">WS-Coordination</span></span>|http://msdn.microsoft.com/ws/2005/08/ws-coordination/|  
|<span data-ttu-id="6c3ee-108">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="6c3ee-108">WS-AtomicTransaction</span></span>|http://msdn.microsoft.com/ws/2005/08/ws-atomictransaction/|  
  
 <span data-ttu-id="6c3ee-109">Interoperabilidade nessas especificações de protocolo é necessária em dois níveis: entre aplicativos e gerenciadores de transações (consulte a figura a seguir).</span><span class="sxs-lookup"><span data-stu-id="6c3ee-109">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="6c3ee-110">Especificações descrevem em detalhes os formatos de mensagem e a mensagem do exchange para ambos os níveis de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-110">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="6c3ee-111">Determinados segurança, confiabilidade e codificações para troca de aplicativo para aplicam como fazem para troca de aplicativo regular.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-111">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="6c3ee-112">No entanto, a interoperabilidade bem-sucedida entre gerenciadores de transações requer contrato de ligação específica, porque ele geralmente não é configurado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-112">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="6c3ee-113">Este tópico descreve uma composição da especificação WS-Atomic transação (WS-AT) com segurança e descreve a associação de segurança usada para comunicação entre os gerenciadores de transações.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-113">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="6c3ee-114">A abordagem descrita neste documento foram testada com êxito com outras implementações de WS-AT e WS-Coordination incluindo IBM, IONA, Sun Microsystems e outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-114">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="6c3ee-115">A figura a seguir ilustra a interoperabilidade entre dois gerenciadores de transações, gerente de transação 1 e 2 do Gerenciador de transações e dois aplicativos, o aplicativo 1 e 2 do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-115">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2.</span></span>  
  
 <span data-ttu-id="6c3ee-116">![Protocolos de transação](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span><span class="sxs-lookup"><span data-stu-id="6c3ee-116">![Transaction Protocols](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span></span>  
  
 <span data-ttu-id="6c3ee-117">Considere um cenário típico de transações WS-Coordination/WS-Atomic com um iniciador (I) e um participante (P).</span><span class="sxs-lookup"><span data-stu-id="6c3ee-117">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="6c3ee-118">O iniciador e o participante têm gerenciadores de transações (ITM e PTM, respectivamente).</span><span class="sxs-lookup"><span data-stu-id="6c3ee-118">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="6c3ee-119">Confirmação de duas fases é conhecida como 2PC neste tópico.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-119">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6c3ee-120">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="6c3ee-120">1. CreateCoordinationContext</span></span>|<span data-ttu-id="6c3ee-121">12. Resposta de mensagem do aplicativo</span><span class="sxs-lookup"><span data-stu-id="6c3ee-121">12. Application Message Response</span></span>|  
|<span data-ttu-id="6c3ee-122">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="6c3ee-122">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="6c3ee-123">13. Confirmação (término)</span><span class="sxs-lookup"><span data-stu-id="6c3ee-123">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="6c3ee-124">3. Registre-se (término)</span><span class="sxs-lookup"><span data-stu-id="6c3ee-124">3. Register (Completion)</span></span>|<span data-ttu-id="6c3ee-125">14. Preparar (2PC)</span><span class="sxs-lookup"><span data-stu-id="6c3ee-125">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="6c3ee-126">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="6c3ee-126">4. RegisterResponse</span></span>|<span data-ttu-id="6c3ee-127">15. Preparar (2PC)</span><span class="sxs-lookup"><span data-stu-id="6c3ee-127">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="6c3ee-128">5. Mensagem de aplicativo</span><span class="sxs-lookup"><span data-stu-id="6c3ee-128">5. Application Message</span></span>|<span data-ttu-id="6c3ee-129">16. Preparada (2PC)</span><span class="sxs-lookup"><span data-stu-id="6c3ee-129">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="6c3ee-130">6. CreateCoordinationContext com contexto</span><span class="sxs-lookup"><span data-stu-id="6c3ee-130">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="6c3ee-131">17. Preparada (2PC)</span><span class="sxs-lookup"><span data-stu-id="6c3ee-131">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="6c3ee-132">7. Registre-se (duráveis)</span><span class="sxs-lookup"><span data-stu-id="6c3ee-132">7. Register (Durable)</span></span>|<span data-ttu-id="6c3ee-133">18. Confirmada (término)</span><span class="sxs-lookup"><span data-stu-id="6c3ee-133">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="6c3ee-134">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="6c3ee-134">8. RegisterResponse</span></span>|<span data-ttu-id="6c3ee-135">19. Confirmação (2PC)</span><span class="sxs-lookup"><span data-stu-id="6c3ee-135">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="6c3ee-136">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="6c3ee-136">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="6c3ee-137">20. Confirmação (2PC)</span><span class="sxs-lookup"><span data-stu-id="6c3ee-137">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="6c3ee-138">10. Registre-se (duráveis)</span><span class="sxs-lookup"><span data-stu-id="6c3ee-138">10. Register (Durable)</span></span>|<span data-ttu-id="6c3ee-139">21. Confirmada (2PC)</span><span class="sxs-lookup"><span data-stu-id="6c3ee-139">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="6c3ee-140">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="6c3ee-140">11. RegisterResponse</span></span>|<span data-ttu-id="6c3ee-141">22. Confirmada (2PC)</span><span class="sxs-lookup"><span data-stu-id="6c3ee-141">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="6c3ee-142">Este documento descreve uma composição da especificação WS-AtomicTransaction com segurança e descreve a associação de segurança usada para comunicação entre os gerenciadores de transações.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-142">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="6c3ee-143">A abordagem descrita neste documento foram testada com êxito com outras implementações de WS-AT e WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-143">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="6c3ee-144">A figura e a tabela ilustram as quatro classes de mensagens do ponto de vista de segurança:</span><span class="sxs-lookup"><span data-stu-id="6c3ee-144">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
-   <span data-ttu-id="6c3ee-145">Mensagens de ativação (CreateCoordinationContext e CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="6c3ee-145">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
-   <span data-ttu-id="6c3ee-146">Mensagens de registro (registrar e RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="6c3ee-146">Registration messages (Register and RegisterResponse)</span></span>  
  
-   <span data-ttu-id="6c3ee-147">Mensagens de protocolo (preparar, reversão, confirmação, anulado e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="6c3ee-147">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
-   <span data-ttu-id="6c3ee-148">Mensagens de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-148">Application messages.</span></span>  
  
 <span data-ttu-id="6c3ee-149">As classes de três mensagem primeiras são consideradas mensagens do Gerenciador de transações e suas configurações de ligação é descrita em "Aplicativo de troca de mensagens" neste tópico.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-149">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="6c3ee-150">A quarta classe da mensagem é o aplicativo de mensagens e é descrita na seção "Exemplos de mensagem" neste tópico.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-150">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="6c3ee-151">Esta seção descreve as associações de protocolo usadas para cada uma dessas classes pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-151">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="6c3ee-152">Os seguintes Namespaces de XML e prefixos associados são usados em todo este documento.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-152">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="6c3ee-153">Prefixo</span><span class="sxs-lookup"><span data-stu-id="6c3ee-153">Prefix</span></span>|<span data-ttu-id="6c3ee-154">URI de Namespace</span><span class="sxs-lookup"><span data-stu-id="6c3ee-154">Namespace URI</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="6c3ee-155">s11</span><span class="sxs-lookup"><span data-stu-id="6c3ee-155">s11</span></span>|http://schemas.xmlsoap.org/soap/envelope|  
|<span data-ttu-id="6c3ee-156">wsa</span><span class="sxs-lookup"><span data-stu-id="6c3ee-156">wsa</span></span>|http://www.w3.org/2004/08/addressing|  
|<span data-ttu-id="6c3ee-157">wscoor</span><span class="sxs-lookup"><span data-stu-id="6c3ee-157">wscoor</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|<span data-ttu-id="6c3ee-158">wsat</span><span class="sxs-lookup"><span data-stu-id="6c3ee-158">wsat</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wsat|  
|<span data-ttu-id="6c3ee-159">t</span><span class="sxs-lookup"><span data-stu-id="6c3ee-159">t</span></span>|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|<span data-ttu-id="6c3ee-160">o</span><span class="sxs-lookup"><span data-stu-id="6c3ee-160">o</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="6c3ee-161">xsd</span><span class="sxs-lookup"><span data-stu-id="6c3ee-161">xsd</span></span>|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="6c3ee-162">Associações do Gerenciador de transações</span><span class="sxs-lookup"><span data-stu-id="6c3ee-162">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="6c3ee-163">R1001: Gerenciadores de transações devem usar o SOAP 1.1 e 08/2004 de WS-Addressing para transações de WS-Atomic e trocas de mensagens WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-163">R1001: Transaction Managers must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="6c3ee-164">Mensagens de aplicativo não são restritos a essas associações e são descritas posteriormente.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-164">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="6c3ee-165">Associação de HTTPS de Gerenciador de transações</span><span class="sxs-lookup"><span data-stu-id="6c3ee-165">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="6c3ee-166">A associação de HTTPS do Gerenciador de transação depende exclusivamente de segurança de transporte para atingir a segurança e estabelecer a relação de confiança entre cada par de receptor de remetente na árvore de transação.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-166">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="6c3ee-167">Configuração do transporte HTTPS</span><span class="sxs-lookup"><span data-stu-id="6c3ee-167">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="6c3ee-168">Certificados X.509 são usados para estabelecer a identidade do Gerenciador de transações.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-168">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="6c3ee-169">Autenticação de cliente/servidor é necessária e autorização de cliente/servidor é deixada como um detalhe de implementação:</span><span class="sxs-lookup"><span data-stu-id="6c3ee-169">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
-   <span data-ttu-id="6c3ee-170">R1111: Os certificados x. 509 apresentados durante a transmissão devem ter um nome de assunto que corresponda o nome de domínio totalmente qualificado (FQDN) do computador de origem.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-170">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
-   <span data-ttu-id="6c3ee-171">B1112: DNS deve ser funcional entre cada par de receptor de remetente no sistema para verificações de nome de assunto de x. 509 seja bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-171">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="6c3ee-172">Ativação e registro de configuração de associação</span><span class="sxs-lookup"><span data-stu-id="6c3ee-172">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="6c3ee-173">WCF requer a associação de solicitação/resposta duplex com correlação via HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-173">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="6c3ee-174">(Para obter mais informações sobre a correlação e as descrições dos padrões de troca de mensagem de solicitação/resposta, consulte transações WS-Atomic, seção 8).</span><span class="sxs-lookup"><span data-stu-id="6c3ee-174">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="6c3ee-175">Configuração de associação de protocolo 2PC</span><span class="sxs-lookup"><span data-stu-id="6c3ee-175">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="6c3ee-176">WCF dá suporte a mensagens unidirecionais (datagram) por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-176">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="6c3ee-177">Correlação entre as mensagens é deixada como um detalhe de implementação.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-177">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="6c3ee-178">B2131: Devem dar suporte a implementações `wsa:ReferenceParameters` conforme descrito em WS-Addressing para alcançar a correlação das mensagens de 2PC do WCF.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-178">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="6c3ee-179">Gerenciador de transações misto de associação de segurança</span><span class="sxs-lookup"><span data-stu-id="6c3ee-179">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="6c3ee-180">Essa é uma alternativa (modo misto) que usa segurança de transporte combinada com o modelo de Token emitido de WS-Coordination para fins de estabelecimento de identidade de associação.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-180">This is an alternate (mixed mode) binding that uses transport security combined with the  WS-Coordination Issued Token model for identity establishment purposes.</span></span>  <span data-ttu-id="6c3ee-181">Ativação e registro são os únicos elementos que diferem entre as duas associações.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-181">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="6c3ee-182">Configuração do transporte HTTPS</span><span class="sxs-lookup"><span data-stu-id="6c3ee-182">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="6c3ee-183">Certificados X.509 são usados para estabelecer a identidade do Gerenciador de transações.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-183">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="6c3ee-184">Autenticação de cliente/servidor é necessária e autorização de cliente/servidor é deixada como um detalhe de implementação.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-184">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="6c3ee-185">Configuração de associação de mensagem de ativação</span><span class="sxs-lookup"><span data-stu-id="6c3ee-185">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="6c3ee-186">Mensagens de ativação geralmente não participam interoperabilidade porque eles ocorrem normalmente entre um aplicativo e seu Gerenciador de transações locais.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-186">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="6c3ee-187">B1221: O WCF usa a associação de HTTPS duplex (descrito na [protocolos de mensagens](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) para mensagens de ativação.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-187">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="6c3ee-188">Mensagens de resposta e solicitação são correlacionadas usando 08/2004 de WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-188">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="6c3ee-189">Especificação WS-AT, seção 8 descreve ainda mais detalhes sobre a correlação e os padrões de troca de mensagem.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-189">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
-   <span data-ttu-id="6c3ee-190">R1222: Ao receber um `CreateCoordinationContext`, o coordenador deve emitir uma `SecurityContextToken` com o segredo associado `STx`.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-190">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="6c3ee-191">Esse token é retornado dentro de um `t:IssuedTokens` cabeçalho seguindo a especificação WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-191">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
-   <span data-ttu-id="6c3ee-192">R1223: Se a ativação ocorrer dentro de um contexto de coordenação existente, o `t:IssuedTokens` cabeçalho com o `SecurityContextToken` associado existente contexto deve fluir no `CreateCoordinationContext` mensagem.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-192">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="6c3ee-193">Uma nova `t:IssuedTokens` cabeçalho deve ser gerado para anexar a de saída `wscoor:CreateCoordinationContextResponse` mensagem.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-193">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="6c3ee-194">Configuração de associação de mensagem de registro</span><span class="sxs-lookup"><span data-stu-id="6c3ee-194">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="6c3ee-195">B1231: O WCF usa a associação de HTTPS duplex (descrito na [protocolos de mensagens](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="6c3ee-195">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="6c3ee-196">Mensagens de resposta e solicitação são correlacionadas usando 08/2004 de WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-196">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="6c3ee-197">WS-AtomicTransaction, seção 8 descreve ainda mais detalhes sobre a correlação e descrições dos padrões de troca de mensagem.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-197">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="6c3ee-198">R1232: Saída `wscoor:Register` mensagens devem usar o `IssuedTokenOverTransport` modo de autenticação descrito em [protocolos de segurança](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="6c3ee-198">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="6c3ee-199">O `wsse:Timestamp` elemento deve ser assinado usando o `SecurityContextToken STx` emitido.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-199">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="6c3ee-200">Essa assinatura é uma prova de posse do token associado à transação específica e é usada para autenticar um participante de inscrição na transação.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-200">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="6c3ee-201">A mensagem RegistrationResponse é enviada novamente via HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-201">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="6c3ee-202">Configuração de associação de protocolo 2PC</span><span class="sxs-lookup"><span data-stu-id="6c3ee-202">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="6c3ee-203">WCF dá suporte a mensagens unidirecionais (datagram) por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-203">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="6c3ee-204">Correlação entre as mensagens é deixada como um detalhe de implementação.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-204">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="6c3ee-205">B2131: Devem dar suporte a implementações `wsa:ReferenceParameters` conforme descrito em WS-Addressing para alcançar a correlação das mensagens de 2PC do WCF.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-205">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="6c3ee-206">Troca de mensagens de aplicativo</span><span class="sxs-lookup"><span data-stu-id="6c3ee-206">Application Message Exchange</span></span>  
 <span data-ttu-id="6c3ee-207">Aplicativos são livres para usar qualquer associação específica para mensagens de aplicativo para aplicativo, desde que a associação atende aos seguintes requisitos de segurança:</span><span class="sxs-lookup"><span data-stu-id="6c3ee-207">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
-   <span data-ttu-id="6c3ee-208">R2001: Mensagens de aplicativo para o aplicativo devem fluir a `t:IssuedTokens` cabeçalho juntamente com o `CoordinationContext` no cabeçalho da mensagem.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-208">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
-   <span data-ttu-id="6c3ee-209">R2002: Integridade e confidencialidade de `t:IssuedToken` deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-209">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="6c3ee-210">O `CoordinationContext` cabeçalho contém `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-210">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="6c3ee-211">Embora a definição de `xsd:AnyURI` permite o uso de URIs absolutos e relativos, o WCF oferece suporte apenas `wscoor:Identifiers`, que são URIs absolutos.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-211">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="6c3ee-212">Se o `wscoor:Identifier` do `wscoor:CoordinationContext` é um URI relativo, falhas serão retornadas de serviços do WCF transacionais.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-212">If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="6c3ee-213">Exemplos de mensagem</span><span class="sxs-lookup"><span data-stu-id="6c3ee-213">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="6c3ee-214">Mensagens de solicitação/resposta CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="6c3ee-214">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="6c3ee-215">As seguintes mensagens seguem um padrão de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-215">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext"></a><span data-ttu-id="6c3ee-216">CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="6c3ee-216">CreateCoordinationContext</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse"></a><span data-ttu-id="6c3ee-217">CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="6c3ee-217">CreateCoordinationContextResponse</span></span>  
  
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
  
### <a name="registration-messages"></a><span data-ttu-id="6c3ee-218">Mensagens de registro</span><span class="sxs-lookup"><span data-stu-id="6c3ee-218">Registration Messages</span></span>  
 <span data-ttu-id="6c3ee-219">As seguintes mensagens são mensagens de registro.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-219">The following messages are registration messages.</span></span>  
  
#### <a name="register"></a><span data-ttu-id="6c3ee-220">Registro</span><span class="sxs-lookup"><span data-stu-id="6c3ee-220">Register</span></span>  
  
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
  
#### <a name="register-response"></a><span data-ttu-id="6c3ee-221">Registrar a resposta</span><span class="sxs-lookup"><span data-stu-id="6c3ee-221">Register Response</span></span>  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="6c3ee-222">Duas mensagens de protocolo de confirmação de fase</span><span class="sxs-lookup"><span data-stu-id="6c3ee-222">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="6c3ee-223">A seguinte mensagem de erro se relaciona com o protocolo de confirmação de duas fases (2PC).</span><span class="sxs-lookup"><span data-stu-id="6c3ee-223">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit"></a><span data-ttu-id="6c3ee-224">Confirmação</span><span class="sxs-lookup"><span data-stu-id="6c3ee-224">Commit</span></span>  
  
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
  
### <a name="application-messages"></a><span data-ttu-id="6c3ee-225">Mensagens de aplicativo</span><span class="sxs-lookup"><span data-stu-id="6c3ee-225">Application Messages</span></span>  
 <span data-ttu-id="6c3ee-226">As seguintes mensagens são mensagens do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6c3ee-226">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="6c3ee-227">Solicitação de mensagem do aplicativo</span><span class="sxs-lookup"><span data-stu-id="6c3ee-227">Application message-Request</span></span>  
  
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
