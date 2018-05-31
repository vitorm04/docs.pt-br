---
title: 'Solução de problemas: o aplicativo de serviço não é instalado'
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
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509654"
---
# <a name="troubleshooting-service-application-won39t-install"></a><span data-ttu-id="e7472-102">Solução de problemas: o aplicativo de serviço não é instalado</span><span class="sxs-lookup"><span data-stu-id="e7472-102">Troubleshooting: Service Application Won&#39;t Install</span></span>
<span data-ttu-id="e7472-103">Se o aplicativo de serviço não for instalado corretamente, verifique se a propriedade <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> da classe de serviço está definida com o mesmo valor que é mostrado no instalador do serviço.</span><span class="sxs-lookup"><span data-stu-id="e7472-103">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="e7472-104">O valor precisa ser o mesmo em ambas as instâncias para que o serviço seja instalado corretamente.</span><span class="sxs-lookup"><span data-stu-id="e7472-104">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7472-105">Você também pode examinar os logs de instalação para obter comentários sobre o processo de instalação.</span><span class="sxs-lookup"><span data-stu-id="e7472-105">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="e7472-106">Você também deve verificar se você tem outro serviço com o mesmo nome já está instalado.</span><span class="sxs-lookup"><span data-stu-id="e7472-106">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="e7472-107">Os nomes de serviço precisam ser exclusivos para que a instalação tenha êxito.</span><span class="sxs-lookup"><span data-stu-id="e7472-107">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7472-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7472-108">See Also</span></span>  
 [<span data-ttu-id="e7472-109">Introdução aos Aplicativos de Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="e7472-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
