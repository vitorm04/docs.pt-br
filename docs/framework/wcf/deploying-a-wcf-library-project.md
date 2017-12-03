---
title: Implantando um projeto de biblioteca do WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dbddd99125e8615640ca39d091e92cdde87c9faf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="deploying-a-wcf-library-project"></a><span data-ttu-id="9aaae-102">Implantando um projeto de biblioteca do WCF</span><span class="sxs-lookup"><span data-stu-id="9aaae-102">Deploying a WCF Library Project</span></span>
<span data-ttu-id="9aaae-103">Este tópico descreve como você pode implantar um [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] projeto de biblioteca de serviço.</span><span class="sxs-lookup"><span data-stu-id="9aaae-103">This topic describes how you can deploy a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Service Library Project.</span></span>  
  
## <a name="deploying-a-wcf-service-library"></a><span data-ttu-id="9aaae-104">Implantando uma biblioteca de serviços WCF</span><span class="sxs-lookup"><span data-stu-id="9aaae-104">Deploying a WCF Service Library</span></span>  
 <span data-ttu-id="9aaae-105">Um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] biblioteca de serviço é uma biblioteca de vínculo dinâmico (DLL).</span><span class="sxs-lookup"><span data-stu-id="9aaae-105">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service library is a dynamic-link library (DLL).</span></span> <span data-ttu-id="9aaae-106">Como tal, ele não pode ser executado por conta própria.</span><span class="sxs-lookup"><span data-stu-id="9aaae-106">As such, it cannot be executed on its own.</span></span> <span data-ttu-id="9aaae-107">Ele precisa ser implantado em um ambiente de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="9aaae-107">It needs to be deployed into a hosting environment.</span></span> <span data-ttu-id="9aaae-108">Para obter mais informações sobre esse processo, consulte [hospedagem e consumindo serviços WCF](http://go.microsoft.com/fwlink/?LinkId=99932).</span><span class="sxs-lookup"><span data-stu-id="9aaae-108">For more information about this process, see [Hosting and Consuming WCF Services](http://go.microsoft.com/fwlink/?LinkId=99932).</span></span>  
  
 <span data-ttu-id="9aaae-109">Um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] biblioteca de serviço pode ser implantada como qualquer outro [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço.</span><span class="sxs-lookup"><span data-stu-id="9aaae-109">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service library can be deployed like any other [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="9aaae-110">No entanto, lembre-se que [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] não oferece suporte à configuração para DLLs.</span><span class="sxs-lookup"><span data-stu-id="9aaae-110">However, be aware that [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] does not support configuration for DLLs.</span></span> <span data-ttu-id="9aaae-111"><xref:System.Configuration>oferece suporte a um arquivo de configuração por domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9aaae-111"><xref:System.Configuration> supports one configuration file per app-domain.</span></span> <span data-ttu-id="9aaae-112">O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projeto de biblioteca de serviço elimina essa limitação, fornecendo um arquivo App. config para a biblioteca durante o desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="9aaae-112">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service library project alleviates this limitation by providing an App.config file for the library during development.</span></span> <span data-ttu-id="9aaae-113">No entanto, o arquivo App. config não é reconhecido após a implantação.</span><span class="sxs-lookup"><span data-stu-id="9aaae-113">However, the App.config file is not recognized after deployment.</span></span>  
  
 <span data-ttu-id="9aaae-114">Você precisa mover seu código de configuração para o arquivo de configuração reconhecido pelo seu ambiente de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="9aaae-114">You have to move your configuration code into the configuration file recognized by your hosting environment.</span></span> <span data-ttu-id="9aaae-115">Para auto-hospedagem, você deve copiar o conteúdo do arquivo App. config no arquivo App. config do executável de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="9aaae-115">For self-hosting, you should copy the contents of the App.config file into the App.config file of the hosting executable.</span></span> <span data-ttu-id="9aaae-116">Se você usar o IIS para hospedar seu serviço, você deve copiar o conteúdo do arquivo App. config no arquivo Web. config do diretório virtual.</span><span class="sxs-lookup"><span data-stu-id="9aaae-116">If you use IIS to host your service, you should copy the contents of the App.config file into the Web.config file of the virtual directory.</span></span>
