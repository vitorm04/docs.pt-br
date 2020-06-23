---
title: Como habilitar o serviço de compartilhamento de porta Net.TCP
description: Saiba como configurar o serviço de compartilhamento de porta TCP NET usando o MMC para habilitar net. TCP, que está desabilitado por padrão.
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 0292559e3befde7f0b00b36aa10a2d9615daf049
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246994"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="b3895-103">Como habilitar o serviço de compartilhamento de porta Net.TCP</span><span class="sxs-lookup"><span data-stu-id="b3895-103">How to: Enable the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="b3895-104">O Windows Communication Foundation (WCF) usa um serviço do Windows chamado serviço de compartilhamento de porta Net. TCP para facilitar o compartilhamento de portas TCP em vários processos.</span><span class="sxs-lookup"><span data-stu-id="b3895-104">Windows Communication Foundation (WCF) uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="b3895-105">Esse serviço é instalado como parte do WCF, mas o serviço não é habilitado por padrão como uma precaução de segurança e, portanto, deve ser habilitado manualmente antes do primeiro uso.</span><span class="sxs-lookup"><span data-stu-id="b3895-105">This service is installed as part of WCF, but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="b3895-106">Este tópico descreve como configurar o serviço de compartilhamento de porta TCP NET usando o snap-in do MMC (console de gerenciamento Microsoft).</span><span class="sxs-lookup"><span data-stu-id="b3895-106">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="b3895-107">Depois de habilitar o serviço de compartilhamento de porta Net. TCP e iniciá-lo manualmente, consulte [como: configurar um serviço WCF para usar o compartilhamento de porta](how-to-configure-a-wcf-service-to-use-port-sharing.md) para obter informações sobre como configurar seu serviço para usar esse serviço.</span><span class="sxs-lookup"><span data-stu-id="b3895-107">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="b3895-108">Para obter um exemplo que usa net. TCP://compartilhamento de porta, consulte o [exemplo de compartilhamento de porta Net. TCP](../samples/net-tcp-port-sharing-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b3895-108">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="b3895-109">Para habilitar o serviço de compartilhamento de porta Net. TCP usando o MMC</span><span class="sxs-lookup"><span data-stu-id="b3895-109">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1. <span data-ttu-id="b3895-110">No menu Iniciar, abra o console de gerenciamento de serviços abrindo uma janela de prompt de comando e digitando `services.msc` ou abrindo executar e digitando `services.msc` na caixa abrir.</span><span class="sxs-lookup"><span data-stu-id="b3895-110">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2. <span data-ttu-id="b3895-111">Na coluna **nome** da lista de serviços, clique com o botão direito do mouse no **serviço de compartilhamento de porta Net. TCP**e selecione **Propriedades** no menu.</span><span class="sxs-lookup"><span data-stu-id="b3895-111">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3. <span data-ttu-id="b3895-112">Para habilitar a inicialização manual do serviço, na janela **Propriedades** , selecione a guia **geral** e, na caixa **tipo de inicialização** , selecione manual e, em seguida, clique em **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="b3895-112">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4. <span data-ttu-id="b3895-113">Para iniciar o serviço, na área status do serviço, clique no botão **Iniciar** .</span><span class="sxs-lookup"><span data-stu-id="b3895-113">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="b3895-114">O status do serviço agora deve exibir "iniciado".</span><span class="sxs-lookup"><span data-stu-id="b3895-114">The service status should now display "Started".</span></span>  
  
5. <span data-ttu-id="b3895-115">Para retornar à lista de serviços, clique em **OK**e saia do console do MMC.</span><span class="sxs-lookup"><span data-stu-id="b3895-115">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3895-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b3895-116">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3895-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="b3895-117">See also</span></span>

- [<span data-ttu-id="b3895-118">Compartilhamento de porta Net.TCP</span><span class="sxs-lookup"><span data-stu-id="b3895-118">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)
- [<span data-ttu-id="b3895-119">Configurando o serviço de compartilhamento de porta Net.TCP</span><span class="sxs-lookup"><span data-stu-id="b3895-119">Configuring the Net.TCP Port Sharing Service</span></span>](configuring-the-net-tcp-port-sharing-service.md)
