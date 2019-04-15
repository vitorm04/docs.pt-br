---
title: 'Solução de problemas: O aplicativo de serviço não é instalado'
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
ms.openlocfilehash: f75a2f33ecde408d2d8e2f2343197ba56c4b8c21
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143813"
---
# <a name="troubleshooting-service-application-wont-install"></a>Solução de problemas: O aplicativo de serviço não é instalado
Se o aplicativo de serviço não for instalado corretamente, verifique se a propriedade <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> da classe de serviço está definida com o mesmo valor que é mostrado no instalador do serviço. O valor precisa ser o mesmo em ambas as instâncias para que o serviço seja instalado corretamente.  
  
> [!NOTE]
>  Você também pode examinar os logs de instalação para obter comentários sobre o processo de instalação.  
  
 Você também deve verificar se você tem outro serviço com o mesmo nome já está instalado. Os nomes de serviço precisam ser exclusivos para que a instalação tenha êxito.  
  
## <a name="see-also"></a>Consulte também

- [Introdução a aplicativos do Serviço Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
