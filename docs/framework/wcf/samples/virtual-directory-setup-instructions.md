---
title: Instruções de definição de diretório virtual
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: a30adb45883ad0803986a237e9ec1967d7f55ca8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624222"
---
# <a name="virtual-directory-setup-instructions"></a>Instruções de definição de diretório virtual
Os exemplos do Windows Communication Foundation (WCF) destinam-se para compartilhar um diretório virtual comum chamado servicemodelsamples que é mapeado para a pasta %SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
> [!NOTE]
>  % SystemDrive % geralmente é c: ou a unidade d:, dependendo do local da unidade em que os serviços de informações da Internet (IIS) está instalado.  
  
 Você pode executar os arquivos Setupvroot.bat e Cleanupvroot.bat a [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) para criar o diretório virtual. Se você preferir criar o diretório virtual manualmente, use os procedimentos a seguir.  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a>Para criar um diretório virtual no IIS 7.0 ou 7.5  
  
1. Do **iniciar** menu, clique em **execute**, em seguida, digite **inetmgr** para abrir o snap-in MMC de serviços de informações da Internet (IIS).  
  
2. No painel esquerdo, expanda o nó com o nome do computador e, em seguida, expanda o **Sites** nó.  
  
3. Clique com botão direito **Site padrão**e, em seguida, selecione **Adicionar aplicativo** para abrir o **janela Adicionar aplicativo**.  
  
4. Na janela, digite `servicemodelsamples` como o alias para o diretório virtual que você está criando.  
  
5. Crie o seguinte diretório: %SystemDrive%\inetpub\wwwroot\servicemodelsamples  
  
6. Defina o caminho físico para % SystemDrive%\inetpub\wwwroot\servicemodelsamples.  A maioria dos exemplos do WCF copia arquivos executáveis de serviço para esse local quando compilado.  
  
7. Clique em **OK**. Agora, o aplicativo Web é criado para os exemplos do WCF.  
  
    > [!NOTE]
    >  Essa tarefa deve ser executada apenas uma vez, porque todas as amostras do WCF usam a mesma servicemodelsamples aplicativo da Web.  
  
    > [!NOTE]
    >  Para fins desta documentação, o termo `virtual directory` é sinônimo de `Web application`.  
  
     Além de criar o diretório virtual, você também deve definir suas propriedades para habilitar os serviços do WCF para serem executados. Veja mais detalhes a seguir.  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a>Para criar um diretório virtual no IIS 5.1 ou 6.0  
  
1. Abra uma janela de prompt de comando e digite `start inetmgr` para abrir o snap-in MMC de serviços de informações da Internet (IIS).  
  
2. No painel esquerdo, expanda o nó com o nome do computador e, em seguida, expanda o **Sites da Web** nó.  
  
3. Clique com botão direito **Site padrão** e selecione **novos, o diretório Virtual** para abrir o Assistente de criação de diretório Virtual.  
  
4. No assistente, digite `servicemodelsamples` como o alias para o diretório virtual que você está criando.  
  
5. Defina o caminho para % SystemDrive%\inetpub\wwwroot\servicemodelsamples. A maioria dos exemplos do WCF copia arquivos executáveis de serviço para esse local quando compilado.  
  
6. Clique em **Avançar**.  
  
7. Por padrão, as caixas de seleção a seguir são selecionadas:  
  
    - **Ler**  
  
    - **Executar scripts (ASP, por exemplo)**  
  
8. Clique em **próxima**e, em seguida, clique em **concluir** para concluir o assistente.  
  
    > [!NOTE]
    >  Essa tarefa deve ser executada apenas uma vez porque todos os exemplos de WCF usam o mesmo diretório virtual servicemodelsamples.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a>Para definir propriedades adicionais de diretório virtual no IIS 7.0 ou 7.5  
  
1. Clique no nó servicemodelsamples. Na parte inferior da janela, duas exibições são listadas. Selecione **exibição de recursos** se ainda não estiver selecionado.  
  
2. Clique duas vezes na entrada de **pesquisa no diretório**.  
  
3. No painel de ações, selecione a **habilitar** opção. Isso permite que você acesse o diretório do diretório usando o Internet Explorer, que é útil quando a depuração de um serviço.  
  
 Por fim, você deve definir as propriedades de segurança da pasta servicemodelsamples para permitir que ela seja acessada por outras pessoas. Veja mais detalhes a seguir.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a>Para definir propriedades adicionais de diretório virtual no IIS 5.1 ou 6.0  
  
1. Clique com botão direito no nó servicemodelsamples e, em seguida, clique em **propriedades**.  
  
2. Por padrão, as caixas de seleção a seguir são selecionadas:  
  
    - **Ler**  
  
    - **Criar log de visitantes**  
  
    - **Indexar este recurso**  
  
3. Selecione o **pesquisa no diretório** caixa de seleção. Isso permite que você acesse o diretório do diretório usando o Internet Explorer, que é útil quando a depuração de um serviço.  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a>Para definir propriedades de segurança da pasta no IIS 7.0 ou 7.5  
  
1. Navegue até % SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
2. Clique com botão direito na pasta servicemodelsamples e clique em **compartilhamento** ou **compartilhamento com**.  
  
3. Clique na seta para baixo à esquerda do **adicionar** botão.  
  
4. Selecione o **localizar** entrada. O **selecionar usuários ou grupos** janela é aberta.  
  
5. Clique em **Avançadas**.  
  
6. Clique em **locais**. O **locais** janela agora está aberta.  
  
7. Selecione a entrada para o computador que está sendo usado. É importante selecionar o computador local e não uma entrada para domínios ou redes que estão listados. Depois de selecionar o computador, clique em **Okey**.  
  
8. Clique em **Localizar agora**. Isso preenche os resultados da pesquisa com os objetos associados ao computador local.  
  
9. Localizar o **IIS_IUSRS** entrada na **nome (nome distinto relativo)** coluna. Selecione essa entrada e clique em **Okey** fechar a pesquisa de janela de resultados.  
  
10. Clique em **Okey** para fechar o **selecionar usuários ou grupos** janela.  
  
11. Clique em **compartilhamento** para manter as alterações.  
  
12. Depois de concluir as alterações para habilitar o compartilhamento, clique em **feito** para fechar o **compartilhamento de arquivos** janela.  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a>Para definir propriedades de segurança da pasta no IIS 5.1 ou 6.0  
  
1. Navegue até % SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
2. Clique com botão direito do **servicemodelsamples** pasta e clique **compartilhamento e segurança.**  
  
3. Clique na guia **Segurança**.  
  
4. Se você estiver usando o IIS 6.0, nos **nomes de usuário ou grupo** caixa de seleção se **conta-convidado da Internet** está listado.  
  
     Se não estiver listado:  
  
    1. Clique em **Iniciar** e em **Painel de Controle**.  
  
    2. Se você não vir as **contas de usuário** ícone, clique em **alterne para modo de exibição de categoria**.  
  
    3. Clique o **contas de usuário** ícone.  
  
    4. Em "ou um ícone do painel de controle," clique em **contas de usuário**.  
  
    5. No **contas de usuário** caixa de diálogo, clique o **avançado** guia.  
  
    6. Clique em **Avançadas**.  
  
    7. No **usuários e grupos locais** caixa de diálogo, clique para expandir a **usuários** pasta.  
  
    8. No painel direito, clique duas vezes **conta-convidado da Internet**.  
  
    9. No **propriedades** caixa de diálogo, copie o nome usado como a conta de convidado da Internet. Por padrão, o nome começa com "USR_" seguido do nome do computador.  
  
    10. Feche a caixa de diálogo **Propriedades** .  
  
    11. Fechar o **usuários e grupos locais** caixa de diálogo.  
  
    12. Fechar o **contas de usuário** caixa de diálogo.  
  
    13. Feche a outra **contas de usuário** caixa de diálogo.  
  
    14. No **servicemodelsamples propriedades** caixa de diálogo do **segurança** , clique em **adicionar**.  
  
    15. Digite o nome do computador seguido por uma barra invertida e, em seguida, cole o nome da conta de usuário da Internet, por exemplo, myMachineName\\% InternetGuestAccountName %  
  
    16. Clique em **verificar nomes** para verificar a adição. Se ele for válido, o nome está em letras maiusculas e é sublinhado.  
  
5. Para o IIS 6.0, também Verifique se o serviço de rede está listado na **nomes de grupo ou usuário** caixa.  
  
     Se o serviço de rede não estiver listado:  
  
    1.  Clique em **Adicionar**.  
  
    2. No **selecionar usuários ou grupos** caixa de diálogo, digite o nome do computador seguido por uma barra invertida.  
  
    3. Tipo de **serviço** após a barra invertida (sem espaço).  
  
    4. Clique em **verificar nomes**.  
  
    5. Se forem localizados vários nomes, selecione **serviço de rede** e clique em **Okey**.  
  
    6. Clique em **Okey** para fechar o **selecionar usuários ou grupos** caixa de diálogo.  
  
6. Se você estiver usando o Windows XP SP2 com o IIS 5.1, verifique se a conta de convidado da Internet e ASPNET estão listados na **nomes de grupo ou usuário** caixa.  
  
     Observe que o usuário ASPNET pode ser um membro do internos **usuários** grupo de segurança. Nesse caso, então, se o **usuários** grupo está listado na caixa de diálogo, você não precisa adicioná-lo como um item separado à lista de usuários permitidos.  
  
     Para verificar se ASPNET faz parte dos **usuários** grupo de segurança:  
  
    1. Sobre o **inicie** menu, clique em **painel de controle**.  
  
    2. Clique o **contas de usuário** ícone.  
  
    3. No **grupo** coluna, verifique se o valor para **ASPNET** for "Users".  
  
## <a name="see-also"></a>Consulte também

- [Instruções de hospedagem do Serviços de Informações da Internet](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
