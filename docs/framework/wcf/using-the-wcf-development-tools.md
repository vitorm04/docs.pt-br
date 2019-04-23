---
title: Utilizando as ferramentas de desenvolvimento do WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 1ffa3be4a6b8976ab978ea995e8b2c1faaacf0ae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144632"
---
# <a name="using-the-wcf-development-tools"></a>Utilizando as ferramentas de desenvolvimento do WCF
Esta seção descreve as ferramentas de desenvolvimento do Visual Studio que podem ajudá-lo a desenvolver seu WCFservice.  
  
 Você pode usar modelos do Visual Studio como uma base para criar rapidamente seu próprio serviço e usar o Host de automático de serviço do WCF e o cliente de teste do WCF para depurar e testar seu serviço. Juntos, essas ferramentas fornecem uma rápida e perfeita de depuração e ciclo de testes e eliminar a necessidade de se comprometer com um modelo de hospedagem em um estágio inicial.  
  
## <a name="the-wcf-developer-tools"></a>As ferramentas de desenvolvedor do WCF  
 [Modelos do Visual Studio do WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 Você pode usar os modelos predefinidos de projeto e item do Visual Studio no Visual Studio para compilar rapidamente os serviços WCF e aplicativos ao redor.  
  
 [Host de serviço do WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 O Host de automático de serviço do WCF (WcfSvcHost.exe) permite que você iniciar o depurador do Visual Studio (F5) para hospedar automaticamente e testar um serviço que você implementou. Em seguida, você pode testar o serviço usando o cliente de teste do WCF (wcfTestClient.exe) ou seu próprio cliente para localizar e corrigir os erros em potencial.  
  
 [Cliente de teste do WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 Cliente de teste do WCF (WcfTestClient.exe) é uma ferramenta de GUI que permite a entrada de parâmetros de tipos arbitrários, enviem essa entrada para o serviço e o modo de exibição que envia a resposta do serviço. Ele fornece um serviço perfeito experiência quando combinado com o Host de automático de serviço do WCF em teste.  
  
 [Gerando classes de tipo de dados por meio de XML](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 Dados XML armazenados na área de transferência podem ser colados em uma página de código. As classes definidas nos dados serão convertidas em tipos de código.  
  
## <a name="using-the-tools-without-administrator-privilege"></a>Usando as ferramentas sem privilégios de administrador  
 Para permitir que usuários sem privilégios de administrador desenvolver serviços WCF, uma ACL (lista de controle de acesso) é criada para o namespace "http://+:8731/Design_Time_Addresses" durante a instalação do Visual Studio. A ACL é definida como (UI), que inclui todos os usuários interativos, conectados à máquina. Os administradores podem adicionar ou remover usuários dessa ACL ou abrir portas adicionais. Essa ACL permite que o WCF ou WF modelos enviar e receber dados em sua configuração padrão. Ele também permite que os usuários usem o Host de automático de serviço do WCF (wcfSvcHost.exe) sem conceder privilégios de administrador.  
  
 Você pode modificar o acesso usando a ferramenta Netsh.exe no [!INCLUDE[wv](../../../includes/wv-md.md)] sob a conta de administrador com privilégios elevados. O exemplo a seguir é um exemplo de uso Netsh.exe.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Para obter mais informações sobre Netsh.exe, consulte [como usar a ferramenta de Netsh.exe e as opções de linha de comando](https://go.microsoft.com/fwlink/?LinkId=97877).  
  
## <a name="see-also"></a>Consulte também

- [Modelos do Visual Studio do WCF](../../../docs/framework/wcf/wcf-vs-templates.md)
- [Host de serviço do WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
- [Cliente de teste do WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
