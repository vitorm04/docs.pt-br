---
title: Protocolos de transação
ms.date: 03/30/2017
ms.assetid: 2820b0ec-2f32-430c-b299-1f0e95e1f2dc
ms.openlocfilehash: 17131c4cd10d9441ec65f9da4137147a703eb87c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600978"
---
# <a name="transaction-protocols"></a><span data-ttu-id="af40c-102">Protocolos de transação</span><span class="sxs-lookup"><span data-stu-id="af40c-102">Transaction Protocols</span></span>
<span data-ttu-id="af40c-103">Windows Communication Foundation (WCF) implementa os protocolos WS-Atomic Transaction e WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="af40c-103">Windows Communication Foundation (WCF) implements WS-Atomic Transaction and WS-Coordination protocols.</span></span>  
  
|<span data-ttu-id="af40c-104">Especificação/documento</span><span class="sxs-lookup"><span data-stu-id="af40c-104">Specification/Document</span></span>|<span data-ttu-id="af40c-105">Versão</span><span class="sxs-lookup"><span data-stu-id="af40c-105">Version</span></span>|<span data-ttu-id="af40c-106">Link</span><span class="sxs-lookup"><span data-stu-id="af40c-106">Link</span></span>|  
|-----------------------------|-------------|----------|  
|<span data-ttu-id="af40c-107">WS-Coordination</span><span class="sxs-lookup"><span data-stu-id="af40c-107">WS-Coordination</span></span>|<span data-ttu-id="af40c-108">1.0</span><span class="sxs-lookup"><span data-stu-id="af40c-108">1.0</span></span><br /><br /> <span data-ttu-id="af40c-109">1.1</span><span class="sxs-lookup"><span data-stu-id="af40c-109">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wscoor/><br /><br /> <https://docs.oasis-open.org/ws-tx/wscoor/2006/06>|  
|<span data-ttu-id="af40c-110">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="af40c-110">WS-AtomicTransaction</span></span>|<span data-ttu-id="af40c-111">1.0</span><span class="sxs-lookup"><span data-stu-id="af40c-111">1.0</span></span><br /><br /> <span data-ttu-id="af40c-112">1.1</span><span class="sxs-lookup"><span data-stu-id="af40c-112">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wsat/><br /><br /> <https://docs.oasis-open.org/ws-tx/wsat/2006/06>|  
  
 <span data-ttu-id="af40c-113">A interoperabilidade nessas especificações de protocolo é necessária em dois níveis: entre aplicativos e gerenciadores de transações (consulte a figura a seguir).</span><span class="sxs-lookup"><span data-stu-id="af40c-113">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="af40c-114">As especificações descrevem detalhadamente os formatos de mensagem e a troca de mensagens para os níveis de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="af40c-114">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="af40c-115">Determinadas segurança, confiabilidade e codificações para troca de aplicativo para aplicativo se aplicam como fazem para o intercâmbio de aplicativos regular.</span><span class="sxs-lookup"><span data-stu-id="af40c-115">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="af40c-116">No entanto, a interoperabilidade bem-sucedida entre gerenciadores de transações requer contrato na associação específica, pois normalmente não é configurada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="af40c-116">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="af40c-117">Este tópico descreve uma composição da especificação WS-Atomic (WS-AT) com segurança e descreve a associação segura usada para comunicação entre gerenciadores de transações.</span><span class="sxs-lookup"><span data-stu-id="af40c-117">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="af40c-118">A abordagem descrita neste documento foi testada com êxito com outras implementações de WS-AT e WS-Coordination, incluindo IBM, IONA, Sun Microsystems e outros.</span><span class="sxs-lookup"><span data-stu-id="af40c-118">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="af40c-119">A figura a seguir descreve a interoperabilidade entre dois gerenciadores de transações, o Gerenciador de transações 1 e o Gerenciador de transações 2 e dois aplicativos, aplicativo 1 e aplicativo 2:</span><span class="sxs-lookup"><span data-stu-id="af40c-119">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2:</span></span>  
  
 ![Captura de tela que mostra a interação entre gerenciadores de transações.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 <span data-ttu-id="af40c-121">Considere um cenário de transação WS-Coordination/WS-Atomic típico com um iniciador (I) e um participante (P).</span><span class="sxs-lookup"><span data-stu-id="af40c-121">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="af40c-122">O iniciador e o participante têm gerenciadores de transações, (ITM e PTM, respectivamente).</span><span class="sxs-lookup"><span data-stu-id="af40c-122">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="af40c-123">A confirmação de duas fases é conhecida como 2PC neste tópico.</span><span class="sxs-lookup"><span data-stu-id="af40c-123">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="af40c-124">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="af40c-124">1. CreateCoordinationContext</span></span>|<span data-ttu-id="af40c-125">12. resposta de mensagem do aplicativo</span><span class="sxs-lookup"><span data-stu-id="af40c-125">12. Application Message Response</span></span>|  
|<span data-ttu-id="af40c-126">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="af40c-126">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="af40c-127">13. Commit (conclusão)</span><span class="sxs-lookup"><span data-stu-id="af40c-127">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="af40c-128">3. registrar (conclusão)</span><span class="sxs-lookup"><span data-stu-id="af40c-128">3. Register (Completion)</span></span>|<span data-ttu-id="af40c-129">14. preparar (2PC)</span><span class="sxs-lookup"><span data-stu-id="af40c-129">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="af40c-130">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="af40c-130">4. RegisterResponse</span></span>|<span data-ttu-id="af40c-131">15. preparar (2PC)</span><span class="sxs-lookup"><span data-stu-id="af40c-131">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="af40c-132">5. mensagem do aplicativo</span><span class="sxs-lookup"><span data-stu-id="af40c-132">5. Application Message</span></span>|<span data-ttu-id="af40c-133">16. preparado (2PC)</span><span class="sxs-lookup"><span data-stu-id="af40c-133">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="af40c-134">6. CreateCoordinationContext com contexto</span><span class="sxs-lookup"><span data-stu-id="af40c-134">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="af40c-135">17. preparado (2PC)</span><span class="sxs-lookup"><span data-stu-id="af40c-135">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="af40c-136">7. registrar (durável)</span><span class="sxs-lookup"><span data-stu-id="af40c-136">7. Register (Durable)</span></span>|<span data-ttu-id="af40c-137">18. confirmado (conclusão)</span><span class="sxs-lookup"><span data-stu-id="af40c-137">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="af40c-138">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="af40c-138">8. RegisterResponse</span></span>|<span data-ttu-id="af40c-139">19. Commit (2PC)</span><span class="sxs-lookup"><span data-stu-id="af40c-139">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="af40c-140">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="af40c-140">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="af40c-141">20. Commit (2PC)</span><span class="sxs-lookup"><span data-stu-id="af40c-141">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="af40c-142">10. Register (durável)</span><span class="sxs-lookup"><span data-stu-id="af40c-142">10. Register (Durable)</span></span>|<span data-ttu-id="af40c-143">21. confirmado (2PC)</span><span class="sxs-lookup"><span data-stu-id="af40c-143">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="af40c-144">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="af40c-144">11. RegisterResponse</span></span>|<span data-ttu-id="af40c-145">22. confirmado (2PC)</span><span class="sxs-lookup"><span data-stu-id="af40c-145">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="af40c-146">Este documento descreve uma composição da especificação WS-AtomicTransaction com segurança e descreve a associação segura usada para comunicação entre gerenciadores de transações.</span><span class="sxs-lookup"><span data-stu-id="af40c-146">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="af40c-147">A abordagem descrita neste documento foi testada com êxito com outras implementações de WS-AT e WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="af40c-147">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="af40c-148">A figura e a tabela ilustram quatro classes de mensagens do ponto de vista da segurança:</span><span class="sxs-lookup"><span data-stu-id="af40c-148">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
- <span data-ttu-id="af40c-149">Mensagens de ativação (CreateCoordinationContext e CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="af40c-149">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
- <span data-ttu-id="af40c-150">Mensagens de registro (Register and RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="af40c-150">Registration messages (Register and RegisterResponse)</span></span>  
  
- <span data-ttu-id="af40c-151">Mensagens de protocolo (preparação, reversão, confirmação, anulada e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="af40c-151">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
- <span data-ttu-id="af40c-152">Mensagens de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="af40c-152">Application messages.</span></span>  
  
 <span data-ttu-id="af40c-153">As três primeiras classes de mensagem são consideradas mensagens do Gerenciador de transações e sua configuração de associação é descrita na "troca de mensagens do aplicativo" mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="af40c-153">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="af40c-154">A quarta classe de mensagem é aplicativo para mensagens de aplicativo e é descrita na seção "exemplos de mensagem" mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="af40c-154">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="af40c-155">Esta seção descreve as associações de protocolo usadas para cada uma dessas classes pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="af40c-155">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="af40c-156">Os namespaces XML e os prefixos associados a seguir são usados em todo este documento.</span><span class="sxs-lookup"><span data-stu-id="af40c-156">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="af40c-157">Prefixo</span><span class="sxs-lookup"><span data-stu-id="af40c-157">Prefix</span></span>|<span data-ttu-id="af40c-158">Versão</span><span class="sxs-lookup"><span data-stu-id="af40c-158">Version</span></span>|<span data-ttu-id="af40c-159">URI de namespace</span><span class="sxs-lookup"><span data-stu-id="af40c-159">Namespace URI</span></span>|  
|------------|-------------|-------------------|  
|<span data-ttu-id="af40c-160">S11</span><span class="sxs-lookup"><span data-stu-id="af40c-160">s11</span></span>||<https://schemas.xmlsoap.org/soap/envelope/>|  
|<span data-ttu-id="af40c-161">WSA</span><span class="sxs-lookup"><span data-stu-id="af40c-161">wsa</span></span>|<span data-ttu-id="af40c-162">Pré-1,0</span><span class="sxs-lookup"><span data-stu-id="af40c-162">Pre-1.0</span></span><br /><br /> <span data-ttu-id="af40c-163">1.0</span><span class="sxs-lookup"><span data-stu-id="af40c-163">1.0</span></span>|`http://www.w3.org/2004/08/addressing`<br /><br /> <https://www.w3.org/2005/08/addressing/>|  
|<span data-ttu-id="af40c-164">wscoor</span><span class="sxs-lookup"><span data-stu-id="af40c-164">wscoor</span></span>|<span data-ttu-id="af40c-165">1.0</span><span class="sxs-lookup"><span data-stu-id="af40c-165">1.0</span></span><br /><br /> <span data-ttu-id="af40c-166">1.1</span><span class="sxs-lookup"><span data-stu-id="af40c-166">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wscoor/><br /><br /> <https://docs.oasis-open.org/ws-tx/wscoor/2006/06>|  
|<span data-ttu-id="af40c-167">WSAT</span><span class="sxs-lookup"><span data-stu-id="af40c-167">wsat</span></span>|<span data-ttu-id="af40c-168">1.0</span><span class="sxs-lookup"><span data-stu-id="af40c-168">1.0</span></span><br /><br /> <span data-ttu-id="af40c-169">1.1</span><span class="sxs-lookup"><span data-stu-id="af40c-169">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wsat/><br /><br /> <https://docs.oasis-open.org/ws-tx/wsat/2006/06>|  
|<span data-ttu-id="af40c-170">t</span><span class="sxs-lookup"><span data-stu-id="af40c-170">t</span></span>|<span data-ttu-id="af40c-171">Pré-1,3</span><span class="sxs-lookup"><span data-stu-id="af40c-171">Pre-1.3</span></span><br /><br /> <span data-ttu-id="af40c-172">1.3</span><span class="sxs-lookup"><span data-stu-id="af40c-172">1.3</span></span>|<http://schemas.xmlsoap.org/ws/2005/02/trust/><br /><br /> <https://docs.oasis-open.org/ws-sx/ws-trust/200512>|  
|<span data-ttu-id="af40c-173">o</span><span class="sxs-lookup"><span data-stu-id="af40c-173">o</span></span>||<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd>|  
|<span data-ttu-id="af40c-174">xsd</span><span class="sxs-lookup"><span data-stu-id="af40c-174">xsd</span></span>||<https://www.w3.org/2001/XMLSchema>|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="af40c-175">Associações do Gerenciador de transações</span><span class="sxs-lookup"><span data-stu-id="af40c-175">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="af40c-176">R1001: os gerenciadores de transações que participam de uma transação WS-AT 1,0 devem usar SOAP 1,1 e WS-Addressing 2004/08 para transações WS-atômica e trocas de mensagens WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="af40c-176">R1001: Transaction Managers participating in a WS-AT 1.0 transaction must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="af40c-177">R1002: os gerenciadores de transações que participam de uma transação WS-AT 1,1 devem usar SOAP 1,1 e WS-Addressing 2005/08 para transações WS-atômica e trocas de mensagens WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="af40c-177">R1002: Transaction Managers participating in a WS-AT 1.1 transaction must use SOAP 1.1 and WS-Addressing 2005/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="af40c-178">As mensagens de aplicativo não são restritas a essas associações e são descritas posteriormente.</span><span class="sxs-lookup"><span data-stu-id="af40c-178">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="af40c-179">Associação HTTPS do Gerenciador de transações</span><span class="sxs-lookup"><span data-stu-id="af40c-179">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="af40c-180">A associação HTTPS do Gerenciador de transações depende exclusivamente da segurança de transporte para obter segurança e estabelecer confiança entre cada par remetente-destinatário na árvore de transações.</span><span class="sxs-lookup"><span data-stu-id="af40c-180">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="af40c-181">Configuração de transporte HTTPS</span><span class="sxs-lookup"><span data-stu-id="af40c-181">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="af40c-182">Os certificados X. 509 são usados para estabelecer a identidade do Gerenciador de transações.</span><span class="sxs-lookup"><span data-stu-id="af40c-182">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="af40c-183">A autenticação de cliente/servidor é necessária e a autorização de cliente/servidor é deixada como um detalhe de implementação:</span><span class="sxs-lookup"><span data-stu-id="af40c-183">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
- <span data-ttu-id="af40c-184">R1111: os certificados X. 509 apresentados pela transmissão devem ter um nome de entidade que corresponda ao FQDN (nome de domínio totalmente qualificado) da máquina de origem.</span><span class="sxs-lookup"><span data-stu-id="af40c-184">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
- <span data-ttu-id="af40c-185">B1112: o DNS deve ser funcional entre cada par remetente-destinatário no sistema para que as verificações de nome de entidade X. 509 tenham sucesso.</span><span class="sxs-lookup"><span data-stu-id="af40c-185">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="af40c-186">Configuração de associação de registro e ativação</span><span class="sxs-lookup"><span data-stu-id="af40c-186">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="af40c-187">O WCF requer Associação duplex de solicitação/resposta com correlação por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="af40c-187">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="af40c-188">(Para obter mais informações sobre correlação e descrições dos padrões de troca de mensagens de solicitação/resposta, consulte WS-Atomic Transaction, seção 8.)</span><span class="sxs-lookup"><span data-stu-id="af40c-188">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="af40c-189">Configuração de associação de protocolo 2PC</span><span class="sxs-lookup"><span data-stu-id="af40c-189">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="af40c-190">O WCF dá suporte a mensagens de uma via (datagrama) via HTTPS.</span><span class="sxs-lookup"><span data-stu-id="af40c-190">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="af40c-191">A correlação entre as mensagens é deixada como um detalhe de implementação.</span><span class="sxs-lookup"><span data-stu-id="af40c-191">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="af40c-192">B1131: as implementações devem dar suporte `wsa:ReferenceParameters` conforme descrito em WS-Addressing para obter a correlação das mensagens 2pc do WCF.</span><span class="sxs-lookup"><span data-stu-id="af40c-192">B1131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="af40c-193">Associação de segurança mista do Gerenciador de transações</span><span class="sxs-lookup"><span data-stu-id="af40c-193">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="af40c-194">Essa é uma associação alternativa (modo misto) que usa a segurança de transporte combinada com o modelo de token emitido pelo WS-Coordination para fins de estabelecimento de identidade.</span><span class="sxs-lookup"><span data-stu-id="af40c-194">This is an alternate (mixed mode) binding that uses transport security combined with the WS-Coordination Issued Token model for identity establishment purposes.</span></span> <span data-ttu-id="af40c-195">A ativação e o registro são os únicos elementos que diferem entre as duas associações.</span><span class="sxs-lookup"><span data-stu-id="af40c-195">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="af40c-196">Configuração de transporte HTTPS</span><span class="sxs-lookup"><span data-stu-id="af40c-196">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="af40c-197">Os certificados X. 509 são usados para estabelecer a identidade do Gerenciador de transações.</span><span class="sxs-lookup"><span data-stu-id="af40c-197">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="af40c-198">A autenticação de cliente/servidor é necessária e a autorização de cliente/servidor é deixada como um detalhe de implementação.</span><span class="sxs-lookup"><span data-stu-id="af40c-198">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="af40c-199">Configuração de associação de mensagem de ativação</span><span class="sxs-lookup"><span data-stu-id="af40c-199">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="af40c-200">As mensagens de ativação geralmente não participam da interoperabilidade porque elas normalmente ocorrem entre um aplicativo e seu Gerenciador de transações local.</span><span class="sxs-lookup"><span data-stu-id="af40c-200">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="af40c-201">B1221: o WCF usa a associação HTTPS duplex (descrita em [protocolos de mensagens](messaging-protocols.md)) para mensagens de ativação.</span><span class="sxs-lookup"><span data-stu-id="af40c-201">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="af40c-202">As mensagens de solicitação e de resposta são correlacionadas usando WS-Addressing 2004/08 para WS-AT 1,0 e WS-Addressing 2005/08 para WS-AT 1,1.</span><span class="sxs-lookup"><span data-stu-id="af40c-202">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="af40c-203">A especificação de transação WS-Atomic, seção 8, descreve mais detalhes sobre a correlação e os padrões de troca de mensagens.</span><span class="sxs-lookup"><span data-stu-id="af40c-203">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
- <span data-ttu-id="af40c-204">R1222: após receber um `CreateCoordinationContext` , o coordenador deve emitir um `SecurityContextToken` com um segredo associado `STx` .</span><span class="sxs-lookup"><span data-stu-id="af40c-204">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="af40c-205">Esse token é retornado dentro de um `t:IssuedTokens` cabeçalho após a especificação WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="af40c-205">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
- <span data-ttu-id="af40c-206">R1223: se a ativação ocorrer em um contexto de coordenação existente, o `t:IssuedTokens` cabeçalho com o `SecurityContextToken` contexto existente associado a deve fluir na `CreateCoordinationContext` mensagem.</span><span class="sxs-lookup"><span data-stu-id="af40c-206">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="af40c-207">Um novo `t:IssuedTokens` cabeçalho deve ser gerado para anexar à mensagem de saída `wscoor:CreateCoordinationContextResponse` .</span><span class="sxs-lookup"><span data-stu-id="af40c-207">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="af40c-208">Configuração de associação de mensagens de registro</span><span class="sxs-lookup"><span data-stu-id="af40c-208">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="af40c-209">B1231: o WCF usa a vinculação HTTPS duplex (descrita em [protocolos de mensagens](messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="af40c-209">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](messaging-protocols.md)).</span></span> <span data-ttu-id="af40c-210">As mensagens de solicitação e de resposta são correlacionadas usando WS-Addressing 2004/08 para WS-AT 1,0 e WS-Addressing 2005/08 para WS-AT 1,1.</span><span class="sxs-lookup"><span data-stu-id="af40c-210">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="af40c-211">O WS-AtomicTransaction, seção 8, descreve mais detalhes sobre correlação e descrições dos padrões de troca de mensagens.</span><span class="sxs-lookup"><span data-stu-id="af40c-211">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="af40c-212">R1232: `wscoor:Register` as mensagens de saída devem usar o `IssuedTokenOverTransport` modo de autenticação descrito em [protocolos de segurança](security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="af40c-212">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](security-protocols.md).</span></span>  
  
 <span data-ttu-id="af40c-213">O `wsse:Timestamp` elemento deve ser assinado usando o `SecurityContextToken STx` emitido.</span><span class="sxs-lookup"><span data-stu-id="af40c-213">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="af40c-214">Essa assinatura é uma prova de posse do token associado à transação específica e é usada para autenticar um participante que está inscrito na transação.</span><span class="sxs-lookup"><span data-stu-id="af40c-214">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="af40c-215">A mensagem RegistrationResponse é enviada de volta por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="af40c-215">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="af40c-216">Configuração de associação de protocolo 2PC</span><span class="sxs-lookup"><span data-stu-id="af40c-216">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="af40c-217">O WCF dá suporte a mensagens de uma via (datagrama) via HTTPS.</span><span class="sxs-lookup"><span data-stu-id="af40c-217">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="af40c-218">A correlação entre as mensagens é deixada como um detalhe de implementação.</span><span class="sxs-lookup"><span data-stu-id="af40c-218">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="af40c-219">B1241: as implementações devem dar suporte `wsa:ReferenceParameters` conforme descrito em WS-Addressing para obter a correlação das mensagens 2pc do WCF.</span><span class="sxs-lookup"><span data-stu-id="af40c-219">B1241: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="af40c-220">Troca de mensagens do aplicativo</span><span class="sxs-lookup"><span data-stu-id="af40c-220">Application Message Exchange</span></span>  
 <span data-ttu-id="af40c-221">Os aplicativos são livres para usar qualquer ligação específica para mensagens de aplicativo para aplicativo, desde que a ligação atenda aos seguintes requisitos de segurança:</span><span class="sxs-lookup"><span data-stu-id="af40c-221">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
- <span data-ttu-id="af40c-222">R2001: as mensagens de aplicativo para aplicativo devem fluir o `t:IssuedTokens` cabeçalho junto com o `CoordinationContext` no cabeçalho da mensagem.</span><span class="sxs-lookup"><span data-stu-id="af40c-222">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
- <span data-ttu-id="af40c-223">R2002: a integridade e a confidencialidade do `t:IssuedToken` devem ser fornecidas.</span><span class="sxs-lookup"><span data-stu-id="af40c-223">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="af40c-224">O `CoordinationContext` cabeçalho contém `wscoor:Identifier` .</span><span class="sxs-lookup"><span data-stu-id="af40c-224">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="af40c-225">Embora a definição de `xsd:AnyURI` permita o uso de URIs absolutos e relativos, o WCF dá suporte apenas `wscoor:Identifiers` a URIs absolutos.</span><span class="sxs-lookup"><span data-stu-id="af40c-225">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="af40c-226">B2003: se o `wscoor:Identifier` do `wscoor:CoordinationContext` for um URI relativo, as falhas serão retornadas dos serviços do WCF transacionais.</span><span class="sxs-lookup"><span data-stu-id="af40c-226">B2003: If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="af40c-227">Exemplos de mensagem</span><span class="sxs-lookup"><span data-stu-id="af40c-227">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="af40c-228">Mensagens de solicitação/resposta do CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="af40c-228">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="af40c-229">As mensagens a seguir seguem um padrão de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="af40c-229">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext-with-wscoor-10"></a><span data-ttu-id="af40c-230">CreateCoordinationContext com WSCoor 1,0</span><span class="sxs-lookup"><span data-stu-id="af40c-230">CreateCoordinationContext with WSCoor 1.0</span></span>  
  
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
        <wsu:Created>2005-12-15T23:36:09.921Z</wsu:Created>  
        <wsu:Expires>2005-12-15T23:41:09.921Z</wsu:Expires>  
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
  
#### <a name="createcoordinationcontext-with-wscoor-11"></a><span data-ttu-id="af40c-231">CreateCoordinationContext com WSCoor 1,1</span><span class="sxs-lookup"><span data-stu-id="af40c-231">CreateCoordinationContext with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>
<s:Header>  
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/CreateCoordinationContext</Action>  
<a:MessageID>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</MessageID>  
<a:ReplyTo>
<Address>https://...</a:Address>
</a:ReplyTo>
<a:To>https://...</a:To>
<wsse:Security>  
 <u:Timestamp>  
<wsu:Created>2005-12-15T23:36:09.921Z</wsu:Created>  
<wsu:Expires>2005-12-15T23:41:09.921Z</wsu:Expires>  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-pre-13-and-wscoor-10"></a><span data-ttu-id="af40c-232">CreateCoordinationContextResponse com confiança pré-1,3 e WSCoor 1,0</span><span class="sxs-lookup"><span data-stu-id="af40c-232">CreateCoordinationContextResponse with Trust Pre-1.3 and WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-13-and-wscoor-11"></a><span data-ttu-id="af40c-233">CreateCoordinationContextResponse com confiança 1,3 e WSCoor 1,1</span><span class="sxs-lookup"><span data-stu-id="af40c-233">CreateCoordinationContextResponse with Trust 1.3 and WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<!-- Data below is shown in the clear for illustration purposes only. -->
<s:Header>
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/CreateCoordinationContextResponse </a:Action>  
<a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
<a:To s:mustUnderstand="1">https://... </a:To>
<t:IssuedTokens>
<wst:RequestSecurityTokenResponse
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"
xmlns:wst="http://docs.oasis-open.org/ws-sx/ws-trust/200512"  
xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
<wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
<wst:RequestedSecurityToken>
<wsc:SecurityContextToken>
<wssu:Identifier> http://fabrikam123.com/SCTi  
</wssu:Identifier>
</wsc:SecurityContextToken>
</wst:RequestedSecurityToken>
<wsp:AppliesTo> http://fabrikam123.com/CCi </wsp:AppliesTo>  
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
  Type="http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey">  
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
<wscoor:Identifier> http://fabrikam123.com/CCi  
</wscoor:Identifier>
<wscoor:Expires>...</wscoor:Expires>  
<wscoor:CoordinationType>...</wscoor:CoordinationType>  
<wscoor:RegistrationService>
<a:Address>https://...</a:Address>  
<a:ReferenceParameters> ...  
</a:ReferenceParameters>  
</wscoor:RegistrationService>
</wscoor:CoordinationContext>
</wscoor:CreateCoordinationContextResponse>
</s:Body>
</s:Envelope>  
```  
  
### <a name="registration-messages"></a><span data-ttu-id="af40c-234">Mensagens de registro</span><span class="sxs-lookup"><span data-stu-id="af40c-234">Registration Messages</span></span>  
 <span data-ttu-id="af40c-235">As mensagens a seguir são mensagens de registro.</span><span class="sxs-lookup"><span data-stu-id="af40c-235">The following messages are registration messages.</span></span>  
  
#### <a name="register-with-wscoor-10"></a><span data-ttu-id="af40c-236">Registre-se no WSCoor 1,0</span><span class="sxs-lookup"><span data-stu-id="af40c-236">Register with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-with-wscoor-11"></a><span data-ttu-id="af40c-237">Registre-se no WSCoor 1,1</span><span class="sxs-lookup"><span data-stu-id="af40c-237">Register with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/Register</a:Action>
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
<wssu:Identifier> http://fabrikam123.com/SCTi  
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
<ds:DigestMethod  
Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
<ds:DigestValue> alRzyhjLgoUOYoh8cx4n75eTcUk=  
</ds:DigestValue>
</ds:Reference>
</ds:SignedInfo>  
<ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=  
</ds:SignatureValue>  
<ds:KeyInfo>
<wsse:SecurityTokenReference xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
  <wsse:Reference URI="http://fabrikam123.com/SCTi"/>  
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
  
#### <a name="register-response-with-wscoor-10"></a><span data-ttu-id="af40c-238">Registrar resposta com o WSCoor 1,0</span><span class="sxs-lookup"><span data-stu-id="af40c-238">Register Response with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-11"></a><span data-ttu-id="af40c-239">Registrar resposta com o WSCoor 1,1</span><span class="sxs-lookup"><span data-stu-id="af40c-239">Register Response with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>
<a:Action> http://docs.oasis-open.org/ws-tx/wscoor/2006/06/RegisterResponse  
</a:Action>
<a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
<a:RelatesTo> urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e </a:RelatesTo>  
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
<a:ReferenceParameters> ... </a:ReferenceParameters>  
</wscoor:CoordinatorProtocolService>
</wscoor:RegisterResponse>
</s:Body>
</s:Envelope>  
```  
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="af40c-240">Mensagens de protocolo de confirmação de duas fases</span><span class="sxs-lookup"><span data-stu-id="af40c-240">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="af40c-241">A mensagem a seguir está relacionada ao protocolo de confirmação de duas fases (2PC).</span><span class="sxs-lookup"><span data-stu-id="af40c-241">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit-with-wsat-10"></a><span data-ttu-id="af40c-242">Confirmar com WSAT 1,0</span><span class="sxs-lookup"><span data-stu-id="af40c-242">Commit with WSAT 1.0</span></span>  
  
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
  
#### <a name="commit-with-wsat-11"></a><span data-ttu-id="af40c-243">Confirmar com WSAT 1,1</span><span class="sxs-lookup"><span data-stu-id="af40c-243">Commit with WSAT 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>
<a:Action>http://docs.oasis-open.org/ws-tx/wsat/2006/06</a:Action>  
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
  
### <a name="application-messages"></a><span data-ttu-id="af40c-244">Mensagens de aplicativo</span><span class="sxs-lookup"><span data-stu-id="af40c-244">Application Messages</span></span>  
 <span data-ttu-id="af40c-245">As mensagens a seguir são mensagens de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="af40c-245">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="af40c-246">Solicitação de mensagem de aplicativo</span><span class="sxs-lookup"><span data-stu-id="af40c-246">Application message-Request</span></span>  
  
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
    <wsse11:EncryptedHeader>  
     <!-- encrypted wscoor:CoordinationContext header containing CCi -->  
    </wsse11:EncryptedHeader>  
    <wsse11:EncryptedHeader>
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
