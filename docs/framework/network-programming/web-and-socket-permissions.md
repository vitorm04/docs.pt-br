---
title: Permissões da Web e de soquete
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- positions [.NET Framework], accepting
- sockets, permissions
- network, permissions
- Internet, permissions
- Network Resources
- SocketPermission class, about SocketPermission class
- positions [.NET Framework], connecting
- WebPermission class, about WebPermission class
- permissions [.NET Framework], sockets
- security [.NET Framework], Internet
- positions [.NET Framework], granting
ms.assetid: d51ad8cb-03ae-4a51-bfcd-cfcf6b98afa9
ms.openlocfilehash: b5767f4e16e691fec5714f98114b3ed9d5692a50
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50205081"
---
# <a name="web-and-socket-permissions"></a><span data-ttu-id="7a66f-102">Permissões da Web e de soquete</span><span class="sxs-lookup"><span data-stu-id="7a66f-102">Web and Socket Permissions</span></span>
<span data-ttu-id="7a66f-103">A segurança da Internet para aplicativos que usam o namespace <xref:System.Net> é fornecida pelas classes <xref:System.Net.WebPermission> e <xref:System.Net.SocketPermission>.</span><span class="sxs-lookup"><span data-stu-id="7a66f-103">Internet security for applications using the <xref:System.Net> namespace is provided by the <xref:System.Net.WebPermission> and <xref:System.Net.SocketPermission> classes.</span></span> <span data-ttu-id="7a66f-104">A classe **WebPermission** controla o direito de um aplicativo de solicitar dados de um URI ou de atender a um URI para a Internet.</span><span class="sxs-lookup"><span data-stu-id="7a66f-104">The **WebPermission** class controls an application's right to request data from a URI or to serve a URI to the Internet.</span></span> <span data-ttu-id="7a66f-105">A classe **SocketPermission** controla o direito de um aplicativo de usar um <xref:System.Net.Sockets.Socket> para aceitar dados em uma porta local ou de entrar em contato com dispositivos remotos usando um protocolo de transporte em outro endereço, com base no host, no número da porta e no protocolo de transporte do soquete.</span><span class="sxs-lookup"><span data-stu-id="7a66f-105">The **SocketPermission** class controls an application's right to use a <xref:System.Net.Sockets.Socket> to accept data on a local port or to contact remote devices using a transport protocol at another address, based on the host, port number, and transport protocol of the socket.</span></span>  
  
 <span data-ttu-id="7a66f-106">A classe de permissão usada depende do tipo de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7a66f-106">Which permission class you use depends on your application type.</span></span> <span data-ttu-id="7a66f-107">Os aplicativos que usam <xref:System.Net.WebRequest> e seus descendentes devem usar a classe **WebPermission** para gerenciar permissões.</span><span class="sxs-lookup"><span data-stu-id="7a66f-107">Applications that use <xref:System.Net.WebRequest> and its descendants should use the **WebPermission** class to manage permissions.</span></span> <span data-ttu-id="7a66f-108">Os aplicativos que usam o acesso no nível do soquete devem usar a classe **SocketPermission** para gerenciar permissões.</span><span class="sxs-lookup"><span data-stu-id="7a66f-108">Applications that use socket-level access should use the **SocketPermission** class to manage permissions.</span></span>  
  
 <span data-ttu-id="7a66f-109">**WebPermission** e **SocketPermission** definem duas permissões: aceitação e conexão.</span><span class="sxs-lookup"><span data-stu-id="7a66f-109">**WebPermission** and **SocketPermission** define two permissions: accept and connect.</span></span> <span data-ttu-id="7a66f-110">A aceitação concede ao aplicativo o direito de responder a uma conexão de entrada de outra entidade.</span><span class="sxs-lookup"><span data-stu-id="7a66f-110">Accept grants the application the right to answer an incoming connection from another party.</span></span> <span data-ttu-id="7a66f-111">Connect concede ao aplicativo o direito de iniciar uma conexão com outra entidade.</span><span class="sxs-lookup"><span data-stu-id="7a66f-111">Connect grants the application the right to initiate a connection to another party.</span></span>  
  
 <span data-ttu-id="7a66f-112">Para instâncias **SocketPermission**, aceitação significa que um aplicativo pode aceitar conexões de entrada em um endereço de transporte local; conexão significa que um aplicativo pode se conectar a um endereço de transporte remoto (ou local).</span><span class="sxs-lookup"><span data-stu-id="7a66f-112">For **SocketPermission** instances, accept means that an application can accept incoming connections on a local transport address; connect means that an application can connect to some remote (or local) transport address.</span></span>  
  
 <span data-ttu-id="7a66f-113">Para instâncias **WebPermission**, aceitação significa que um aplicativo pode exportar o URI controlado pela **WebPermission** para o mundo; conexão significa que um aplicativo pode acessar esse URI (seja ele local ou remoto).</span><span class="sxs-lookup"><span data-stu-id="7a66f-113">For **WebPermission** instances, accept means that an application can export the URI controlled by the **WebPermission** to the world; connect means that an application can access that URI (whether it is remote or local).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a66f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7a66f-114">See Also</span></span>  
 [<span data-ttu-id="7a66f-115">Segurança</span><span class="sxs-lookup"><span data-stu-id="7a66f-115">Security</span></span>](../../../docs/standard/security/index.md)  
 [<span data-ttu-id="7a66f-116">Segurança na programação de rede</span><span class="sxs-lookup"><span data-stu-id="7a66f-116">Security in Network Programming</span></span>](../../../docs/framework/network-programming/security-in-network-programming.md)
