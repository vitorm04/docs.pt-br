---
title: Isolamento de rede para Aplicativos da Windows Store
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
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
caps.latest.revision: 7
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6a8a01e89977ea4fb9487520f2baa35028720e9d
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="network-isolation-for-windows-store-apps"></a><span data-ttu-id="fde3d-102">Isolamento de rede para Aplicativos da Windows Store</span><span class="sxs-lookup"><span data-stu-id="fde3d-102">Network Isolation for Windows Store Apps</span></span>
<span data-ttu-id="fde3d-103">As classes nos namespaces <xref:System.Net>, <xref:System.Net.Http> e <xref:System.Net.Http.Headers> podem ser usadas para desenvolver Aplicativos da Windows Store ou aplic. da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="fde3d-103">Classes in the <xref:System.Net>,  <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces can be used to develop Windows Store  apps  or desktop apps.</span></span> <span data-ttu-id="fde3d-104">Quando usadas em um aplicativo da Windows Store, as classes nesses namespaces são afetadas pelo isolamento de rede, parte do modelo de segurança do aplicativo usado pelo [!INCLUDE[win8](../../../includes/win8-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fde3d-104">When used in a Windows Store app, classes in these namespaces are affected by network isolation, part of the application security model used by the [!INCLUDE[win8](../../../includes/win8-md.md)].</span></span> <span data-ttu-id="fde3d-105">Para que o sistema permita o acesso à rede, os recursos de rede apropriados deverão ser habilitados no manifesto do aplicativo para um aplicativo da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="fde3d-105">The appropriate network capabilities must be enabled in the app manifest for a Windows Store app for the system to allow network access.</span></span>  
  
## <a name="checklist-for-network-isolation"></a><span data-ttu-id="fde3d-106">Lista de verificação para isolamento de rede</span><span class="sxs-lookup"><span data-stu-id="fde3d-106">Checklist for Network Isolation</span></span>  
 <span data-ttu-id="fde3d-107">Use esta lista de verificação para verificar se o isolamento de rede está configurado para o aplicativo da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="fde3d-107">Use this checklist to be sure that network isolation is configured for your Windows Store app.</span></span>  
  
1.  <span data-ttu-id="fde3d-108">Determine a direção das solicitações de acesso de rede necessárias para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fde3d-108">Determine the direction of network access requests needed by the app.</span></span> <span data-ttu-id="fde3d-109">Isso pode ser solicitações de saída iniciadas pelo cliente ou solicitações de entrada não solicitadas ou pode ser ainda uma combinação de ambos esses tipos de solicitação de rede.</span><span class="sxs-lookup"><span data-stu-id="fde3d-109">This can be either outbound client-initiated requests or inbound unsolicited requests or it could be a combination of both of these network request types.</span></span>  
  
2.  <span data-ttu-id="fde3d-110">Determine o tipo de recursos de rede com os quais o aplicativo se comunicará.</span><span class="sxs-lookup"><span data-stu-id="fde3d-110">Determine the type of network resources that that app will communicate with.</span></span> <span data-ttu-id="fde3d-111">Um aplicativo pode precisar se comunicar com recursos confiáveis em uma rede doméstica ou corporativa.</span><span class="sxs-lookup"><span data-stu-id="fde3d-111">An app may need to communicate with trusted resources on a Home or Work network.</span></span> <span data-ttu-id="fde3d-112">Um aplicativo pode precisar se comunicar com recursos na Internet.</span><span class="sxs-lookup"><span data-stu-id="fde3d-112">An app might need to communicate with resources on the Internet.</span></span> <span data-ttu-id="fde3d-113">Um aplicativo pode precisar de acesso a ambos os tipos de recursos de rede.</span><span class="sxs-lookup"><span data-stu-id="fde3d-113">An app might need access to both types of network resources.</span></span>  
  
3.  <span data-ttu-id="fde3d-114">Configure as funcionalidades de isolamento de rede mínimas necessárias no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fde3d-114">Configure the minimum-required networking isolation capabilities in the app manifest.</span></span>  
  
4.  <span data-ttu-id="fde3d-115">Implante e execute seu aplicativo para testá-lo usando as ferramentas de isolamento de rede fornecidas para solução de problemas.</span><span class="sxs-lookup"><span data-stu-id="fde3d-115">Deploy and run your app to test it using the network isolation tools provided for troubleshooting.</span></span>  
  
 <span data-ttu-id="fde3d-116">Para obter informações mais detalhadas sobre como configurar funcionalidades de rede e as ferramentas de isolamento usadas para solucionar problemas de isolamento de rede, consulte [Como configurar funcionalidades de isolamento de rede](http://go.microsoft.com/fwlink/?LinkID=228265) na documentação do desenvolvedor de [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fde3d-116">For more detailed information on how to configure network capabilities and isolation tools used for troubleshooting network isolation, see [How to configure network isolation capabilities](http://go.microsoft.com/fwlink/?LinkID=228265) in the [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] developer documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fde3d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fde3d-117">See Also</span></span>  
 <span data-ttu-id="fde3d-118">[Conectando-se a um serviço Web](http://go.microsoft.com/fwlink/?LinkID=245696) </span><span class="sxs-lookup"><span data-stu-id="fde3d-118">[Connecting to a web service](http://go.microsoft.com/fwlink/?LinkID=245696) </span></span>  
 <span data-ttu-id="fde3d-119">[Diretrizes e lista de verificação para isolamento de rede](http://go.microsoft.com/fwlink/?LinkID=228265) </span><span class="sxs-lookup"><span data-stu-id="fde3d-119">[Guidelines and checklist for network isolation](http://go.microsoft.com/fwlink/?LinkID=228265) </span></span>  
 <span data-ttu-id="fde3d-120">[Início rápido: conectar-se usando HttpClient](http://go.microsoft.com/fwlink/?LinkId=245697) </span><span class="sxs-lookup"><span data-stu-id="fde3d-120">[Quickstart: Connecting using HttpClient](http://go.microsoft.com/fwlink/?LinkId=245697) </span></span>  
 <span data-ttu-id="fde3d-121">[Como usar manipuladores HttpClient](http://go.microsoft.com/fwlink/?LinkId=245699) </span><span class="sxs-lookup"><span data-stu-id="fde3d-121">[How to use HttpClient handlers](http://go.microsoft.com/fwlink/?LinkId=245699) </span></span>  
 <span data-ttu-id="fde3d-122">[Como proteger conexões HttpClient](http://go.microsoft.com/fwlink/?LinkId=245698) </span><span class="sxs-lookup"><span data-stu-id="fde3d-122">[How to secure HttpClient connections](http://go.microsoft.com/fwlink/?LinkId=245698) </span></span>  
 [<span data-ttu-id="fde3d-123">Amostra de HttpClient</span><span class="sxs-lookup"><span data-stu-id="fde3d-123">HttpClient Sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=242550)

