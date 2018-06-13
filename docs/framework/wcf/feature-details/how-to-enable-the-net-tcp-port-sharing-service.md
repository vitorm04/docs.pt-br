---
title: Como habilitar o serviço de compartilhamento de porta Net.TCP
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 4b5a18e11d9fc15f23b5353883a63d838face58a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490754"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="00cdf-102">Como habilitar o serviço de compartilhamento de porta Net.TCP</span><span class="sxs-lookup"><span data-stu-id="00cdf-102">How to: Enable the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="00cdf-103">Windows Communication Foundation (WCF) usa um serviço do Windows chamado o serviço de compartilhamento de porta NET. TCP para facilitar o compartilhamento de portas TCP entre vários processos.</span><span class="sxs-lookup"><span data-stu-id="00cdf-103">Windows Communication Foundation (WCF) uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="00cdf-104">Esse serviço é instalado como parte do WCF, mas o serviço não está habilitado por padrão como uma precaução de segurança e portanto deve ser habilitado manualmente antes da primeira utilização.</span><span class="sxs-lookup"><span data-stu-id="00cdf-104">This service is installed as part of WCF, but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="00cdf-105">Este tópico descreve como configurar o serviço de compartilhamento de porta de TCP Net usando o snap-In do Console de gerenciamento Microsoft (MMC).</span><span class="sxs-lookup"><span data-stu-id="00cdf-105">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="00cdf-106">Depois de habilitar o serviço de compartilhamento de porta NET. TCP e iniciá-lo manualmente, consulte [como: configurar um serviço WCF para usar o compartilhamento de porta](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) para obter informações sobre como configurar seu serviço para usar este serviço.</span><span class="sxs-lookup"><span data-stu-id="00cdf-106">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="00cdf-107">Para obter um exemplo que usa o compartilhamento de porta net.tcp://, consulte o [exemplo de compartilhamento de porta NET. TCP](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).</span><span class="sxs-lookup"><span data-stu-id="00cdf-107">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="00cdf-108">Para habilitar o usando o MMC Serviço de compartilhamento de porta de NET. TCP</span><span class="sxs-lookup"><span data-stu-id="00cdf-108">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1.  <span data-ttu-id="00cdf-109">No menu Iniciar, abra o Console de gerenciamento de serviços, abrindo uma janela de Prompt de comando e digitando `services.msc` ou abrindo executar e digitando `services.msc` na caixa Abrir.</span><span class="sxs-lookup"><span data-stu-id="00cdf-109">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2.  <span data-ttu-id="00cdf-110">No **nome** coluna da lista de serviços, clique com botão direito do **serviço de compartilhamento de porta NET. TCP**e selecione **propriedades** no menu.</span><span class="sxs-lookup"><span data-stu-id="00cdf-110">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3.  <span data-ttu-id="00cdf-111">Para habilitar a inicialização manual do serviço, no **propriedades** janela Selecionar o **geral** guia e no **tipo de inicialização** caixa de seleção Manual e, em seguida, clique em **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="00cdf-111">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4.  <span data-ttu-id="00cdf-112">Para iniciar o serviço, na área de status do serviço, clique o **iniciar** botão.</span><span class="sxs-lookup"><span data-stu-id="00cdf-112">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="00cdf-113">O status do serviço agora deve exibir "Iniciado".</span><span class="sxs-lookup"><span data-stu-id="00cdf-113">The service status should now display "Started".</span></span>  
  
5.  <span data-ttu-id="00cdf-114">Para retornar à lista de serviços, clique o **Okey**e saia do Console do MMC.</span><span class="sxs-lookup"><span data-stu-id="00cdf-114">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00cdf-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="00cdf-115">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00cdf-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00cdf-116">See Also</span></span>  
 [<span data-ttu-id="00cdf-117">Compartilhamento de porta do NET.TCP</span><span class="sxs-lookup"><span data-stu-id="00cdf-117">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 [<span data-ttu-id="00cdf-118">Configurando o serviço de compartilhamento de porta NET.TCP</span><span class="sxs-lookup"><span data-stu-id="00cdf-118">Configuring the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
