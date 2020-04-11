---
title: Procedimento de configuração único para exemplos do Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
ms.openlocfilehash: 954ec04d2ef1ca7667b4f75a8a6652010b5dbd33
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121625"
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a>Procedimento de configuração único para exemplos do Windows Communication Foundation

A maioria das amostras da Windows Communication Foundation (WCF) estão hospedadas no Internet Information Services (IIS) e são executadas a partir de um diretório virtual comum. Este procedimento de configuração única cria uma pasta no disco; também adiciona um diretório virtual ao IIS chamado **ServiceModelSamples**.

O diretório virtual **ServiceModelSamples** é usado para construir e executar todas as amostras que usam um serviço hospedado no IIS. Este é o único diretório virtual necessário para executar as amostras. A construção de uma amostra substituirá qualquer serviço implantado anteriormente neste diretório virtual; apenas a amostra mais recente construída será implantada e disponível neste diretório virtual.

> [!NOTE]
> Você deve executar todos os comandos sob uma conta de administrador local. Se você estiver usando o Windows 7, Windows Vista ou Windows Server 2008 R2, você também deve executar o prompt de comando com privilégios elevados. Para isso, clique com o botão direito do mouse no ícone de solicitação de comando e clique **em Executar como administrador**. Todos os comandos neste tópico devem ser executados em um prompt de comando que tenha as configurações de caminho apropriadas.  A maneira mais fácil de garantir isso é usando o Prompt de comando do Visual Studio. Para abrir este prompt, clique em **Iniciar**, selecione **Todos os programas,** role até **o Visual Studio 2010,** selecione **Visual Studio Tools,** clique com o botão de **comando do Visual Studio (2010)** e clique em **Executar como administrador**. Se você tiver uma das edições do Visual Studio Express instaladas, este prompt de comando não estará disponível e você terá que adicionar "C:\Windows\Microsoft.Net\Framework\v4.0" ao caminho do sistema.

### <a name="one-time-setup-procedure-for-wcf-samples"></a>Procedimento de configuração único para amostras wcf

1. Certifique-se de que ASP.NET esteja configurado. Para obter mais informações sobre como configurar ASP.NET, consulte [Instruções de hospedagem do Serviço de Informações da Internet](internet-information-service-hosting-instructions.md).

2. Certifique-se de que o .NET Framework 4 esteja instalado. Pesquise o seguinte diretório para v4.0 (ou posterior): **\Windows\Microsoft.NET\Framework**

3. Certifique-se de ter o Visual Studio 2012 ou posterior instalado, ou seu sistema operacional é o Windows Server 2008 SP2 ou posterior.

4. Execute os seguintes comandos: Para obter mais informações sobre por que esses comandos devem ser executados, consulte [Falhas de serviço hospedadas no IIS](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752252(v=vs.90)).

    > [!WARNING]
    > Se o IIS for reinstalado, os seguintes comandos precisarão ser executados novamente.

    ```console
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r
    ```

    > [!WARNING]
    > A execução do comando `aspnet_regiis –i –enable` fará com que o Pool de aplicativos padrão seja executado usando o .NET Framework 4, o que pode produzir problemas de incompatibilidade para outros aplicativos no mesmo computador.

5. Siga as [Instruções](firewall-instructions.md) de Firewall para habilitar as portas usadas pelas amostras.

6. Verifique o seguinte diretório \<padrão: InstallDrive>:**\WF_WCF_Samples**. Se as amostras foram previamente instaladas, este é o diretório padrão.

7. Se as amostras não estiverem instaladas, instale-as no [Windows Communication Foundation (WCF) e na Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).

8. Depois de instalar as amostras, vá para : \<InstallDrive>:**\WF_WCF_Samples\WCF\Configuração\\ **

9. Execute o arquivo de lote **Setupvroot.bat.** As seguintes etapas são executadas:

    - Um diretório virtual é criado no IIS chamado ServiceModelSamples.

    - Novos diretórios de disco são criados chamados %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples e %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin.

    Se preferir configurar esses diretórios manualmente, consulte as [Instruções de configuração do diretório virtual](virtual-directory-setup-instructions.md). Para reverter todas as alterações feitas nesta etapa, execute cleanupvroot.bat depois de terminar de usar as amostras.

    > [!NOTE]
    > Este procedimento deve ser realizado apenas uma vez em um computador, a menos que cleanupvroot.bat seja executado.

10. Você deve conceder permissão para modificar para %SystemDrive%\inetpub\wwwroot para a conta em que você está construindo as amostras e o usuário do Serviço de Rede. Durante a construção, algumas amostras hospedadas na Web podem tentar copiar os binários compilados para o local mencionado anteriormente e, se você não tiver definido as permissões apropriadas, a compilação será rompida. Alternativamente, você pode deixar as permissões como elas são e executar o prompt de comando SDK ou Visual Studio Command Prompt (2012) como Administrador, ou construir as amostras no Visual Studio 2012, também executado como Administrador.

    > [!NOTE]
    > Se esta etapa não for concluída, todas as amostras hospedadas pelo IIS falharão durante a construção. Certifique-se de definir as permissões corretamente ou executar o prompt de comando SDK e o Visual Studio Command Prompt (2012) como Administrador.

11. Criar um diretório C:\logs no computador; algumas amostras podem estar esperando por isso. Certifique-se de que a conta apropriada tenha acesso à gravação concedido a esta pasta. Para windows 7, Windows Vista e Windows Server 2008 R2, esta conta é **Network Service**. Para o Windows Server 2008, a conta é NT Authority\Network Service. Para Windows XP e Windows Server 2003, a conta é ASPNET.

12. Execute o arquivo Setupcerttool.bat. Este arquivo está localizado \<na pasta InstallPath>\WF_WCF_Samples\WCF\Setup\\\.  Este script executará as seguintes tarefas:

    - Construa a ferramenta FindPrivateKey.

    - Crie um diretório chamado %ProgramFiles%\ServiceModelSampleTools.

    - Copie a nova ferramenta FindPrivateKey para este diretório.

    Esta ferramenta é exigida por amostras que usam certificados e estão hospedadas no IIS.

    > [!NOTE]
    > Para efeitos de segurança, lembre-se de remover a definição de diretório virtual e as permissões concedidas nas etapas de configuração acima, executando o arquivo em lote chamado Cleanupvroot.bat depois que você terminar com as amostras.

13. As amostras autohospedadas (não hospedadas no IIS) exigem permissão para registrar endereços HTTP no computador para ouvir. A permissão para uma reserva http namespace vem da conta de usuário usada para executar a amostra. Por padrão, as contas do administrador têm a permissão para registrar qualquer endereço HTTP. Contas não administradoras devem ser concedidas permissão para os namespaces HTTP usados pelas amostras. Para obter mais informações sobre como configurar reservas de namespace, confira [Configurando HTTP e HTTPS](../feature-details/configuring-http-and-https.md).

14. Algumas amostras requerem fila de mensagens. Consulte [Instalando a fila de mensagens (MSMQ)](installing-message-queuing-msmq.md) para obter instruções de instalação.

    > [!NOTE]
    > Certifique-se de iniciar o serviço MSMQ antes de executar quaisquer amostras que exijam fila de mensagens.

15. Algumas amostras exigem certificados. Consulte as instruções de instalação do certificado de instalação do Certificado de Uso [da Internet (IIS).](iis-server-certificate-installation-instructions.md)
