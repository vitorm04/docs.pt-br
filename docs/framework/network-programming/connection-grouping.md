---
title: Agrupamento de conexão
ms.date: 03/30/2017
helpviewer_keywords:
- Internet, connections
- connections [.NET Framework], grouping
- WebRequest class, connection grouping
- network resources, connections
- connection pooling
ms.assetid: 2ec502e8-4ba0-4c22-9410-f28eaf4eee63
ms.openlocfilehash: 00ccc11919f0ccd4f9361bfd8f265dea1ad2390d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184555"
---
# <a name="connection-grouping"></a><span data-ttu-id="07922-102">Agrupamento de conexão</span><span class="sxs-lookup"><span data-stu-id="07922-102">Connection Grouping</span></span>
<span data-ttu-id="07922-103">O agrupamento de conexão associa solicitações específicas em um único aplicativo a um pool de conexão definido.</span><span class="sxs-lookup"><span data-stu-id="07922-103">Connection grouping associates specific requests within a single application to a defined connection pool.</span></span> <span data-ttu-id="07922-104">Isso pode ser necessário para um aplicativo de camada intermediária que se conecta a um servidor back-end em nome de um usuário e usa um protocolo de autenticação que dá suporte à delegação, como o Kerberos ou para um aplicativo de camada intermediária que fornece suas próprias credenciais, como no exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="07922-104">This can be required by a middle-tier application that connects to a back-end server on behalf of a user and uses an authentication protocol that supports delegation, such as Kerberos, or by a middle-tier application that supplies its own credentials, as in the example below.</span></span> <span data-ttu-id="07922-105">Por exemplo, suponha que um usuário, Julio, visite um site interno que exibe suas informações de folha de pagamento.</span><span class="sxs-lookup"><span data-stu-id="07922-105">For example, suppose a user, Joe, visits an internal Web site that displays his payroll information.</span></span> <span data-ttu-id="07922-106">Depois de autenticar Julio, o servidor de aplicativos de camada intermediária usa as credenciais de Julio para se conectar ao servidor back-end para recuperar suas informações de folha de pagamento.</span><span class="sxs-lookup"><span data-stu-id="07922-106">After authenticating Joe, the middle-tier application server uses Joe's credentials to connect to the back-end server to retrieve his payroll information.</span></span> <span data-ttu-id="07922-107">Em seguida, Sara visita o site e solicita suas informações de folha de pagamento.</span><span class="sxs-lookup"><span data-stu-id="07922-107">Next, Susan visits the site and requests her payroll information.</span></span> <span data-ttu-id="07922-108">Como o aplicativo de camada intermediária já fez uma conexão usando as credenciais de Julio, o servidor back-end responde com as informações de Julio.</span><span class="sxs-lookup"><span data-stu-id="07922-108">Because the middle-tier application has already made a connection using Joe's credentials, the back-end server responds with Joe's information.</span></span> <span data-ttu-id="07922-109">No entanto, se o aplicativo atribuir cada solicitação enviada para o servidor back-end a um grupo de conexão formado com base no nome de usuário, cada usuário pertencerá a um pool de conexão separado e não poderá compartilhar informações de autenticação acidentalmente com outro usuário.</span><span class="sxs-lookup"><span data-stu-id="07922-109">However, if the application assigns each request sent to the back-end server to a connection group formed from the user name, then each user belongs to a separate connection pool and cannot accidentally share authentication information with another user.</span></span>  
  
 <span data-ttu-id="07922-110">Para atribuir uma solicitação a um grupo de conexão específico, é necessário atribuir um nome à propriedade <xref:System.Net.WebRequest.ConnectionGroupName%2A> da <xref:System.Net.WebRequest> antes de fazer a solicitação.</span><span class="sxs-lookup"><span data-stu-id="07922-110">To assign a request to a specific connection group, you must assign a name to the <xref:System.Net.WebRequest.ConnectionGroupName%2A> property of your <xref:System.Net.WebRequest> before making the request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07922-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07922-111">See also</span></span>

- [<span data-ttu-id="07922-112">Gerenciando conexões</span><span class="sxs-lookup"><span data-stu-id="07922-112">Managing Connections</span></span>](../../../docs/framework/network-programming/managing-connections.md)
- [<span data-ttu-id="07922-113">Como: Atribuir informações de usuário a conexões de grupo</span><span class="sxs-lookup"><span data-stu-id="07922-113">How to: Assign User Information to Group Connections</span></span>](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)
