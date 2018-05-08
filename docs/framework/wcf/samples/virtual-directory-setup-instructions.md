---
title: Instruções de definição de diretório virtual
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: a6fc8309563e78f919fe1e2009c1f46801c32913
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="virtual-directory-setup-instructions"></a>Instruções de definição de diretório virtual
Os exemplos do Windows Communication Foundation (WCF) devem compartilhar um diretório virtual comum denominado servicemodelsamples que é mapeada para a pasta %SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
> [!NOTE]
>  % SystemDrive % normalmente é c: ou d:., dependendo do local de unidade em que os serviços de informações da Internet (IIS) está instalado.  
  
 Você pode executar os arquivos de Setupvroot.bat e Cleanupvroot.bat o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) para criar o diretório virtual. Se você preferir criar o diretório virtual manualmente, use os procedimentos a seguir.  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a>Para criar um diretório virtual no IIS 7.0 ou 7.5  
  
1.  Do **iniciar** menu, clique em **executar**, em seguida, digite **inetmgr** para abrir o snap-in MMC de serviços de informações da Internet (IIS).  
  
2.  No painel esquerdo, expanda o nó com o nome do computador e, em seguida, expanda o **Sites** nó.  
  
3.  Clique com botão direito **Default Web Site**e, em seguida, selecione **Adicionar aplicativo** para abrir o **janela Adicionar aplicativo**.  
  
4.  Na janela, digite `servicemodelsamples` como o alias do diretório virtual que você está criando.  
  
5.  Crie o seguinte diretório: %SystemDrive%\inetpub\wwwroot\servicemodelsamples  
  
6.  Defina o caminho físico para % SystemDrive%\inetpub\wwwroot\servicemodelsamples.  A maioria dos exemplos do WCF copia arquivos executáveis de serviço para esse local quando compilado.  
  
7.  Clique em **OK**. O aplicativo Web é criado para os exemplos do WCF.  
  
    > [!NOTE]
    >  Essa tarefa deve ser executada apenas uma vez, porque todos os [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] exemplos usam o mesmo servicemodelsamples aplicativo Web.  
  
    > [!NOTE]
    >  Para fins desta documentação, o termo `virtual directory` é sinônimo de `Web application`.  
  
     Além de criar o diretório virtual, você também deve definir as propriedades para habilitar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços para serem executados. Veja mais detalhes a seguir.  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a>Para criar um diretório virtual no IIS 5.1 ou 6.0  
  
1.  Abra uma janela de prompt de comando e digite `start inetmgr` para abrir o snap-in MMC de serviços de informações da Internet (IIS).  
  
2.  No painel esquerdo, expanda o nó com o nome do computador e, em seguida, expanda o **Sites da Web** nó.  
  
3.  Clique com botão direito **Default Web Site** e selecione **novo, o diretório Virtual** para abrir o Assistente de criação de diretório Virtual.  
  
4.  No assistente, digite `servicemodelsamples` como o alias do diretório virtual que você está criando.  
  
5.  Defina o caminho % SystemDrive%\inetpub\wwwroot\servicemodelsamples. A maioria do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] exemplos copiar arquivos executáveis de serviço para esse local quando compilado.  
  
6.  Clique em **Avançar**.  
  
7.  Por padrão, as seguintes caixas de seleção são selecionadas:  
  
    -   **Leitura**  
  
    -   **Executar scripts (como ASP)**  
  
8.  Clique em **próximo**e, em seguida, clique em **concluir** para concluir o assistente.  
  
    > [!NOTE]
    >  Essa tarefa deve ser executada apenas uma vez, porque todos os [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] exemplos usam o mesmo diretório virtual servicemodelsamples.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a>Para definir propriedades adicionais de diretório virtual no IIS 7.0 ou 7.5  
  
1.  Clique no nó servicemodelsamples. Na parte inferior da janela, duas exibições são listadas. Selecione **exibição de recursos** se ainda não estiver selecionada.  
  
2.  Clique duas vezes na entrada de **pesquisa no diretório**.  
  
3.  No painel Ações, selecione o **habilitar** opção. Isso permite que você acesse o diretório do diretório usando o Internet Explorer, que é útil quando a depuração de um serviço.  
  
 Por fim, você deve definir as propriedades de segurança da pasta servicemodelsamples para permitir que ele seja acessado por outras pessoas. Veja mais detalhes a seguir.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a>Para definir propriedades adicionais de diretório virtual no IIS 5.1 ou 6.0  
  
1.  Com o botão direito no nó servicemodelsamples e, em seguida, clique em **propriedades**.  
  
2.  Por padrão, as seguintes caixas de seleção são selecionadas:  
  
    -   **Leitura**  
  
    -   **Criar log de visitantes**  
  
    -   **Indexar este recurso**  
  
3.  Selecione o **pesquisa no diretório** caixa de seleção. Isso permite que você acesse o diretório do diretório usando o Internet Explorer, que é útil quando a depuração de um serviço.  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a>Para definir propriedades de segurança da pasta no IIS 7.0 ou 7.5  
  
1.  Navegue até % SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
2.  Clique na pasta servicemodelsamples e clique em **compartilhamento** ou **compartilhamento com**.  
  
3.  Clique na seta para baixo à esquerda do **adicionar** botão.  
  
4.  Selecione o **localizar** entrada. O **selecionar usuários ou grupos** janela será aberta.  
  
5.  Clique em **Avançadas**.  
  
6.  Clique em **locais**. O **locais** janela agora está aberta.  
  
7.  Selecione a entrada para o computador que está sendo usado. É importante selecionar o computador local e não uma entrada para qualquer domínios ou redes que estão listadas. Depois de selecionar o computador, clique em **Okey**.  
  
8.  Clique em **Localizar agora**. Isso preenche os resultados da pesquisa com os objetos associados ao computador local.  
  
9. Localizar o **IIS_IUSRS** entrada o **nome (nome distinto relativo)** coluna. Selecione a entrada e clique em **Okey** fechar a pesquisa de janela de resultados.  
  
10. Clique em **Okey** para fechar o **selecionar usuários ou grupos** janela.  
  
11. Clique em **compartilhamento** para manter as alterações.  
  
12. Depois que as alterações para permitir o compartilhamento forem concluídas, clique em **feito** para fechar o **compartilhamento de arquivos** janela.  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a>Para definir propriedades de segurança da pasta no IIS 5.1 ou 6.0  
  
1.  Navegue até % SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
2.  Clique com botão direito do **servicemodelsamples** pasta e clique **compartilhamento e segurança.**  
  
3.  Clique na guia **Segurança**.  
  
4.  Se você estiver usando o IIS 6.0 no **nomes de grupo ou usuário** caixa de seleção se **conta de convidado da Internet** está listado.  
  
     Se não estiver listado:  
  
    1.  Clique em **iniciar** e, em seguida, clique em **painel de controle**.  
  
    2.  Se você não vir o **contas de usuário** ícone, clique em **alternar para modo de exibição de categoria**.  
  
    3.  Clique o **contas de usuário** ícone.  
  
    4.  Em "ou um ícone do painel de controle," clique **contas de usuário**.  
  
    5.  No **contas de usuário** caixa de diálogo, clique o **avançado** guia.  
  
    6.  Clique em **Avançadas**.  
  
    7.  No **usuários e grupos locais** caixa de diálogo, clique para expandir o **usuários** pasta.  
  
    8.  No painel direito, clique duas vezes em **conta de convidado da Internet**.  
  
    9. No **propriedades** caixa de diálogo, copie o nome usado como a conta de convidado da Internet. Por padrão, o nome começa com "USR_" seguido do nome do computador.  
  
    10. Feche a caixa de diálogo **Propriedades** .  
  
    11. Fechar o **usuários e grupos locais** caixa de diálogo.  
  
    12. Fechar o **contas de usuário** caixa de diálogo.  
  
    13. Feche o outro **contas de usuário** caixa de diálogo.  
  
    14. No **servicemodelsamples propriedades** caixa de diálogo de **segurança** , clique em **adicionar**.  
  
    15. Digite o nome do computador seguido por uma barra invertida e, em seguida, cole o nome da conta de usuário de Internet, por exemplo, myMachineName\\InternetGuestAccountName %  
  
    16. Clique em **verificar nomes** para verificar a adição. Se ele for válido, o nome está em letras maiusculas e está sublinhado.  
  
5.  Para o IIS 6.0, verifique também se o serviço de rede está listado no **nomes de grupo ou usuário** caixa.  
  
     Se o serviço de rede não estiver listado:  
  
    1.  Clique em **Adicionar**.  
  
    2.  No **selecionar usuários ou grupos** caixa de diálogo, digite o nome do computador seguido por uma barra invertida.  
  
    3.  Tipo **serviço** após a barra invertida (sem espaço).  
  
    4.  Clique em **verificar nomes**.  
  
    5.  Se forem localizados vários nomes, selecione **serviço de rede** e clique em **Okey**.  
  
    6.  Clique em **Okey** para fechar o **selecionar usuários ou grupos** caixa de diálogo.  
  
6.  Se você estiver usando o Windows XP SP2 com o IIS 5.1, verifique se a conta de convidado da Internet e ASPNET estão listados no **nomes de grupo ou usuário** caixa.  
  
     Observe que o usuário ASPNET pode ser um membro de interno **usuários** grupo de segurança. Nesse caso, se, em seguida, o **usuários** grupo está listado na caixa de diálogo, você não precisa adicioná-lo como um item separado para a lista de usuários autorizados.  
  
     Para verificar se ASPNET faz parte do **usuários** grupo de segurança:  
  
    1.  Sobre o **iniciar** menu, clique em **painel de controle**.  
  
    2.  Clique o **contas de usuário** ícone.  
  
    3.  No **grupo** coluna, verifique se o valor de **ASPNET** for "Users".  
  
## <a name="see-also"></a>Consulte também  
 [Instruções de hospedagem do Serviços de Informações da Internet](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
