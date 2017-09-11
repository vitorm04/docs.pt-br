---
title: "Agrupamento de conexão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Internet, connections
- connections [.NET Framework], grouping
- WebRequest class, connection grouping
- network resources, connections
- connection pooling
ms.assetid: 2ec502e8-4ba0-4c22-9410-f28eaf4eee63
caps.latest.revision: 7
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8f16a539bb7c2bef494c7b5551e1f12bc71de60f
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="connection-grouping"></a><span data-ttu-id="3c08f-102">Agrupamento de conexão</span><span class="sxs-lookup"><span data-stu-id="3c08f-102">Connection Grouping</span></span>
<span data-ttu-id="3c08f-103">O agrupamento de conexão associa solicitações específicas em um único aplicativo a um pool de conexão definido.</span><span class="sxs-lookup"><span data-stu-id="3c08f-103">Connection grouping associates specific requests within a single application to a defined connection pool.</span></span> <span data-ttu-id="3c08f-104">Isso pode ser necessário para um aplicativo de camada intermediária que se conecta a um servidor back-end em nome de um usuário e usa um protocolo de autenticação que dá suporte à delegação, como o Kerberos ou para um aplicativo de camada intermediária que fornece suas próprias credenciais, como no exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="3c08f-104">This can be required by a middle-tier application that connects to a back-end server on behalf of a user and uses an authentication protocol that supports delegation, such as Kerberos, or by a middle-tier application that supplies its own credentials, as in the example below.</span></span> <span data-ttu-id="3c08f-105">Por exemplo, suponha que um usuário, Julio, visite um site interno que exibe suas informações de folha de pagamento.</span><span class="sxs-lookup"><span data-stu-id="3c08f-105">For example, suppose a user, Joe, visits an internal Web site that displays his payroll information.</span></span> <span data-ttu-id="3c08f-106">Depois de autenticar Julio, o servidor de aplicativos de camada intermediária usa as credenciais de Julio para se conectar ao servidor back-end para recuperar suas informações de folha de pagamento.</span><span class="sxs-lookup"><span data-stu-id="3c08f-106">After authenticating Joe, the middle-tier application server uses Joe's credentials to connect to the back-end server to retrieve his payroll information.</span></span> <span data-ttu-id="3c08f-107">Em seguida, Sara visita o site e solicita suas informações de folha de pagamento.</span><span class="sxs-lookup"><span data-stu-id="3c08f-107">Next, Susan visits the site and requests her payroll information.</span></span> <span data-ttu-id="3c08f-108">Como o aplicativo de camada intermediária já fez uma conexão usando as credenciais de Julio, o servidor back-end responde com as informações de Julio.</span><span class="sxs-lookup"><span data-stu-id="3c08f-108">Because the middle-tier application has already made a connection using Joe's credentials, the back-end server responds with Joe's information.</span></span> <span data-ttu-id="3c08f-109">No entanto, se o aplicativo atribuir cada solicitação enviada para o servidor back-end a um grupo de conexão formado com base no nome de usuário, cada usuário pertencerá a um pool de conexão separado e não poderá compartilhar informações de autenticação acidentalmente com outro usuário.</span><span class="sxs-lookup"><span data-stu-id="3c08f-109">However, if the application assigns each request sent to the back-end server to a connection group formed from the user name, then each user belongs to a separate connection pool and cannot accidentally share authentication information with another user.</span></span>  
  
 <span data-ttu-id="3c08f-110">Para atribuir uma solicitação a um grupo de conexão específico, é necessário atribuir um nome à propriedade <xref:System.Net.WebRequest.ConnectionGroupName%2A> da <xref:System.Net.WebRequest> antes de fazer a solicitação.</span><span class="sxs-lookup"><span data-stu-id="3c08f-110">To assign a request to a specific connection group, you must assign a name to the <xref:System.Net.WebRequest.ConnectionGroupName%2A> property of your <xref:System.Net.WebRequest> before making the request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c08f-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c08f-111">See Also</span></span>  
 <span data-ttu-id="3c08f-112">[Gerenciando conexões](../../../docs/framework/network-programming/managing-connections.md) </span><span class="sxs-lookup"><span data-stu-id="3c08f-112">[Managing Connections](../../../docs/framework/network-programming/managing-connections.md) </span></span>  
 [<span data-ttu-id="3c08f-113">Como atribuir informações de usuário a conexões de grupo</span><span class="sxs-lookup"><span data-stu-id="3c08f-113">How to: Assign User Information to Group Connections</span></span>](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)

