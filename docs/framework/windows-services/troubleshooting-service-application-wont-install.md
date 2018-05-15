---
title: 'Solução de problemas: Ganho de aplicativo de serviço&#39;instalação t'
ms.date: 03/30/2017
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
author: ghogen
manager: douge
ms.openlocfilehash: 1f3e5674f9a52627efdc24d6c70c0ab16dcdbbbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-service-application-won39t-install"></a><span data-ttu-id="b5f31-102">Solução de problemas: Ganho de aplicativo de serviço&#39;instalação t</span><span class="sxs-lookup"><span data-stu-id="b5f31-102">Troubleshooting: Service Application Won&#39;t Install</span></span>
<span data-ttu-id="b5f31-103">Se seu aplicativo de serviço não será instalado corretamente, verifique para certificar-se de que o <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> propriedade para a classe de serviço é definida com o mesmo valor, conforme é mostrado no instalador do serviço.</span><span class="sxs-lookup"><span data-stu-id="b5f31-103">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="b5f31-104">O valor deve ser o mesmo em ambas as instâncias para que o serviço seja instalado corretamente.</span><span class="sxs-lookup"><span data-stu-id="b5f31-104">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5f31-105">Você também pode examinar os logs de instalação para obter comentários sobre o processo de instalação.</span><span class="sxs-lookup"><span data-stu-id="b5f31-105">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="b5f31-106">Você também deve verificar para determinar se você tiver outro serviço com o mesmo nome já está instalado.</span><span class="sxs-lookup"><span data-stu-id="b5f31-106">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="b5f31-107">Nomes de serviço devem ser exclusivos para a instalação tenha êxito.</span><span class="sxs-lookup"><span data-stu-id="b5f31-107">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5f31-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5f31-108">See Also</span></span>  
 [<span data-ttu-id="b5f31-109">Introdução aos Aplicativos de Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="b5f31-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
