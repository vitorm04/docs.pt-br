---
title: "Procedimento de configuração único para exemplos do Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
caps.latest.revision: "83"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ffc74fdbec204b798ee93a8ee2c91db992a83cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a>Procedimento de configuração único para exemplos do Windows Communication Foundation
A maioria do [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] exemplos são hospedados em serviços de informações da Internet (IIS) e executar a partir de um diretório virtual comum. Este procedimento de configuração única cria uma pasta no disco; Ele também adiciona um diretório virtual IIS chamado **ServiceModelSamples**.  
  
 O **ServiceModelSamples** diretório virtual é usado para criar e executar todas as amostras que usam um serviço hospedado no IIS. Este é o diretório virtual somente é necessário para executar os exemplos. Criar um exemplo substituirá qualquer serviço implantado anteriormente neste diretório virtual; somente o exemplo construído mais recentemente será implantado e disponíveis neste diretório virtual.  
  
> [!NOTE]
>  Você deve executar todos os comandos em uma conta de administrador local. Se você estiver usando o Windows 7, [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], ou Windows Server 2008 R2, você também deve executar o prompt de comando com privilégios elevados. Para fazer isso, clique no ícone de prompt de comando e, em seguida, clique em **executar como administrador**. Todos os comandos neste tópico devem ser executados em um prompt de comando com as configurações de caminho adequado.  A maneira mais fácil de garantir que isso é usando o Prompt de comando do Visual Studio. Para abrir este prompt, clique em **iniciar**, selecione **todos os programas**, role para baixo até **Visual Studio 2010**, selecione **ferramentas do Visual Studio**, Clique com botão direito **Prompt de comando do Visual Studio (2010)**e, em seguida, clique em **executar como administrador**. Se você tiver uma das edições Express do Visual Studio instaladas, esse prompt de comando não está disponível e você terá que adicionar "C:\Windows\Microsoft.Net\Framework\v4.0" ao caminho do sistema.  
  
### <a name="one-time-setup-procedure-for-wcf-samples"></a>Procedimento de configuração única para obter exemplos do WCF  
  
1.  Certifique-se de que [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] está configurado. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]como configurar o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], consulte [instruções de hospedagem do serviço Internet informações](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md).  
  
2.  Certifique-se de que [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] está instalado. Procure o seguinte diretório para v 4.0 (ou posterior): **\Windows\Microsoft.NET\Framework**  
  
3.  Se [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] não estiver instalado, e o sistema operacional não é Windows Server 2008 SP2 ou posterior, instalar [251798 Hotfix](http://go.microsoft.com/fwlink/?LinkId=184693).  
  
4.  Execute os seguintes comandos. Para obter mais informações sobre por que esses comandos devem ser executados, consulte [IIS serviço hospedado não](http://msdn.microsoft.com/en-us/ee5499fc-1b10-4cda-a9b1-13dba70f05f8).  
  
    > [!WARNING]
    >  Se o IIS for reinstalado, os comandos a seguir precisa ser executado novamente.  
  
    ```  
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable  
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r  
    ```  
  
    > [!WARNING]
    >  Executar o comando `aspnet_regiis –i –enable` fará com que o Pool de aplicativos padrão execução usando [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], que pode gerar problemas de incompatibilidade de outros aplicativos no mesmo computador.  
  
5.  Siga o [instruções do Firewall](../../../../docs/framework/wcf/samples/firewall-instructions.md) para habilitar as portas usadas pelos exemplos.  
  
6.  Verifique o seguinte diretório padrão: \<Unidade_de_instalação >:**\WF_WCF_Samples**. Se os exemplos foram instalados anteriormente, isso é o diretório padrão.  
  
7.  Se os exemplos não estão instalados, instalá-los do local de download de exemplos para [Visual C#](http://go.microsoft.com/fwlink/?LinkId=190939) ou [Visual Basic](http://go.microsoft.com/fwlink/?LinkID=193373).  
  
8.  Depois de instalar os exemplos, acesse: \<Unidade_de_instalação >:**\WF_WCF_Samples\WCF\Setup\\**  
  
9. Execute o **Setupvroot.bat** arquivo em lotes. As etapas a seguir são executadas:  
  
    -   Um diretório virtual é criado em IIS chamado ServiceModelSamples.  
  
    -   Novos diretórios de disco são criados %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples nomeado e % SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin.  
  
     Se você preferir configurar essas pastas manualmente, consulte o [as instruções de configuração do diretório Virtual](../../../../docs/framework/wcf/samples/virtual-directory-setup-instructions.md). Para reverter todas as alterações feitas nesta etapa, execute cleanupvroot.bat depois que você terminar de usar os exemplos.  
  
    > [!NOTE]
    >  Esse procedimento deve ser executado apenas uma vez em um computador, a menos que cleanupvroot.bat é executado.  
  
10. Você deve conceder permissão para modificar para %SystemDrive%\inetpub\wwwroot para a conta sob a qual você está criando os exemplos e o usuário do serviço de rede. Durante a compilação, alguns exemplos de Web hospedada podem tentar copiar os binários compilados para o local mencionado anteriormente e, se você não tiver definido as permissões apropriadas, o build será interrompido. Como alternativa, você pode deixar as permissões e executar o prompt de comando do SDK ou o Prompt de comando do Visual Studio (2012) como administrador ou compilar os exemplos [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], também execute como administrador.  
  
    > [!NOTE]
    >  Se essa etapa não for concluída, todos os exemplos hospedados no IIS falhará durante a compilação. Certifique-se de que você defina as permissões corretamente, ou executar o prompt de comando do SDK e o Prompt de comando do Visual Studio (2012) como administrador.  
  
11. Criar um diretório c:\Logs. no computador. Alguns exemplos podem ser esperando que ela. Certifique-se de que a conta apropriada tem acesso de gravação concedido para esta pasta. Para o Windows 7, [!INCLUDE[wv](../../../../includes/wv-md.md)], e o Windows Server 2008 R2, essa conta é **serviço de rede**. Para [!INCLUDE[lserver](../../../../includes/lserver-md.md)], a conta é NT Authority\Network Service. Para [!INCLUDE[wxp](../../../../includes/wxp-md.md)] e [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], a conta é ASPNET.  
  
12. Execute o arquivo Setupcerttool.bat. Esse arquivo está localizado no \<InstallPath > \WF_WCF_Samples\WCF\Setup\ pasta.  Esse script executará as seguintes tarefas:  
  
    -   A ferramenta de FindPrivateKey de compilação.  
  
    -   Crie um diretório chamado % ProgramFiles%\ServiceModelSampleTools.  
  
    -   Copie a nova ferramenta FindPrivateKey neste diretório.  
  
     Essa ferramenta é exigida pelo exemplos que usam certificados e são hospedados no IIS.  
  
    > [!NOTE]
    >  Para fins de segurança, lembre-se de remover a definição de diretório virtual e as permissões concedidas nas etapas de configuração acima, executando o arquivo em lotes chamado Cleanupvroot.bat depois de concluir os exemplos.  
  
13. Exemplos que são hospedados internamente (não é hospedados no IIS) exigem a permissão para registrar os endereços HTTP no computador para escuta. A permissão para uma reserva de espaço para nome HTTP vem da conta de usuário usada para executar o exemplo. Por padrão, as contas de administrador têm permissão para registrar qualquer endereço HTTP. Contas de administrador não devem ter permissão para os namespaces HTTP utilizados pelos exemplos. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]como definir reservas de namespace, consulte [Configurando HTTP e HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).  
  
14. Alguns exemplos exigem o enfileiramento de mensagens. Consulte [instalar o enfileiramento de mensagens (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md) para instruções de instalação.  
  
    > [!NOTE]
    >  Certifique-se de que você iniciar o serviço MSMQ antes de executar qualquer exemplos que exigem o enfileiramento de mensagens.  
  
15. Alguns exemplos exigem certificados. Consulte [serviços de informações da Internet (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
## <a name="see-also"></a>Consulte também
