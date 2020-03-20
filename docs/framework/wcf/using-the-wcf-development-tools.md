---
title: Utilizando as ferramentas de desenvolvimento do WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 82bb7e225492bcdba4d2e611de405a09571355c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183075"
---
# <a name="using-the-wcf-development-tools"></a>Utilizando as ferramentas de desenvolvimento do WCF
Esta seção descreve as ferramentas de desenvolvimento do Visual Studio que podem ajudá-lo a desenvolver seu serviço WCFservice.  
  
 Você pode usar os modelos do Visual Studio como base para construir rapidamente seu próprio serviço e, em seguida, usar o WCF Service Auto Host e o WCF Test Client para depurar e testar seu serviço. Essas ferramentas juntas fornecem um ciclo rápido e perfeito de depuração e teste, e impedem a necessidade de se comprometer com um modelo de hospedagem em um estágio inicial.  

 > [!NOTE]
 > Começando pelo Visual Studio 2017, as ferramentas de desenvolvimento do WCF não são instaladas por padrão. Para usar esses recursos, você deve garantir que o componente da Windows Communication Foundation seja selecionado no instalador do Visual Studio.
  
## <a name="the-wcf-developer-tools"></a>As ferramentas de desenvolvedor do WCF  
 [Modelos do Visual Studio do WCF](wcf-vs-templates.md)  
  
 Você pode usar o projeto visual studio predefinido e modelos de itens no Visual Studio para criar rapidamente serviços WCF e aplicativos ao redor.  
  
 [Host de serviço do WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)  
  
 O WCF Service Auto Host (WcfSvcHost.exe) permite que você inicie o depurador visual studio (F5) para hospedar e testar automaticamente um serviço que você implementou. Em seguida, você pode testar o serviço usando o WCF Test Client (wcfTestClient.exe) ou seu próprio cliente para encontrar e corrigir quaisquer possíveis erros.  
  
 [Cliente de Teste do WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)  
  
 WCF Test Client (WcfTestClient.exe) é uma ferramenta de GUI que permite inserir parâmetros de tipos arbitrários, enviar essa entrada para o serviço e visualizar a resposta que o serviço envia de volta. Ele fornece uma experiência perfeita de teste de serviço quando combinado com o WCF Service Auto Host.  
  
 [Gerando classes de tipo de dados por meio de XML](generating-data-type-classes-from-xml.md)  
  
 Os dados XML armazenados na área de transferência podem ser colados em uma página de código. As classes definidas nos dados serão convertidas em tipos de código.  
  
## <a name="using-the-tools-without-administrator-privilege"></a>Usando as Ferramentas sem privilégio de administrador  
 Para permitir que os usuários sem privilégio de administrador desenvolvam serviços WCF,http://+:8731/Design_Time_Addressesuma ACL (Access Control List) é criada para o namespace " durante a instalação do Visual Studio. A ACL é definida como (UI), que inclui todos os usuários interativos conectados à máquina. Os administradores podem adicionar ou remover usuários desta ACL ou abrir portas adicionais. Esta ACL permite que os modelos WCF ou WF enviem e recebam dados em sua configuração padrão. Ele também permite que os usuários usem o WCF Service Auto Host (wcfSvcHost.exe) sem conceder privilégios de administrador.  
  
 Você pode modificar o acesso usando a ferramenta Netsh.exe no Windows Vista a conta de administrador elevada. A seguir, um exemplo de uso do Netsh.exe.  
  
```console  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Para obter mais informações sobre o Netsh.exe, consulte [Como usar a ferramenta Netsh.exe e os switches de linha de comando](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10)).  
  
## <a name="see-also"></a>Confira também

- [Modelos do Visual Studio do WCF](wcf-vs-templates.md)
- [Host de serviço do WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [Cliente de Teste do WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
