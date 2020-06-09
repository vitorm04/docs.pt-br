---
title: Como habilitar o serviço de compartilhamento de porta Net.TCP
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 8b305b98d620636328866bce848411f395053485
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593121"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="9d26a-102">Como habilitar o serviço de compartilhamento de porta Net.TCP</span><span class="sxs-lookup"><span data-stu-id="9d26a-102">How to: Enable the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="9d26a-103">O Windows Communication Foundation (WCF) usa um serviço do Windows chamado serviço de compartilhamento de porta Net. TCP para facilitar o compartilhamento de portas TCP em vários processos.</span><span class="sxs-lookup"><span data-stu-id="9d26a-103">Windows Communication Foundation (WCF) uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="9d26a-104">Esse serviço é instalado como parte do WCF, mas o serviço não é habilitado por padrão como uma precaução de segurança e, portanto, deve ser habilitado manualmente antes do primeiro uso.</span><span class="sxs-lookup"><span data-stu-id="9d26a-104">This service is installed as part of WCF, but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="9d26a-105">Este tópico descreve como configurar o serviço de compartilhamento de porta TCP NET usando o snap-in do MMC (console de gerenciamento Microsoft).</span><span class="sxs-lookup"><span data-stu-id="9d26a-105">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="9d26a-106">Depois de habilitar o serviço de compartilhamento de porta Net. TCP e iniciá-lo manualmente, consulte [como: configurar um serviço WCF para usar o compartilhamento de porta](how-to-configure-a-wcf-service-to-use-port-sharing.md) para obter informações sobre como configurar seu serviço para usar esse serviço.</span><span class="sxs-lookup"><span data-stu-id="9d26a-106">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="9d26a-107">Para obter um exemplo que usa net. TCP://compartilhamento de porta, consulte o [exemplo de compartilhamento de porta Net. TCP](../samples/net-tcp-port-sharing-sample.md).</span><span class="sxs-lookup"><span data-stu-id="9d26a-107">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="9d26a-108">Para habilitar o serviço de compartilhamento de porta Net. TCP usando o MMC</span><span class="sxs-lookup"><span data-stu-id="9d26a-108">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1. <span data-ttu-id="9d26a-109">No menu Iniciar, abra o console de gerenciamento de serviços abrindo uma janela de prompt de comando e digitando `services.msc` ou abrindo executar e digitando `services.msc` na caixa abrir.</span><span class="sxs-lookup"><span data-stu-id="9d26a-109">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2. <span data-ttu-id="9d26a-110">Na coluna **nome** da lista de serviços, clique com o botão direito do mouse no **serviço de compartilhamento de porta Net. TCP**e selecione **Propriedades** no menu.</span><span class="sxs-lookup"><span data-stu-id="9d26a-110">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3. <span data-ttu-id="9d26a-111">Para habilitar a inicialização manual do serviço, na janela **Propriedades** , selecione a guia **geral** e, na caixa **tipo de inicialização** , selecione manual e, em seguida, clique em **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="9d26a-111">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4. <span data-ttu-id="9d26a-112">Para iniciar o serviço, na área status do serviço, clique no botão **Iniciar** .</span><span class="sxs-lookup"><span data-stu-id="9d26a-112">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="9d26a-113">O status do serviço agora deve exibir "iniciado".</span><span class="sxs-lookup"><span data-stu-id="9d26a-113">The service status should now display "Started".</span></span>  
  
5. <span data-ttu-id="9d26a-114">Para retornar à lista de serviços, clique em **OK**e saia do console do MMC.</span><span class="sxs-lookup"><span data-stu-id="9d26a-114">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d26a-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d26a-115">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d26a-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="9d26a-116">See also</span></span>

- [<span data-ttu-id="9d26a-117">Compartilhamento de porta Net.TCP</span><span class="sxs-lookup"><span data-stu-id="9d26a-117">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)
- [<span data-ttu-id="9d26a-118">Configurando o serviço de compartilhamento de porta Net.TCP</span><span class="sxs-lookup"><span data-stu-id="9d26a-118">Configuring the Net.TCP Port Sharing Service</span></span>](configuring-the-net-tcp-port-sharing-service.md)
