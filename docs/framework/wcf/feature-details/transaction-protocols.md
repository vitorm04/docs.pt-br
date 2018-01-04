---
title: "Protocolos de transação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2820b0ec-2f32-430c-b299-1f0e95e1f2dc
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13784a3a5062705abba1b3bbb33a04e66bd22072
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-protocols"></a><span data-ttu-id="938bf-102">Protocolos de transação</span><span class="sxs-lookup"><span data-stu-id="938bf-102">Transaction Protocols</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="938bf-103">implementa os protocolos WS-AT e coordenação WS.</span><span class="sxs-lookup"><span data-stu-id="938bf-103"> implements WS-Atomic Transaction and WS-Coordination protocols.</span></span>  
  
|<span data-ttu-id="938bf-104">Documento de especificação /</span><span class="sxs-lookup"><span data-stu-id="938bf-104">Specification/Document</span></span>|<span data-ttu-id="938bf-105">Versão</span><span class="sxs-lookup"><span data-stu-id="938bf-105">Version</span></span>|<span data-ttu-id="938bf-106">Link</span><span class="sxs-lookup"><span data-stu-id="938bf-106">Link</span></span>|  
|-----------------------------|-------------|----------|  
|<span data-ttu-id="938bf-107">Coordenação WS</span><span class="sxs-lookup"><span data-stu-id="938bf-107">WS-Coordination</span></span>|<span data-ttu-id="938bf-108">1.0</span><span class="sxs-lookup"><span data-stu-id="938bf-108">1.0</span></span><br /><br /> <span data-ttu-id="938bf-109">1.1</span><span class="sxs-lookup"><span data-stu-id="938bf-109">1.1</span></span>|[<span data-ttu-id="938bf-110">http://go.microsoft.com/fwlink/?LinkId=96104</span><span class="sxs-lookup"><span data-stu-id="938bf-110">http://go.microsoft.com/fwlink/?LinkId=96104</span></span>](http://go.microsoft.com/fwlink/?LinkId=96104)<br /><br /> [<span data-ttu-id="938bf-111">http://go.microsoft.com/fwlink/?LinkId=96079</span><span class="sxs-lookup"><span data-stu-id="938bf-111">http://go.microsoft.com/fwlink/?LinkId=96079</span></span>](http://go.microsoft.com/fwlink/?LinkId=96079)|  
|<span data-ttu-id="938bf-112">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="938bf-112">WS-AtomicTransaction</span></span>|<span data-ttu-id="938bf-113">1.0</span><span class="sxs-lookup"><span data-stu-id="938bf-113">1.0</span></span><br /><br /> <span data-ttu-id="938bf-114">1.1</span><span class="sxs-lookup"><span data-stu-id="938bf-114">1.1</span></span>|[<span data-ttu-id="938bf-115">http://go.microsoft.com/fwlink/?LinkId=96080</span><span class="sxs-lookup"><span data-stu-id="938bf-115">http://go.microsoft.com/fwlink/?LinkId=96080</span></span>](http://go.microsoft.com/fwlink/?LinkId=96080)<br /><br /> <span data-ttu-id="938bf-116">http://go.microsoft.com/fwlink/?LinkId=96081</span><span class="sxs-lookup"><span data-stu-id="938bf-116">http://go.microsoft.com/fwlink/?LinkId=96081</span></span>|  
  
 <span data-ttu-id="938bf-117">Interoperabilidade nessas especificações de protocolo é necessária em dois níveis: entre aplicativos e gerenciadores de transações (consulte a figura a seguir).</span><span class="sxs-lookup"><span data-stu-id="938bf-117">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="938bf-118">Especificações descrevem detalhadamente os formatos de mensagem e a mensagem do exchange para ambos os níveis de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="938bf-118">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="938bf-119">Determinados segurança, confiabilidade e codificações para o aplicativo para exchange se aplicam para troca de aplicativo comum.</span><span class="sxs-lookup"><span data-stu-id="938bf-119">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="938bf-120">No entanto, interoperabilidade com êxito entre gerenciadores de transações exige contrato na associação de determinado, porque geralmente não está configurado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="938bf-120">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="938bf-121">Este tópico descreve uma composição da especificação de transação WS-Atomic (WS-AT) com segurança e descreve a associação de segurança usada para comunicação entre os gerenciadores de transações.</span><span class="sxs-lookup"><span data-stu-id="938bf-121">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="938bf-122">A abordagem descrita neste documento foram testada com êxito com outras implementações do WS-AT e coordenação WS incluindo IBM, IONA, Sun Microsystems e outros.</span><span class="sxs-lookup"><span data-stu-id="938bf-122">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="938bf-123">A figura a seguir ilustra a interoperabilidade entre dois gerenciadores de transações, gerente de transação 1 e 2 do Gerenciador de transações e dois aplicativos, o aplicativo 1 e 2 do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="938bf-123">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2.</span></span>  
  
 <span data-ttu-id="938bf-124">![Protocolos de transação](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span><span class="sxs-lookup"><span data-stu-id="938bf-124">![Transaction Protocols](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span></span>  
  
 <span data-ttu-id="938bf-125">Considere um cenário típico de WS-coordenação/WS-AT com um iniciador (I) e um participante (P).</span><span class="sxs-lookup"><span data-stu-id="938bf-125">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="938bf-126">O iniciador e o participante tem gerenciadores de transações (ITM e PTM, respectivamente).</span><span class="sxs-lookup"><span data-stu-id="938bf-126">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="938bf-127">Confirmação de duas fases é conhecida como 2PC neste tópico.</span><span class="sxs-lookup"><span data-stu-id="938bf-127">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="938bf-128">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="938bf-128">1. CreateCoordinationContext</span></span>|<span data-ttu-id="938bf-129">12. Resposta de mensagem do aplicativo</span><span class="sxs-lookup"><span data-stu-id="938bf-129">12. Application Message Response</span></span>|  
|<span data-ttu-id="938bf-130">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="938bf-130">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="938bf-131">13. Confirmação (preenchimento)</span><span class="sxs-lookup"><span data-stu-id="938bf-131">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="938bf-132">3. Registro (preenchimento)</span><span class="sxs-lookup"><span data-stu-id="938bf-132">3. Register (Completion)</span></span>|<span data-ttu-id="938bf-133">14. Preparar (2PC)</span><span class="sxs-lookup"><span data-stu-id="938bf-133">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="938bf-134">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="938bf-134">4. RegisterResponse</span></span>|<span data-ttu-id="938bf-135">15. Preparar (2PC)</span><span class="sxs-lookup"><span data-stu-id="938bf-135">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="938bf-136">5. Mensagem de aplicativo</span><span class="sxs-lookup"><span data-stu-id="938bf-136">5. Application Message</span></span>|<span data-ttu-id="938bf-137">16. Preparada (2PC)</span><span class="sxs-lookup"><span data-stu-id="938bf-137">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="938bf-138">6. CreateCoordinationContext com contexto</span><span class="sxs-lookup"><span data-stu-id="938bf-138">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="938bf-139">17. Preparada (2PC)</span><span class="sxs-lookup"><span data-stu-id="938bf-139">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="938bf-140">7. Registro (durável)</span><span class="sxs-lookup"><span data-stu-id="938bf-140">7. Register (Durable)</span></span>|<span data-ttu-id="938bf-141">18. Confirmada (preenchimento)</span><span class="sxs-lookup"><span data-stu-id="938bf-141">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="938bf-142">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="938bf-142">8. RegisterResponse</span></span>|<span data-ttu-id="938bf-143">19. 2PC (confirmação)</span><span class="sxs-lookup"><span data-stu-id="938bf-143">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="938bf-144">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="938bf-144">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="938bf-145">20. 2PC (confirmação)</span><span class="sxs-lookup"><span data-stu-id="938bf-145">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="938bf-146">10. Registro (durável)</span><span class="sxs-lookup"><span data-stu-id="938bf-146">10. Register (Durable)</span></span>|<span data-ttu-id="938bf-147">21. Confirmada (2PC)</span><span class="sxs-lookup"><span data-stu-id="938bf-147">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="938bf-148">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="938bf-148">11. RegisterResponse</span></span>|<span data-ttu-id="938bf-149">22. Confirmada (2PC)</span><span class="sxs-lookup"><span data-stu-id="938bf-149">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="938bf-150">Este documento descreve uma composição da especificação WS-AtomicTransaction com segurança e a associação de segurança usada para comunicação entre os gerenciadores de transações.</span><span class="sxs-lookup"><span data-stu-id="938bf-150">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="938bf-151">A abordagem descrita neste documento foram testada com êxito com outras implementações do WS-AT e coordenação WS.</span><span class="sxs-lookup"><span data-stu-id="938bf-151">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="938bf-152">A figura e a tabela ilustram quatro classes de mensagens a partir do ponto de vista de segurança:</span><span class="sxs-lookup"><span data-stu-id="938bf-152">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
-   <span data-ttu-id="938bf-153">Mensagens de ativação (CreateCoordinationContext e CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="938bf-153">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
-   <span data-ttu-id="938bf-154">Mensagens de registro (o registro e RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="938bf-154">Registration messages (Register and RegisterResponse)</span></span>  
  
-   <span data-ttu-id="938bf-155">Mensagens de protocolo (preparar, Rollback, confirmação, Aborted e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="938bf-155">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
-   <span data-ttu-id="938bf-156">Mensagens de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="938bf-156">Application messages.</span></span>  
  
 <span data-ttu-id="938bf-157">Classes de três mensagem primeiro são consideradas mensagens do Gerenciador de transações e sua configuração de associação é descrita em "Aplicativo de troca de mensagens" neste tópico.</span><span class="sxs-lookup"><span data-stu-id="938bf-157">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="938bf-158">A quarta classe da mensagem é mensagens de aplicativo e é descrita na seção "Exemplos de mensagem" neste tópico.</span><span class="sxs-lookup"><span data-stu-id="938bf-158">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="938bf-159">Esta seção descreve as associações de protocolo usadas para cada uma dessas classes por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="938bf-159">This section describes the protocol bindings used for each of these classes by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="938bf-160">Os seguintes Namespaces de XML e prefixos associados são usados em todo este documento.</span><span class="sxs-lookup"><span data-stu-id="938bf-160">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="938bf-161">Prefixo</span><span class="sxs-lookup"><span data-stu-id="938bf-161">Prefix</span></span>|<span data-ttu-id="938bf-162">Versão</span><span class="sxs-lookup"><span data-stu-id="938bf-162">Version</span></span>|<span data-ttu-id="938bf-163">URI de Namespace</span><span class="sxs-lookup"><span data-stu-id="938bf-163">Namespace URI</span></span>|  
|------------|-------------|-------------------|  
|<span data-ttu-id="938bf-164">S11</span><span class="sxs-lookup"><span data-stu-id="938bf-164">s11</span></span>||[<span data-ttu-id="938bf-165">http://go.microsoft.com/fwlink/?LinkId=96014</span><span class="sxs-lookup"><span data-stu-id="938bf-165">http://go.microsoft.com/fwlink/?LinkId=96014</span></span>](http://go.microsoft.com/fwlink/?LinkId=96014)|  
|<span data-ttu-id="938bf-166">wsa</span><span class="sxs-lookup"><span data-stu-id="938bf-166">wsa</span></span>|<span data-ttu-id="938bf-167">Pré-1.0</span><span class="sxs-lookup"><span data-stu-id="938bf-167">Pre-1.0</span></span><br /><br /> <span data-ttu-id="938bf-168">1.0</span><span class="sxs-lookup"><span data-stu-id="938bf-168">1.0</span></span>|<span data-ttu-id="938bf-169">http://www.w3.org/2004/08/Addressing</span><span class="sxs-lookup"><span data-stu-id="938bf-169">http://www.w3.org/2004/08/addressing</span></span><br /><br /> [<span data-ttu-id="938bf-170">http://go.microsoft.com/fwlink/?LinkId=96022</span><span class="sxs-lookup"><span data-stu-id="938bf-170">http://go.microsoft.com/fwlink/?LinkId=96022</span></span>](http://go.microsoft.com/fwlink/?LinkId=96022)|  
|<span data-ttu-id="938bf-171">wscoor</span><span class="sxs-lookup"><span data-stu-id="938bf-171">wscoor</span></span>|<span data-ttu-id="938bf-172">1.0</span><span class="sxs-lookup"><span data-stu-id="938bf-172">1.0</span></span><br /><br /> <span data-ttu-id="938bf-173">1.1</span><span class="sxs-lookup"><span data-stu-id="938bf-173">1.1</span></span>|[<span data-ttu-id="938bf-174">http://go.microsoft.com/fwlink/?LinkId=96078</span><span class="sxs-lookup"><span data-stu-id="938bf-174">http://go.microsoft.com/fwlink/?LinkId=96078</span></span>](http://go.microsoft.com/fwlink/?LinkId=96078)<br /><br /> [<span data-ttu-id="938bf-175">http://go.microsoft.com/fwlink/?LinkId=96079</span><span class="sxs-lookup"><span data-stu-id="938bf-175">http://go.microsoft.com/fwlink/?LinkId=96079</span></span>](http://go.microsoft.com/fwlink/?LinkId=96079)|  
|<span data-ttu-id="938bf-176">WSAT</span><span class="sxs-lookup"><span data-stu-id="938bf-176">wsat</span></span>|<span data-ttu-id="938bf-177">1.0</span><span class="sxs-lookup"><span data-stu-id="938bf-177">1.0</span></span><br /><br /> <span data-ttu-id="938bf-178">1.1</span><span class="sxs-lookup"><span data-stu-id="938bf-178">1.1</span></span>|[<span data-ttu-id="938bf-179">http://go.microsoft.com/fwlink/?LinkId=96080</span><span class="sxs-lookup"><span data-stu-id="938bf-179">http://go.microsoft.com/fwlink/?LinkId=96080</span></span>](http://go.microsoft.com/fwlink/?LinkId=96080)<br /><br /> [<span data-ttu-id="938bf-180">http://go.microsoft.com/fwlink/?LinkId=96081</span><span class="sxs-lookup"><span data-stu-id="938bf-180">http://go.microsoft.com/fwlink/?LinkId=96081</span></span>](http://go.microsoft.com/fwlink/?LinkId=96081)|  
|<span data-ttu-id="938bf-181">t</span><span class="sxs-lookup"><span data-stu-id="938bf-181">t</span></span>|<span data-ttu-id="938bf-182">Pré-1.3</span><span class="sxs-lookup"><span data-stu-id="938bf-182">Pre-1.3</span></span><br /><br /> <span data-ttu-id="938bf-183">1.3</span><span class="sxs-lookup"><span data-stu-id="938bf-183">1.3</span></span>|[<span data-ttu-id="938bf-184">http://go.microsoft.com/fwlink/?LinkId=96082</span><span class="sxs-lookup"><span data-stu-id="938bf-184">http://go.microsoft.com/fwlink/?LinkId=96082</span></span>](http://go.microsoft.com/fwlink/?LinkId=96082)<br /><br /> [<span data-ttu-id="938bf-185">http://go.microsoft.com/fwlink/?LinkId=96100</span><span class="sxs-lookup"><span data-stu-id="938bf-185">http://go.microsoft.com/fwlink/?LinkId=96100</span></span>](http://go.microsoft.com/fwlink/?LinkId=96100)|  
|<span data-ttu-id="938bf-186">o</span><span class="sxs-lookup"><span data-stu-id="938bf-186">o</span></span>||[<span data-ttu-id="938bf-187">http://go.microsoft.com/fwlink/?LinkId=96101</span><span class="sxs-lookup"><span data-stu-id="938bf-187">http://go.microsoft.com/fwlink/?LinkId=96101</span></span>](http://go.microsoft.com/fwlink/?LinkId=96101)|  
|<span data-ttu-id="938bf-188">XSD</span><span class="sxs-lookup"><span data-stu-id="938bf-188">xsd</span></span>||[<span data-ttu-id="938bf-189">http://go.microsoft.com/fwlink/?LinkId=96102</span><span class="sxs-lookup"><span data-stu-id="938bf-189">http://go.microsoft.com/fwlink/?LinkId=96102</span></span>](http://go.microsoft.com/fwlink/?LinkId=96102)|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="938bf-190">Associações do Gerenciador de transações</span><span class="sxs-lookup"><span data-stu-id="938bf-190">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="938bf-191">R1001: Gerenciadores de transações que participam de uma transação WS-AT 1.0 devem usar os SOAP 1.1 e 08/2004 do WS-Addressing para transações de WS-Atomic e trocas de mensagens de coordenação WS.</span><span class="sxs-lookup"><span data-stu-id="938bf-191">R1001: Transaction Managers participating in a WS-AT 1.0 transaction must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="938bf-192">R1002: Gerenciadores de transações que participam de uma transação WS-AT 1.1 devem usar os SOAP 1.1 e WS-Addressing 2005/08 para transações de WS-Atomic e trocas de mensagens de coordenação WS.</span><span class="sxs-lookup"><span data-stu-id="938bf-192">R1002: Transaction Managers participating in a WS-AT 1.1 transaction must use SOAP 1.1 and WS-Addressing 2005/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="938bf-193">As mensagens de aplicativo não são restritos a essas associações e são descritas posteriormente.</span><span class="sxs-lookup"><span data-stu-id="938bf-193">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="938bf-194">Associação de HTTPS de Gerenciador de transações</span><span class="sxs-lookup"><span data-stu-id="938bf-194">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="938bf-195">A associação de HTTPS de Gerenciador de transação depende exclusivamente de segurança de transporte para obter segurança e estabelecer relação de confiança entre cada par de remetente e o receptor na árvore de transação.</span><span class="sxs-lookup"><span data-stu-id="938bf-195">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="938bf-196">Configuração de transporte HTTPS</span><span class="sxs-lookup"><span data-stu-id="938bf-196">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="938bf-197">Certificados x. 509 são usados para estabelecer a identidade do Gerenciador de transações.</span><span class="sxs-lookup"><span data-stu-id="938bf-197">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="938bf-198">Autenticação de cliente/servidor é necessária e autorização do cliente/servidor é mantida como um detalhe de implementação:</span><span class="sxs-lookup"><span data-stu-id="938bf-198">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
-   <span data-ttu-id="938bf-199">R1111: Certificados x. 509 apresentados pela conexão devem ter um nome de assunto que corresponda o nome de domínio totalmente qualificado (FQDN) do computador de origem.</span><span class="sxs-lookup"><span data-stu-id="938bf-199">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
-   <span data-ttu-id="938bf-200">B1112: O DNS deve ser funcional entre cada par de remetente e o receptor do sistema para verificações de nome de assunto de x. 509 seja bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="938bf-200">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="938bf-201">Ativação e registro de configuração de associação</span><span class="sxs-lookup"><span data-stu-id="938bf-201">Activation and Registration Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="938bf-202">requer a associação de solicitação/resposta duplex com correlação via HTTPS.</span><span class="sxs-lookup"><span data-stu-id="938bf-202"> requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="938bf-203">(Para obter mais informações sobre a correlação e descrições dos padrões de troca de mensagem de solicitação/resposta, consulte transação WS-Atomic, 8 de seção).</span><span class="sxs-lookup"><span data-stu-id="938bf-203">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="938bf-204">Configuração de associação de protocolo 2PC</span><span class="sxs-lookup"><span data-stu-id="938bf-204">2PC Protocol Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="938bf-205">oferece suporte a mensagens unidirecionais (datagrama) sobre HTTPS.</span><span class="sxs-lookup"><span data-stu-id="938bf-205"> supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="938bf-206">Correlação entre as mensagens será deixada como um detalhe de implementação.</span><span class="sxs-lookup"><span data-stu-id="938bf-206">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="938bf-207">B1131: Implementações devem suportar `wsa:ReferenceParameters` conforme descrito em WS-Addressing para alcançar a correlação de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]do 2PC mensagens.</span><span class="sxs-lookup"><span data-stu-id="938bf-207">B1131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="938bf-208">Gerenciador de transações misto associação de segurança</span><span class="sxs-lookup"><span data-stu-id="938bf-208">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="938bf-209">Esta é uma alternativa (misto) que usa a segurança de transporte combinada com o modelo de Token emitido de coordenação WS para fins de estabelecimento de identidade de associação.</span><span class="sxs-lookup"><span data-stu-id="938bf-209">This is an alternate (mixed mode) binding that uses transport security combined with the WS-Coordination Issued Token model for identity establishment purposes.</span></span> <span data-ttu-id="938bf-210">Ativação e registro são os únicos elementos que diferem entre as duas associações.</span><span class="sxs-lookup"><span data-stu-id="938bf-210">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="938bf-211">Configuração de transporte HTTPS</span><span class="sxs-lookup"><span data-stu-id="938bf-211">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="938bf-212">Certificados x. 509 são usados para estabelecer a identidade do Gerenciador de transações.</span><span class="sxs-lookup"><span data-stu-id="938bf-212">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="938bf-213">Autenticação de cliente/servidor é necessária e autorização do cliente/servidor é mantida como um detalhe de implementação.</span><span class="sxs-lookup"><span data-stu-id="938bf-213">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="938bf-214">Configuração de associação de mensagem de ativação</span><span class="sxs-lookup"><span data-stu-id="938bf-214">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="938bf-215">Mensagens de ativação geralmente não participar de interoperabilidade porque eles ocorrem normalmente entre um aplicativo e seu gerente de transação local.</span><span class="sxs-lookup"><span data-stu-id="938bf-215">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="938bf-216">B1221: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa associação de HTTPS duplex (descrito na [protocolos de mensagens](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) para mensagens de ativação.</span><span class="sxs-lookup"><span data-stu-id="938bf-216">B1221: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="938bf-217">Mensagens de resposta e solicitação são correlacionadas usando 08/2004 do WS-Addressing para WS-AT 1.0 e WS-Addressing 2005/08 1.1 WS-AT.</span><span class="sxs-lookup"><span data-stu-id="938bf-217">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="938bf-218">Especificação WS-AT, 8 de seção, descreve mais detalhes sobre a correlação e os padrões de troca de mensagem.</span><span class="sxs-lookup"><span data-stu-id="938bf-218">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
-   <span data-ttu-id="938bf-219">R1222: após receber uma `CreateCoordinationContext`, o coordenador deve emitir uma `SecurityContextToken` com segredo associado `STx`.</span><span class="sxs-lookup"><span data-stu-id="938bf-219">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="938bf-220">Esse token é retornado em uma `t:IssuedTokens` cabeçalho após a especificação WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="938bf-220">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
-   <span data-ttu-id="938bf-221">R1223: Se a ativação ocorrer dentro de um contexto de coordenação existente, o `t:IssuedTokens` cabeçalho com o `SecurityContextToken` associado existente contexto deve fluir no `CreateCoordinationContext` mensagem.</span><span class="sxs-lookup"><span data-stu-id="938bf-221">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="938bf-222">Um novo `t:IssuedTokens` cabeçalho deve ser gerado para anexar para a saída `wscoor:CreateCoordinationContextResponse` mensagem.</span><span class="sxs-lookup"><span data-stu-id="938bf-222">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="938bf-223">Configuração de associação de mensagem de registro</span><span class="sxs-lookup"><span data-stu-id="938bf-223">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="938bf-224">B1231: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa associação de HTTPS duplex (descrito na [protocolos de mensagens](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="938bf-224">B1231: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="938bf-225">Mensagens de resposta e solicitação são correlacionadas usando 08/2004 do WS-Addressing para WS-AT 1.0 e WS-Addressing 2005/08 1.1 WS-AT.</span><span class="sxs-lookup"><span data-stu-id="938bf-225">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="938bf-226">WS-AtomicTransaction, 8 de seção descreve mais detalhes sobre a correlação e descrições dos padrões de troca de mensagem.</span><span class="sxs-lookup"><span data-stu-id="938bf-226">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="938bf-227">R1232: Saída `wscoor:Register` mensagens devem usar o `IssuedTokenOverTransport` o modo de autenticação descrito [protocolos de segurança](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="938bf-227">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="938bf-228">O `wsse:Timestamp` elemento deve ser assinado usando o `SecurityContextToken``STx` emitido.</span><span class="sxs-lookup"><span data-stu-id="938bf-228">The `wsse:Timestamp` element must be signed using the `SecurityContextToken``STx` issued.</span></span> <span data-ttu-id="938bf-229">Esta assinatura é uma prova de posse do token associado à transação específica e é usada para autenticar um participante inscrição na transação.</span><span class="sxs-lookup"><span data-stu-id="938bf-229">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="938bf-230">A mensagem RegistrationResponse é enviada novamente por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="938bf-230">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="938bf-231">Configuração de associação de protocolo 2PC</span><span class="sxs-lookup"><span data-stu-id="938bf-231">2PC Protocol Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="938bf-232">oferece suporte a mensagens unidirecionais (datagrama) sobre HTTPS.</span><span class="sxs-lookup"><span data-stu-id="938bf-232"> supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="938bf-233">Correlação entre as mensagens será deixada como um detalhe de implementação.</span><span class="sxs-lookup"><span data-stu-id="938bf-233">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="938bf-234">B1241: Implementações devem suportar `wsa:ReferenceParameters` conforme descrito em WS-Addressing para alcançar a correlação de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]do 2PC mensagens.</span><span class="sxs-lookup"><span data-stu-id="938bf-234">B1241: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="938bf-235">Troca de mensagens de aplicativo</span><span class="sxs-lookup"><span data-stu-id="938bf-235">Application Message Exchange</span></span>  
 <span data-ttu-id="938bf-236">Aplicativos estão livres para usar qualquer associação específica para mensagens de aplicativo, desde que a associação atende aos seguintes requisitos de segurança:</span><span class="sxs-lookup"><span data-stu-id="938bf-236">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
-   <span data-ttu-id="938bf-237">R2001: Mensagens de aplicativo para o aplicativo devem fluir de `t:IssuedTokens` cabeçalho junto com o `CoordinationContext` no cabeçalho da mensagem.</span><span class="sxs-lookup"><span data-stu-id="938bf-237">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
-   <span data-ttu-id="938bf-238">R2002: Integridade e confidencialidade de `t:IssuedToken` deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="938bf-238">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="938bf-239">O `CoordinationContext` cabeçalho contém `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="938bf-239">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="938bf-240">Enquanto a definição de `xsd:AnyURI` permite o uso de absolute e relative URIs, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oferece suporte apenas para `wscoor:Identifiers`, que são URIs absolutos.</span><span class="sxs-lookup"><span data-stu-id="938bf-240">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="938bf-241">B2003: Se o `wscoor:Identifier` do `wscoor:CoordinationContext` é um URI relativo, falhas serão retornadas de transacional [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços.</span><span class="sxs-lookup"><span data-stu-id="938bf-241">B2003: If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="938bf-242">Exemplos de mensagem</span><span class="sxs-lookup"><span data-stu-id="938bf-242">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="938bf-243">Mensagens de solicitação/resposta CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="938bf-243">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="938bf-244">As seguintes mensagens sigam um padrão de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="938bf-244">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext-with-wscoor-10"></a><span data-ttu-id="938bf-245">CreateCoordinationContext com WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="938bf-245">CreateCoordinationContext with WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontext-with-wscoor-11"></a><span data-ttu-id="938bf-246">CreateCoordinationContext com WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="938bf-246">CreateCoordinationContext with WSCoor 1.1</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-pre-13-and-wscoor-10"></a><span data-ttu-id="938bf-247">CreateCoordinationContextResponse com confiança Pre-1.3 e WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="938bf-247">CreateCoordinationContextResponse with Trust Pre-1.3 and WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-13-and-wscoor-11"></a><span data-ttu-id="938bf-248">CreateCoordinationContextResponse com confiança 1.3 e WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="938bf-248">CreateCoordinationContextResponse with Trust 1.3 and WSCoor 1.1</span></span>  
  
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
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-     wssecurity-utility-1.0.xsd"   
xmlns:wst=http://docs.oasis-open.org/ws-sx/ws-trust/200512  
xmlns:wsc=http://schemas.xmlsoap.org/ws/2005/02/sc  
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
  ValueType=http://schemas.xmlsoap.org/ws/2005/02/sc/sct  
  URI="http://fabrikam123.com/SCTi"/>  
</wsse:SecurityTokenReference>   
</wst:RequestedAttachedReference>   
<wst:RequestedUnattachedReference>   
<wsse:SecurityTokenReference>   
<wsse:Reference  
 ValueType=http://schemas.xmlsoap.org/ws/2005/02/sc/sct  
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
  
### <a name="registration-messages"></a><span data-ttu-id="938bf-249">Mensagens de registro</span><span class="sxs-lookup"><span data-stu-id="938bf-249">Registration Messages</span></span>  
 <span data-ttu-id="938bf-250">As seguintes mensagens são mensagens de registro.</span><span class="sxs-lookup"><span data-stu-id="938bf-250">The following messages are registration messages.</span></span>  
  
#### <a name="register-with-wscoor-10"></a><span data-ttu-id="938bf-251">Registrar com WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="938bf-251">Register with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-with-wscoor-11"></a><span data-ttu-id="938bf-252">Registrar com WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="938bf-252">Register with WSCoor 1.1</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-10"></a><span data-ttu-id="938bf-253">Registrar a resposta com WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="938bf-253">Register Response with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-11"></a><span data-ttu-id="938bf-254">Registrar a resposta com WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="938bf-254">Register Response with WSCoor 1.1</span></span>  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="938bf-255">Duas mensagens de protocolo de confirmação de fase</span><span class="sxs-lookup"><span data-stu-id="938bf-255">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="938bf-256">A seguinte mensagem de erro se relaciona com o protocolo de confirmação de duas fases (2PC).</span><span class="sxs-lookup"><span data-stu-id="938bf-256">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit-with-wsat-10"></a><span data-ttu-id="938bf-257">Confirmar com WSAT 1.0</span><span class="sxs-lookup"><span data-stu-id="938bf-257">Commit with WSAT 1.0</span></span>  
  
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
  
#### <a name="commit-with-wsat-11"></a><span data-ttu-id="938bf-258">Confirmar com WSAT 1.1</span><span class="sxs-lookup"><span data-stu-id="938bf-258">Commit with WSAT 1.1</span></span>  
  
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
  
### <a name="application-messages"></a><span data-ttu-id="938bf-259">Mensagens de aplicativo</span><span class="sxs-lookup"><span data-stu-id="938bf-259">Application Messages</span></span>  
 <span data-ttu-id="938bf-260">As seguintes mensagens são mensagens do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="938bf-260">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="938bf-261">Solicitação de mensagem do aplicativo</span><span class="sxs-lookup"><span data-stu-id="938bf-261">Application message-Request</span></span>  
  
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
