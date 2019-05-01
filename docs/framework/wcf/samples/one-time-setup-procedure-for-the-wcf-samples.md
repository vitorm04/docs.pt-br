---
title: Procedimento de configuração único para exemplos do Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
ms.openlocfilehash: 2b9d84089cdd987f2e2b1e3d23354505520a80f8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052099"
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a>Procedimento de configuração único para exemplos do Windows Communication Foundation
A maioria dos exemplos do Windows Communication Foundation (WCF) é hospedada em serviços de informações da Internet (IIS) e executar a partir de um diretório virtual comum. Este procedimento de configuração única cria uma pasta no disco; Ele também adiciona um diretório virtual IIS chamado **ServiceModelSamples**.

 O **ServiceModelSamples** diretório virtual é usado para criar e executar todas as amostras que usam um serviço hospedado pelo IIS. Isso é o diretório virtual apenas que é necessário para executar os exemplos. Criação de uma amostra substituirá qualquer serviço implantado anteriormente neste diretório virtual; apenas a amostra construída mais recentemente será implantado e está disponível neste diretório virtual.

> [!NOTE]
>  Você deve executar todos os comandos em uma conta de administrador local. Se você estiver usando o Windows 7, [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], ou Windows Server 2008 R2, você também deve executar o prompt de comando com privilégios elevados. Para fazer isso, clique com botão direito no ícone do prompt de comando e, em seguida, clique em **executar como administrador**. Todos os comandos neste tópico devem ser executados em um prompt de comando que tem as configurações de caminho apropriada.  A maneira mais fácil para garantir que isso é usando o Prompt de comando do Visual Studio. Para abrir esse prompt, clique em **inicie**, selecione **todos os programas**, role para baixo até **Visual Studio 2010**, selecione **ferramentas do Visual Studio**, Clique com botão direito **Prompt de comando do Visual Studio (2010)** e, em seguida, clique em **executar como administrador**. Se você tiver uma das edições do Visual Studio Express instaladas, esse prompt de comando não está disponível e você terá que adicionar "C:\Windows\Microsoft.Net\Framework\v4.0" ao caminho do sistema.  
  
### <a name="one-time-setup-procedure-for-wcf-samples"></a>Procedimento de configuração única para obter exemplos WCF  
  
1. Certifique-se de que [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] está configurado. Para obter mais informações sobre como configurar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], consulte [hospedagem instruções de serviço de informações da Internet](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md).  
  
2. Certifique-se de que [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] está instalado. Pesquisar o seguinte diretório for v4.0 (ou posterior): **\Windows\Microsoft.NET\Framework**  
  
3. Se o Visual Studio 2012 não está instalado e seu sistema operacional não é Windows Server 2008 SP2 ou posterior, instale [251798 Hotfix](https://go.microsoft.com/fwlink/?LinkId=184693).  
  
4. Execute os comandos a seguir. Para obter mais informações sobre por que esses comandos devem ser executados, consulte [IIS serviço hospedado não](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752252(v=vs.90)).  
  
    > [!WARNING]
    >  Se o IIS for reinstalado, os comandos a seguir precisará ser executado novamente.

    ```
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r
    ```

    > [!WARNING]
    >  Executar o comando `aspnet_regiis –i –enable` fará o Pool de aplicativos padrão execução usando [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], que pode gerar problemas de incompatibilidade para outros aplicativos no mesmo computador.  
  
5. Siga as [instruções do Firewall](../../../../docs/framework/wcf/samples/firewall-instructions.md) para habilitar as portas usadas pelos exemplos.  
  
6. Verifique o seguinte diretório padrão: \<InstallDrive>:**\WF_WCF_Samples**. Se os exemplos foram instalados anteriormente, isso é o diretório padrão.  
  
7. Se os exemplos não são instalados, instalá-los do local de download de exemplos [Visual c#](https://go.microsoft.com/fwlink/?LinkId=190939) ou [Visual Basic](https://go.microsoft.com/fwlink/?LinkID=193373).  
  
8. Depois de instalar os exemplos, vá para: \<InstallDrive>:**\WF_WCF_Samples\WCF\Setup\\**  
  
9. Execute o **Setupvroot.bat** arquivo em lotes. As etapas a seguir são executadas:  
  
    - Um diretório virtual é criado em IIS chamado ServiceModelSamples.  
  
    - Novos diretórios de disco são criados %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples nomeado e % SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin.  
  
     Se você preferir configurar esses diretórios manualmente, consulte o [instruções de configuração de diretório Virtual](../../../../docs/framework/wcf/samples/virtual-directory-setup-instructions.md). Para reverter todas as alterações feitas nesta etapa, execute cleanupvroot.bat depois de terminar de usar os exemplos.  
  
    > [!NOTE]
    >  Esse procedimento deve ser executado apenas uma vez em um computador, a menos que cleanupvroot.bat é executado.

10. Você deve conceder permissão para modificar para %SystemDrive%\inetpub\wwwroot para a conta sob a qual você está compilando os exemplos e o usuário do serviço de rede. Durante a compilação, alguns exemplos hospedados na Web podem tentar copiar os binários compilados para o local mencionado anteriormente, e se você não tiver definido as permissões apropriadas, o build será interrompido. Como alternativa, você pode deixar as permissões que são e executar o prompt de comando do SDK ou o Prompt de comando do Visual Studio (2012) como administrador, ou criar os exemplos no Visual Studio 2012, também executar como administrador.

    > [!NOTE]
    >  Se essa etapa não for concluída, todos os exemplos hospedados no IIS falhará durante a compilação. Certifique-se de que você defina as permissões corretamente ou executar o prompt de comando do SDK e o Prompt de comando do Visual Studio (2012) como administrador.

11. Criar um diretório c:\Logs. no computador. Alguns exemplos podem ser esperando por eles. Certifique-se de que a conta apropriada tem acesso de gravação concedido a essa pasta. Para o Windows 7, [!INCLUDE[wv](../../../../includes/wv-md.md)], e Windows Server 2008 R2, essa conta seja **serviço de rede**. Para [!INCLUDE[lserver](../../../../includes/lserver-md.md)], a conta é NT Authority\Network Service. Para [!INCLUDE[wxp](../../../../includes/wxp-md.md)] e [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], a conta é ASPNET.

12. Execute o arquivo Setupcerttool.bat. Esse arquivo está localizado no \<InstallPath > pasta \WF_WCF_Samples\WCF\Setup\.  Esse script executará as seguintes tarefas:

    - Compile a ferramenta de FindPrivateKey.

    - Crie um diretório chamado % ProgramFiles%\ServiceModelSampleTools.

    - Copie a nova ferramenta FindPrivateKey neste diretório.

     Essa ferramenta é necessária para exemplos que usam certificados e são hospedados no IIS.

    > [!NOTE]
    >  Para fins de segurança, lembre-se de remover a definição do diretório virtual e as permissões concedidas nas etapas de configuração acima, executando o arquivo em lotes chamado Cleanupvroot.bat depois de terminar de usar os exemplos.

13. Exemplos que são hospedados internamente (não é hospedados no IIS) exigem a permissão para registrar endereços HTTP no computador para escuta. A permissão para uma reserva de namespace HTTP vem de conta de usuário usada para executar o exemplo. Por padrão, as contas de administrador têm permissão para registrar qualquer endereço HTTP. Contas de administrador não devem ter a permissão para os namespaces HTTP utilizados pelos exemplos. Para obter mais informações sobre como configurar reservas de namespace, confira [Configurando HTTP e HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).

14. Alguns exemplos exigem que o enfileiramento de mensagens. Ver [instalar o enfileiramento de mensagens (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md) para instruções de instalação.

    > [!NOTE]
    >  Certifique-se de que você iniciar o serviço MSMQ, antes de executar qualquer exemplos que exigem o enfileiramento de mensagens.

15. Alguns exemplos exigem certificados. Ver [instruções de instalação de certificado de servidor (IIS) do Internet Information Services](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).
