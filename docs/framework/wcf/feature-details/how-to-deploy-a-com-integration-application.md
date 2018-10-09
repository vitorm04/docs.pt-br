---
title: Como implantar uma aplicação de integração + COM
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: e338641b801113c5cd6ff4ec380f60f9ef900fc2
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873080"
---
# <a name="how-to-deploy-a-com-integration-application"></a><span data-ttu-id="5692e-102">Como implantar uma aplicação de integração + COM</span><span class="sxs-lookup"><span data-stu-id="5692e-102">How to: Deploy a COM+ Integration Application</span></span>
<span data-ttu-id="5692e-103">Quando você tiver gravado um aplicativo COM+ integration, você talvez queira implantá-lo em outro computador.</span><span class="sxs-lookup"><span data-stu-id="5692e-103">Once you have written a COM+ integration application, you may want to deploy it on another machine.</span></span> <span data-ttu-id="5692e-104">Este tópico descreve como mover um aplicativo de integração COM+ de um computador para outro.</span><span class="sxs-lookup"><span data-stu-id="5692e-104">This topic describes how to move a COM+ integration application from one machine to another.</span></span>  
  
### <a name="moving-a-com-hosted-integration-app"></a><span data-ttu-id="5692e-105">Mover um COM+ hospedou o aplicativo de integração</span><span class="sxs-lookup"><span data-stu-id="5692e-105">Moving a COM+ hosted Integration App</span></span>  
  
1.  <span data-ttu-id="5692e-106">Certifique-se de que o WCF está instalado em ambos os computadores.</span><span class="sxs-lookup"><span data-stu-id="5692e-106">Ensure that WCF is installed on both machines.</span></span>  
  
2.  <span data-ttu-id="5692e-107">Exportar o aplicativo do computador A.</span><span class="sxs-lookup"><span data-stu-id="5692e-107">Export the application from machine A.</span></span>  
  
3.  <span data-ttu-id="5692e-108">Importe o aplicativo no computador B.</span><span class="sxs-lookup"><span data-stu-id="5692e-108">Import the application on machine B.</span></span>  
  
4.  <span data-ttu-id="5692e-109">Defina o diretório raiz do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5692e-109">Set the Application Root Directory.</span></span> <span data-ttu-id="5692e-110">Por convenção, isso é %PROGRAMFILES%/ComPlus aplicativos / {AppGUID}.</span><span class="sxs-lookup"><span data-stu-id="5692e-110">By convention, this is %PROGRAMFILES%/ComPlus Applications/{AppGUID}.</span></span>  
  
5.  <span data-ttu-id="5692e-111">Copie os arquivos config e Application.manifest do diretório raiz do aplicativo em um computador para o diretório raiz do aplicativo no computador B.</span><span class="sxs-lookup"><span data-stu-id="5692e-111">Copy the Application.config and Application.manifest files from the application root directory on machine A to the application root directory on machine B.</span></span>  
  
6.  <span data-ttu-id="5692e-112">Edite os endereços de ponto de extremidade de serviço no arquivo config no computador B para identificar a máquina apropriada.</span><span class="sxs-lookup"><span data-stu-id="5692e-112">Edit the service endpoint addresses in the Application.config file on machine B to identify the appropriate machine.</span></span> <span data-ttu-id="5692e-113">Por exemplo, altere `http://machineA/MyService` para `http://machineB/MyService`.</span><span class="sxs-lookup"><span data-stu-id="5692e-113">For example, change `http://machineA/MyService` to `http://machineB/MyService`.</span></span>  
  
### <a name="moving-a-web-hosted-integration-application"></a><span data-ttu-id="5692e-114">Mover um aplicativo hospedado na Web de integração</span><span class="sxs-lookup"><span data-stu-id="5692e-114">Moving a Web-hosted integration application</span></span>  
  
1.  <span data-ttu-id="5692e-115">Certifique-se de que o WCF está instalado em ambos os computadores.</span><span class="sxs-lookup"><span data-stu-id="5692e-115">Ensure that WCF is installed on both machines.</span></span>  
  
2.  <span data-ttu-id="5692e-116">Exportar o aplicativo do computador A.</span><span class="sxs-lookup"><span data-stu-id="5692e-116">Export the application from machine A.</span></span>  
  
3.  <span data-ttu-id="5692e-117">Importe o aplicativo no computador B.</span><span class="sxs-lookup"><span data-stu-id="5692e-117">Import the application on machine B.</span></span>  
  
4.  <span data-ttu-id="5692e-118">Criar uma raiz virtual do IIS no computador B.</span><span class="sxs-lookup"><span data-stu-id="5692e-118">Create an IIS vroot on machine B.</span></span>  
  
5.  <span data-ttu-id="5692e-119">Copiar o arquivo. svc (componentName.svc) e o arquivo Web. config do vroot na máquina A para o vroot recém-criado no computador B.</span><span class="sxs-lookup"><span data-stu-id="5692e-119">Copy the .svc file (componentName.svc) and the Web.config file from the vroot on machine A to the newly created vroot on machine B.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5692e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5692e-120">See Also</span></span>  
 [<span data-ttu-id="5692e-121">Visão geral da integração de aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="5692e-121">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)  
 [<span data-ttu-id="5692e-122">Como definir configurações de serviço COM+</span><span class="sxs-lookup"><span data-stu-id="5692e-122">How to: Configure COM+ Service Settings</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)  
 [<span data-ttu-id="5692e-123">Como usar a ferramenta de configuração de modelo de serviço do COM+</span><span class="sxs-lookup"><span data-stu-id="5692e-123">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
