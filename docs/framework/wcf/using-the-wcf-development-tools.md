---
title: Utilizando as ferramentas de desenvolvimento do WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9532363adafd492ca35e10e6d20c788ddf5b1d17
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-wcf-development-tools"></a>Utilizando as ferramentas de desenvolvimento do WCF
Esta seção descreve o [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] ferramentas de desenvolvimento que podem ajudá-lo a desenvolver sua [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]serviço.  
  
 Você pode usar o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] , em seguida, usar modelos como uma base para criar rapidamente seu próprio serviço [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host automática do serviço e [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] cliente testar, depurar e testar seu serviço. Juntos, essas ferramentas fornecem uma rápida e transparente de depuração e ciclo de testes e eliminar a necessidade de confirmação a um modelo de hospedagem mais cedo.  
  
## <a name="the-wcf-developer-tools"></a>As ferramentas de desenvolvedor do WCF  
 [WCF Visual Studio Templates](../../../docs/framework/wcf/wcf-vs-templates.md) (Modelos do Visual Studio do WCF)  
  
 Você pode usar predefinida [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] modelos de projeto e item em [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] para criar rapidamente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ao redor de aplicativos e serviços.  
  
 [WCF Service Host (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md) [Host de serviço do WCF (WcfSvcHost.exe)]  
  
 O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host automática de serviço (WcfSvcHost.exe) permite que você inicie a [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] depurador (F5) para hospedar e testar um serviço que você implementou automaticamente. Você pode testar, em seguida, o serviço usando o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] seu próprio cliente ou cliente de teste (wcfTestClient.exe) para localizar e corrigir quaisquer erros potenciais.  
  
 [WCF Test Client (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md) [Cliente de teste do WCF (WcfTestClient.exe)]  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Cliente de teste (WcfTestClient.exe) é uma ferramenta de interface gráfica do usuário que permite a entrada de parâmetros de tipos arbitrários, envie de entrada para o serviço e o modo de exibição que envia a resposta do serviço. Fornece um serviço contínuo testando experiência quando combinado com [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host do serviço automaticamente.  
  
 [Generating Data Type Classes from XML](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md) (Gerando classes de tipo de dados por meio de XML)  
  
 Dados XML armazenados na área de transferência podem ser colados em uma página de código. As classes definidas nos dados serão convertidas para tipos de código.  
  
## <a name="using-the-tools-without-administrator-privilege"></a>Usando as ferramentas sem privilégios de administrador  
 Para permitir que usuários sem privilégios de administrador para desenvolver [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services, uma ACL (lista de controle de acesso) é criada para o namespace "http://+:8731/Design_Time_Addresses" durante a instalação do [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. A ACL é definida como (IU), que inclui todos os usuários interativos, conectados à máquina. Administradores podem adicionar ou remover usuários dessa ACL ou abrir portas adicionais. Essa ACL permite modelos WCF ou WF para enviar e receber dados em sua configuração padrão. Ele também permite que os usuários usem o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host automática de serviço (wcfSvcHost.exe) sem conceder privilégios de administrador.  
  
 Você pode modificar o acesso usando a ferramenta Netsh.exe [!INCLUDE[wv](../../../includes/wv-md.md)] na conta de administrador com privilégios elevados. Este é um exemplo de uso Netsh.exe.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]Netsh.exe, consulte [como usar a ferramenta Netsh.exe e as opções de linha de comando](http://go.microsoft.com/fwlink/?LinkId=97877).  
  
## <a name="see-also"></a>Consulte também  
 [WCF Visual Studio Templates](../../../docs/framework/wcf/wcf-vs-templates.md) (Modelos do Visual Studio do WCF)  
 [WCF Service Host (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md) [Host de serviço do WCF (WcfSvcHost.exe)]  
 [WCF Test Client (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md) [Cliente de teste do WCF (WcfTestClient.exe)]
