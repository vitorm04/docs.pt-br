---
title: 'Solução de problemas: O aplicativo de serviço não é instalado'
description: Solucionar problemas se o aplicativo de serviço não for instalado. Certifique-se de que a propriedade ServiceName da classe de serviço esteja definida corretamente.
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
ms.openlocfilehash: 4a57fb6975a6ded48abf7c8fd7eacec16e4f94d8
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925521"
---
# <a name="troubleshooting-service-application-wont-install"></a><span data-ttu-id="733b5-104">Solução de problemas: O aplicativo de serviço não é instalado</span><span class="sxs-lookup"><span data-stu-id="733b5-104">Troubleshooting: Service Application Won't Install</span></span>
<span data-ttu-id="733b5-105">Se o aplicativo de serviço não for instalado corretamente, verifique se a propriedade <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> da classe de serviço está definida com o mesmo valor que é mostrado no instalador do serviço.</span><span class="sxs-lookup"><span data-stu-id="733b5-105">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="733b5-106">O valor precisa ser o mesmo em ambas as instâncias para que o serviço seja instalado corretamente.</span><span class="sxs-lookup"><span data-stu-id="733b5-106">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="733b5-107">Você também pode examinar os logs de instalação para obter comentários sobre o processo de instalação.</span><span class="sxs-lookup"><span data-stu-id="733b5-107">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="733b5-108">Você também deve verificar se você tem outro serviço com o mesmo nome já está instalado.</span><span class="sxs-lookup"><span data-stu-id="733b5-108">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="733b5-109">Os nomes de serviço precisam ser exclusivos para que a instalação tenha êxito.</span><span class="sxs-lookup"><span data-stu-id="733b5-109">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="733b5-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="733b5-110">See also</span></span>

- [<span data-ttu-id="733b5-111">Introdução a aplicativos do Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="733b5-111">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
