---
title: Utilizando as ferramentas de desenvolvimento do WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7ec09b6b99b831245d11d858f90c27de05d1e21f
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="e330f-102">Utilizando as ferramentas de desenvolvimento do WCF</span><span class="sxs-lookup"><span data-stu-id="e330f-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="e330f-103">Esta seção descreve as ferramentas de desenvolvimento do Visual Studio que podem ajudá-lo a desenvolver sua [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]serviço.</span><span class="sxs-lookup"><span data-stu-id="e330f-103">This section describes the Visual Studio development tools that can assist you in developing your [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]service.</span></span>  
  
 <span data-ttu-id="e330f-104">Você pode usar os modelos do Visual Studio como uma base para rapidamente criar seu próprio serviço, em seguida, usar [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host automática do serviço e [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] cliente testar, depurar e testar seu serviço.</span><span class="sxs-lookup"><span data-stu-id="e330f-104">You can use the Visual Studio templates as a foundation to quickly build your own service, then use [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host and [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test Client to debug and test your service.</span></span> <span data-ttu-id="e330f-105">Juntos, essas ferramentas fornecem uma rápida e transparente de depuração e ciclo de testes e eliminar a necessidade de confirmação a um modelo de hospedagem mais cedo.</span><span class="sxs-lookup"><span data-stu-id="e330f-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="e330f-106">As ferramentas de desenvolvedor do WCF</span><span class="sxs-lookup"><span data-stu-id="e330f-106">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="e330f-107">Modelos do Visual Studio do WCF</span><span class="sxs-lookup"><span data-stu-id="e330f-107">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 <span data-ttu-id="e330f-108">Você pode usar os modelos predefinidos de projeto e item do Visual Studio no Visual Studio para criar rapidamente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ao redor de aplicativos e serviços.</span><span class="sxs-lookup"><span data-stu-id="e330f-108">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="e330f-109">Host de serviço do WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="e330f-109">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="e330f-110">O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host automática de serviço (WcfSvcHost.exe) permite que você iniciar o depurador do Visual Studio (F5) para hospedar e testar um serviço que você implementou automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e330f-110">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="e330f-111">Você pode testar, em seguida, o serviço usando o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] seu próprio cliente ou cliente de teste (wcfTestClient.exe) para localizar e corrigir quaisquer erros potenciais.</span><span class="sxs-lookup"><span data-stu-id="e330f-111">You can then test the service using the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="e330f-112">Cliente de teste do WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="e330f-112">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="e330f-113"> Cliente de teste (WcfTestClient.exe) é uma ferramenta de interface gráfica do usuário que permite a entrada de parâmetros de tipos arbitrários, envie de entrada para o serviço e o modo de exibição que envia a resposta do serviço.</span><span class="sxs-lookup"><span data-stu-id="e330f-113"> Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="e330f-114">Fornece um serviço contínuo testando experiência quando combinado com [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host do serviço automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e330f-114">It provides a seamless service testing experience when combined with [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host.</span></span>  
  
 [<span data-ttu-id="e330f-115">Gerando classes de tipo de dados por meio de XML</span><span class="sxs-lookup"><span data-stu-id="e330f-115">Generating Data Type Classes from XML</span></span>](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="e330f-116">Dados XML armazenados na área de transferência podem ser colados em uma página de código.</span><span class="sxs-lookup"><span data-stu-id="e330f-116">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="e330f-117">As classes definidas nos dados serão convertidas para tipos de código.</span><span class="sxs-lookup"><span data-stu-id="e330f-117">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="e330f-118">Usando as ferramentas sem privilégios de administrador</span><span class="sxs-lookup"><span data-stu-id="e330f-118">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="e330f-119">Para permitir que usuários sem privilégios de administrador para desenvolver [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services, uma ACL (lista de controle de acesso) é criada para o namespace "http://+:8731/Design_Time_Addresses" durante a instalação do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e330f-119">To enable users without administrator privilege to develop [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="e330f-120">A ACL é definida como (IU), que inclui todos os usuários interativos, conectados à máquina.</span><span class="sxs-lookup"><span data-stu-id="e330f-120">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="e330f-121">Administradores podem adicionar ou remover usuários dessa ACL ou abrir portas adicionais. Essa ACL permite modelos WCF ou WF para enviar e receber dados em sua configuração padrão.</span><span class="sxs-lookup"><span data-stu-id="e330f-121">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="e330f-122">Ele também permite que os usuários usem o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host automática de serviço (wcfSvcHost.exe) sem conceder privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="e330f-122">It also enables users to use the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="e330f-123">Você pode modificar o acesso usando a ferramenta Netsh.exe [!INCLUDE[wv](../../../includes/wv-md.md)] na conta de administrador com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="e330f-123">You can modify access using the Netsh.exe tool in [!INCLUDE[wv](../../../includes/wv-md.md)] under the elevated administrator account.</span></span> <span data-ttu-id="e330f-124">Este é um exemplo de uso Netsh.exe.</span><span class="sxs-lookup"><span data-stu-id="e330f-124">The following is an example of using Netsh.exe.</span></span>  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 <span data-ttu-id="e330f-125">Para obter mais informações sobre Netsh.exe, consulte [como usar a ferramenta Netsh.exe e as opções de linha de comando](http://go.microsoft.com/fwlink/?LinkId=97877).</span><span class="sxs-lookup"><span data-stu-id="e330f-125">For more information about Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](http://go.microsoft.com/fwlink/?LinkId=97877).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e330f-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e330f-126">See Also</span></span>  
 [<span data-ttu-id="e330f-127">Modelos do Visual Studio do WCF</span><span class="sxs-lookup"><span data-stu-id="e330f-127">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [<span data-ttu-id="e330f-128">Host de serviço do WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="e330f-128">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [<span data-ttu-id="e330f-129">Cliente de teste do WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="e330f-129">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
