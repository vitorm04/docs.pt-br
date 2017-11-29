---
title: Isolamento de rede para Aplicativos da Windows Store
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b6c0665a379f02a74bd0f3631aa26b41dd6ece5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="network-isolation-for-windows-store-apps"></a><span data-ttu-id="d8ae4-102">Isolamento de rede para Aplicativos da Windows Store</span><span class="sxs-lookup"><span data-stu-id="d8ae4-102">Network Isolation for Windows Store Apps</span></span>
<span data-ttu-id="d8ae4-103">As classes nos namespaces <xref:System.Net>, <xref:System.Net.Http> e <xref:System.Net.Http.Headers> podem ser usadas para desenvolver Aplicativos da Windows Store ou aplic. da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d8ae4-103">Classes in the <xref:System.Net>,  <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces can be used to develop Windows Store  apps  or desktop apps.</span></span> <span data-ttu-id="d8ae4-104">Quando usadas em um aplicativo da Windows Store, as classes nesses namespaces são afetadas pelo isolamento de rede, parte do modelo de segurança do aplicativo usado pelo [!INCLUDE[win8](../../../includes/win8-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d8ae4-104">When used in a Windows Store app, classes in these namespaces are affected by network isolation, part of the application security model used by the [!INCLUDE[win8](../../../includes/win8-md.md)].</span></span> <span data-ttu-id="d8ae4-105">Para que o sistema permita o acesso à rede, os recursos de rede apropriados deverão ser habilitados no manifesto do aplicativo para um aplicativo da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="d8ae4-105">The appropriate network capabilities must be enabled in the app manifest for a Windows Store app for the system to allow network access.</span></span>  
  
## <a name="checklist-for-network-isolation"></a><span data-ttu-id="d8ae4-106">Lista de verificação para isolamento de rede</span><span class="sxs-lookup"><span data-stu-id="d8ae4-106">Checklist for Network Isolation</span></span>  
 <span data-ttu-id="d8ae4-107">Use esta lista de verificação para verificar se o isolamento de rede está configurado para o aplicativo da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="d8ae4-107">Use this checklist to be sure that network isolation is configured for your Windows Store app.</span></span>  
  
1.  <span data-ttu-id="d8ae4-108">Determine a direção das solicitações de acesso de rede necessárias para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d8ae4-108">Determine the direction of network access requests needed by the app.</span></span> <span data-ttu-id="d8ae4-109">Isso pode ser solicitações de saída iniciadas pelo cliente ou solicitações de entrada não solicitadas ou pode ser ainda uma combinação de ambos esses tipos de solicitação de rede.</span><span class="sxs-lookup"><span data-stu-id="d8ae4-109">This can be either outbound client-initiated requests or inbound unsolicited requests or it could be a combination of both of these network request types.</span></span>  
  
2.  <span data-ttu-id="d8ae4-110">Determine o tipo de recursos de rede com os quais o aplicativo se comunicará.</span><span class="sxs-lookup"><span data-stu-id="d8ae4-110">Determine the type of network resources that that app will communicate with.</span></span> <span data-ttu-id="d8ae4-111">Um aplicativo pode precisar se comunicar com recursos confiáveis em uma rede doméstica ou corporativa.</span><span class="sxs-lookup"><span data-stu-id="d8ae4-111">An app may need to communicate with trusted resources on a Home or Work network.</span></span> <span data-ttu-id="d8ae4-112">Um aplicativo pode precisar se comunicar com recursos na Internet.</span><span class="sxs-lookup"><span data-stu-id="d8ae4-112">An app might need to communicate with resources on the Internet.</span></span> <span data-ttu-id="d8ae4-113">Um aplicativo pode precisar de acesso a ambos os tipos de recursos de rede.</span><span class="sxs-lookup"><span data-stu-id="d8ae4-113">An app might need access to both types of network resources.</span></span>  
  
3.  <span data-ttu-id="d8ae4-114">Configure as funcionalidades de isolamento de rede mínimas necessárias no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d8ae4-114">Configure the minimum-required networking isolation capabilities in the app manifest.</span></span>  
  
4.  <span data-ttu-id="d8ae4-115">Implante e execute seu aplicativo para testá-lo usando as ferramentas de isolamento de rede fornecidas para solução de problemas.</span><span class="sxs-lookup"><span data-stu-id="d8ae4-115">Deploy and run your app to test it using the network isolation tools provided for troubleshooting.</span></span>  
  
 <span data-ttu-id="d8ae4-116">Para obter informações mais detalhadas sobre como configurar funcionalidades de rede e as ferramentas de isolamento usadas para solucionar problemas de isolamento de rede, consulte [Como configurar funcionalidades de isolamento de rede](http://go.microsoft.com/fwlink/?LinkID=228265) na documentação do desenvolvedor de [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d8ae4-116">For more detailed information on how to configure network capabilities and isolation tools used for troubleshooting network isolation, see [How to configure network isolation capabilities](http://go.microsoft.com/fwlink/?LinkID=228265) in the [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] developer documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ae4-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8ae4-117">See Also</span></span>  
 [<span data-ttu-id="d8ae4-118">Conectando-se a um serviço web</span><span class="sxs-lookup"><span data-stu-id="d8ae4-118">Connecting to a web service</span></span>](http://go.microsoft.com/fwlink/?LinkID=245696)  
 [<span data-ttu-id="d8ae4-119">Diretrizes e lista de verificação para isolamento de rede</span><span class="sxs-lookup"><span data-stu-id="d8ae4-119">Guidelines and checklist for network isolation</span></span>](http://go.microsoft.com/fwlink/?LinkID=228265)  
 [<span data-ttu-id="d8ae4-120">Início rápido: Conectando usando HttpClient</span><span class="sxs-lookup"><span data-stu-id="d8ae4-120">Quickstart: Connecting using HttpClient</span></span>](http://go.microsoft.com/fwlink/?LinkId=245697)  
 [<span data-ttu-id="d8ae4-121">Como usar HttpClient manipuladores</span><span class="sxs-lookup"><span data-stu-id="d8ae4-121">How to use HttpClient handlers</span></span>](http://go.microsoft.com/fwlink/?LinkId=245699)  
 [<span data-ttu-id="d8ae4-122">Como proteger HttpClient conexões</span><span class="sxs-lookup"><span data-stu-id="d8ae4-122">How to secure HttpClient connections</span></span>](http://go.microsoft.com/fwlink/?LinkId=245698)  
 [<span data-ttu-id="d8ae4-123">Amostra de HttpClient</span><span class="sxs-lookup"><span data-stu-id="d8ae4-123">HttpClient Sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=242550)
