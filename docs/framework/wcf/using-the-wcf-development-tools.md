---
title: Utilizando as ferramentas de desenvolvimento do WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 41d2ee2881b79ffb086a931ec6d271d409ac66db
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="using-the-wcf-development-tools"></a>Utilizando as ferramentas de desenvolvimento do WCF
Esta seção descreve as ferramentas de desenvolvimento do Visual Studio que podem ajudá-lo a desenvolver sua WCFservice.  
  
 Você pode usar os modelos do Visual Studio como uma base para criar rapidamente seu próprio serviço e usar o Host de automática de serviço do WCF e do cliente de teste do WCF para depurar e testar seu serviço. Juntos, essas ferramentas fornecem uma rápida e transparente de depuração e ciclo de testes e eliminar a necessidade de confirmação a um modelo de hospedagem mais cedo.  
  
## <a name="the-wcf-developer-tools"></a>As ferramentas de desenvolvedor do WCF  
 [Modelos do Visual Studio do WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 Você pode usar os modelos predefinidos de projeto e item do Visual Studio no Visual Studio para criar rapidamente os serviços WCF e aplicativos ao redor.  
  
 [Host de serviço do WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 O Host de automático do serviço WCF (WcfSvcHost.exe) permite que você iniciar o depurador do Visual Studio (F5) para hospedar e testar um serviço que você implementou automaticamente. Em seguida, você pode testar o serviço usando o cliente de teste do WCF (wcfTestClient.exe) ou seu próprio cliente para localizar e corrigir todos os possíveis erros.  
  
 [Cliente de teste do WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 Cliente de teste do WCF (WcfTestClient.exe) é uma ferramenta de interface gráfica do usuário que permite a entrada de parâmetros de tipos arbitrários, envie de entrada para o serviço e o modo de exibição que envia a resposta do serviço. Ele fornece um serviço perfeito experiência quando combinado com o Host de automático do serviço WCF em teste.  
  
 [Gerando classes de tipo de dados por meio de XML](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 Dados XML armazenados na área de transferência podem ser colados em uma página de código. As classes definidas nos dados serão convertidas para tipos de código.  
  
## <a name="using-the-tools-without-administrator-privilege"></a>Usando as ferramentas sem privilégios de administrador  
 Para permitir que usuários sem privilégios de administrador desenvolver serviços WCF, uma ACL (lista de controle de acesso) é criada para o namespace "http://+:8731/Design_Time_Addresses" durante a instalação do Visual Studio. A ACL é definida como (IU), que inclui todos os usuários interativos, conectados à máquina. Administradores podem adicionar ou remover usuários dessa ACL ou abrir portas adicionais. Essa ACL permite modelos WCF ou WF para enviar e receber dados em sua configuração padrão. Ele também permite que os usuários usem o Host de automático do serviço WCF (wcfSvcHost.exe) sem conceder privilégios de administrador.  
  
 Você pode modificar o acesso usando a ferramenta Netsh.exe [!INCLUDE[wv](../../../includes/wv-md.md)] na conta de administrador com privilégios elevados. Este é um exemplo de uso Netsh.exe.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Para obter mais informações sobre Netsh.exe, consulte [como usar a ferramenta Netsh.exe e as opções de linha de comando](http://go.microsoft.com/fwlink/?LinkId=97877).  
  
## <a name="see-also"></a>Consulte também  
 [Modelos do Visual Studio do WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [Host de serviço do WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [Cliente de teste do WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
