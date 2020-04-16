---
title: Protocolos de transação versão 1.0
ms.date: 03/30/2017
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
ms.openlocfilehash: a775ca395e01e7ecbc676ba3ec97d19ae10b4f49
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464027"
---
# <a name="transaction-protocols-version-10"></a><span data-ttu-id="430bc-102">Protocolos de transação versão 1.0</span><span class="sxs-lookup"><span data-stu-id="430bc-102">Transaction Protocols version 1.0</span></span>
<span data-ttu-id="430bc-103">A versão 1 da Windows Communication Foundation (WCF) implementa a versão 1.0 dos protocolos WS-Atomic Transaction e WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="430bc-103">Windows Communication Foundation (WCF) version 1 implements version 1.0 of the WS-Atomic Transaction and WS-Coordination protocols.</span></span> <span data-ttu-id="430bc-104">Para obter mais informações sobre a versão 1.1, consulte [Protocolos de transação](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="430bc-104">For more information about version 1.1, see [Transaction Protocols](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span></span>  
  
|<span data-ttu-id="430bc-105">Especificação/Documento</span><span class="sxs-lookup"><span data-stu-id="430bc-105">Specification/Document</span></span>|<span data-ttu-id="430bc-106">Link</span><span class="sxs-lookup"><span data-stu-id="430bc-106">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="430bc-107">Coordenação ws</span><span class="sxs-lookup"><span data-stu-id="430bc-107">WS-Coordination</span></span>|<https://specs.xmlsoap.org/ws/2004/10/wscoor/wscoor.pdf>|  
|<span data-ttu-id="430bc-108">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="430bc-108">WS-AtomicTransaction</span></span>|<https://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf>|  
  
 <span data-ttu-id="430bc-109">A interoperabilidade nessas especificações de protocolo é exigida em dois níveis: entre aplicativos e entre gerentes de transações (veja a figura a seguir).</span><span class="sxs-lookup"><span data-stu-id="430bc-109">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="430bc-110">As especificações descrevem em grande detalhe os formatos de mensagem e a troca de mensagens para ambos os níveis de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="430bc-110">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="430bc-111">Certas seguranças, confiabilidade e codificações para troca de aplicativos para aplicativos se aplicam à troca regular de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="430bc-111">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="430bc-112">No entanto, a interoperabilidade bem-sucedida entre os gerentes de transação requer concordância sobre a vinculação específica, porque geralmente não é configurada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="430bc-112">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="430bc-113">Este tópico descreve uma composição da especificação WS-Atomic Transaction (WS-AT) com segurança e descreve a vinculação segura usada para comunicação entre os gerentes de transações.</span><span class="sxs-lookup"><span data-stu-id="430bc-113">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="430bc-114">A abordagem descrita neste documento foi testada com sucesso com outras implementações do WS-AT e ws-coordination, incluindo IBM, IONA, Sun Microsystems, entre outras.</span><span class="sxs-lookup"><span data-stu-id="430bc-114">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="430bc-115">A figura a seguir mostra a interoperabilidade entre dois gerentes de transação, o Gerenciador de Transações 1 e o Gerenciador de Transações 2, e dois aplicativos, Aplicativo 1 e Aplicativo 2:</span><span class="sxs-lookup"><span data-stu-id="430bc-115">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2:</span></span>  
  
 ![Captura de tela que mostra a interação entre os gerentes de transações.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 <span data-ttu-id="430bc-117">Considere um cenário típico de WS-Coordination/WS-Atomic Transaction com um Iniciador (I) e um Participante (P).</span><span class="sxs-lookup"><span data-stu-id="430bc-117">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="430bc-118">Tanto o Iniciador quanto o Participante possuem Gerentes de Transações (ITM e PTM, respectivamente).</span><span class="sxs-lookup"><span data-stu-id="430bc-118">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="430bc-119">O compromisso em duas fases é referido como 2PC neste tópico.</span><span class="sxs-lookup"><span data-stu-id="430bc-119">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="430bc-120">1. Criar CoordenaçãoContexto</span><span class="sxs-lookup"><span data-stu-id="430bc-120">1. CreateCoordinationContext</span></span>|<span data-ttu-id="430bc-121">12. Resposta de mensagem de aplicativo</span><span class="sxs-lookup"><span data-stu-id="430bc-121">12. Application Message Response</span></span>|  
|<span data-ttu-id="430bc-122">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="430bc-122">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="430bc-123">13. Comprometer (Conclusão)</span><span class="sxs-lookup"><span data-stu-id="430bc-123">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="430bc-124">3. Registre-se (Conclusão)</span><span class="sxs-lookup"><span data-stu-id="430bc-124">3. Register (Completion)</span></span>|<span data-ttu-id="430bc-125">14. Prepare (2PC)</span><span class="sxs-lookup"><span data-stu-id="430bc-125">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="430bc-126">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="430bc-126">4. RegisterResponse</span></span>|<span data-ttu-id="430bc-127">15. Prepare (2PC)</span><span class="sxs-lookup"><span data-stu-id="430bc-127">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="430bc-128">5. Mensagem de aplicativo</span><span class="sxs-lookup"><span data-stu-id="430bc-128">5. Application Message</span></span>|<span data-ttu-id="430bc-129">16. Preparado (2PC)</span><span class="sxs-lookup"><span data-stu-id="430bc-129">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="430bc-130">6. CriarCoordenaçãoContexto com Contexto</span><span class="sxs-lookup"><span data-stu-id="430bc-130">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="430bc-131">17. Preparado (2PC)</span><span class="sxs-lookup"><span data-stu-id="430bc-131">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="430bc-132">7. Registre-se (Durável)</span><span class="sxs-lookup"><span data-stu-id="430bc-132">7. Register (Durable)</span></span>|<span data-ttu-id="430bc-133">18. Comprometido (Conclusão)</span><span class="sxs-lookup"><span data-stu-id="430bc-133">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="430bc-134">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="430bc-134">8. RegisterResponse</span></span>|<span data-ttu-id="430bc-135">19. Comprometer (2PC)</span><span class="sxs-lookup"><span data-stu-id="430bc-135">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="430bc-136">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="430bc-136">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="430bc-137">20. Comprometer (2PC)</span><span class="sxs-lookup"><span data-stu-id="430bc-137">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="430bc-138">10. Registro (Durável)</span><span class="sxs-lookup"><span data-stu-id="430bc-138">10. Register (Durable)</span></span>|<span data-ttu-id="430bc-139">21. Comprometido (2PC)</span><span class="sxs-lookup"><span data-stu-id="430bc-139">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="430bc-140">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="430bc-140">11. RegisterResponse</span></span>|<span data-ttu-id="430bc-141">22. Comprometido (2PC)</span><span class="sxs-lookup"><span data-stu-id="430bc-141">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="430bc-142">Este documento descreve uma composição da especificação WS-AtomicTransaction com segurança e descreve a vinculação segura usada para comunicação entre os gerentes de transações.</span><span class="sxs-lookup"><span data-stu-id="430bc-142">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="430bc-143">A abordagem descrita neste documento foi testada com sucesso com outras implementações do WS-AT e ws-coordination.</span><span class="sxs-lookup"><span data-stu-id="430bc-143">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="430bc-144">A figura e a tabela ilustram quatro classes de mensagens do ponto de vista da segurança:</span><span class="sxs-lookup"><span data-stu-id="430bc-144">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
- <span data-ttu-id="430bc-145">Mensagens de ativação (CreateCoordinationContext e CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="430bc-145">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
- <span data-ttu-id="430bc-146">Mensagens de registro (Register and RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="430bc-146">Registration messages (Register and RegisterResponse)</span></span>  
  
- <span data-ttu-id="430bc-147">Mensagens de protocolo (Prepare, Rerole, Comprometa, Aborte e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="430bc-147">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
- <span data-ttu-id="430bc-148">Mensagens de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="430bc-148">Application messages.</span></span>  
  
 <span data-ttu-id="430bc-149">As três primeiras classes de mensagens são consideradas mensagens do Gerenciador de Transações e sua configuração vinculativa é descrita na "Troca de mensagens de aplicativo" mais tarde neste tópico.</span><span class="sxs-lookup"><span data-stu-id="430bc-149">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="430bc-150">A quarta classe de mensagem é aplicativo para mensagens de aplicativo e é descrita na seção "Exemplos de mensagens" mais tarde neste tópico.</span><span class="sxs-lookup"><span data-stu-id="430bc-150">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="430bc-151">Esta seção descreve as vinculações de protocolo usadas para cada uma dessas classes pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="430bc-151">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="430bc-152">Os seguintes Namespaces XML e prefixos associados são usados ao longo deste documento.</span><span class="sxs-lookup"><span data-stu-id="430bc-152">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="430bc-153">Prefixo</span><span class="sxs-lookup"><span data-stu-id="430bc-153">Prefix</span></span>|<span data-ttu-id="430bc-154">URI de namespace</span><span class="sxs-lookup"><span data-stu-id="430bc-154">Namespace URI</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="430bc-155">s11</span><span class="sxs-lookup"><span data-stu-id="430bc-155">s11</span></span>|http://schemas.xmlsoap.org/soap/envelope|  
|<span data-ttu-id="430bc-156">Wsa</span><span class="sxs-lookup"><span data-stu-id="430bc-156">wsa</span></span>|http://www.w3.org/2004/08/addressing|  
|<span data-ttu-id="430bc-157">wscoor</span><span class="sxs-lookup"><span data-stu-id="430bc-157">wscoor</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|<span data-ttu-id="430bc-158">wsat</span><span class="sxs-lookup"><span data-stu-id="430bc-158">wsat</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wsat|  
|<span data-ttu-id="430bc-159">t</span><span class="sxs-lookup"><span data-stu-id="430bc-159">t</span></span>|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|<span data-ttu-id="430bc-160">o</span><span class="sxs-lookup"><span data-stu-id="430bc-160">o</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="430bc-161">xsd</span><span class="sxs-lookup"><span data-stu-id="430bc-161">xsd</span></span>|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="430bc-162">Vinculações do Gerenciador de Transações</span><span class="sxs-lookup"><span data-stu-id="430bc-162">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="430bc-163">R1001: Os gerentes de transação devem usar o SOAP 1.1 e o WS-Addressing 2004/08 para trocas de mensagens WS-Atomic Transaction e WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="430bc-163">R1001: Transaction Managers must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="430bc-164">As mensagens de aplicativo não são restritas a essas vinculações e são descritas posteriormente.</span><span class="sxs-lookup"><span data-stu-id="430bc-164">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="430bc-165">Vinculação HTTPS do Gerenciador de Transações</span><span class="sxs-lookup"><span data-stu-id="430bc-165">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="430bc-166">A vinculação HTTPS do gerenciador de transações depende exclusivamente da segurança do transporte para obter segurança e estabelecer confiança entre cada par de remetente-receptor na árvore de transações.</span><span class="sxs-lookup"><span data-stu-id="430bc-166">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="430bc-167">Configuração de transporte HTTPS</span><span class="sxs-lookup"><span data-stu-id="430bc-167">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="430bc-168">Os certificados X.509 são usados para estabelecer a identidade do gerenciador de transações.</span><span class="sxs-lookup"><span data-stu-id="430bc-168">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="430bc-169">A autenticação do cliente/servidor é necessária e a autorização do cliente/servidor é deixada como um detalhe de implementação:</span><span class="sxs-lookup"><span data-stu-id="430bc-169">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
- <span data-ttu-id="430bc-170">R1111: Os certificados X.509 apresentados sobre o fio devem ter um nome de assunto que corresponda ao nome de domínio totalmente qualificado (FQDN) da máquina de origem.</span><span class="sxs-lookup"><span data-stu-id="430bc-170">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
- <span data-ttu-id="430bc-171">B1112: O DNS deve ser funcional entre cada par de remetente-receptor no sistema para que o nome do sujeito X.509 seja bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="430bc-171">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="430bc-172">Configuração de ativação e registro</span><span class="sxs-lookup"><span data-stu-id="430bc-172">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="430bc-173">O WCF requer a vinculação duplex de solicitação/resposta com correlação sobre HTTPS.</span><span class="sxs-lookup"><span data-stu-id="430bc-173">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="430bc-174">(Para obter mais informações sobre correlação e descrições dos padrões de troca de mensagens de solicitação/resposta, consulte Transação WS-Atomic, Seção 8.)</span><span class="sxs-lookup"><span data-stu-id="430bc-174">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="430bc-175">Configuração de vinculação do protocolo 2PC</span><span class="sxs-lookup"><span data-stu-id="430bc-175">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="430bc-176">O WCF suporta mensagens unidirecionais (datagram) sobre HTTPS.</span><span class="sxs-lookup"><span data-stu-id="430bc-176">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="430bc-177">A correlação entre as mensagens é deixada como um detalhe de implementação.</span><span class="sxs-lookup"><span data-stu-id="430bc-177">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="430bc-178">B2131: As implementações devem apoiar `wsa:ReferenceParameters` conforme descrito no WS-Addressing para alcançar a correlação das mensagens 2PC do WCF.</span><span class="sxs-lookup"><span data-stu-id="430bc-178">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="430bc-179">Vinculação de segurança mista do gerenciador de transações</span><span class="sxs-lookup"><span data-stu-id="430bc-179">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="430bc-180">Esta é uma vinculação alternativa (modo misto) que usa segurança de transporte combinada com o modelo De token emitido pelo WS-Coordination para fins de estabelecimento de identidade.</span><span class="sxs-lookup"><span data-stu-id="430bc-180">This is an alternate (mixed mode) binding that uses transport security combined with the  WS-Coordination Issued Token model for identity establishment purposes.</span></span>  <span data-ttu-id="430bc-181">Ativação e Registro são os únicos elementos que diferem entre as duas ligações.</span><span class="sxs-lookup"><span data-stu-id="430bc-181">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="430bc-182">Configuração de transporte HTTPS</span><span class="sxs-lookup"><span data-stu-id="430bc-182">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="430bc-183">Os certificados X.509 são usados para estabelecer a identidade do gerenciador de transações.</span><span class="sxs-lookup"><span data-stu-id="430bc-183">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="430bc-184">A autenticação do cliente/servidor é necessária e a autorização do cliente/servidor é deixada como um detalhe de implementação.</span><span class="sxs-lookup"><span data-stu-id="430bc-184">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="430bc-185">Configuração de vinculação de mensagem de ativação</span><span class="sxs-lookup"><span data-stu-id="430bc-185">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="430bc-186">As mensagens de ativação geralmente não participam da interoperabilidade porque normalmente ocorrem entre um aplicativo e seu gerenciador de transações local.</span><span class="sxs-lookup"><span data-stu-id="430bc-186">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="430bc-187">B1221: O WCF usa a vinculação HTTPS duplex (descrita em [Protocolos de Mensagens)](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)para mensagens de ativação.</span><span class="sxs-lookup"><span data-stu-id="430bc-187">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="430bc-188">As mensagens de solicitação e resposta estão correlacionadas usando o WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="430bc-188">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="430bc-189">A especificação ws-atomic transaction, Seção 8, descreve mais detalhes sobre correlação e os padrões de troca de mensagens.</span><span class="sxs-lookup"><span data-stu-id="430bc-189">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
- <span data-ttu-id="430bc-190">R1222: Ao `CreateCoordinationContext`receber um , `SecurityContextToken` o Coordenador `STx`deve emitir um segredo associado .</span><span class="sxs-lookup"><span data-stu-id="430bc-190">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="430bc-191">Este token é devolvido `t:IssuedTokens` dentro de um cabeçalho seguindo a especificação ws-trust.</span><span class="sxs-lookup"><span data-stu-id="430bc-191">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
- <span data-ttu-id="430bc-192">R1223: Se a ativação ocorrer dentro `t:IssuedTokens` de `SecurityContextToken` um contexto de coordenação `CreateCoordinationContext` existente, o cabeçalho com o contexto existente deve fluir na mensagem.</span><span class="sxs-lookup"><span data-stu-id="430bc-192">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="430bc-193">Um `t:IssuedTokens` novo cabeçalho deve ser gerado `wscoor:CreateCoordinationContextResponse` para anexar à mensagem de saída.</span><span class="sxs-lookup"><span data-stu-id="430bc-193">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="430bc-194">Configuração de vinculação de mensagem de registro</span><span class="sxs-lookup"><span data-stu-id="430bc-194">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="430bc-195">B1231: O WCF usa a vinculação HTTPS duplex (descrita em [Protocolos de Mensagens](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="430bc-195">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="430bc-196">As mensagens de solicitação e resposta estão correlacionadas usando o WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="430bc-196">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="430bc-197">WS-AtomicTransaction, Seção 8, descreve mais detalhes sobre correlação e descrições dos padrões de troca de mensagens.</span><span class="sxs-lookup"><span data-stu-id="430bc-197">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="430bc-198">R1232: As `wscoor:Register` mensagens de `IssuedTokenOverTransport` saída devem usar o modo de autenticação descrito nos [Protocolos de Segurança](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="430bc-198">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="430bc-199">O `wsse:Timestamp` elemento deve ser `SecurityContextToken STx` assinado usando o emitido.</span><span class="sxs-lookup"><span data-stu-id="430bc-199">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="430bc-200">Esta assinatura é uma prova de posse do token associado à transação específica e é usada para autenticar um participante alistando-se na transação.</span><span class="sxs-lookup"><span data-stu-id="430bc-200">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="430bc-201">A mensagem RegistrationResponse é enviada de volta pelo HTTPS.</span><span class="sxs-lookup"><span data-stu-id="430bc-201">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="430bc-202">Configuração de vinculação do protocolo 2PC</span><span class="sxs-lookup"><span data-stu-id="430bc-202">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="430bc-203">O WCF suporta mensagens unidirecionais (datagram) sobre HTTPS.</span><span class="sxs-lookup"><span data-stu-id="430bc-203">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="430bc-204">A correlação entre as mensagens é deixada como um detalhe de implementação.</span><span class="sxs-lookup"><span data-stu-id="430bc-204">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="430bc-205">B2131: As implementações devem apoiar `wsa:ReferenceParameters` conforme descrito no WS-Addressing para alcançar a correlação das mensagens 2PC do WCF.</span><span class="sxs-lookup"><span data-stu-id="430bc-205">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="430bc-206">Troca de mensagens de aplicativo</span><span class="sxs-lookup"><span data-stu-id="430bc-206">Application Message Exchange</span></span>  
 <span data-ttu-id="430bc-207">Os aplicativos são livres para usar qualquer vinculação específica para mensagens de aplicativo para aplicativo, desde que a vinculação atenda aos seguintes requisitos de segurança:</span><span class="sxs-lookup"><span data-stu-id="430bc-207">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
- <span data-ttu-id="430bc-208">R2001: As mensagens de aplicativo `t:IssuedTokens` para aplicativo `CoordinationContext` devem fluir o cabeçalho juntamente com o cabeçalho da mensagem.</span><span class="sxs-lookup"><span data-stu-id="430bc-208">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
- <span data-ttu-id="430bc-209">R2002: A integridade e `t:IssuedToken` a confidencialidade devem ser fornecidas.</span><span class="sxs-lookup"><span data-stu-id="430bc-209">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="430bc-210">O `CoordinationContext` cabeçalho contém `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="430bc-210">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="430bc-211">Enquanto a `xsd:AnyURI` definição de permite o uso de URIs `wscoor:Identifiers`absolutas e relativas, o WCF suporta apenas , que são URIs absolutas.</span><span class="sxs-lookup"><span data-stu-id="430bc-211">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="430bc-212">Se `wscoor:Identifier` o `wscoor:CoordinationContext` do é um URI relativo, as falhas serão devolvidas de serviços WCF transacionais.</span><span class="sxs-lookup"><span data-stu-id="430bc-212">If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="430bc-213">Exemplos de mensagens</span><span class="sxs-lookup"><span data-stu-id="430bc-213">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="430bc-214">Criarmensageações de solicitação/resposta de contexto de coordenação</span><span class="sxs-lookup"><span data-stu-id="430bc-214">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="430bc-215">As mensagens a seguir seguem um padrão de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="430bc-215">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext"></a><span data-ttu-id="430bc-216">CriarCoordenaçãoContexto</span><span class="sxs-lookup"><span data-stu-id="430bc-216">CreateCoordinationContext</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse"></a><span data-ttu-id="430bc-217">CriarCoordenaçãoContextResponse</span><span class="sxs-lookup"><span data-stu-id="430bc-217">CreateCoordinationContextResponse</span></span>  
  
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
  
### <a name="registration-messages"></a><span data-ttu-id="430bc-218">Mensagens de registro</span><span class="sxs-lookup"><span data-stu-id="430bc-218">Registration Messages</span></span>  
 <span data-ttu-id="430bc-219">As seguintes mensagens são mensagens de registro.</span><span class="sxs-lookup"><span data-stu-id="430bc-219">The following messages are registration messages.</span></span>  
  
#### <a name="register"></a><span data-ttu-id="430bc-220">Registrar </span><span class="sxs-lookup"><span data-stu-id="430bc-220">Register</span></span>  
  
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
  
#### <a name="register-response"></a><span data-ttu-id="430bc-221">Registrar resposta</span><span class="sxs-lookup"><span data-stu-id="430bc-221">Register Response</span></span>  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="430bc-222">Mensagens de protocolo de confirmação de duas fases</span><span class="sxs-lookup"><span data-stu-id="430bc-222">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="430bc-223">A mensagem a seguir diz respeito ao protocolo de confirmação bifásica (2PC).</span><span class="sxs-lookup"><span data-stu-id="430bc-223">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit"></a><span data-ttu-id="430bc-224">Commit</span><span class="sxs-lookup"><span data-stu-id="430bc-224">Commit</span></span>  
  
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
  
### <a name="application-messages"></a><span data-ttu-id="430bc-225">Mensagens de aplicativo</span><span class="sxs-lookup"><span data-stu-id="430bc-225">Application Messages</span></span>  
 <span data-ttu-id="430bc-226">As seguintes mensagens são mensagens de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="430bc-226">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="430bc-227">Solicitação de mensagem do aplicativo</span><span class="sxs-lookup"><span data-stu-id="430bc-227">Application message-Request</span></span>  
  
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
